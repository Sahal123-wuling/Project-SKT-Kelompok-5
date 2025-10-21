
# Proyek SKT Kelompok 5: “Edge Gateway & Cloud Integration Project using DWSIM, Influx DB and Thinksboard in Hydroponic/Houseplant Factory”

Repositori ini berisi implementasi perangkat keras dan lunak lengkap untuk tugas mata kuliah **Sistem Kontrol Terdistribusi (SKT)** di Departemen Teknik Instrumentasi, Institut Teknologi Sepuluh Nopember (ITS).

Proyek ini dikerjakan oleh **Kelompok 5**:
* Muhammad Sahal Rajendra
* Muhammad Rif'al Faiz Arivito


---

## Tampilan Dashboard Monitoring (ThingsBoard)

![Gambar WhatsApp 2025-10-21 pukul 21 01 33_369fbf27](https://github.com/user-attachments/assets/234c91a9-a7ee-480e-aa6b-06f0a1549bac)

## Tampilan DWSIM
![Gambar WhatsApp 2025-10-21 pukul 23 29 31_8f27e402](https://github.com/user-attachments/assets/c95e1099-c837-4f3e-bbfb-2e246cf57a88)
![Gambar WhatsApp 2025-10-21 pukul 23 29 56_0ff6403e](https://github.com/user-attachments/assets/52137812-3b85-4b7d-89c1-3c8d4ccbee6e)

## Tampilan InfluxDB
![Gambar WhatsApp 2025-10-21 pukul 23 44 08_5b5a812c](https://github.com/user-attachments/assets/acfd0de2-152e-4b09-8631-6cef242bd72b)
![Gambar WhatsApp 2025-10-21 pukul 23 44 13_8445d824](https://github.com/user-attachments/assets/a6c8e592-943e-4404-997c-ea6d5b5d45c9)


## Ringkasan Proyek

Sistem ini dirancang untuk mengelola kualitas udara dalam sebuah ruangan secara otomatis. Proses ini dilakukan dengan memonitor data suhu (temperature) dan kelembapan (humidity) secara *real-time*.

Berdasarkan *setpoint* yang telah ditentukan, sistem akan mengendalikan dua aktuator:
1.  **Servo Motor:** Untuk mengatur bukaan *damper* (saluran udara).
2.  **Relay:** Untuk mengaktifkan/menonaktifkan *exhaust fan*.

## Arsitektur Teknologi

Inti dari sistem ini adalah mikrokontroler **ESP32-S3**. Keunikan proyek ini adalah firmware-nya yang tidak ditulis dalam C++/Arduino, melainkan dibangun sepenuhnya menggunakan bahasa pemrograman **Rust**, yang dikenal karena keamanan memori dan performanya.

Data telemetri dari sistem dikirim ke dua platform cloud:
1.  **ThingsBoard:** Digunakan untuk visualisasi, monitoring operasional, dan kontrol *real-time*.
2.  **InfluxDB:** Berfungsi sebagai *database time-series* untuk pencatatan dan analisis data historis.

## Fitur Teknis Utama

* **Sensor Industrial:** Menggunakan sensor suhu & kelembapan **SHT20**.
* **Komunikasi Modbus RTU:** Komunikasi antara sensor SHT20 dan ESP32 menggunakan protokol Modbus RTU melalui antarmuka **RS485**, yang menjamin keandalan data dan ketahanan terhadap *noise* (gangguan) di lingkungan industri.
* **Kontroler Modern:** Implementasi pada ESP32-S3 dengan firmware berbasis Rust.
* **Visualisasi Data Cloud:** Terintegrasi penuh dengan dashboard ThingsBoard untuk pemantauan jarak jauh.
* **Pencatatan Data Historis:** Data secara otomatis dicatat ke InfluxDB untuk analisis tren jangka panjang.

## Isi Repositori
* DWSIM
import xml.etree.ElementTree as ET
import os
import time
import threading
import customtkinter as ctk
from tkinter import filedialog, messagebox
from influxdb_client import InfluxDBClient, Point
from influxdb_client.client.write_api import SYNCHRONOUS
import matplotlib.pyplot as plt
from matplotlib.backends.backend_tkagg import FigureCanvasTkAgg

# --- KONFIGURASI INFLUXDB CLOUD ---
INFLUXDB_URL = "https://us-east-1-1.aws.cloud2.influxdata.com"
INFLUXDB_TOKEN = "4iveQHlkSl7m-EArzJZKxVLXB5G9FP21VTcbujdk_pfm7NHBGel2DZDECdLt-LLNtTMvQXFI1qlx2clomBSeOw=="
INFLUXDB_ORG = "skt"
INFLUXDB_BUCKET = "skt1"

running = False  # Flag loop pengiriman

# --- FUNGSI LOGIKA ---
def extract_temperatures_from_xml(file_path):
    """
    Membaca file XML DWSIM dan mengembalikan dictionary stream_name: temperature(°C)
    """
    temperatures = {}
    try:
        tree = ET.parse(file_path)
        root = tree.getroot()

        # Pemetaan ID stream ke tag
        stream_tags = {}
        for graphic_object in root.findall(".//GraphicObject[ObjectType='MaterialStream']"):
            stream_id = graphic_object.find('Name').text
            stream_tag = graphic_object.find('Tag').text
            if stream_id and stream_tag:
                stream_tags[stream_id] = stream_tag

        # Ambil temperatur
        for sim_object in root.findall(".//SimulationObject[Type='DWSIM.Thermodynamics.Streams.MaterialStream']"):
            stream_id = sim_object.find('Name').text
            if stream_id in stream_tags:
                temp_kelvin_element = sim_object.find(".//Phase[ComponentName='Mixture']/Properties/temperature")
                if temp_kelvin_element is not None:
                    temp_kelvin = float(temp_kelvin_element.text)
                    temp_celsius = temp_kelvin - 273.15
                    stream_name = stream_tags[stream_id]
                    temperatures[stream_name] = temp_celsius

        return temperatures

    except Exception as e:
        messagebox.showerror("Error", f"Gagal membaca XML: {e}")
        return None


def send_to_influxdb(client, data):
    """
    Mengirim data temperatur ke InfluxDB Cloud
    """
    try:
        write_api = client.write_api(write_options=SYNCHRONOUS)
        points = []
        for stream_name, temp_celsius in data.items():
            point = (
                Point("heat_exchanger_monitoring")
                .tag("stream_name", stream_name)
                .field("temperature_celsius", float(f"{temp_celsius:.2f}"))
            )
            points.append(point)

        write_api.write(bucket=INFLUXDB_BUCKET, org=INFLUXDB_ORG, record=points)
        return True
    except Exception as e:
        messagebox.showerror("Error", f"Gagal mengirim ke InfluxDB Cloud: {e}")
        return False


# --- FUNGSI UI ---
def browse_file():
    file_path = filedialog.askopenfilename(filetypes=[("XML Files", "*.xml")])
    if file_path:
        xml_path_entry.delete(0, ctk.END)
        xml_path_entry.insert(0, file_path)


def start_monitoring():
    global running
    running = True
    start_button.configure(state="disabled")
    stop_button.configure(state="normal")
    thread = threading.Thread(target=monitor_loop)
    thread.daemon = True
    thread.start()


def stop_monitoring():
    global running
    running = False
    start_button.configure(state="normal")
    stop_button.configure(state="disabled")


def monitor_loop():
    global running

    file_path = xml_path_entry.get().strip()
    interval = int(interval_entry.get())

    if not os.path.exists(file_path):
        messagebox.showerror("Error", "File XML tidak ditemukan.")
        return

    client = InfluxDBClient(url=INFLUXDB_URL, token=INFLUXDB_TOKEN, org=INFLUXDB_ORG)

    while running:
        data = extract_temperatures_from_xml(file_path)
        if data:
            update_display(data)
            update_graph(data)
            success = send_to_influxdb(client, data)
            if success:
                status_label.configure(text=f"Data dikirim ke InfluxDB Cloud @ {time.strftime('%H:%M:%S')}", text_color="lightgreen")
        else:
            status_label.configure(text="Gagal membaca data dari XML.", text_color="red")

        for i in range(interval):
            if not running:
                break
            time.sleep(1)


def update_display(data):
    text_output.delete("1.0", ctk.END)
    for name, temp in data.items():
        text_output.insert(ctk.END, f"{name}: {temp:.2f} °C\n")


# --- GRAFIK ---
def update_graph(data):
    ax.clear()
    streams = list(data.keys())
    temps = list(data.values())

    colors = ["#5DADE2" if "Cold" in s else "#2874A6" if "Hot" in s else "#3498DB" for s in streams]
    ax.bar(streams, temps, color=colors)

    for i, v in enumerate(temps):
        ax.text(i, v + 0.5, f"{v:.1f}°C", ha='center', color='white', fontsize=10, fontweight='bold')

    ax.set_title("Grafik Temperatur Heat Exchanger", fontsize=13, color="white", fontweight="bold")
    ax.set_ylabel("Temperature (°C)", color="white")
    ax.set_ylim(min(temps) - 5, max(temps) + 10)
    ax.grid(True, linestyle="--", alpha=0.3)
    ax.tick_params(colors="white")
    canvas.draw()


# --- SETUP DASHBOARD ---
ctk.set_appearance_mode("dark")
ctk.set_default_color_theme("blue")

app = ctk.CTk()
app.title("Project SKT Kelompok 5")
app.geometry("900x720")

# Judul Utama
title_label = ctk.CTkLabel(
    app,
    text="💧 Project SKT Kelompok 5 💧",
    font=("Segoe UI", 22, "bold"),
    text_color="#5DADE2"
)
title_label.pack(pady=15)

# Frame utama
frame = ctk.CTkFrame(app, corner_radius=10, fg_color="#0d3b66")
frame.pack(padx=20, pady=10, fill="x")

# Path XML
ctk.CTkLabel(frame, text="Path File XML DWSIM:", text_color="white").pack(anchor="w")
xml_path_entry = ctk.CTkEntry(frame, width=500)
xml_path_entry.pack(side="left", padx=5, pady=5)
browse_btn = ctk.CTkButton(frame, text="Browse", command=browse_file, fg_color="#1f77b4")
browse_btn.pack(side="left", padx=5, pady=5)

# Interval
interval_frame = ctk.CTkFrame(app, fg_color="#0d3b66")
interval_frame.pack(pady=10)
ctk.CTkLabel(interval_frame, text="Interval Kirim (detik):", text_color="white").pack(side="left")
interval_entry = ctk.CTkEntry(interval_frame, width=60)
interval_entry.insert(0, "60")
interval_entry.pack(side="left", padx=5)

# Tombol kontrol
btn_frame = ctk.CTkFrame(app, fg_color="#0d3b66")
btn_frame.pack(pady=10)
start_button = ctk.CTkButton(btn_frame, text="Start", fg_color="#1E88E5", command=start_monitoring)
start_button.pack(side="left", padx=10)
stop_button = ctk.CTkButton(btn_frame, text="Stop", fg_color="#D32F2F", command=stop_monitoring, state="disabled")
stop_button.pack(side="left", padx=10)

# Output data
ctk.CTkLabel(app, text="Data Temperatur:", text_color="#AED6F1").pack(anchor="w", padx=20)
text_output = ctk.CTkTextbox(app, height=150)
text_output.pack(padx=20, pady=10, fill="x")

# Grafik
ctk.CTkLabel(app, text="Grafik Temperatur:", text_color="#AED6F1", font=("Segoe UI", 13, "bold")).pack(anchor="w", padx=20)
graph_frame = ctk.CTkFrame(app, corner_radius=10, fg_color="#0d3b66")
graph_frame.pack(padx=20, pady=10, fill="both", expand=True)

fig, ax = plt.subplots(figsize=(7, 4))
fig.patch.set_facecolor("#0d3b66")
ax.set_facecolor("#0d3b66")
ax.tick_params(colors="white")
ax.yaxis.label.set_color("white")
ax.xaxis.label.set_color("white")
ax.title.set_color("white")

canvas = FigureCanvasTkAgg(fig, master=graph_frame)
canvas.get_tk_widget().pack(fill="both", expand=True)

# Status
status_label = ctk.CTkLabel(app, text="Menunggu aksi...", text_color="#F7DC6F")
status_label.pack(pady=10)

# Jalankan
app.mainloop()
