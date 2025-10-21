
# Proyek SKT Kelompok 5: “Edge Gateway & Cloud Integration Project using DWSIM, Influx DB and Thinksboard in Hydroponic/Houseplant Factory”

Repositori ini berisi implementasi perangkat keras dan lunak lengkap untuk tugas mata kuliah **Sistem Kontrol Terdistribusi (SKT)** di Departemen Teknik Instrumentasi, Institut Teknologi Sepuluh Nopember (ITS).

Proyek ini dikerjakan oleh **Kelompok 5**:
* Muhammad Sahal Rajendra
* Muhammad Rif'al Faiz Arivito


---

## Tampilan Dashboard Monitoring (ThingsBoard)

![Gambar WhatsApp 2025-10-21 pukul 21 01 33_369fbf27](https://github.com/user-attachments/assets/234c91a9-a7ee-480e-aa6b-06f0a1549bac)




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
  ﻿<?xml version="1.0" encoding="utf-8"?>
<DWSIM_Simulation_Data>
  <GeneralInfo>
    <BuildVersion>9.0.5.0</BuildVersion>
    <BuildDate>2000-01-06T00:00:00</BuildDate>
    <OSInfo>Microsoft Windows 11 Pro, Version 10.0.26200.0, Win32NT Platform</OSInfo>
    <SavedOn>2025-10-13T23:20:18.5003257+07:00</SavedOn>
    <SavedFromClassicUI>true</SavedFromClassicUI>
  </GeneralInfo>
  <SimulationObjects>
    <SimulationObject>
      <Type>DWSIM.Thermodynamics.Streams.MaterialStream</Type>
      <ObjectClass>Streams</ObjectClass>
      <SupportsDynamicMode>true</SupportsDynamicMode>
      <HasPropertiesForDynamicMode>false</HasPropertiesForDynamicMode>
      <OverrideSingleCompoundFlashBehavior>false</OverrideSingleCompoundFlashBehavior>
      <FloatingTableAmountBasis>DefaultBasis</FloatingTableAmountBasis>
      <DefinedFlow>Mole</DefinedFlow>
      <ForcePhase>GlobalDef</ForcePhase>
      <TotalEnergyFlow>-212.445220198455</TotalEnergyFlow>
      <AtEquilibrium>true</AtEquilibrium>
      <ComponentDescription>CorrentedeMatria</ComponentDescription>
      <ComponentName>MAT-74ccf612-ceca-42d3-be4b-99be4e44403c</ComponentName>
      <Name2>MAT-74ccf612-ceca-42d3-be4b-99be4e44403c</Name2>
      <code>0</code>
      <InputComposition />
      <IsElectrolyteStream>false</IsElectrolyteStream>
      <ReferenceSolvent></ReferenceSolvent>
      <SpecType>Temperature_and_Pressure</SpecType>
      <CompositionBasis>Molar_Fractions</CompositionBasis>
      <EditorState>{"MainSelectedTab":0,"InputCompositionBasis":0,"CompoundsSelectedTab":0,"CompoundsAmountBasis":0,"CompoundsProperty":0,"CompoundsAmountSelectedTab":0,"CompoundsPropertySelectedTab":0,"PhasePropsSelectedTab":0,"MainSelectedTab0":0,"ShowAsPercentage":0}</EditorState>
      <MobileCompatible>true</MobileCompatible>
      <StreamType>Feed</StreamType>
      <IsDirty>true</IsDirty>
      <CanUsePreviousResults>false</CanUsePreviousResults>
      <DynamicsSpec>Pressure</DynamicsSpec>
      <DynamicsOnly>false</DynamicsOnly>
      <Visible>true</Visible>
      <OverrideCalculationRoutine>false</OverrideCalculationRoutine>
      <StoreDetailedDebugReport>false</StoreDetailedDebugReport>
      <IsFunctional>true</IsFunctional>
      <PreferredFlashAlgorithmTag></PreferredFlashAlgorithmTag>
      <Calculated>true</Calculated>
      <DebugMode>false</DebugMode>
      <LastUpdated>10/13/2025 23:18:29</LastUpdated>
      <ErrorMessage></ErrorMessage>
      <Annotation></Annotation>
      <IsAdjustAttached>false</IsAdjustAttached>
      <AttachedAdjustId></AttachedAdjustId>
      <AdjustVarType>Manipulated</AdjustVarType>
      <IsSpecAttached>false</IsSpecAttached>
      <AttachedSpecId></AttachedSpecId>
      <SpecVarType>Source</SpecVarType>
      <Name>MAT-74ccf612-ceca-42d3-be4b-99be4e44403c</Name>
      <UserDefinedChartNames />
      <ProductName>Material Stream</ProductName>
      <ProductDescription>Contains information about compounds flowing at specified state conditions</ProductDescription>
      <ProductAuthor>Daniel Wagner</ProductAuthor>
      <ProductContactInfo>https://dwsim.inforside.com.br</ProductContactInfo>
      <ProductPage>https://dwsim.inforside.com.br</ProductPage>
      <ProductVersion>9.0.5.0</ProductVersion>
      <ProductAssembly>DWSIM.SharedClasses</ProductAssembly>
      <IsSource>false</IsSource>
      <IsSink>false</IsSink>
      <DynamicProperties />
      <DynamicPropertiesDescriptions />
      <DynamicPropertiesUnitTypes />
      <AttachedUtilities />
      <PropertyPackage>PP-8472280c-ba09-46b4-aa6d-ff14bc089901</PropertyPackage>
      <Phases>
        <Phase>
          <ID>0</ID>
          <Compounds>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Cis-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>1</MassFraction>
              <MoleFraction>1</MoleFraction>
              <Molarity>40.8763188891033</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>0</FugacityCoeff>
              <Kvalue>NaN</Kvalue>
              <lnKvalue>NaN</lnKvalue>
              <MassFlow>1.55850888888889</MassFlow>
              <MolarFlow>27.7777777777778</MolarFlow>
              <Name>Cis-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>0</PartialVolume>
              <VolumetricFlow>0.679556734380569</VolumetricFlow>
              <VolumetricFraction>1</VolumetricFraction>
              <DiffusionCoefficient>Infinity</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Trans-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>0</MassFraction>
              <MoleFraction>0</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>0</FugacityCoeff>
              <Kvalue>NaN</Kvalue>
              <lnKvalue>NaN</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Trans-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>0</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>Infinity</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
          </Compounds>
          <Properties>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties>
          <ComponentDescription></ComponentDescription>
          <ComponentName>Mixture</ComponentName>
          <Compounds>System.Collections.Generic.Dictionary`2[System.String,DWSIM.Interfaces.ICompound]</Compounds>
          <Name>Mixture</Name>
          <Properties1>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties1>
          <Properties>
            <Type>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Type>
            <density>2.29341982801407</density>
            <enthalpy>-4.42067715623471</enthalpy>
            <entropy>-0.0104069145626997</entropy>
            <heatCapacityCp>1.43803194603212</heatCapacityCp>
            <heatCapacityCv>1.27166239754802</heatCapacityCv>
            <massflow>1.55850888888889</massflow>
            <molar_enthalpy>-248.027927144395</molar_enthalpy>
            <molar_entropy>-0.583893678667488</molar_entropy>
            <molarflow>27.7777777777778</molarflow>
            <molecularWeight>56.10632</molecularWeight>
            <pressure>101325</pressure>
            <surfaceTension>NaN</surfaceTension>
            <temperature>298.15</temperature>
            <thermalConductivity>0.0135371033580031</thermalConductivity>
            <volumetric_flow>0.679556734380569</volumetric_flow>
            <gibbs_free_energy>-1.3178555793658</gibbs_free_energy>
            <helmholtz_energy>-44.300790997908</helmholtz_energy>
            <internal_energy>-47.4036125747769</internal_energy>
            <molar_gibbs_free_energy>-73.9400268496832</molar_gibbs_free_energy>
            <molar_helmholtz_energy>-2485.55435598174</molar_helmholtz_energy>
            <molar_internal_energy>-2659.64225627645</molar_internal_energy>
          </Properties>
        </Phase>
        <Phase>
          <ID>1</ID>
          <Compounds>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Cis-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>NaN</MassFraction>
              <MoleFraction>NaN</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>0</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>NaN</MassFlow>
              <MolarFlow>NaN</MolarFlow>
              <Name>Cis-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0908841538100594</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Trans-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>NaN</MassFraction>
              <MoleFraction>NaN</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>0</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>NaN</MassFlow>
              <MolarFlow>NaN</MolarFlow>
              <Name>Trans-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0936026552224616</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
          </Compounds>
          <Properties>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties>
          <ComponentDescription></ComponentDescription>
          <ComponentName>OverallLiquid</ComponentName>
          <Compounds>System.Collections.Generic.Dictionary`2[System.String,DWSIM.Interfaces.ICompound]</Compounds>
          <Name>OverallLiquid</Name>
          <Properties1>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties1>
          <Properties>
            <Type>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Type>
            <density>0</density>
            <enthalpy>0</enthalpy>
            <entropy>0</entropy>
            <heatCapacityCp>0</heatCapacityCp>
            <heatCapacityCv>0</heatCapacityCv>
            <kinematic_viscosity>0</kinematic_viscosity>
            <massflow>0</massflow>
            <massfraction>0</massfraction>
            <molar_enthalpy>NaN</molar_enthalpy>
            <molar_entropy>NaN</molar_entropy>
            <molarflow>0</molarflow>
            <molarfraction>0</molarfraction>
            <molecularWeight>NaN</molecularWeight>
            <surfaceTension>NaN</surfaceTension>
            <thermalConductivity>0</thermalConductivity>
            <viscosity>0</viscosity>
            <volumetric_flow>0</volumetric_flow>
            <gibbs_free_energy>0</gibbs_free_energy>
            <helmholtz_energy>0</helmholtz_energy>
            <internal_energy>0</internal_energy>
            <molar_gibbs_free_energy>NaN</molar_gibbs_free_energy>
            <molar_helmholtz_energy>NaN</molar_helmholtz_energy>
            <molar_internal_energy>NaN</molar_internal_energy>
            <volumetricFraction>0</volumetricFraction>
          </Properties>
        </Phase>
        <Phase>
          <ID>2</ID>
          <Compounds>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Cis-2-butene</ComponentName>
              <ActivityCoeff>0.473376626638674</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>1</MassFraction>
              <MoleFraction>1</MoleFraction>
              <Molarity>40.8763188891033</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>1</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>1.55850888888889</MassFlow>
              <MolarFlow>27.7777777777778</MolarFlow>
              <Name>Cis-2-butene</Name>
              <PartialPressure>101325</PartialPressure>
              <PartialVolume>24.4640424377005</PartialVolume>
              <VolumetricFlow>0.679556734380569</VolumetricFlow>
              <VolumetricFraction>1</VolumetricFraction>
              <DiffusionCoefficient>5.33526792561562E-11</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Trans-2-butene</ComponentName>
              <ActivityCoeff>1</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>0</MassFraction>
              <MoleFraction>0</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>1</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Trans-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>24.4640424377005</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>5.33526792561562E-11</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
          </Compounds>
          <Properties>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties>
          <ComponentDescription></ComponentDescription>
          <ComponentName>Vapor</ComponentName>
          <Compounds>System.Collections.Generic.Dictionary`2[System.String,DWSIM.Interfaces.ICompound]</Compounds>
          <Name>Vapor</Name>
          <Properties1>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties1>
          <Properties>
            <Type>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Type>
            <compressibilityFactor>0.972888392352657</compressibilityFactor>
            <density>2.29341982801407</density>
            <enthalpy>-4.42067715623471</enthalpy>
            <enthalpyF>-136.313127062056</enthalpyF>
            <entropy>-0.0104069145626997</entropy>
            <entropyF>-8.79562496558887</entropyF>
            <heatCapacityCp>1.43803194603212</heatCapacityCp>
            <heatCapacityCv>1.27166239754802</heatCapacityCv>
            <jouleThomsonCoefficient>1.39239358719211E-07</jouleThomsonCoefficient>
            <kinematic_viscosity>3.58028058970648E-06</kinematic_viscosity>
            <massflow>1.55850888888889</massflow>
            <massfraction>1</massfraction>
            <molar_enthalpy>-248.027927144395</molar_enthalpy>
            <molar_entropy>-0.583893678667488</molar_entropy>
            <molarflow>27.7777777777778</molarflow>
            <molarfraction>1</molarfraction>
            <molecularWeight>56.10632</molecularWeight>
            <speedOfSound>NaN</speedOfSound>
            <thermalConductivity>0.0135371033580031</thermalConductivity>
            <viscosity>8.21108649428676E-06</viscosity>
            <volumetric_flow>0.679556734380569</volumetric_flow>
            <bulk_modulus>-3720.20943454263</bulk_modulus>
            <gibbs_free_energy>-1.3178555793658</gibbs_free_energy>
            <helmholtz_energy>-44.300790997908</helmholtz_energy>
            <internal_energy>-47.4036125747769</internal_energy>
            <isothermal_compressibility>-0.000268802070849794</isothermal_compressibility>
            <molar_gibbs_free_energy>-73.9400268496832</molar_gibbs_free_energy>
            <molar_helmholtz_energy>-2485.55435598174</molar_helmholtz_energy>
            <molar_internal_energy>-2659.64225627645</molar_internal_energy>
            <idealGasHeatCapacityCp>1.42281674350925</idealGasHeatCapacityCp>
            <idealGasHeatCapacityRatio>1.11625531233432</idealGasHeatCapacityRatio>
            <volumetricFraction>1</volumetricFraction>
          </Properties>
        </Phase>
        <Phase>
          <ID>3</ID>
          <Compounds>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Cis-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>1</MassFraction>
              <MoleFraction>1</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>2.1212315525052</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Cis-2-butene</Name>
              <PartialPressure>214933.787057589</PartialPressure>
              <PartialVolume>-0.0908841538100594</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Trans-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>0</MassFraction>
              <MoleFraction>0</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>2.31740714037102</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Trans-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0936026552224616</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
          </Compounds>
          <Properties>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties>
          <ComponentDescription></ComponentDescription>
          <ComponentName>Liquid1</ComponentName>
          <Compounds>System.Collections.Generic.Dictionary`2[System.String,DWSIM.Interfaces.ICompound]</Compounds>
          <Name>Liquid1</Name>
          <Properties1>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties1>
          <Properties>
            <Type>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Type>
            <surfaceTension>0.0139178830082261</surfaceTension>
            <gibbs_free_energy>0</gibbs_free_energy>
            <helmholtz_energy>0</helmholtz_energy>
            <internal_energy>0</internal_energy>
            <molar_gibbs_free_energy>0</molar_gibbs_free_energy>
            <molar_helmholtz_energy>0</molar_helmholtz_energy>
            <molar_internal_energy>0</molar_internal_energy>
            <volumetricFraction>0</volumetricFraction>
          </Properties>
        </Phase>
        <Phase>
          <ID>4</ID>
          <Compounds>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Cis-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>0</MassFraction>
              <MoleFraction>0</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>NaN</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Cis-2-butene</Name>
              <PartialPressure>NaN</PartialPressure>
              <PartialVolume>-0.0908841538100594</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Trans-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>0</MassFraction>
              <MoleFraction>0</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>NaN</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Trans-2-butene</Name>
              <PartialPressure>NaN</PartialPressure>
              <PartialVolume>-0.0936026552224616</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
          </Compounds>
          <Properties>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties>
          <ComponentDescription></ComponentDescription>
          <ComponentName>Liquid2</ComponentName>
          <Compounds>System.Collections.Generic.Dictionary`2[System.String,DWSIM.Interfaces.ICompound]</Compounds>
          <Name>Liquid2</Name>
          <Properties1>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties1>
          <Properties>
            <Type>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Type>
            <surfaceTension>0</surfaceTension>
            <gibbs_free_energy>0</gibbs_free_energy>
            <helmholtz_energy>0</helmholtz_energy>
            <internal_energy>0</internal_energy>
            <molar_gibbs_free_energy>0</molar_gibbs_free_energy>
            <molar_helmholtz_energy>0</molar_helmholtz_energy>
            <molar_internal_energy>0</molar_internal_energy>
            <volumetricFraction>0</volumetricFraction>
          </Properties>
        </Phase>
        <Phase>
          <ID>5</ID>
          <Compounds>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Cis-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>0</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Cis-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0908841538100594</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Trans-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>0</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Trans-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0936026552224616</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
          </Compounds>
          <Properties>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties>
          <ComponentDescription></ComponentDescription>
          <ComponentName>Liquid3</ComponentName>
          <Compounds>System.Collections.Generic.Dictionary`2[System.String,DWSIM.Interfaces.ICompound]</Compounds>
          <Name>Liquid3</Name>
          <Properties1>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties1>
          <Properties>
            <Type>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Type>
            <gibbs_free_energy>0</gibbs_free_energy>
            <helmholtz_energy>0</helmholtz_energy>
            <internal_energy>0</internal_energy>
            <molar_gibbs_free_energy>0</molar_gibbs_free_energy>
            <molar_helmholtz_energy>0</molar_helmholtz_energy>
            <molar_internal_energy>0</molar_internal_energy>
          </Properties>
        </Phase>
        <Phase>
          <ID>6</ID>
          <Compounds>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Cis-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>0</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Cis-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0908841538100594</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Trans-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>0</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Trans-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0936026552224616</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
          </Compounds>
          <Properties>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties>
          <ComponentDescription></ComponentDescription>
          <ComponentName>Aqueous</ComponentName>
          <Compounds>System.Collections.Generic.Dictionary`2[System.String,DWSIM.Interfaces.ICompound]</Compounds>
          <Name>Aqueous</Name>
          <Properties1>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties1>
          <Properties>
            <Type>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Type>
            <gibbs_free_energy>0</gibbs_free_energy>
            <helmholtz_energy>0</helmholtz_energy>
            <internal_energy>0</internal_energy>
            <molar_gibbs_free_energy>0</molar_gibbs_free_energy>
            <molar_helmholtz_energy>0</molar_helmholtz_energy>
            <molar_internal_energy>0</molar_internal_energy>
          </Properties>
        </Phase>
        <Phase>
          <ID>7</ID>
          <Compounds>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Cis-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>1</MassFraction>
              <MoleFraction>1</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>1</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Cis-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0908841538100594</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Trans-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>0</MassFraction>
              <MoleFraction>0</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>1</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Trans-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0936026552224616</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
          </Compounds>
          <Properties>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties>
          <ComponentDescription></ComponentDescription>
          <ComponentName>Solid</ComponentName>
          <Compounds>System.Collections.Generic.Dictionary`2[System.String,DWSIM.Interfaces.ICompound]</Compounds>
          <Name>Solid</Name>
          <Properties1>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties1>
          <Properties>
            <Type>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Type>
            <gibbs_free_energy>0</gibbs_free_energy>
            <helmholtz_energy>0</helmholtz_energy>
            <internal_energy>0</internal_energy>
            <molar_gibbs_free_energy>0</molar_gibbs_free_energy>
            <molar_helmholtz_energy>0</molar_helmholtz_energy>
            <molar_internal_energy>0</molar_internal_energy>
            <volumetricFraction>0</volumetricFraction>
          </Properties>
        </Phase>
      </Phases>
    </SimulationObject>
    <SimulationObject>
      <Type>DWSIM.UnitOperations.Reactors.Reactor_CSTR</Type>
      <EquipmentTypes>
        <Item></Item>
        <Item>Stirred Tank</Item>
      </EquipmentTypes>
      <SupportsDynamicMode>true</SupportsDynamicMode>
      <HasPropertiesForDynamicMode>true</HasPropertiesForDynamicMode>
      <ResidenceTimeL>1.39942701144276</ResidenceTimeL>
      <ResidenceTimeV>1.39942701144276</ResidenceTimeV>
      <Tolerance>1E-05</Tolerance>
      <MaxIterations>1000</MaxIterations>
      <IsothermalTemperature>0</IsothermalTemperature>
      <Volume>0.9509900499</Volume>
      <Headspace>0</Headspace>
      <CatalystAmount>0</CatalystAmount>
      <MobileCompatible>true</MobileCompatible>
      <ObjectClass>Reactors</ObjectClass>
      <OutletTemperature>298.15</OutletTemperature>
      <ReactorOperationMode>Isothermic</ReactorOperationMode>
      <ReactionSetID>DefaultSet</ReactionSetID>
      <ReactionSetName></ReactionSetName>
      <DeltaT>0</DeltaT>
      <DeltaQ>2.75335310107039E-14</DeltaQ>
      <ExternalSolverID></ExternalSolverID>
      <ExternalSolverConfigData></ExternalSolverConfigData>
      <ParticleSizeDistributions />
      <SupportsParticleSizeDistributions>false</SupportsParticleSizeDistributions>
      <SupportsRestoreStateAfterError>true</SupportsRestoreStateAfterError>
      <SelectedEquipmentType></SelectedEquipmentType>
      <ComponentDescription>ReatorCSTR</ComponentDescription>
      <ComponentName>CSTR-0d4ae06a-1a6d-4af2-9208-57387f7ee67d</ComponentName>
      <IsDirty>true</IsDirty>
      <CanUsePreviousResults>false</CanUsePreviousResults>
      <DynamicsSpec>Pressure</DynamicsSpec>
      <DynamicsOnly>false</DynamicsOnly>
      <Visible>true</Visible>
      <OverrideCalculationRoutine>false</OverrideCalculationRoutine>
      <StoreDetailedDebugReport>false</StoreDetailedDebugReport>
      <IsFunctional>true</IsFunctional>
      <PreferredFlashAlgorithmTag></PreferredFlashAlgorithmTag>
      <Calculated>true</Calculated>
      <DebugMode>false</DebugMode>
      <LastUpdated>10/13/2025 23:18:29</LastUpdated>
      <ErrorMessage></ErrorMessage>
      <Annotation></Annotation>
      <IsAdjustAttached>true</IsAdjustAttached>
      <AttachedAdjustId>AJ08992d3d-559e-4471-90a1-ec01510757d9</AttachedAdjustId>
      <AdjustVarType>Controlled</AdjustVarType>
      <IsSpecAttached>false</IsSpecAttached>
      <AttachedSpecId></AttachedSpecId>
      <SpecVarType>Source</SpecVarType>
      <Name>CSTR-0d4ae06a-1a6d-4af2-9208-57387f7ee67d</Name>
      <UserDefinedChartNames />
      <ProductName>Continuous Stirred Tank Reactor (CSTR)</ProductName>
      <ProductDescription>CSTR model, supports Kinetic and HetCat reactions</ProductDescription>
      <ProductAuthor>Daniel Wagner</ProductAuthor>
      <ProductContactInfo>https://dwsim.inforside.com.br</ProductContactInfo>
      <ProductPage>https://dwsim.inforside.com.br</ProductPage>
      <ProductVersion>9.0.5.0</ProductVersion>
      <ProductAssembly>DWSIM.SharedClasses</ProductAssembly>
      <IsSource>false</IsSource>
      <IsSink>false</IsSink>
      <DynamicProperties>
        <Property>
          <Name>Operating Pressure</Name>
          <PropertyType>System.Double</PropertyType>
          <Data>0.0</Data>
        </Property>
        <Property>
          <Name>Liquid Level</Name>
          <PropertyType>System.Double</PropertyType>
          <Data>0.0</Data>
        </Property>
        <Property>
          <Name>Height</Name>
          <PropertyType>System.Double</PropertyType>
          <Data>1.0</Data>
        </Property>
        <Property>
          <Name>Minimum Pressure</Name>
          <PropertyType>System.Double</PropertyType>
          <Data>101325.0</Data>
        </Property>
        <Property>
          <Name>Initialize using Inlet Stream</Name>
          <PropertyType>System.Double</PropertyType>
          <Data>0.0</Data>
        </Property>
        <Property>
          <Name>Reset Contents</Name>
          <PropertyType>System.Double</PropertyType>
          <Data>0.0</Data>
        </Property>
      </DynamicProperties>
      <DynamicPropertiesDescriptions>
        <Property>
          <Name>Operating Pressure</Name>
          <PropertyType>System.String</PropertyType>
          <Data>"Current Operating Pressure"</Data>
        </Property>
        <Property>
          <Name>Liquid Level</Name>
          <PropertyType>System.String</PropertyType>
          <Data>"Current Liquid Level"</Data>
        </Property>
        <Property>
          <Name>Height</Name>
          <PropertyType>System.String</PropertyType>
          <Data>"Available Height for Liquid"</Data>
        </Property>
        <Property>
          <Name>Minimum Pressure</Name>
          <PropertyType>System.String</PropertyType>
          <Data>"Minimum Dynamic Pressure for this Reactor."</Data>
        </Property>
        <Property>
          <Name>Initialize using Inlet Stream</Name>
          <PropertyType>System.String</PropertyType>
          <Data>"Initializes the CSTR contents with information from the inlet stream."</Data>
        </Property>
        <Property>
          <Name>Reset Contents</Name>
          <PropertyType>System.String</PropertyType>
          <Data>"Empties the CSTR's content on the next run."</Data>
        </Property>
      </DynamicPropertiesDescriptions>
      <DynamicPropertiesUnitTypes>
        <Property>
          <Name>Operating Pressure</Name>
          <PropertyType>DWSIM.Interfaces.Enums.UnitOfMeasure</PropertyType>
          <Data>46</Data>
        </Property>
        <Property>
          <Name>Liquid Level</Name>
          <PropertyType>DWSIM.Interfaces.Enums.UnitOfMeasure</PropertyType>
          <Data>13</Data>
        </Property>
        <Property>
          <Name>Height</Name>
          <PropertyType>DWSIM.Interfaces.Enums.UnitOfMeasure</PropertyType>
          <Data>13</Data>
        </Property>
        <Property>
          <Name>Minimum Pressure</Name>
          <PropertyType>DWSIM.Interfaces.Enums.UnitOfMeasure</PropertyType>
          <Data>46</Data>
        </Property>
        <Property>
          <Name>Initialize using Inlet Stream</Name>
          <PropertyType>DWSIM.Interfaces.Enums.UnitOfMeasure</PropertyType>
          <Data>66</Data>
        </Property>
        <Property>
          <Name>Reset Contents</Name>
          <PropertyType>DWSIM.Interfaces.Enums.UnitOfMeasure</PropertyType>
          <Data>66</Data>
        </Property>
      </DynamicPropertiesUnitTypes>
      <AttachedUtilities />
      <PropertyPackage>PP-8472280c-ba09-46b4-aa6d-ff14bc089901</PropertyPackage>
      <ReactionConversions />
      <CompoundConversions>
        <Compound ID="Cis-2-butene">1.27897692436818E-16</Compound>
      </CompoundConversions>
    </SimulationObject>
    <SimulationObject>
      <Type>DWSIM.UnitOperations.Streams.EnergyStream</Type>
      <ObjectClass>Streams</ObjectClass>
      <SupportsDynamicMode>true</SupportsDynamicMode>
      <HasPropertiesForDynamicMode>false</HasPropertiesForDynamicMode>
      <ComponentDescription>CorrentedeEnergia</ComponentDescription>
      <ComponentName>EN-542636a7-33d3-4a63-a18a-dc59bfe40459</ComponentName>
      <EnergyFlow>2.75335310107039E-14</EnergyFlow>
      <MobileCompatible>true</MobileCompatible>
      <Name2>EN-542636a7-33d3-4a63-a18a-dc59bfe40459</Name2>
      <code>0</code>
      <IsDirty>true</IsDirty>
      <CanUsePreviousResults>false</CanUsePreviousResults>
      <DynamicsSpec>Pressure</DynamicsSpec>
      <DynamicsOnly>false</DynamicsOnly>
      <Visible>true</Visible>
      <OverrideCalculationRoutine>false</OverrideCalculationRoutine>
      <StoreDetailedDebugReport>false</StoreDetailedDebugReport>
      <IsFunctional>true</IsFunctional>
      <PreferredFlashAlgorithmTag></PreferredFlashAlgorithmTag>
      <Calculated>true</Calculated>
      <DebugMode>false</DebugMode>
      <LastUpdated>10/13/2025 23:18:29</LastUpdated>
      <ErrorMessage></ErrorMessage>
      <Annotation></Annotation>
      <IsAdjustAttached>false</IsAdjustAttached>
      <AttachedAdjustId></AttachedAdjustId>
      <AdjustVarType>Manipulated</AdjustVarType>
      <IsSpecAttached>false</IsSpecAttached>
      <AttachedSpecId></AttachedSpecId>
      <SpecVarType>Source</SpecVarType>
      <Name>EN-542636a7-33d3-4a63-a18a-dc59bfe40459</Name>
      <UserDefinedChartNames />
      <ProductName>Energy Stream</ProductName>
      <ProductDescription>Energy flow from/to Unit Operations</ProductDescription>
      <ProductAuthor>Daniel Wagner</ProductAuthor>
      <ProductContactInfo>https://dwsim.inforside.com.br</ProductContactInfo>
      <ProductPage>https://dwsim.inforside.com.br</ProductPage>
      <ProductVersion>9.0.5.0</ProductVersion>
      <ProductAssembly>DWSIM.SharedClasses</ProductAssembly>
      <IsSource>false</IsSource>
      <IsSink>false</IsSink>
      <DynamicProperties />
      <DynamicPropertiesDescriptions />
      <DynamicPropertiesUnitTypes />
      <AttachedUtilities />
    </SimulationObject>
    <SimulationObject>
      <Type>DWSIM.Thermodynamics.Streams.MaterialStream</Type>
      <ObjectClass>Streams</ObjectClass>
      <SupportsDynamicMode>true</SupportsDynamicMode>
      <HasPropertiesForDynamicMode>false</HasPropertiesForDynamicMode>
      <OverrideSingleCompoundFlashBehavior>false</OverrideSingleCompoundFlashBehavior>
      <FloatingTableAmountBasis>DefaultBasis</FloatingTableAmountBasis>
      <DefinedFlow>Mass</DefinedFlow>
      <ForcePhase>GlobalDef</ForcePhase>
      <TotalEnergyFlow>-212.445220198052</TotalEnergyFlow>
      <AtEquilibrium>true</AtEquilibrium>
      <ComponentDescription>CorrentedeMatria</ComponentDescription>
      <ComponentName>MAT-d456af80-baca-4162-ba65-7ae84575ce5f</ComponentName>
      <Name2>MAT-d456af80-baca-4162-ba65-7ae84575ce5f</Name2>
      <code>0</code>
      <InputComposition />
      <IsElectrolyteStream>false</IsElectrolyteStream>
      <ReferenceSolvent></ReferenceSolvent>
      <SpecType>Temperature_and_Pressure</SpecType>
      <CompositionBasis>Molar_Fractions</CompositionBasis>
      <EditorState>{}</EditorState>
      <MobileCompatible>true</MobileCompatible>
      <StreamType>Product</StreamType>
      <IsDirty>true</IsDirty>
      <CanUsePreviousResults>false</CanUsePreviousResults>
      <DynamicsSpec>Pressure</DynamicsSpec>
      <DynamicsOnly>false</DynamicsOnly>
      <Visible>true</Visible>
      <OverrideCalculationRoutine>false</OverrideCalculationRoutine>
      <StoreDetailedDebugReport>false</StoreDetailedDebugReport>
      <IsFunctional>true</IsFunctional>
      <PreferredFlashAlgorithmTag></PreferredFlashAlgorithmTag>
      <Calculated>true</Calculated>
      <DebugMode>false</DebugMode>
      <LastUpdated>10/13/2025 23:18:29</LastUpdated>
      <ErrorMessage></ErrorMessage>
      <Annotation></Annotation>
      <IsAdjustAttached>false</IsAdjustAttached>
      <AttachedAdjustId></AttachedAdjustId>
      <AdjustVarType>Manipulated</AdjustVarType>
      <IsSpecAttached>false</IsSpecAttached>
      <AttachedSpecId></AttachedSpecId>
      <SpecVarType>Source</SpecVarType>
      <Name>MAT-d456af80-baca-4162-ba65-7ae84575ce5f</Name>
      <UserDefinedChartNames />
      <ProductName>Material Stream</ProductName>
      <ProductDescription>Contains information about compounds flowing at specified state conditions</ProductDescription>
      <ProductAuthor>Daniel Wagner</ProductAuthor>
      <ProductContactInfo>https://dwsim.inforside.com.br</ProductContactInfo>
      <ProductPage>https://dwsim.inforside.com.br</ProductPage>
      <ProductVersion>9.0.5.0</ProductVersion>
      <ProductAssembly>DWSIM.SharedClasses</ProductAssembly>
      <IsSource>false</IsSource>
      <IsSink>false</IsSink>
      <DynamicProperties />
      <DynamicPropertiesDescriptions />
      <DynamicPropertiesUnitTypes />
      <AttachedUtilities />
      <PropertyPackage>PP-8472280c-ba09-46b4-aa6d-ff14bc089901</PropertyPackage>
      <Phases>
        <Phase>
          <ID>0</ID>
          <Compounds>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Cis-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>1</MassFraction>
              <MoleFraction>1</MoleFraction>
              <Molarity>40.876318889079</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>0</FugacityCoeff>
              <Kvalue>NaN</Kvalue>
              <lnKvalue>NaN</lnKvalue>
              <MassFlow>1.55850888888889</MassFlow>
              <MolarFlow>27.7777777777778</MolarFlow>
              <Name>Cis-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>0</PartialVolume>
              <VolumetricFlow>0.679556734380973</VolumetricFlow>
              <VolumetricFraction>1</VolumetricFraction>
              <DiffusionCoefficient>Infinity</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Trans-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>0</MassFraction>
              <MoleFraction>0</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>0</FugacityCoeff>
              <Kvalue>NaN</Kvalue>
              <lnKvalue>NaN</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Trans-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>0</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>Infinity</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
          </Compounds>
          <Properties>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties>
          <ComponentDescription></ComponentDescription>
          <ComponentName>Mixture</ComponentName>
          <Compounds>System.Collections.Generic.Dictionary`2[System.String,DWSIM.Interfaces.ICompound]</Compounds>
          <Name>Mixture</Name>
          <Properties1>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties1>
          <Properties>
            <Type>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Type>
            <density>2.29341982801271</density>
            <enthalpy>-4.42067715597577</enthalpy>
            <entropy>-0.0104069145618312</entropy>
            <heatCapacityCp>1.43803194603277</heatCapacityCp>
            <heatCapacityCv>1.27166239754871</heatCapacityCv>
            <massflow>1.55850888888889</massflow>
            <massfraction>1</massfraction>
            <molar_enthalpy>-248.027927129867</molar_enthalpy>
            <molar_entropy>-0.583893678618761</molar_entropy>
            <molarflow>27.7777777777778</molarflow>
            <molecularWeight>56.10632</molecularWeight>
            <pressure>101325</pressure>
            <surfaceTension>NaN</surfaceTension>
            <temperature>298.150000000177</temperature>
            <thermalConductivity>0.0135371033580214</thermalConductivity>
            <volumetric_flow>0.679556734380973</volumetric_flow>
            <gibbs_free_energy>-1.31785557936395</gibbs_free_energy>
            <helmholtz_energy>-44.3007909979336</helmholtz_energy>
            <internal_energy>-47.4036125745455</internal_energy>
            <molar_gibbs_free_energy>-73.9400268495793</molar_gibbs_free_energy>
            <molar_helmholtz_energy>-2485.55435598318</molar_helmholtz_energy>
            <molar_internal_energy>-2659.64225626347</molar_internal_energy>
          </Properties>
        </Phase>
        <Phase>
          <ID>1</ID>
          <Compounds>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Cis-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>NaN</MassFraction>
              <MoleFraction>NaN</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>0</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>NaN</MassFlow>
              <MolarFlow>NaN</MolarFlow>
              <Name>Cis-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0908841543583719</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Trans-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>NaN</MassFraction>
              <MoleFraction>NaN</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>0</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>NaN</MassFlow>
              <MolarFlow>NaN</MolarFlow>
              <Name>Trans-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0936026552203673</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
          </Compounds>
          <Properties>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties>
          <ComponentDescription></ComponentDescription>
          <ComponentName>OverallLiquid</ComponentName>
          <Compounds>System.Collections.Generic.Dictionary`2[System.String,DWSIM.Interfaces.ICompound]</Compounds>
          <Name>OverallLiquid</Name>
          <Properties1>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties1>
          <Properties>
            <Type>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Type>
            <density>0</density>
            <enthalpy>0</enthalpy>
            <entropy>0</entropy>
            <heatCapacityCp>0</heatCapacityCp>
            <heatCapacityCv>0</heatCapacityCv>
            <kinematic_viscosity>0</kinematic_viscosity>
            <massflow>0</massflow>
            <massfraction>0</massfraction>
            <molar_enthalpy>NaN</molar_enthalpy>
            <molar_entropy>NaN</molar_entropy>
            <molarflow>0</molarflow>
            <molarfraction>0</molarfraction>
            <molecularWeight>NaN</molecularWeight>
            <surfaceTension>NaN</surfaceTension>
            <thermalConductivity>0</thermalConductivity>
            <viscosity>0</viscosity>
            <volumetric_flow>0</volumetric_flow>
            <gibbs_free_energy>0</gibbs_free_energy>
            <helmholtz_energy>0</helmholtz_energy>
            <internal_energy>0</internal_energy>
            <molar_gibbs_free_energy>NaN</molar_gibbs_free_energy>
            <molar_helmholtz_energy>NaN</molar_helmholtz_energy>
            <molar_internal_energy>NaN</molar_internal_energy>
            <volumetricFraction>0</volumetricFraction>
          </Properties>
        </Phase>
        <Phase>
          <ID>2</ID>
          <Compounds>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Cis-2-butene</ComponentName>
              <ActivityCoeff>0.473376626635979</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>1</MassFraction>
              <MoleFraction>1</MoleFraction>
              <Molarity>40.876318889079</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>1</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>1.55850888888889</MassFlow>
              <MolarFlow>27.7777777777778</MolarFlow>
              <Name>Cis-2-butene</Name>
              <PartialPressure>101325</PartialPressure>
              <PartialVolume>24.464042437715</PartialVolume>
              <VolumetricFlow>0.679556734380973</VolumetricFlow>
              <VolumetricFraction>1</VolumetricFraction>
              <DiffusionCoefficient>5.33526792562117E-11</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Trans-2-butene</ComponentName>
              <ActivityCoeff>1</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>0</MassFraction>
              <MoleFraction>0</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>1</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Trans-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>24.464042437715</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>5.33526792562117E-11</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
          </Compounds>
          <Properties>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties>
          <ComponentDescription></ComponentDescription>
          <ComponentName>Vapor</ComponentName>
          <Compounds>System.Collections.Generic.Dictionary`2[System.String,DWSIM.Interfaces.ICompound]</Compounds>
          <Name>Vapor</Name>
          <Properties1>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties1>
          <Properties>
            <Type>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Type>
            <compressibilityFactor>0.972888392352701</compressibilityFactor>
            <density>2.29341982801271</density>
            <enthalpy>-4.42067715597577</enthalpy>
            <enthalpyF>-136.313127061797</enthalpyF>
            <entropy>-0.0104069145618312</entropy>
            <entropyF>-8.795624965588</entropyF>
            <heatCapacityCp>1.43803194603277</heatCapacityCp>
            <heatCapacityCv>1.27166239754871</heatCapacityCv>
            <jouleThomsonCoefficient>1.39239358717988E-07</jouleThomsonCoefficient>
            <kinematic_viscosity>3.58028058971046E-06</kinematic_viscosity>
            <massflow>1.55850888888889</massflow>
            <massfraction>1</massfraction>
            <molar_enthalpy>-248.027927129867</molar_enthalpy>
            <molar_entropy>-0.583893678618761</molar_entropy>
            <molarflow>27.7777777777778</molarflow>
            <molarfraction>1</molarfraction>
            <molecularWeight>56.10632</molecularWeight>
            <speedOfSound>NaN</speedOfSound>
            <thermalConductivity>0.0135371033580214</thermalConductivity>
            <viscosity>8.211086494291E-06</viscosity>
            <volumetric_flow>0.679556734380973</volumetric_flow>
            <bulk_modulus>-3720.20943454907</bulk_modulus>
            <gibbs_free_energy>-1.31785557936395</gibbs_free_energy>
            <helmholtz_energy>-44.3007909979336</helmholtz_energy>
            <internal_energy>-47.4036125745455</internal_energy>
            <isothermal_compressibility>-0.000268802070849328</isothermal_compressibility>
            <molar_gibbs_free_energy>-73.9400268495793</molar_gibbs_free_energy>
            <molar_helmholtz_energy>-2485.55435598318</molar_helmholtz_energy>
            <molar_internal_energy>-2659.64225626347</molar_internal_energy>
            <idealGasHeatCapacityCp>1.42281674350992</idealGasHeatCapacityCp>
            <idealGasHeatCapacityRatio>1.11625531233426</idealGasHeatCapacityRatio>
            <volumetricFraction>1</volumetricFraction>
          </Properties>
        </Phase>
        <Phase>
          <ID>3</ID>
          <Compounds>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Cis-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>1</MassFraction>
              <MoleFraction>1</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>2.12123155251737</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Cis-2-butene</Name>
              <PartialPressure>214933.787058822</PartialPressure>
              <PartialVolume>-0.0908841543583719</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Trans-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>0</MassFraction>
              <MoleFraction>0</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>2.31740714038411</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Trans-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0936026552203673</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
          </Compounds>
          <Properties>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties>
          <ComponentDescription></ComponentDescription>
          <ComponentName>Liquid1</ComponentName>
          <Compounds>System.Collections.Generic.Dictionary`2[System.String,DWSIM.Interfaces.ICompound]</Compounds>
          <Name>Liquid1</Name>
          <Properties1>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties1>
          <Properties>
            <Type>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Type>
            <surfaceTension>0.0139178830082037</surfaceTension>
            <gibbs_free_energy>0</gibbs_free_energy>
            <helmholtz_energy>0</helmholtz_energy>
            <internal_energy>0</internal_energy>
            <molar_gibbs_free_energy>0</molar_gibbs_free_energy>
            <molar_helmholtz_energy>0</molar_helmholtz_energy>
            <molar_internal_energy>0</molar_internal_energy>
            <volumetricFraction>0</volumetricFraction>
          </Properties>
        </Phase>
        <Phase>
          <ID>4</ID>
          <Compounds>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Cis-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>1</MassFraction>
              <MoleFraction>1</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>2.12123155251737</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Cis-2-butene</Name>
              <PartialPressure>214933.787058822</PartialPressure>
              <PartialVolume>-0.0908841543583719</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Trans-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>0</MassFraction>
              <MoleFraction>0</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>2.31740714038411</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Trans-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0936026552203673</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
          </Compounds>
          <Properties>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties>
          <ComponentDescription></ComponentDescription>
          <ComponentName>Liquid2</ComponentName>
          <Compounds>System.Collections.Generic.Dictionary`2[System.String,DWSIM.Interfaces.ICompound]</Compounds>
          <Name>Liquid2</Name>
          <Properties1>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties1>
          <Properties>
            <Type>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Type>
            <surfaceTension>0.0139178830082037</surfaceTension>
            <gibbs_free_energy>0</gibbs_free_energy>
            <helmholtz_energy>0</helmholtz_energy>
            <internal_energy>0</internal_energy>
            <molar_gibbs_free_energy>0</molar_gibbs_free_energy>
            <molar_helmholtz_energy>0</molar_helmholtz_energy>
            <molar_internal_energy>0</molar_internal_energy>
            <volumetricFraction>0</volumetricFraction>
          </Properties>
        </Phase>
        <Phase>
          <ID>5</ID>
          <Compounds>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Cis-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>0</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Cis-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0908841543583719</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Trans-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>0</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Trans-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0936026552203673</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
          </Compounds>
          <Properties>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties>
          <ComponentDescription></ComponentDescription>
          <ComponentName>Liquid3</ComponentName>
          <Compounds>System.Collections.Generic.Dictionary`2[System.String,DWSIM.Interfaces.ICompound]</Compounds>
          <Name>Liquid3</Name>
          <Properties1>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties1>
          <Properties>
            <Type>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Type>
            <gibbs_free_energy>0</gibbs_free_energy>
            <helmholtz_energy>0</helmholtz_energy>
            <internal_energy>0</internal_energy>
            <molar_gibbs_free_energy>0</molar_gibbs_free_energy>
            <molar_helmholtz_energy>0</molar_helmholtz_energy>
            <molar_internal_energy>0</molar_internal_energy>
          </Properties>
        </Phase>
        <Phase>
          <ID>6</ID>
          <Compounds>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Cis-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>0</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Cis-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0908841543583719</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Trans-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>0</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Trans-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0936026552203673</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
          </Compounds>
          <Properties>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties>
          <ComponentDescription></ComponentDescription>
          <ComponentName>Aqueous</ComponentName>
          <Compounds>System.Collections.Generic.Dictionary`2[System.String,DWSIM.Interfaces.ICompound]</Compounds>
          <Name>Aqueous</Name>
          <Properties1>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties1>
          <Properties>
            <Type>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Type>
            <gibbs_free_energy>0</gibbs_free_energy>
            <helmholtz_energy>0</helmholtz_energy>
            <internal_energy>0</internal_energy>
            <molar_gibbs_free_energy>0</molar_gibbs_free_energy>
            <molar_helmholtz_energy>0</molar_helmholtz_energy>
            <molar_internal_energy>0</molar_internal_energy>
          </Properties>
        </Phase>
        <Phase>
          <ID>7</ID>
          <Compounds>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Cis-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>1</MassFraction>
              <MoleFraction>1</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>1</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Cis-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0908841543583719</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
            <Compound>
              <Type>DWSIM.Thermodynamics.BaseClasses.Compound</Type>
              <ComponentDescription></ComponentDescription>
              <ComponentName>Trans-2-butene</ComponentName>
              <ActivityCoeff>0</ActivityCoeff>
              <PetroleumFraction>false</PetroleumFraction>
              <MassFraction>0</MassFraction>
              <MoleFraction>0</MoleFraction>
              <Molarity>0</Molarity>
              <Molality>0</Molality>
              <FugacityCoeff>1</FugacityCoeff>
              <Kvalue>0</Kvalue>
              <lnKvalue>0</lnKvalue>
              <MassFlow>0</MassFlow>
              <MolarFlow>0</MolarFlow>
              <Name>Trans-2-butene</Name>
              <PartialPressure>0</PartialPressure>
              <PartialVolume>-0.0936026552203673</PartialVolume>
              <VolumetricFlow>0</VolumetricFlow>
              <VolumetricFraction>0</VolumetricFraction>
              <DiffusionCoefficient>NaN</DiffusionCoefficient>
              <EnthalpyF_Dmol>0</EnthalpyF_Dmol>
              <EntropyF_Dmol>0</EntropyF_Dmol>
              <DynamicProperties />
            </Compound>
          </Compounds>
          <Properties>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties>
          <ComponentDescription></ComponentDescription>
          <ComponentName>Solid</ComponentName>
          <Compounds>System.Collections.Generic.Dictionary`2[System.String,DWSIM.Interfaces.ICompound]</Compounds>
          <Name>Solid</Name>
          <Properties1>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Properties1>
          <Properties>
            <Type>DWSIM.Thermodynamics.BaseClasses.PhaseProperties</Type>
            <gibbs_free_energy>0</gibbs_free_energy>
            <helmholtz_energy>0</helmholtz_energy>
            <internal_energy>0</internal_energy>
            <molar_gibbs_free_energy>0</molar_gibbs_free_energy>
            <molar_helmholtz_energy>0</molar_helmholtz_energy>
            <molar_internal_energy>0</molar_internal_energy>
            <volumetricFraction>0</volumetricFraction>
          </Properties>
        </Phase>
      </Phases>
    </SimulationObject>
    <SimulationObject>
      <Type>DWSIM.UnitOperations.SpecialOps.Adjust</Type>
      <SolvingMethodSelf>0</SolvingMethodSelf>
      <SimultaneousAdjust>true</SimultaneousAdjust>
      <MaxVal>2</MaxVal>
      <MinVal>0.2</MinVal>
      <RvOk>false</RvOk>
      <MvOk>false</MvOk>
      <CvOk>false</CvOk>
      <ManipulatedVariable></ManipulatedVariable>
      <ControlledVariable></ControlledVariable>
      <ReferenceVariable></ReferenceVariable>
      <Status></Status>
      <AdjustValue>90</AdjustValue>
      <Referenced>false</Referenced>
      <StepSize>0.1</StepSize>
      <Tolerance>0.0001</Tolerance>
      <MaximumIterations>10</MaximumIterations>
      <MobileCompatible>true</MobileCompatible>
      <ObjectClass>Logical</ObjectClass>
      <IsDirty>true</IsDirty>
      <CanUsePreviousResults>false</CanUsePreviousResults>
      <DynamicsSpec>Pressure</DynamicsSpec>
      <DynamicsOnly>false</DynamicsOnly>
      <Visible>true</Visible>
      <OverrideCalculationRoutine>false</OverrideCalculationRoutine>
      <StoreDetailedDebugReport>false</StoreDetailedDebugReport>
      <IsFunctional>true</IsFunctional>
      <ComponentDescription>Ajuste</ComponentDescription>
      <ComponentName>AJ08992d3d-559e-4471-90a1-ec01510757d9</ComponentName>
      <SupportsDynamicMode>false</SupportsDynamicMode>
      <HasPropertiesForDynamicMode>false</HasPropertiesForDynamicMode>
      <PreferredFlashAlgorithmTag></PreferredFlashAlgorithmTag>
      <Calculated>false</Calculated>
      <DebugMode>false</DebugMode>
      <LastUpdated>01/01/0001 00:00:00</LastUpdated>
      <Annotation></Annotation>
      <IsAdjustAttached>false</IsAdjustAttached>
      <AttachedAdjustId></AttachedAdjustId>
      <AdjustVarType>Manipulated</AdjustVarType>
      <IsSpecAttached>false</IsSpecAttached>
      <AttachedSpecId></AttachedSpecId>
      <SpecVarType>Source</SpecVarType>
      <Name>AJ08992d3d-559e-4471-90a1-ec01510757d9</Name>
      <UserDefinedChartNames />
      <ProductName>Controller Block</ProductName>
      <ProductDescription>Logical block for controlling a variable in the flowsheet</ProductDescription>
      <ProductAuthor>Daniel Wagner</ProductAuthor>
      <ProductContactInfo>https://dwsim.inforside.com.br</ProductContactInfo>
      <ProductPage>https://dwsim.inforside.com.br</ProductPage>
      <ProductVersion>9.0.5.0</ProductVersion>
      <ProductAssembly>DWSIM.SharedClasses</ProductAssembly>
      <IsSource>false</IsSource>
      <IsSink>false</IsSink>
      <DynamicProperties />
      <DynamicPropertiesDescriptions />
      <DynamicPropertiesUnitTypes />
      <AttachedUtilities />
      <ManipulatedObjectData ID="CSTR-0d4ae06a-1a6d-4af2-9208-57387f7ee67d" Name="CSTR-1" Property="PROP_CS_2" ObjectType="" />
      <ControlledObjectData ID="CSTR-0d4ae06a-1a6d-4af2-9208-57387f7ee67d" Name="CSTR-1" Property="Cis-2-butene: Conversion" ObjectType="" />
      <ReferencedObjectData ID="" Name="" Property="" ObjectType="" />
    </SimulationObject>
  </SimulationObjects>
  <Settings>
    <Type>DWSIM.SharedClasses.DWSIM.Flowsheet.FlowsheetVariables</Type>
    <SimulationMode></SimulationMode>
    <BackupFileName>_backup_20251013_231833.dwbcs</BackupFileName>
    <FilePath>C:\Users\User\Downloads\CSTR DWSIM.dwxmz</FilePath>
    <FlowsheetQuickConnect>false</FlowsheetQuickConnect>
    <FlowsheetShowCalculationQueue>false</FlowsheetShowCalculationQueue>
    <FlowsheetShowConsoleWindow>false</FlowsheetShowConsoleWindow>
    <FlowsheetShowCOReportsWindow>false</FlowsheetShowCOReportsWindow>
    <FlowsheetShowWatchWindow>false</FlowsheetShowWatchWindow>
    <FlowsheetMultiSelectMode>false</FlowsheetMultiSelectMode>
    <FlowsheetSnapToGrid>false</FlowsheetSnapToGrid>
    <FlowsheetDisplayGrid>false</FlowsheetDisplayGrid>
    <FractionNumberFormat>G8</FractionNumberFormat>
    <Key>844A7263357F5F4E97B7A6BDC498AE26C02E9A7E</Key>
    <NumberFormat>G6</NumberFormat>
    <Password></Password>
    <SimulationAuthor>DESKTOP-RKB5BM8\User</SimulationAuthor>
    <SimulationComments></SimulationComments>
    <SimulationName>MySimulation_36</SimulationName>
    <UsePassword>false</UsePassword>
    <SelectedUnitSystem1>
      <Type>DWSIM.SharedClasses.SystemsOfUnits.SIUnits_Custom5</Type>
      <accel>m/s2</accel>
      <activity>Pa</activity>
      <activityCoefficient>-</activityCoefficient>
      <area>m2</area>
      <cakeresistance>m/kg</cakeresistance>
      <cinematic_viscosity>m2/s</cinematic_viscosity>
      <compressibility>1/Pa</compressibility>
      <compressibilityfactor>-</compressibilityfactor>
      <deltaP>bar</deltaP>
      <deltaT>C.</deltaT>
      <density>kg/m3</density>
      <diameter>mm</diameter>
      <distance>m</distance>
      <enthalpy>kJ/kg</enthalpy>
      <entropy>kJ/[kg.K]</entropy>
      <excessEnthalpy>kJ/kg</excessEnthalpy>
      <excessEntropy>kJ/[kg.K]</excessEntropy>
      <force>N</force>
      <foulingfactor>K.m2/W</foulingfactor>
      <fugacity>Pa</fugacity>
      <fugacityCoefficient>-</fugacityCoefficient>
      <gor>m3/m3</gor>
      <head>m</head>
      <heat_transf_coeff>W/[m2.K]</heat_transf_coeff>
      <heatCapacityCp>kJ/[kg.K]</heatCapacityCp>
      <heatCapacityCv>kJ/[kg.K]</heatCapacityCv>
      <heatflow>kW</heatflow>
      <heat>kJ</heat>
      <idealGasHeatCapacity>kJ/[kg.K]</idealGasHeatCapacity>
      <jouleThomsonCoefficient>K/Pa</jouleThomsonCoefficient>
      <kvalue>-</kvalue>
      <logfugacityCoefficient>-</logfugacityCoefficient>
      <logKvalue>-</logKvalue>
      <mass>kg</mass>
      <mass_conc>kg/m3</mass_conc>
      <massflow>kg/h</massflow>
      <massfraction>-</massfraction>
      <mediumresistance>m-1</mediumresistance>
      <molar_conc>kmol/m3</molar_conc>
      <molar_enthalpy>kJ/kmol</molar_enthalpy>
      <molar_entropy>kJ/[kmol.K]</molar_entropy>
      <molar_volume>m3/kmol</molar_volume>
      <molarflow>kmol/h</molarflow>
      <molarfraction>-</molarfraction>
      <molecularWeight>kg/kmol</molecularWeight>
      <Name>C5</Name>
      <pdp_boilingPointTemperature>C</pdp_boilingPointTemperature>
      <pdp_meltingTemperature>C</pdp_meltingTemperature>
      <pressure>bar</pressure>
      <reac_rate>kmol/[m3.h]</reac_rate>
      <reac_rate_heterog>kmol/[kg.s]</reac_rate_heterog>
      <spec_vol>m3/kg</spec_vol>
      <speedOfSound>m/s</speedOfSound>
      <surfaceTension>N/m</surfaceTension>
      <temperature>C</temperature>
      <thermalConductivity>W/[m.K]</thermalConductivity>
      <thermalConductivityOfLiquid>W/[m.K]</thermalConductivityOfLiquid>
      <thermalConductivityOfVapor>W/[m.K]</thermalConductivityOfVapor>
      <thickness>mm</thickness>
      <time>h</time>
      <vaporPressure>bar</vaporPressure>
      <velocity>m/s</velocity>
      <viscosity>Pa.s</viscosity>
      <viscosityOfLiquid>Pa.s</viscosityOfLiquid>
      <viscosityOfVapor>Pa.s</viscosityOfVapor>
      <volume>m3</volume>
      <volumetricFlow>m3/h</volumetricFlow>
      <diffusivity>m2/s</diffusivity>
      <conductance>[kg/s]/[Pa^0.5]</conductance>
      <mole>kmol</mole>
      <emission_factor>[kg/s]/kW</emission_factor>
      <specific_power>kW/[kg/s]</specific_power>
    </SelectedUnitSystem1>
    <SimultaneousAdjustSolverEnabled>true</SimultaneousAdjustSolverEnabled>
    <SpreadsheetUseRegionalSeparator>false</SpreadsheetUseRegionalSeparator>
    <EnergyBalanceCheck>ShowWarning</EnergyBalanceCheck>
    <MassBalanceCheck>ShowWarning</MassBalanceCheck>
    <EnergyBalanceRelativeTolerance>0.01</EnergyBalanceRelativeTolerance>
    <MassBalanceRelativeTolerance>0.01</MassBalanceRelativeTolerance>
    <DisplayCornerPropertyList>false</DisplayCornerPropertyList>
    <DisplayCornerPropertyListPosition>RightBottom</DisplayCornerPropertyListPosition>
    <DisplayFloatingPropertyTables>true</DisplayFloatingPropertyTables>
    <DisplayCornerPropertyListFontColor>DimGray</DisplayCornerPropertyListFontColor>
    <DisplayCornerPropertyListFontName>Consolas</DisplayCornerPropertyListFontName>
    <DisplayCornerPropertyListFontSize>8</DisplayCornerPropertyListFontSize>
    <DisplayCornerPropertyListPadding>4</DisplayCornerPropertyListPadding>
    <DefaultFloatingTableCompoundAmountBasis>Molar_Fractions</DefaultFloatingTableCompoundAmountBasis>
    <DisplayFloatingTableCompoundAmounts>true</DisplayFloatingTableCompoundAmounts>
    <SpreadsheetUnitLockingMode>true</SpreadsheetUnitLockingMode>
    <CompoundOrderingMode>AsAdded</CompoundOrderingMode>
    <FlowsheetControlPanelMode>false</FlowsheetControlPanelMode>
    <SkipEquilibriumCalculationOnDefinedStreams>true</SkipEquilibriumCalculationOnDefinedStreams>
    <ForceStreamPhase>None</ForceStreamPhase>
    <DisplayUserDefinedPropertiesEditor>false</DisplayUserDefinedPropertiesEditor>
    <LabelFontSize>10</LabelFontSize>
    <FlowsheetColorTheme>0</FlowsheetColorTheme>
    <RegularFontName>OpenSans_SemiCondensed-Regular</RegularFontName>
    <BoldFontName>OpenSans_SemiCondensed-SemiBold</BoldFontName>
    <ItalicFontName>OpenSans_SemiCondensed-Italic</ItalicFontName>
    <BoldItalicFontName>OpenSans_SemiCondensed-MediumItalic</BoldItalicFontName>
    <DisplayEnergyStreamPowerValue>true</DisplayEnergyStreamPowerValue>
    <DisplayMaterialStreamMassFlowValue>false</DisplayMaterialStreamMassFlowValue>
    <DisplayMaterialStreamMolarFlowValue>false</DisplayMaterialStreamMolarFlowValue>
    <DisplayMaterialStreamVolFlowValue>false</DisplayMaterialStreamVolFlowValue>
    <DisplayMaterialStreamTemperatureValue>false</DisplayMaterialStreamTemperatureValue>
    <DisplayMaterialStreamPressureValue>false</DisplayMaterialStreamPressureValue>
    <DisplayMaterialStreamEnergyFlowValue>false</DisplayMaterialStreamEnergyFlowValue>
    <AddObjectsWithStreams>2</AddObjectsWithStreams>
    <DisplayDynamicPropertyValues>true</DisplayDynamicPropertyValues>
    <CurrentWeather>
      <Type>DWSIM.SharedClasses.WeatherData</Type>
      <CurrentCondition>Sunny</CurrentCondition>
      <WindSpeed_km_h>5</WindSpeed_km_h>
      <RelativeHumidity_pct>30</RelativeHumidity_pct>
      <Temperature_C>30</Temperature_C>
      <SolarIrradiation_kWh_m2>1</SolarIrradiation_kWh_m2>
      <Latitude>0</Latitude>
      <Longitude>0</Longitude>
      <AtmosphericPressure_Pa>101325</AtmosphericPressure_Pa>
    </CurrentWeather>
    <CustomCalculationOrder />
    <SpecCalculationMode>AfterSourceObject</SpecCalculationMode>
    <ForceObjectSolving>true</ForceObjectSolving>
    <SaveFlowsheetMessagesInFile>true</SaveFlowsheetMessagesInFile>
    <RTFAnnotations></RTFAnnotations>
    <EnabledUndoRedo>false</EnabledUndoRedo>
    <EnableGHGEmissionsSubsystem>false</EnableGHGEmissionsSubsystem>
    <FlowsheetTransitionObject>
      <Type>DWSIM.SharedClasses.DWSIM.Flowsheet.FlowsheetTransitionRestore</Type>
      <FeatureName></FeatureName>
      <FeatureType></FeatureType>
      <Action></Action>
      <Location></Location>
      <Position />
    </FlowsheetTransitionObject>
    <UniqueID>e75bd31f-dd11-4c72-8f89-1dbf265a216c</UniqueID>
    <RestoreUnitOperationStateAfterError>false</RestoreUnitOperationStateAfterError>
    <VisibleProperties>
      <ObjectType Value="AbsorptionColumn">
        <PropertyID Value="PROP_AC_0" />
        <PropertyID Value="PROP_AC_1" />
        <PropertyID Value="PROP_AC_2" />
        <PropertyID Value="Estimated Height" />
        <PropertyID Value="Estimated Diameter" />
        <PropertyID Value="Number of Stages" />
      </ObjectType>
      <ObjectType Value="Adjust">
        <PropertyID Value="MinVal" />
        <PropertyID Value="MaxVal" />
        <PropertyID Value="AdjustValue" />
        <PropertyID Value="Tolerance" />
        <PropertyID Value="StepSize" />
        <PropertyID Value="MaximumIterations" />
      </ObjectType>
      <ObjectType Value="AnalogGauge">
        <PropertyID Value="Monitored Value" />
      </ObjectType>
      <ObjectType Value="CapeOpenUO" />
      <ObjectType Value="ComponentSeparator">
        <PropertyID Value="PROP_CP_0" />
        <PropertyID Value="SpecifiedStreamIndex" />
      </ObjectType>
      <ObjectType Value="Compressor">
        <PropertyID Value="PROP_CO_0" />
        <PropertyID Value="PROP_CO_1" />
        <PropertyID Value="PROP_CO_2" />
        <PropertyID Value="PROP_CO_3" />
        <PropertyID Value="PROP_CO_4" />
        <PropertyID Value="PolytropicEfficiency" />
        <PropertyID Value="AdiabaticCoefficient" />
        <PropertyID Value="PolytropicCoefficient" />
        <PropertyID Value="AdiabaticHead" />
        <PropertyID Value="PolytropicHead" />
        <PropertyID Value="RotationSpeed" />
        <PropertyID Value="PressureRatio" />
      </ObjectType>
      <ObjectType Value="Cooler">
        <PropertyID Value="Flow Conductance" />
        <PropertyID Value="Volume" />
        <PropertyID Value="Minimum Pressure" />
        <PropertyID Value="Initialize using Inlet Stream" />
        <PropertyID Value="Reset Content" />
        <PropertyID Value="PROP_CL_0" />
        <PropertyID Value="PROP_CL_1" />
        <PropertyID Value="PROP_CL_2" />
        <PropertyID Value="PROP_CL_3" />
        <PropertyID Value="PROP_CL_4" />
        <PropertyID Value="PROP_CL_5" />
      </ObjectType>
      <ObjectType Value="CustomUO" />
      <ObjectType Value="DigitalGauge">
        <PropertyID Value="Monitored Value" />
      </ObjectType>
      <ObjectType Value="DistillationColumn">
        <PropertyID Value="PROP_DC_2" />
        <PropertyID Value="PROP_DC_5" />
        <PropertyID Value="PROP_DC_6" />
        <PropertyID Value="PROP_DC_7" />
        <PropertyID Value="PROP_DC_8" />
        <PropertyID Value="Condenser_Specification_Value" />
        <PropertyID Value="Reboiler_Specification_Value" />
        <PropertyID Value="Global_Stage_Efficiency" />
        <PropertyID Value="Condenser_Calculated_Value" />
        <PropertyID Value="Reboiler_Calculated_Value" />
        <PropertyID Value="Estimated Height" />
        <PropertyID Value="Estimated Diameter" />
      </ObjectType>
      <ObjectType Value="DummyUnitOperation" />
      <ObjectType Value="EnergyRecycle">
        <PropertyID Value="PROP_ER_0" />
        <PropertyID Value="PROP_ER_1" />
        <PropertyID Value="PROP_ER_2" />
      </ObjectType>
      <ObjectType Value="EnergyStream">
        <PropertyID Value="PROP_ES_0" />
      </ObjectType>
      <ObjectType Value="ExcelUO">
        <PropertyID Value="Calc_dQ" />
      </ObjectType>
      <ObjectType Value="Expander">
        <PropertyID Value="PROP_TU_0" />
        <PropertyID Value="PROP_TU_1" />
        <PropertyID Value="PROP_TU_2" />
        <PropertyID Value="PROP_TU_3" />
        <PropertyID Value="PROP_TU_4" />
        <PropertyID Value="PolytropicEfficiency" />
        <PropertyID Value="AdiabaticCoefficient" />
        <PropertyID Value="PolytropicCoefficient" />
        <PropertyID Value="AdiabaticHead" />
        <PropertyID Value="PolytropicHead" />
        <PropertyID Value="RotationSpeed" />
        <PropertyID Value="PressureRatio" />
      </ObjectType>
      <ObjectType Value="Filter">
        <PropertyID Value="PROP_FT_0" />
        <PropertyID Value="PROP_FT_1" />
        <PropertyID Value="PROP_FT_2" />
        <PropertyID Value="PROP_FT_3" />
        <PropertyID Value="PROP_FT_4" />
        <PropertyID Value="PROP_FT_5" />
        <PropertyID Value="PROP_FT_6" />
        <PropertyID Value="PROP_FT_7" />
      </ObjectType>
      <ObjectType Value="Flowsheet" />
      <ObjectType Value="Heater">
        <PropertyID Value="Flow Conductance" />
        <PropertyID Value="Volume" />
        <PropertyID Value="Minimum Pressure" />
        <PropertyID Value="Initialize using Inlet Stream" />
        <PropertyID Value="Reset Content" />
        <PropertyID Value="PROP_HT_0" />
        <PropertyID Value="PROP_HT_1" />
        <PropertyID Value="PROP_HT_2" />
        <PropertyID Value="PROP_HT_3" />
        <PropertyID Value="PROP_HT_4" />
        <PropertyID Value="PROP_HT_5" />
      </ObjectType>
      <ObjectType Value="HeatExchanger">
        <PropertyID Value="PROP_HX_0" />
        <PropertyID Value="PROP_HX_1" />
        <PropertyID Value="PROP_HX_2" />
        <PropertyID Value="PROP_HX_3" />
        <PropertyID Value="PROP_HX_4" />
        <PropertyID Value="PROP_HX_25" />
        <PropertyID Value="PROP_HX_26" />
        <PropertyID Value="PROP_HX_27" />
        <PropertyID Value="PROP_HX_28" />
        <PropertyID Value="PROP_HX_32" />
        <PropertyID Value="PROP_HX_33" />
      </ObjectType>
      <ObjectType Value="Input" />
      <ObjectType Value="LevelGauge">
        <PropertyID Value="Monitored Value" />
      </ObjectType>
      <ObjectType Value="MaterialStream">
        <PropertyID Value="PROP_MS_0" />
        <PropertyID Value="PROP_MS_1" />
        <PropertyID Value="PROP_MS_2" />
        <PropertyID Value="PROP_MS_3" />
        <PropertyID Value="PROP_MS_4" />
        <PropertyID Value="PROP_MS_9" />
        <PropertyID Value="PROP_MS_10" />
        <PropertyID Value="PROP_MS_27" />
        <PropertyID Value="PROP_MS_130" />
        <PropertyID Value="PROP_MS_154" />
      </ObjectType>
      <ObjectType Value="Mixer" />
      <ObjectType Value="OrificePlate">
        <PropertyID Value="PROP_OP_0" />
        <PropertyID Value="PROP_OP_1" />
        <PropertyID Value="PROP_OP_2" />
        <PropertyID Value="PROP_OP_3" />
        <PropertyID Value="PROP_OP_4" />
        <PropertyID Value="PROP_OP_5" />
        <PropertyID Value="PROP_OP_6" />
        <PropertyID Value="PROP_OP_7" />
      </ObjectType>
      <ObjectType Value="PIDController">
        <PropertyID Value="Active" />
        <PropertyID Value="ManualOverride" />
        <PropertyID Value="LastError" />
        <PropertyID Value="CurrentError" />
        <PropertyID Value="CumulativeError" />
        <PropertyID Value="SetPointAbs" />
        <PropertyID Value="Kp" />
        <PropertyID Value="Ki" />
        <PropertyID Value="Kd" />
        <PropertyID Value="Output" />
        <PropertyID Value="OutputMin" />
        <PropertyID Value="OutputMax" />
        <PropertyID Value="OutputAbs" />
      </ObjectType>
      <ObjectType Value="Pipe">
        <PropertyID Value="PROP_PS_0" />
        <PropertyID Value="PressureDropStatic" />
        <PropertyID Value="PressureDropFriction" />
        <PropertyID Value="PROP_PS_1" />
        <PropertyID Value="PROP_PS_2" />
        <PropertyID Value="PROP_PS_8" />
        <PropertyID Value="PROP_PS_9" />
      </ObjectType>
      <ObjectType Value="Pump">
        <PropertyID Value="PROP_PU_0" />
        <PropertyID Value="PROP_PU_1" />
        <PropertyID Value="PROP_PU_2" />
        <PropertyID Value="PROP_PU_3" />
        <PropertyID Value="PROP_PU_4" />
        <PropertyID Value="PROP_PU_5" />
        <PropertyID Value="PROP_PU_6" />
        <PropertyID Value="PROP_PU_7" />
      </ObjectType>
      <ObjectType Value="PythonController">
        <PropertyID Value="Active" />
        <PropertyID Value="SetPoint" />
        <PropertyID Value="Output" />
      </ObjectType>
      <ObjectType Value="Reactor_Conversion">
        <PropertyID Value="Operating Pressure (Dynamics)" />
        <PropertyID Value="Liquid Level" />
        <PropertyID Value="Volume" />
        <PropertyID Value="Height" />
        <PropertyID Value="Minimum Pressure" />
        <PropertyID Value="Initialize using Inlet Stream" />
        <PropertyID Value="Reset Contents" />
        <PropertyID Value="PROP_CR_0" />
        <PropertyID Value="Calculation Mode" />
      </ObjectType>
      <ObjectType Value="Reactor_CSTR">
        <PropertyID Value="Operating Pressure" />
        <PropertyID Value="Liquid Level" />
        <PropertyID Value="Height" />
        <PropertyID Value="Minimum Pressure" />
        <PropertyID Value="Initialize using Inlet Stream" />
        <PropertyID Value="Reset Contents" />
        <PropertyID Value="PROP_CS_0" />
        <PropertyID Value="PROP_CS_1" />
        <PropertyID Value="PROP_CS_2" />
        <PropertyID Value="PROP_CS_3" />
        <PropertyID Value="PROP_CS_4" />
        <PropertyID Value="PROP_CS_5" />
        <PropertyID Value="PROP_CS_6" />
        <PropertyID Value="PROP_CS_7" />
        <PropertyID Value="Calculation Mode" />
      </ObjectType>
      <ObjectType Value="Reactor_Equilibrium">
        <PropertyID Value="Operating Pressure (Dynamics)" />
        <PropertyID Value="Liquid Level" />
        <PropertyID Value="Volume" />
        <PropertyID Value="Height" />
        <PropertyID Value="Minimum Pressure" />
        <PropertyID Value="Initialize using Inlet Stream" />
        <PropertyID Value="Reset Contents" />
        <PropertyID Value="PROP_EQ_0" />
        <PropertyID Value="PROP_EQ_1" />
        <PropertyID Value="Calculation Mode" />
        <PropertyID Value="Initial Gibbs Energy" />
        <PropertyID Value="Final Gibbs Energy" />
      </ObjectType>
      <ObjectType Value="Reactor_Gibbs">
        <PropertyID Value="Operating Pressure (Dynamics)" />
        <PropertyID Value="Liquid Level" />
        <PropertyID Value="Volume" />
        <PropertyID Value="Height" />
        <PropertyID Value="Minimum Pressure" />
        <PropertyID Value="Initialize using Inlet Stream" />
        <PropertyID Value="Reset Contents" />
        <PropertyID Value="PROP_GR_0" />
        <PropertyID Value="PROP_GR_1" />
        <PropertyID Value="Calculation Mode" />
        <PropertyID Value="Initial Gibbs Energy" />
        <PropertyID Value="Final Gibbs Energy" />
        <PropertyID Value="Element Balance Residue" />
      </ObjectType>
      <ObjectType Value="Reactor_PFR">
        <PropertyID Value="Max Sections" />
        <PropertyID Value="Reset Contents" />
        <PropertyID Value="PROP_PF_0" />
        <PropertyID Value="PROP_PF_1" />
        <PropertyID Value="PROP_PF_2" />
        <PropertyID Value="PROP_PF_3" />
        <PropertyID Value="PROP_PF_4" />
        <PropertyID Value="PROP_PF_5" />
        <PropertyID Value="PROP_PF_6" />
        <PropertyID Value="PROP_PF_7" />
        <PropertyID Value="PROP_PF_8" />
        <PropertyID Value="PROP_PF_9" />
        <PropertyID Value="PROP_PF_10" />
        <PropertyID Value="PROP_PF_11" />
        <PropertyID Value="PROP_PF_12" />
        <PropertyID Value="Calculation Mode" />
      </ObjectType>
      <ObjectType Value="Recycle">
        <PropertyID Value="PROP_RY_0" />
        <PropertyID Value="PROP_RY_1" />
        <PropertyID Value="PROP_RY_2" />
        <PropertyID Value="PROP_RY_3" />
        <PropertyID Value="PROP_RY_4" />
        <PropertyID Value="PROP_RY_5" />
        <PropertyID Value="PROP_RY_6" />
      </ObjectType>
      <ObjectType Value="ShortcutColumn">
        <PropertyID Value="PROP_SC_0" />
        <PropertyID Value="PROP_SC_1" />
        <PropertyID Value="PROP_SC_2" />
        <PropertyID Value="PROP_SC_3" />
        <PropertyID Value="PROP_SC_4" />
        <PropertyID Value="PROP_SC_5" />
        <PropertyID Value="PROP_SC_6" />
        <PropertyID Value="PROP_SC_7" />
        <PropertyID Value="PROP_SC_8" />
        <PropertyID Value="PROP_SC_9" />
        <PropertyID Value="PROP_SC_10" />
        <PropertyID Value="PROP_SC_11" />
        <PropertyID Value="PROP_SC_12" />
        <PropertyID Value="PROP_SC_13" />
        <PropertyID Value="PROP_SC_14" />
        <PropertyID Value="Stage Height" />
        <PropertyID Value="Estimated Height" />
        <PropertyID Value="Estimated Diameter" />
      </ObjectType>
      <ObjectType Value="SolidsSeparator">
        <PropertyID Value="PROP_SS_1" />
        <PropertyID Value="PROP_SS_2" />
      </ObjectType>
      <ObjectType Value="Spec">
        <PropertyID Value="SpecMin" />
        <PropertyID Value="SpecMax" />
        <PropertyID Value="Expression" />
      </ObjectType>
      <ObjectType Value="Splitter">
        <PropertyID Value="PROP_SP_1" />
        <PropertyID Value="PROP_SP_2" />
      </ObjectType>
      <ObjectType Value="Switch" />
      <ObjectType Value="Tank">
        <PropertyID Value="Liquid Level" />
        <PropertyID Value="Height" />
        <PropertyID Value="Initialize using Inlet Stream" />
        <PropertyID Value="Reset Content" />
        <PropertyID Value="PROP_TK_0" />
        <PropertyID Value="PROP_TK_1" />
        <PropertyID Value="PROP_TK_2" />
      </ObjectType>
      <ObjectType Value="Valve">
        <PropertyID Value="Actuator Delay" />
        <PropertyID Value="PROP_VA_0" />
        <PropertyID Value="PROP_VA_1" />
        <PropertyID Value="PROP_VA_2" />
        <PropertyID Value="PROP_VA_3" />
        <PropertyID Value="PROP_VA_4" />
        <PropertyID Value="PROP_VA_5" />
        <PropertyID Value="PROP_VA_6" />
        <PropertyID Value="Actual Flow Coefficient" />
      </ObjectType>
      <ObjectType Value="Vessel">
        <PropertyID Value="Vessel Orientation" />
        <PropertyID Value="Operating Pressure" />
        <PropertyID Value="Liquid Level" />
        <PropertyID Value="Get Volume from Dimensions" />
        <PropertyID Value="Volume" />
        <PropertyID Value="Get Height from Dimensions" />
        <PropertyID Value="Height" />
        <PropertyID Value="Minimum Pressure" />
        <PropertyID Value="Initialize using Inlet Stream" />
        <PropertyID Value="Reset Content" />
        <PropertyID Value="PROP_SV_0" />
        <PropertyID Value="PROP_SV_1" />
      </ObjectType>
      <ObjectType Value="NeuralNetworkUnitOperation">
        <PropertyID Value="Status" />
        <PropertyID Value="Status" />
      </ObjectType>
      <ObjectType Value="HydroelectricTurbine">
        <PropertyID Value="Efficiency" />
        <PropertyID Value="Static Head" />
        <PropertyID Value="Velocity Head" />
        <PropertyID Value="Total Head" />
        <PropertyID Value="Inlet Velocity" />
        <PropertyID Value="Outlet Velocity" />
        <PropertyID Value="Generated Power" />
      </ObjectType>
      <ObjectType Value="PEMFC_Amphlett">
        <PropertyID Value="i-start" />
        <PropertyID Value="i-stop" />
        <PropertyID Value="i-step" />
        <PropertyID Value="A" />
        <PropertyID Value="l" />
        <PropertyID Value="lambda" />
        <PropertyID Value="R" />
        <PropertyID Value="JMax" />
        <PropertyID Value="N" />
      </ObjectType>
      <ObjectType Value="SolarPanel">
        <PropertyID Value="Efficiency" />
        <PropertyID Value="User-Defined Solar Irradiation" />
        <PropertyID Value="Actual Solar Irradiation" />
        <PropertyID Value="Panel Area" />
        <PropertyID Value="Number of Panels" />
        <PropertyID Value="Generated Power" />
      </ObjectType>
      <ObjectType Value="WaterElectrolyzer">
        <PropertyID Value="Voltage" />
        <PropertyID Value="Thermoneutral Voltage" />
        <PropertyID Value="Reversible Voltage" />
        <PropertyID Value="Number of Cells" />
        <PropertyID Value="Cell Voltage" />
        <PropertyID Value="Waste Heat" />
        <PropertyID Value="Current" />
        <PropertyID Value="Electron Transfer" />
        <PropertyID Value="Efficiency" />
        <PropertyID Value="Input Efficiency" />
      </ObjectType>
      <ObjectType Value="WindTurbine">
        <PropertyID Value="Efficiency" />
        <PropertyID Value="User-Defined Wind Speed" />
        <PropertyID Value="Actual Wind Speed" />
        <PropertyID Value="User-Defined Air Temperature" />
        <PropertyID Value="Actual Air Temperature" />
        <PropertyID Value="User-Defined Air Pressure" />
        <PropertyID Value="Actual Air Pressure" />
        <PropertyID Value="User-Defined Relative Humidity" />
        <PropertyID Value="Actual Relative Humidity" />
        <PropertyID Value="Disk Area" />
        <PropertyID Value="Rotor Diameter" />
        <PropertyID Value="Number of Units" />
        <PropertyID Value="Generated Power" />
        <PropertyID Value="Maximum Theoretical Power" />
        <PropertyID Value="Calculated Air Density" />
      </ObjectType>
      <ObjectType Value="Reactor_ReaktoroGibbs" />
    </VisibleProperties>
  </Settings>
  <DynamicProperties />
  <GraphicObjects>
    <GraphicObject>
      <Type>DWSIM.Drawing.SkiaSharp.GraphicObjects.Shapes.MaterialStreamGraphic</Type>
      <SemiTransparent>false</SemiTransparent>
      <LineWidth>1</LineWidth>
      <GradientMode>true</GradientMode>
      <LineColor>#ff4682b4</LineColor>
      <LineColorDark>#fff5f5f5</LineColorDark>
      <Fill>true</Fill>
      <FillColor>#ffffffff</FillColor>
      <FillColorDark>#ffffffff</FillColorDark>
      <GradientColor1>#ffd3d3d3</GradientColor1>
      <GradientColor2>#ffffffff</GradientColor2>
      <FontSize>10</FontSize>
      <OverrideColors>false</OverrideColors>
      <FontStyle>Bold</FontStyle>
      <Calculated>true</Calculated>
      <Active>true</Active>
      <Description>Material Stream</Description>
      <FlippedH>false</FlippedH>
      <FlippedV>false</FlippedV>
      <IsEnergyStream>false</IsEnergyStream>
      <ObjectType>MaterialStream</ObjectType>
      <Shape>0</Shape>
      <ShapeOverride>DefaultShape</ShapeOverride>
      <Status>Calculated</Status>
      <AutoSize>false</AutoSize>
      <Height>20</Height>
      <IsConnector>false</IsConnector>
      <Name>MAT-74ccf612-ceca-42d3-be4b-99be4e44403c</Name>
      <Tag>Feed</Tag>
      <Width>20</Width>
      <X>84</X>
      <Y>119</Y>
      <Selected>false</Selected>
      <Rotation>0</Rotation>
      <DrawMode>0</DrawMode>
      <DrawLabel>true</DrawLabel>
      <InputConnectors>
        <Connector IsAttached="false" />
      </InputConnectors>
      <OutputConnectors>
        <Connector IsAttached="true" ConnType="ConOut" AttachedToObjID="CSTR-0d4ae06a-1a6d-4af2-9208-57387f7ee67d" AttachedToConnIndex="0" AttachedToEnergyConn="False" />
      </OutputConnectors>
      <EnergyConnector>
        <Connector IsAttached="false" />
      </EnergyConnector>
      <SpecialConnectors />
    </GraphicObject>
    <GraphicObject>
      <Type>DWSIM.Drawing.SkiaSharp.GraphicObjects.Shapes.CSTRGraphic</Type>
      <SemiTransparent>false</SemiTransparent>
      <LineWidth>1</LineWidth>
      <GradientMode>true</GradientMode>
      <LineColor>#ff4682b4</LineColor>
      <LineColorDark>#fff5f5f5</LineColorDark>
      <Fill>true</Fill>
      <FillColor>#ffffffff</FillColor>
      <FillColorDark>#ffffffff</FillColorDark>
      <GradientColor1>#ffd3d3d3</GradientColor1>
      <GradientColor2>#ffffffff</GradientColor2>
      <FontSize>10</FontSize>
      <OverrideColors>false</OverrideColors>
      <FontStyle>Bold</FontStyle>
      <Calculated>true</Calculated>
      <Active>true</Active>
      <Description>CSTR</Description>
      <FlippedH>false</FlippedH>
      <FlippedV>false</FlippedV>
      <IsEnergyStream>false</IsEnergyStream>
      <ObjectType>RCT_CSTR</ObjectType>
      <Shape>0</Shape>
      <ShapeOverride>DefaultShape</ShapeOverride>
      <Status>Calculated</Status>
      <AutoSize>false</AutoSize>
      <Height>50</Height>
      <IsConnector>false</IsConnector>
      <Name>CSTR-0d4ae06a-1a6d-4af2-9208-57387f7ee67d</Name>
      <Tag>CSTR-1</Tag>
      <Width>50</Width>
      <X>190</X>
      <Y>123</Y>
      <Selected>true</Selected>
      <Rotation>0</Rotation>
      <DrawMode>0</DrawMode>
      <DrawLabel>true</DrawLabel>
      <InputConnectors>
        <Connector IsAttached="true" ConnType="ConIn" AttachedFromObjID="MAT-74ccf612-ceca-42d3-be4b-99be4e44403c" AttachedFromConnIndex="0" AttachedFromEnergyConn="False" />
        <Connector IsAttached="true" ConnType="ConEn" AttachedFromObjID="EN-542636a7-33d3-4a63-a18a-dc59bfe40459" AttachedFromConnIndex="0" AttachedFromEnergyConn="True" />
      </InputConnectors>
      <OutputConnectors>
        <Connector IsAttached="true" ConnType="ConOut" AttachedToObjID="MAT-d456af80-baca-4162-ba65-7ae84575ce5f" AttachedToConnIndex="0" AttachedToEnergyConn="False" />
        <Connector IsAttached="false" />
      </OutputConnectors>
      <EnergyConnector>
        <Connector IsAttached="false" />
      </EnergyConnector>
      <SpecialConnectors />
    </GraphicObject>
    <GraphicObject>
      <Type>DWSIM.Drawing.SkiaSharp.GraphicObjects.Shapes.MaterialStreamGraphic</Type>
      <SemiTransparent>false</SemiTransparent>
      <LineWidth>1</LineWidth>
      <GradientMode>true</GradientMode>
      <LineColor>#ff4682b4</LineColor>
      <LineColorDark>#fff5f5f5</LineColorDark>
      <Fill>true</Fill>
      <FillColor>#ffffffff</FillColor>
      <FillColorDark>#ffffffff</FillColorDark>
      <GradientColor1>#ffd3d3d3</GradientColor1>
      <GradientColor2>#ffffffff</GradientColor2>
      <FontSize>10</FontSize>
      <OverrideColors>false</OverrideColors>
      <FontStyle>Bold</FontStyle>
      <Calculated>true</Calculated>
      <Active>true</Active>
      <Description>Material Stream</Description>
      <FlippedH>false</FlippedH>
      <FlippedV>false</FlippedV>
      <IsEnergyStream>false</IsEnergyStream>
      <ObjectType>MaterialStream</ObjectType>
      <Shape>0</Shape>
      <ShapeOverride>DefaultShape</ShapeOverride>
      <Status>Calculated</Status>
      <AutoSize>false</AutoSize>
      <Height>20</Height>
      <IsConnector>false</IsConnector>
      <Name>MAT-d456af80-baca-4162-ba65-7ae84575ce5f</Name>
      <Tag>2</Tag>
      <Width>20</Width>
      <X>450</X>
      <Y>129</Y>
      <Selected>false</Selected>
      <Rotation>0</Rotation>
      <DrawMode>0</DrawMode>
      <DrawLabel>true</DrawLabel>
      <InputConnectors>
        <Connector IsAttached="true" ConnType="ConIn" AttachedFromObjID="CSTR-0d4ae06a-1a6d-4af2-9208-57387f7ee67d" AttachedFromConnIndex="0" AttachedFromEnergyConn="False" />
      </InputConnectors>
      <OutputConnectors>
        <Connector IsAttached="false" />
      </OutputConnectors>
      <EnergyConnector>
        <Connector IsAttached="false" />
      </EnergyConnector>
      <SpecialConnectors />
    </GraphicObject>
    <GraphicObject>
      <Type>DWSIM.Drawing.SkiaSharp.GraphicObjects.Shapes.EnergyStreamGraphic</Type>
      <SemiTransparent>false</SemiTransparent>
      <LineWidth>1</LineWidth>
      <GradientMode>true</GradientMode>
      <LineColor>#ff4682b4</LineColor>
      <LineColorDark>#fff5f5f5</LineColorDark>
      <Fill>true</Fill>
      <FillColor>#ffd3d3d3</FillColor>
      <FillColorDark>#ffffffff</FillColorDark>
      <GradientColor1>#ffd3d3d3</GradientColor1>
      <GradientColor2>#ffffffff</GradientColor2>
      <FontSize>10</FontSize>
      <OverrideColors>false</OverrideColors>
      <FontStyle>Bold</FontStyle>
      <Calculated>true</Calculated>
      <Active>true</Active>
      <Description>Energy Stream</Description>
      <FlippedH>false</FlippedH>
      <FlippedV>false</FlippedV>
      <IsEnergyStream>true</IsEnergyStream>
      <ObjectType>EnergyStream</ObjectType>
      <Shape>0</Shape>
      <ShapeOverride>DefaultShape</ShapeOverride>
      <Status>Calculated</Status>
      <AutoSize>false</AutoSize>
      <Height>20</Height>
      <IsConnector>false</IsConnector>
      <Name>EN-542636a7-33d3-4a63-a18a-dc59bfe40459</Name>
      <Tag>E1</Tag>
      <Width>20</Width>
      <X>146</X>
      <Y>208</Y>
      <Selected>false</Selected>
      <Rotation>0</Rotation>
      <DrawMode>0</DrawMode>
      <DrawLabel>true</DrawLabel>
      <InputConnectors>
        <Connector IsAttached="false" />
      </InputConnectors>
      <OutputConnectors>
        <Connector IsAttached="true" ConnType="ConOut" AttachedToObjID="CSTR-0d4ae06a-1a6d-4af2-9208-57387f7ee67d" AttachedToConnIndex="1" AttachedToEnergyConn="False" />
      </OutputConnectors>
      <EnergyConnector>
        <Connector IsAttached="false" />
      </EnergyConnector>
      <SpecialConnectors />
    </GraphicObject>
    <GraphicObject>
      <Type>DWSIM.Drawing.SkiaSharp.GraphicObjects.Shapes.AdjustGraphic</Type>
      <ConnectedToMv>
        <Type>DWSIM.Drawing.SkiaSharp.GraphicObjects.Shapes.CSTRGraphic</Type>
        <SemiTransparent>false</SemiTransparent>
        <LineWidth>1</LineWidth>
        <GradientMode>true</GradientMode>
        <LineColor>#ff4682b4</LineColor>
        <LineColorDark>#fff5f5f5</LineColorDark>
        <Fill>true</Fill>
        <FillColor>#ffffffff</FillColor>
        <FillColorDark>#ffffffff</FillColorDark>
        <GradientColor1>#ffd3d3d3</GradientColor1>
        <GradientColor2>#ffffffff</GradientColor2>
        <FontSize>10</FontSize>
        <OverrideColors>false</OverrideColors>
        <FontStyle>Bold</FontStyle>
        <Calculated>true</Calculated>
        <Active>true</Active>
        <Description>CSTR</Description>
        <FlippedH>false</FlippedH>
        <FlippedV>false</FlippedV>
        <IsEnergyStream>false</IsEnergyStream>
        <ObjectType>RCT_CSTR</ObjectType>
        <Shape>0</Shape>
        <ShapeOverride>DefaultShape</ShapeOverride>
        <Status>Calculated</Status>
        <AutoSize>false</AutoSize>
        <Height>50</Height>
        <IsConnector>false</IsConnector>
        <Name>CSTR-0d4ae06a-1a6d-4af2-9208-57387f7ee67d</Name>
        <Tag>CSTR-1</Tag>
        <Width>50</Width>
        <X>190</X>
        <Y>123</Y>
        <Selected>true</Selected>
        <Rotation>0</Rotation>
        <DrawMode>0</DrawMode>
        <DrawLabel>true</DrawLabel>
        <InputConnectors>
          <Connector IsAttached="true" ConnType="ConIn" AttachedFromObjID="MAT-74ccf612-ceca-42d3-be4b-99be4e44403c" AttachedFromConnIndex="0" AttachedFromEnergyConn="False" />
          <Connector IsAttached="true" ConnType="ConEn" AttachedFromObjID="EN-542636a7-33d3-4a63-a18a-dc59bfe40459" AttachedFromConnIndex="0" AttachedFromEnergyConn="True" />
        </InputConnectors>
        <OutputConnectors>
          <Connector IsAttached="true" ConnType="ConOut" AttachedToObjID="MAT-d456af80-baca-4162-ba65-7ae84575ce5f" AttachedToConnIndex="0" AttachedToEnergyConn="False" />
          <Connector IsAttached="false" />
        </OutputConnectors>
        <EnergyConnector>
          <Connector IsAttached="false" />
        </EnergyConnector>
        <SpecialConnectors />
      </ConnectedToMv>
      <ConnectedToCv>
        <Type>DWSIM.Drawing.SkiaSharp.GraphicObjects.Shapes.CSTRGraphic</Type>
        <SemiTransparent>false</SemiTransparent>
        <LineWidth>1</LineWidth>
        <GradientMode>true</GradientMode>
        <LineColor>#ff4682b4</LineColor>
        <LineColorDark>#fff5f5f5</LineColorDark>
        <Fill>true</Fill>
        <FillColor>#ffffffff</FillColor>
        <FillColorDark>#ffffffff</FillColorDark>
        <GradientColor1>#ffd3d3d3</GradientColor1>
        <GradientColor2>#ffffffff</GradientColor2>
        <FontSize>10</FontSize>
        <OverrideColors>false</OverrideColors>
        <FontStyle>Bold</FontStyle>
        <Calculated>true</Calculated>
        <Active>true</Active>
        <Description>CSTR</Description>
        <FlippedH>false</FlippedH>
        <FlippedV>false</FlippedV>
        <IsEnergyStream>false</IsEnergyStream>
        <ObjectType>RCT_CSTR</ObjectType>
        <Shape>0</Shape>
        <ShapeOverride>DefaultShape</ShapeOverride>
        <Status>Calculated</Status>
        <AutoSize>false</AutoSize>
        <Height>50</Height>
        <IsConnector>false</IsConnector>
        <Name>CSTR-0d4ae06a-1a6d-4af2-9208-57387f7ee67d</Name>
        <Tag>CSTR-1</Tag>
        <Width>50</Width>
        <X>190</X>
        <Y>123</Y>
        <Selected>true</Selected>
        <Rotation>0</Rotation>
        <DrawMode>0</DrawMode>
        <DrawLabel>true</DrawLabel>
        <InputConnectors>
          <Connector IsAttached="true" ConnType="ConIn" AttachedFromObjID="MAT-74ccf612-ceca-42d3-be4b-99be4e44403c" AttachedFromConnIndex="0" AttachedFromEnergyConn="False" />
          <Connector IsAttached="true" ConnType="ConEn" AttachedFromObjID="EN-542636a7-33d3-4a63-a18a-dc59bfe40459" AttachedFromConnIndex="0" AttachedFromEnergyConn="True" />
        </InputConnectors>
        <OutputConnectors>
          <Connector IsAttached="true" ConnType="ConOut" AttachedToObjID="MAT-d456af80-baca-4162-ba65-7ae84575ce5f" AttachedToConnIndex="0" AttachedToEnergyConn="False" />
          <Connector IsAttached="false" />
        </OutputConnectors>
        <EnergyConnector>
          <Connector IsAttached="false" />
        </EnergyConnector>
        <SpecialConnectors />
      </ConnectedToCv>
      <SemiTransparent>false</SemiTransparent>
      <LineWidth>1</LineWidth>
      <GradientMode>true</GradientMode>
      <LineColor>#fffa8072</LineColor>
      <LineColorDark>#fff5f5f5</LineColorDark>
      <Fill>true</Fill>
      <FillColor>#ffffffff</FillColor>
      <FillColorDark>#ffffffff</FillColorDark>
      <GradientColor1>#ffd3d3d3</GradientColor1>
      <GradientColor2>#ffffffff</GradientColor2>
      <FontSize>10</FontSize>
      <OverrideColors>false</OverrideColors>
      <FontStyle>Bold</FontStyle>
      <Calculated>false</Calculated>
      <Active>true</Active>
      <Description>Steady-State Controller Block</Description>
      <FlippedH>false</FlippedH>
      <FlippedV>false</FlippedV>
      <IsEnergyStream>false</IsEnergyStream>
      <ObjectType>OT_Adjust</ObjectType>
      <Shape>0</Shape>
      <ShapeOverride>DefaultShape</ShapeOverride>
      <Status>NotCalculated</Status>
      <AutoSize>false</AutoSize>
      <Height>20</Height>
      <IsConnector>false</IsConnector>
      <Name>AJ08992d3d-559e-4471-90a1-ec01510757d9</Name>
      <Tag>C-1</Tag>
      <Width>20</Width>
      <X>281</X>
      <Y>51</Y>
      <Selected>false</Selected>
      <Rotation>0</Rotation>
      <DrawMode>0</DrawMode>
      <DrawLabel>true</DrawLabel>
      <InputConnectors />
      <OutputConnectors />
      <EnergyConnector>
        <Connector IsAttached="false" />
      </EnergyConnector>
      <SpecialConnectors />
    </GraphicObject>
  </GraphicObjects>
  <PropertyPackages>
    <PropertyPackage>
      <ID>PP-8472280c-ba09-46b4-aa6d-ff14bc089901</ID>
      <Type>DWSIM.Thermodynamics.PropertyPackages.NRTLPropertyPackage</Type>
      <ComponentName>NRTL</ComponentName>
      <ComponentDescription>Uses NRTL (Non-Random Two-Liquid) model to calculate liquid-phase activity coefficients.</ComponentDescription>
      <Tag>NRTL (1)</Tag>
      <UseHenryConstants>true</UseHenryConstants>
      <AutoEstimateMissingNRTLUNIQUACParameters>true</AutoEstimateMissingNRTLUNIQUACParameters>
      <SingleCompoundCheckThreshold>0.99999</SingleCompoundCheckThreshold>
      <OverrideKvalFugCoeff>false</OverrideKvalFugCoeff>
      <OverrideEnthalpyCalculation>false</OverrideEnthalpyCalculation>
      <OverrideEntropyCalculation>false</OverrideEntropyCalculation>
      <LiquidDensityCalculationMode_Subcritical>Rackett_and_ExpData</LiquidDensityCalculationMode_Subcritical>
      <LiquidDensityCalculationMode_Supercritical>Rackett_and_ExpData</LiquidDensityCalculationMode_Supercritical>
      <LiquidDensity_CorrectExpDataForPressure>true</LiquidDensity_CorrectExpDataForPressure>
      <LiquidDensity_UsePenelouxVolumeTranslation>true</LiquidDensity_UsePenelouxVolumeTranslation>
      <LiquidViscosityCalculationMode_Subcritical>ExpData</LiquidViscosityCalculationMode_Subcritical>
      <LiquidViscosityCalculationMode_Supercritical>Letsou_Stiel</LiquidViscosityCalculationMode_Supercritical>
      <LiquidViscosity_CorrectExpDataForPressure>true</LiquidViscosity_CorrectExpDataForPressure>
      <LiquidViscosity_MixingRule>MoleAverage</LiquidViscosity_MixingRule>
      <VaporPhaseFugacityCalculationMode>Ideal</VaporPhaseFugacityCalculationMode>
      <SolidPhaseFugacityCalculationMethod>FromLiquidFugacity</SolidPhaseFugacityCalculationMethod>
      <SolidPhaseFugacity_UseIdealLiquidPhaseFugacity>false</SolidPhaseFugacity_UseIdealLiquidPhaseFugacity>
      <SolidPhaseEnthalpy_UsesCp>false</SolidPhaseEnthalpy_UsesCp>
      <EnthalpyEntropyCpCvCalculationMode>LeeKesler</EnthalpyEntropyCpCvCalculationMode>
      <LiquidEnthalpyEntropyCpCvCalculationMode_EOS>EOS</LiquidEnthalpyEntropyCpCvCalculationMode_EOS>
      <LiquidFugacity_UsePoyntingCorrectionFactor>true</LiquidFugacity_UsePoyntingCorrectionFactor>
      <ActivityCoefficientModels_IgnoreMissingInteractionParameters>false</ActivityCoefficientModels_IgnoreMissingInteractionParameters>
      <IgnoreVaporFractionLimit>false</IgnoreVaporFractionLimit>
      <IgnoreSalinityLimit>false</IgnoreSalinityLimit>
      <CalculateAdditionalMaterialStreamProperties>true</CalculateAdditionalMaterialStreamProperties>
      <FlashCalculationApproach>NestedLoops</FlashCalculationApproach>
      <DisplayMissingCompoundPropertiesWarning>false</DisplayMissingCompoundPropertiesWarning>
      <ForcedSolids>[]</ForcedSolids>
      <PropertyOverrides>{}</PropertyOverrides>
      <InteractionParameters_PR />
      <InteractionParameters_NRTL>
        <InteractionParameter Compound1="Cis-2-butene" Compound2="Trans-2-butene" ID1="" ID2="" A12="-159.524565291064" A21="168.571391928172" B12="0" B21="0" C12="0" C21="0" alpha12="0.2" />
      </InteractionParameters_NRTL>
      <FlashSettings>
        <Setting Name="Replace_PTFlash" Value="False" />
        <Setting Name="ValidateEquilibriumCalc" Value="False" />
        <Setting Name="UsePhaseIdentificationAlgorithm" Value="False" />
        <Setting Name="CalculateBubbleAndDewPoints" Value="False" />
        <Setting Name="ValidationGibbsTolerance" Value="0.01" />
        <Setting Name="PHFlash_Maximum_Number_Of_External_Iterations" Value="100" />
        <Setting Name="PHFlash_External_Loop_Tolerance" Value="0.0001" />
        <Setting Name="PHFlash_Maximum_Number_Of_Internal_Iterations" Value="100" />
        <Setting Name="PHFlash_Internal_Loop_Tolerance" Value="0.0001" />
        <Setting Name="PTFlash_Maximum_Number_Of_External_Iterations" Value="100" />
        <Setting Name="PTFlash_External_Loop_Tolerance" Value="0.0001" />
        <Setting Name="PTFlash_Maximum_Number_Of_Internal_Iterations" Value="100" />
        <Setting Name="PTFlash_Internal_Loop_Tolerance" Value="0.0001" />
        <Setting Name="NL_FastMode" Value="True" />
        <Setting Name="IO_FastMode" Value="True" />
        <Setting Name="GM_OptimizationMethod" Value="IPOPT" />
        <Setting Name="ThreePhaseFlashStabTestSeverity" Value="0" />
        <Setting Name="ThreePhaseFlashStabTestCompIds" Value="" />
        <Setting Name="PVFlash_FixedDampingFactor" Value="1.0" />
        <Setting Name="PVFlash_MaximumTemperatureChange" Value="10.0" />
        <Setting Name="PVFlash_TemperatureDerivativeEpsilon" Value="0.1" />
        <Setting Name="ST_Number_of_Random_Tries" Value="20" />
        <Setting Name="CheckIncipientLiquidForStability" Value="False" />
        <Setting Name="PHFlash_MaximumTemperatureChange" Value="30.0" />
        <Setting Name="PTFlash_DampingFactor" Value="1.0" />
        <Setting Name="ForceEquilibriumCalculationType" Value="Default" />
        <Setting Name="ImmiscibleWaterOption" Value="False" />
        <Setting Name="HandleSolidsInDefaultEqCalcMode" Value="False" />
        <Setting Name="UseIOFlash" Value="False" />
        <Setting Name="GibbsMinimizationExternalSolver" Value="" />
        <Setting Name="GibbsMinimizationExternalSolverConfigData" Value="" />
        <Setting Name="PHFlash_Use_Interpolated_Result_In_Oscillating_Temperature_Cases" Value="False" />
        <Setting Name="PVFlash_TryIdealCalcOnFailure" Value="True" />
        <Setting Name="FailSafeCalculationMode" Value="1" />
        <Setting Name="PVFlash_FivePointStencilNumericalDerivative" Value="False" />
      </FlashSettings>
    </PropertyPackage>
  </PropertyPackages>
  <Compounds>
    <Compound>
      <Type>DWSIM.Thermodynamics.BaseClasses.ConstantProperties</Type>
      <Acentric_Factor>0.203</Acentric_Factor>
      <BO_BSW>0</BO_BSW>
      <BO_GOR>0</BO_GOR>
      <BO_OilVisc1>0</BO_OilVisc1>
      <BO_OilVisc2>0</BO_OilVisc2>
      <BO_OilViscTemp1>0</BO_OilViscTemp1>
      <BO_OilViscTemp2>0</BO_OilViscTemp2>
      <BO_PNA_A>0</BO_PNA_A>
      <BO_PNA_N>0</BO_PNA_N>
      <BO_PNA_P>0</BO_PNA_P>
      <BO_SGG>0</BO_SGG>
      <BO_SGO>0</BO_SGO>
      <CAS_Number>590-18-1</CAS_Number>
      <Chao_Seader_Acentricity>0.2575</Chao_Seader_Acentricity>
      <Chao_Seader_Liquid_Molar_Volume>91.2</Chao_Seader_Liquid_Molar_Volume>
      <Chao_Seader_Solubility_Parameter>0.00330266217268</Chao_Seader_Solubility_Parameter>
      <Charge>0</Charge>
      <ChemicalStructure></ChemicalStructure>
      <Comments></Comments>
      <CompCreatorStudyFile></CompCreatorStudyFile>
      <Critical_Compressibility>0.269</Critical_Compressibility>
      <Critical_Pressure>4210000</Critical_Pressure>
      <Critical_Temperature>435.5</Critical_Temperature>
      <Critical_Volume>0.2338</Critical_Volume>
      <CurrentDB>ChemSep</CurrentDB>
      <Dipole_Moment>1E-30</Dipole_Moment>
      <Electrolyte_Cp0>0</Electrolyte_Cp0>
      <Electrolyte_DelGF>0</Electrolyte_DelGF>
      <Electrolyte_DelHF>0</Electrolyte_DelHF>
      <EnthalpyOfFusionAtTf>7.3094</EnthalpyOfFusionAtTf>
      <Formula>CH3CHCHCH3</Formula>
      <HVap_A>34358000</HVap_A>
      <HVap_B>0.38004</HVap_B>
      <HVap_C>0</HVap_C>
      <HVap_D>0</HVap_D>
      <HVap_E>0</HVap_E>
      <HVap_TMAX>435.5</HVap_TMAX>
      <HVap_TMIN>134.26</HVap_TMIN>
      <HydrationNumber>0</HydrationNumber>
      <ID>205</ID>
      <Ideal_Gas_Heat_Capacity_Const_A>53149</Ideal_Gas_Heat_Capacity_Const_A>
      <Ideal_Gas_Heat_Capacity_Const_B>-719.47</Ideal_Gas_Heat_Capacity_Const_B>
      <Ideal_Gas_Heat_Capacity_Const_C>12.619</Ideal_Gas_Heat_Capacity_Const_C>
      <Ideal_Gas_Heat_Capacity_Const_D>-4.7815E-05</Ideal_Gas_Heat_Capacity_Const_D>
      <Ideal_Gas_Heat_Capacity_Const_E>4.5198E-10</Ideal_Gas_Heat_Capacity_Const_E>
      <IdealgasCpEquation>16</IdealgasCpEquation>
      <IG_Enthalpy_of_Formation_25C>-131.892449905822</IG_Enthalpy_of_Formation_25C>
      <IG_Entropy_of_Formation_25C>-4.34956767414714</IG_Entropy_of_Formation_25C>
      <IG_Gibbs_Energy_of_Formation_25C>1164.93115214115</IG_Gibbs_Energy_of_Formation_25C>
      <InChI></InChI>
      <Ion_CpAq_a>0</Ion_CpAq_a>
      <Ion_CpAq_b>0</Ion_CpAq_b>
      <Ion_CpAq_c>0</Ion_CpAq_c>
      <IsBlackOil>false</IsBlackOil>
      <IsCOOLPROPSupported>true</IsCOOLPROPSupported>
      <IsFPROPSSupported>false</IsFPROPSSupported>
      <IsHydratedSalt>false</IsHydratedSalt>
      <IsHYPO>0</IsHYPO>
      <IsIon>false</IsIon>
      <IsModified>false</IsModified>
      <IsPF>0</IsPF>
      <IsSalt>false</IsSalt>
      <Liquid_Density_Const_A>1.1591</Liquid_Density_Const_A>
      <Liquid_Density_Const_B>0.27085</Liquid_Density_Const_B>
      <Liquid_Density_Const_C>435.5</Liquid_Density_Const_C>
      <Liquid_Density_Const_D>0.28116</Liquid_Density_Const_D>
      <Liquid_Density_Const_E>0</Liquid_Density_Const_E>
      <Liquid_Density_Tmax>435.5</Liquid_Density_Tmax>
      <Liquid_Density_Tmin>134.26</Liquid_Density_Tmin>
      <Liquid_Heat_Capacity_Const_A>79532</Liquid_Heat_Capacity_Const_A>
      <Liquid_Heat_Capacity_Const_B>110.96</Liquid_Heat_Capacity_Const_B>
      <Liquid_Heat_Capacity_Const_C>9.7654</Liquid_Heat_Capacity_Const_C>
      <Liquid_Heat_Capacity_Const_D>-0.0036798</Liquid_Heat_Capacity_Const_D>
      <Liquid_Heat_Capacity_Const_E>1.9578E-05</Liquid_Heat_Capacity_Const_E>
      <Liquid_Heat_Capacity_Tmax>366.48</Liquid_Heat_Capacity_Tmax>
      <Liquid_Heat_Capacity_Tmin>133.15</Liquid_Heat_Capacity_Tmin>
      <Liquid_Thermal_Conductivity_Const_A>-0.032373</Liquid_Thermal_Conductivity_Const_A>
      <Liquid_Thermal_Conductivity_Const_B>19.125</Liquid_Thermal_Conductivity_Const_B>
      <Liquid_Thermal_Conductivity_Const_C>-1.716</Liquid_Thermal_Conductivity_Const_C>
      <Liquid_Thermal_Conductivity_Const_D>0.00030408</Liquid_Thermal_Conductivity_Const_D>
      <Liquid_Thermal_Conductivity_Const_E>-4.2934E-06</Liquid_Thermal_Conductivity_Const_E>
      <Liquid_Thermal_Conductivity_Tmax>373.15</Liquid_Thermal_Conductivity_Tmax>
      <Liquid_Thermal_Conductivity_Tmin>134.26</Liquid_Thermal_Conductivity_Tmin>
      <Liquid_Viscosity_Const_A>-17.96838</Liquid_Viscosity_Const_A>
      <Liquid_Viscosity_Const_B>892.0637</Liquid_Viscosity_Const_B>
      <Liquid_Viscosity_Const_C>1.159883</Liquid_Viscosity_Const_C>
      <Liquid_Viscosity_Const_D>-2.883463E-06</Liquid_Viscosity_Const_D>
      <Liquid_Viscosity_Const_E>2</Liquid_Viscosity_Const_E>
      <LiquidDensityEquation>105</LiquidDensityEquation>
      <LiquidHeatCapacityEquation>16</LiquidHeatCapacityEquation>
      <LiquidThermalConductivityEquation>16</LiquidThermalConductivityEquation>
      <LiquidViscosityEquation>101</LiquidViscosityEquation>
      <Molar_Weight>56.10632</Molar_Weight>
      <MolarVolume_k1i>0</MolarVolume_k1i>
      <MolarVolume_k2i>0</MolarVolume_k2i>
      <MolarVolume_k3i>0</MolarVolume_k3i>
      <MolarVolume_v2i>0</MolarVolume_v2i>
      <MolarVolume_v3i>0</MolarVolume_v3i>
      <Name>Cis-2-butene</Name>
      <NBP>276.87</NBP>
      <NegativeIon></NegativeIon>
      <NegativeIonStoichCoeff>0</NegativeIonStoichCoeff>
      <Normal_Boiling_Point>276.87</Normal_Boiling_Point>
      <OriginalDB>ChemSep</OriginalDB>
      <PC_SAFT_epsilon_k>0</PC_SAFT_epsilon_k>
      <PC_SAFT_m>0</PC_SAFT_m>
      <PC_SAFT_sigma>0</PC_SAFT_sigma>
      <PositiveIon></PositiveIon>
      <PositiveIonStoichCoeff>0</PositiveIonStoichCoeff>
      <PR_Volume_Translation_Coefficient>0</PR_Volume_Translation_Coefficient>
      <SMILES>C/C=C\C</SMILES>
      <Solid_Density_Const_A>17.618</Solid_Density_Const_A>
      <Solid_Density_Const_B>-0.014457</Solid_Density_Const_B>
      <Solid_Density_Const_C>0</Solid_Density_Const_C>
      <Solid_Density_Const_D>0</Solid_Density_Const_D>
      <Solid_Density_Const_E>0</Solid_Density_Const_E>
      <Solid_Density_Tmax>134.26</Solid_Density_Tmax>
      <Solid_Density_Tmin>53.7</Solid_Density_Tmin>
      <Solid_Heat_Capacity_Const_A>-11156</Solid_Heat_Capacity_Const_A>
      <Solid_Heat_Capacity_Const_B>837.19</Solid_Heat_Capacity_Const_B>
      <Solid_Heat_Capacity_Const_C>4.9352</Solid_Heat_Capacity_Const_C>
      <Solid_Heat_Capacity_Const_D>-0.095117</Solid_Heat_Capacity_Const_D>
      <Solid_Heat_Capacity_Const_E>0.00037586</Solid_Heat_Capacity_Const_E>
      <Solid_Heat_Capacity_Tmax>134.26</Solid_Heat_Capacity_Tmax>
      <Solid_Heat_Capacity_Tmin>15</Solid_Heat_Capacity_Tmin>
      <SolidDensityAtTs>0</SolidDensityAtTs>
      <SolidDensityEquation>2</SolidDensityEquation>
      <SolidHeatCapacityEquation>100</SolidHeatCapacityEquation>
      <SolidTs>0</SolidTs>
      <SRK_Volume_Translation_Coefficient>0</SRK_Volume_Translation_Coefficient>
      <StandardStateMolarVolume>0</StandardStateMolarVolume>
      <StoichSum>0</StoichSum>
      <Surface_Tension_Const_A>-0.010924</Surface_Tension_Const_A>
      <Surface_Tension_Const_B>29.613</Surface_Tension_Const_B>
      <Surface_Tension_Const_C>-3.1507</Surface_Tension_Const_C>
      <Surface_Tension_Const_D>0.00043968</Surface_Tension_Const_D>
      <Surface_Tension_Const_E>-8.7176E-06</Surface_Tension_Const_E>
      <Surface_Tension_Tmax>435.5</Surface_Tension_Tmax>
      <Surface_Tension_Tmin>134.26</Surface_Tension_Tmin>
      <SurfaceTensionEquation>16</SurfaceTensionEquation>
      <TemperatureOfFusion>134.26</TemperatureOfFusion>
      <UNIQUAC_Q>2.563</UNIQUAC_Q>
      <UNIQUAC_R>2.9189</UNIQUAC_R>
      <Vapor_Pressure_Constant_A>82.92441</Vapor_Pressure_Constant_A>
      <Vapor_Pressure_Constant_B>-5022.628</Vapor_Pressure_Constant_B>
      <Vapor_Pressure_Constant_C>-9.652369</Vapor_Pressure_Constant_C>
      <Vapor_Pressure_Constant_D>1.33961E-05</Vapor_Pressure_Constant_D>
      <Vapor_Pressure_Constant_E>2</Vapor_Pressure_Constant_E>
      <Vapor_Pressure_TMAX>435.58</Vapor_Pressure_TMAX>
      <Vapor_Pressure_TMIN>134.26</Vapor_Pressure_TMIN>
      <Vapor_Thermal_Conductivity_Const_A>7.5196E-05</Vapor_Thermal_Conductivity_Const_A>
      <Vapor_Thermal_Conductivity_Const_B>1.0578</Vapor_Thermal_Conductivity_Const_B>
      <Vapor_Thermal_Conductivity_Const_C>-53.701</Vapor_Thermal_Conductivity_Const_C>
      <Vapor_Thermal_Conductivity_Const_D>131760</Vapor_Thermal_Conductivity_Const_D>
      <Vapor_Thermal_Conductivity_Const_E>0</Vapor_Thermal_Conductivity_Const_E>
      <Vapor_Thermal_Conductivity_Tmax>1273.15</Vapor_Thermal_Conductivity_Tmax>
      <Vapor_Thermal_Conductivity_Tmin>134.26</Vapor_Thermal_Conductivity_Tmin>
      <Vapor_Viscosity_Const_A>4.0697E-08</Vapor_Viscosity_Const_A>
      <Vapor_Viscosity_Const_B>0.91942</Vapor_Viscosity_Const_B>
      <Vapor_Viscosity_Const_C>-12.143</Vapor_Viscosity_Const_C>
      <Vapor_Viscosity_Const_D>1343.2</Vapor_Viscosity_Const_D>
      <Vapor_Viscosity_Const_E>0</Vapor_Viscosity_Const_E>
      <Vapor_Viscosity_Tmax>1000</Vapor_Viscosity_Tmax>
      <Vapor_Viscosity_Tmin>134.26</Vapor_Viscosity_Tmin>
      <VaporizationEnthalpyEquation>106</VaporizationEnthalpyEquation>
      <VaporPressureEquation>101</VaporPressureEquation>
      <VaporThermalConductivityEquation>102</VaporThermalConductivityEquation>
      <VaporViscosityEquation>102</VaporViscosityEquation>
      <Z_Rackett>0.2705</Z_Rackett>
      <FullerDiffusionVolume>82.08</FullerDiffusionVolume>
      <LennardJonesDiameter>5.556787E-10</LennardJonesDiameter>
      <LennardJonesEnergy>251.7732</LennardJonesEnergy>
      <Parachor>0.0315</Parachor>
      <Tag></Tag>
      <COSTALD_SRK_Acentric_Factor>0.20385</COSTALD_SRK_Acentric_Factor>
      <COSTALD_Characteristic_Volume>0.23104</COSTALD_Characteristic_Volume>
      <IsSolid>false</IsSolid>
      <ChemSepFamily>10</ChemSepFamily>
      <Vapor_Pressure_Regression_Fit>0</Vapor_Pressure_Regression_Fit>
      <Vapor_Pressure_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Vapor_Pressure_Tabular_Data>
      <Ideal_Gas_Heat_Capacity_Regression_Fit>0</Ideal_Gas_Heat_Capacity_Regression_Fit>
      <Ideal_Gas_Heat_Capacity_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Ideal_Gas_Heat_Capacity_Tabular_Data>
      <Liquid_Viscosity_Regression_Fit>0</Liquid_Viscosity_Regression_Fit>
      <Liquid_Viscosity_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Liquid_Viscosity_Tabular_Data>
      <Liquid_Density_Regression_Fit>0</Liquid_Density_Regression_Fit>
      <Liquid_Density_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Liquid_Density_Tabular_Data>
      <Liquid_Heat_Capacity_Regression_Fit>0</Liquid_Heat_Capacity_Regression_Fit>
      <Liquid_Heat_Capacity_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Liquid_Heat_Capacity_Tabular_Data>
      <Liquid_Thermal_Conductivity_Regression_Fit>0</Liquid_Thermal_Conductivity_Regression_Fit>
      <Liquid_Thermal_Conductivity_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Liquid_Thermal_Conductivity_Tabular_Data>
      <Vapor_Thermal_Conductivity_Regression_Fit>0</Vapor_Thermal_Conductivity_Regression_Fit>
      <Vapor_Thermal_Conductivity_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Vapor_Thermal_Conductivity_Tabular_Data>
      <Vapor_Viscosity_Regression_Fit>0</Vapor_Viscosity_Regression_Fit>
      <Vapor_Viscosity_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Vapor_Viscosity_Tabular_Data>
      <Solid_Density_Regression_Fit>0</Solid_Density_Regression_Fit>
      <Solid_Density_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Solid_Density_Tabular_Data>
      <Surface_Tension_Regression_Fit>0</Surface_Tension_Regression_Fit>
      <Surface_Tension_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Surface_Tension_Tabular_Data>
      <Solid_Heat_Capacity_Regression_Fit>0</Solid_Heat_Capacity_Regression_Fit>
      <Solid_Heat_Capacity_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Solid_Heat_Capacity_Tabular_Data>
      <Enthalpy_Of_Vaporization_Regression_Fit>0</Enthalpy_Of_Vaporization_Regression_Fit>
      <Enthalpy_Of_Vaporization_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Enthalpy_Of_Vaporization_Tabular_Data>
      <StandardHeatOfCombustion_LHV>-45162.4701103191</StandardHeatOfCombustion_LHV>
      <DynamicProperties />
      <UNIFACGroups>
        <Item GroupID="1" Value="2" />
        <Item GroupID="6" Value="1" />
      </UNIFACGroups>
      <MODFACGroups>
        <Item GroupID="1" Value="2" />
        <Item GroupID="6" Value="1" />
      </MODFACGroups>
      <NISTMODFACGroups>
        <Item GroupID="1" Value="2" />
        <Item GroupID="6" Value="1" />
      </NISTMODFACGroups>
      <Elements>
        <Item Name="C" Value="4" />
        <Item Name="H" Value="8" />
      </Elements>
    </Compound>
    <Compound>
      <Type>DWSIM.Thermodynamics.BaseClasses.ConstantProperties</Type>
      <Acentric_Factor>0.218</Acentric_Factor>
      <BO_BSW>0</BO_BSW>
      <BO_GOR>0</BO_GOR>
      <BO_OilVisc1>0</BO_OilVisc1>
      <BO_OilVisc2>0</BO_OilVisc2>
      <BO_OilViscTemp1>0</BO_OilViscTemp1>
      <BO_OilViscTemp2>0</BO_OilViscTemp2>
      <BO_PNA_A>0</BO_PNA_A>
      <BO_PNA_N>0</BO_PNA_N>
      <BO_PNA_P>0</BO_PNA_P>
      <BO_SGG>0</BO_SGG>
      <BO_SGO>0</BO_SGO>
      <CAS_Number>624-64-6</CAS_Number>
      <Chao_Seader_Acentricity>0.2138</Chao_Seader_Acentricity>
      <Chao_Seader_Liquid_Molar_Volume>89.3483</Chao_Seader_Liquid_Molar_Volume>
      <Chao_Seader_Solubility_Parameter>0.0033934523142</Chao_Seader_Solubility_Parameter>
      <Charge>0</Charge>
      <ChemicalStructure></ChemicalStructure>
      <Comments></Comments>
      <CompCreatorStudyFile></CompCreatorStudyFile>
      <Critical_Compressibility>0.276</Critical_Compressibility>
      <Critical_Pressure>4100000</Critical_Pressure>
      <Critical_Temperature>428.6</Critical_Temperature>
      <Critical_Volume>0.2377</Critical_Volume>
      <CurrentDB>ChemSep</CurrentDB>
      <Dipole_Moment>0</Dipole_Moment>
      <Electrolyte_Cp0>0</Electrolyte_Cp0>
      <Electrolyte_DelGF>0</Electrolyte_DelGF>
      <Electrolyte_DelHF>0</Electrolyte_DelHF>
      <EnthalpyOfFusionAtTf>9.7575</EnthalpyOfFusionAtTf>
      <Formula>CH3CHCHCH3</Formula>
      <HVap_A>33476000</HVap_A>
      <HVap_B>0.31355</HVap_B>
      <HVap_C>0.41478</HVap_C>
      <HVap_D>-0.75555</HVap_D>
      <HVap_E>0.40695</HVap_E>
      <HVap_TMAX>428.6</HVap_TMAX>
      <HVap_TMIN>167.62</HVap_TMIN>
      <HydrationNumber>0</HydrationNumber>
      <ID>206</ID>
      <Ideal_Gas_Heat_Capacity_Const_A>60006</Ideal_Gas_Heat_Capacity_Const_A>
      <Ideal_Gas_Heat_Capacity_Const_B>-649.72</Ideal_Gas_Heat_Capacity_Const_B>
      <Ideal_Gas_Heat_Capacity_Const_C>12.368</Ideal_Gas_Heat_Capacity_Const_C>
      <Ideal_Gas_Heat_Capacity_Const_D>0.00014661</Ideal_Gas_Heat_Capacity_Const_D>
      <Ideal_Gas_Heat_Capacity_Const_E>-5.1566E-08</Ideal_Gas_Heat_Capacity_Const_E>
      <IdealgasCpEquation>16</IdealgasCpEquation>
      <IG_Enthalpy_of_Formation_25C>-196.0563444546</IG_Enthalpy_of_Formation_25C>
      <IG_Entropy_of_Formation_25C>-4.43565037687903</IG_Entropy_of_Formation_25C>
      <IG_Gibbs_Energy_of_Formation_25C>1126.43281541188</IG_Gibbs_Energy_of_Formation_25C>
      <InChI></InChI>
      <Ion_CpAq_a>0</Ion_CpAq_a>
      <Ion_CpAq_b>0</Ion_CpAq_b>
      <Ion_CpAq_c>0</Ion_CpAq_c>
      <IsBlackOil>false</IsBlackOil>
      <IsCOOLPROPSupported>true</IsCOOLPROPSupported>
      <IsFPROPSSupported>false</IsFPROPSSupported>
      <IsHydratedSalt>false</IsHydratedSalt>
      <IsHYPO>0</IsHYPO>
      <IsIon>false</IsIon>
      <IsModified>false</IsModified>
      <IsPF>0</IsPF>
      <IsSalt>false</IsSalt>
      <Liquid_Density_Const_A>1.1523</Liquid_Density_Const_A>
      <Liquid_Density_Const_B>0.27235</Liquid_Density_Const_B>
      <Liquid_Density_Const_C>428.6</Liquid_Density_Const_C>
      <Liquid_Density_Const_D>0.28543</Liquid_Density_Const_D>
      <Liquid_Density_Const_E>0</Liquid_Density_Const_E>
      <Liquid_Density_Tmax>428.6</Liquid_Density_Tmax>
      <Liquid_Density_Tmin>167.62</Liquid_Density_Tmin>
      <Liquid_Heat_Capacity_Const_A>98730</Liquid_Heat_Capacity_Const_A>
      <Liquid_Heat_Capacity_Const_B>549.96</Liquid_Heat_Capacity_Const_B>
      <Liquid_Heat_Capacity_Const_C>0.83133</Liquid_Heat_Capacity_Const_C>
      <Liquid_Heat_Capacity_Const_D>0.038607</Liquid_Heat_Capacity_Const_D>
      <Liquid_Heat_Capacity_Const_E>-4.4392E-05</Liquid_Heat_Capacity_Const_E>
      <Liquid_Heat_Capacity_Tmax>280</Liquid_Heat_Capacity_Tmax>
      <Liquid_Heat_Capacity_Tmin>167.62</Liquid_Heat_Capacity_Tmin>
      <Liquid_Thermal_Conductivity_Const_A>0.060004</Liquid_Thermal_Conductivity_Const_A>
      <Liquid_Thermal_Conductivity_Const_B>368.81</Liquid_Thermal_Conductivity_Const_B>
      <Liquid_Thermal_Conductivity_Const_C>-7.3737</Liquid_Thermal_Conductivity_Const_C>
      <Liquid_Thermal_Conductivity_Const_D>0.025078</Liquid_Thermal_Conductivity_Const_D>
      <Liquid_Thermal_Conductivity_Const_E>-4.9526E-05</Liquid_Thermal_Conductivity_Const_E>
      <Liquid_Thermal_Conductivity_Tmax>392.74</Liquid_Thermal_Conductivity_Tmax>
      <Liquid_Thermal_Conductivity_Tmin>167.6</Liquid_Thermal_Conductivity_Tmin>
      <Liquid_Viscosity_Const_A>-16.05639</Liquid_Viscosity_Const_A>
      <Liquid_Viscosity_Const_B>833.2986</Liquid_Viscosity_Const_B>
      <Liquid_Viscosity_Const_C>0.849646</Liquid_Viscosity_Const_C>
      <Liquid_Viscosity_Const_D>-2.292227E-06</Liquid_Viscosity_Const_D>
      <Liquid_Viscosity_Const_E>2</Liquid_Viscosity_Const_E>
      <LiquidDensityEquation>105</LiquidDensityEquation>
      <LiquidHeatCapacityEquation>16</LiquidHeatCapacityEquation>
      <LiquidThermalConductivityEquation>16</LiquidThermalConductivityEquation>
      <LiquidViscosityEquation>101</LiquidViscosityEquation>
      <Molar_Weight>56.10632</Molar_Weight>
      <MolarVolume_k1i>0</MolarVolume_k1i>
      <MolarVolume_k2i>0</MolarVolume_k2i>
      <MolarVolume_k3i>0</MolarVolume_k3i>
      <MolarVolume_v2i>0</MolarVolume_v2i>
      <MolarVolume_v3i>0</MolarVolume_v3i>
      <Name>Trans-2-butene</Name>
      <NBP>274.03</NBP>
      <NegativeIon></NegativeIon>
      <NegativeIonStoichCoeff>0</NegativeIonStoichCoeff>
      <Normal_Boiling_Point>274.03</Normal_Boiling_Point>
      <OriginalDB>ChemSep</OriginalDB>
      <PC_SAFT_epsilon_k>0</PC_SAFT_epsilon_k>
      <PC_SAFT_m>0</PC_SAFT_m>
      <PC_SAFT_sigma>0</PC_SAFT_sigma>
      <PositiveIon></PositiveIon>
      <PositiveIonStoichCoeff>0</PositiveIonStoichCoeff>
      <PR_Volume_Translation_Coefficient>0</PR_Volume_Translation_Coefficient>
      <SMILES>C/C=C/C</SMILES>
      <Solid_Density_Const_A>16.597</Solid_Density_Const_A>
      <Solid_Density_Const_B>-0.011008</Solid_Density_Const_B>
      <Solid_Density_Const_C>0</Solid_Density_Const_C>
      <Solid_Density_Const_D>0</Solid_Density_Const_D>
      <Solid_Density_Const_E>0</Solid_Density_Const_E>
      <Solid_Density_Tmax>167.62</Solid_Density_Tmax>
      <Solid_Density_Tmin>67.05</Solid_Density_Tmin>
      <Solid_Heat_Capacity_Const_A>-11577</Solid_Heat_Capacity_Const_A>
      <Solid_Heat_Capacity_Const_B>924.59</Solid_Heat_Capacity_Const_B>
      <Solid_Heat_Capacity_Const_C>-0.075824</Solid_Heat_Capacity_Const_C>
      <Solid_Heat_Capacity_Const_D>-0.037583</Solid_Heat_Capacity_Const_D>
      <Solid_Heat_Capacity_Const_E>0.00018647</Solid_Heat_Capacity_Const_E>
      <Solid_Heat_Capacity_Tmax>167.62</Solid_Heat_Capacity_Tmax>
      <Solid_Heat_Capacity_Tmin>14.56</Solid_Heat_Capacity_Tmin>
      <SolidDensityAtTs>0</SolidDensityAtTs>
      <SolidDensityEquation>2</SolidDensityEquation>
      <SolidHeatCapacityEquation>100</SolidHeatCapacityEquation>
      <SolidTs>0</SolidTs>
      <SRK_Volume_Translation_Coefficient>0</SRK_Volume_Translation_Coefficient>
      <StandardStateMolarVolume>0</StandardStateMolarVolume>
      <StoichSum>0</StoichSum>
      <Surface_Tension_Const_A>-0.0071116</Surface_Tension_Const_A>
      <Surface_Tension_Const_B>84.381</Surface_Tension_Const_B>
      <Surface_Tension_Const_C>-4.1149</Surface_Tension_Const_C>
      <Surface_Tension_Const_D>0.0047521</Surface_Tension_Const_D>
      <Surface_Tension_Const_E>-1.6755E-05</Surface_Tension_Const_E>
      <Surface_Tension_Tmax>428.6</Surface_Tension_Tmax>
      <Surface_Tension_Tmin>167.62</Surface_Tension_Tmin>
      <SurfaceTensionEquation>16</SurfaceTensionEquation>
      <TemperatureOfFusion>167.62</TemperatureOfFusion>
      <UNIQUAC_Q>2.563</UNIQUAC_Q>
      <UNIQUAC_R>2.9189</UNIQUAC_R>
      <Vapor_Pressure_Constant_A>56.602</Vapor_Pressure_Constant_A>
      <Vapor_Pressure_Constant_B>-4026.7</Vapor_Pressure_Constant_B>
      <Vapor_Pressure_Constant_C>-5.5178</Vapor_Pressure_Constant_C>
      <Vapor_Pressure_Constant_D>7.9176E-06</Vapor_Pressure_Constant_D>
      <Vapor_Pressure_Constant_E>2</Vapor_Pressure_Constant_E>
      <Vapor_Pressure_TMAX>428.63</Vapor_Pressure_TMAX>
      <Vapor_Pressure_TMIN>167.62</Vapor_Pressure_TMIN>
      <Vapor_Thermal_Conductivity_Const_A>7.8563E-05</Vapor_Thermal_Conductivity_Const_A>
      <Vapor_Thermal_Conductivity_Const_B>1.0565</Vapor_Thermal_Conductivity_Const_B>
      <Vapor_Thermal_Conductivity_Const_C>14.753</Vapor_Thermal_Conductivity_Const_C>
      <Vapor_Thermal_Conductivity_Const_D>105810</Vapor_Thermal_Conductivity_Const_D>
      <Vapor_Thermal_Conductivity_Const_E>0</Vapor_Thermal_Conductivity_Const_E>
      <Vapor_Thermal_Conductivity_Tmax>1257</Vapor_Thermal_Conductivity_Tmax>
      <Vapor_Thermal_Conductivity_Tmin>167.62</Vapor_Thermal_Conductivity_Tmin>
      <Vapor_Viscosity_Const_A>1.0493E-06</Vapor_Viscosity_Const_A>
      <Vapor_Viscosity_Const_B>0.48674</Vapor_Viscosity_Const_B>
      <Vapor_Viscosity_Const_C>358.01</Vapor_Viscosity_Const_C>
      <Vapor_Viscosity_Const_D>137.53</Vapor_Viscosity_Const_D>
      <Vapor_Viscosity_Const_E>0</Vapor_Viscosity_Const_E>
      <Vapor_Viscosity_Tmax>1000</Vapor_Viscosity_Tmax>
      <Vapor_Viscosity_Tmin>167.62</Vapor_Viscosity_Tmin>
      <VaporizationEnthalpyEquation>106</VaporizationEnthalpyEquation>
      <VaporPressureEquation>101</VaporPressureEquation>
      <VaporThermalConductivityEquation>102</VaporThermalConductivityEquation>
      <VaporViscosityEquation>102</VaporViscosityEquation>
      <Z_Rackett>0.2721</Z_Rackett>
      <FullerDiffusionVolume>82.08</FullerDiffusionVolume>
      <LennardJonesDiameter>5.417894E-10</LennardJonesDiameter>
      <LennardJonesEnergy>271.7928</LennardJonesEnergy>
      <Parachor>0.0318</Parachor>
      <Tag></Tag>
      <COSTALD_SRK_Acentric_Factor>0.21525</COSTALD_SRK_Acentric_Factor>
      <COSTALD_Characteristic_Volume>0.23668</COSTALD_Characteristic_Volume>
      <IsSolid>false</IsSolid>
      <ChemSepFamily>10</ChemSepFamily>
      <Vapor_Pressure_Regression_Fit>0</Vapor_Pressure_Regression_Fit>
      <Vapor_Pressure_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Vapor_Pressure_Tabular_Data>
      <Ideal_Gas_Heat_Capacity_Regression_Fit>0</Ideal_Gas_Heat_Capacity_Regression_Fit>
      <Ideal_Gas_Heat_Capacity_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Ideal_Gas_Heat_Capacity_Tabular_Data>
      <Liquid_Viscosity_Regression_Fit>0</Liquid_Viscosity_Regression_Fit>
      <Liquid_Viscosity_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Liquid_Viscosity_Tabular_Data>
      <Liquid_Density_Regression_Fit>0</Liquid_Density_Regression_Fit>
      <Liquid_Density_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Liquid_Density_Tabular_Data>
      <Liquid_Heat_Capacity_Regression_Fit>0</Liquid_Heat_Capacity_Regression_Fit>
      <Liquid_Heat_Capacity_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Liquid_Heat_Capacity_Tabular_Data>
      <Liquid_Thermal_Conductivity_Regression_Fit>0</Liquid_Thermal_Conductivity_Regression_Fit>
      <Liquid_Thermal_Conductivity_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Liquid_Thermal_Conductivity_Tabular_Data>
      <Vapor_Thermal_Conductivity_Regression_Fit>0</Vapor_Thermal_Conductivity_Regression_Fit>
      <Vapor_Thermal_Conductivity_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Vapor_Thermal_Conductivity_Tabular_Data>
      <Vapor_Viscosity_Regression_Fit>0</Vapor_Viscosity_Regression_Fit>
      <Vapor_Viscosity_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Vapor_Viscosity_Tabular_Data>
      <Solid_Density_Regression_Fit>0</Solid_Density_Regression_Fit>
      <Solid_Density_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Solid_Density_Tabular_Data>
      <Surface_Tension_Regression_Fit>0</Surface_Tension_Regression_Fit>
      <Surface_Tension_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Surface_Tension_Tabular_Data>
      <Solid_Heat_Capacity_Regression_Fit>0</Solid_Heat_Capacity_Regression_Fit>
      <Solid_Heat_Capacity_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Solid_Heat_Capacity_Tabular_Data>
      <Enthalpy_Of_Vaporization_Regression_Fit>0</Enthalpy_Of_Vaporization_Regression_Fit>
      <Enthalpy_Of_Vaporization_Tabular_Data>
        <Type>DWSIM.SharedClasses.TabularData</Type>
        <XName></XName>
        <YName></YName>
        <XUnit></XUnit>
        <YUnit></YUnit>
        <XData />
        <YData />
        <Source></Source>
        <Comments></Comments>
      </Enthalpy_Of_Vaporization_Tabular_Data>
      <StandardHeatOfCombustion_LHV>-45092.9592245579</StandardHeatOfCombustion_LHV>
      <DynamicProperties />
      <UNIFACGroups>
        <Item GroupID="1" Value="2" />
        <Item GroupID="6" Value="1" />
      </UNIFACGroups>
      <MODFACGroups>
        <Item GroupID="1" Value="2" />
        <Item GroupID="6" Value="1" />
      </MODFACGroups>
      <NISTMODFACGroups>
        <Item GroupID="1" Value="2" />
        <Item GroupID="6" Value="1" />
      </NISTMODFACGroups>
      <Elements>
        <Item Name="C" Value="4" />
        <Item Name="H" Value="8" />
      </Elements>
    </Compound>
  </Compounds>
  <ReactionSets>
    <ReactionSet>
      <ID>DefaultSet</ID>
      <Name>Default Set</Name>
      <Description>Set Reaksi Default</Description>
      <Reactions>
        <Reaction Key="68400fd9-e4c1-45f9-987e-f732f9882f59" ReactionID="68400fd9-e4c1-45f9-987e-f732f9882f59" Rank="0" IsActive="true" />
      </Reactions>
    </ReactionSet>
  </ReactionSets>
  <Reactions>
    <Reaction>
      <Type>DWSIM.Thermodynamics.BaseClasses.Reaction</Type>
      <BaseReactant>Cis-2-butene</BaseReactant>
      <Description></Description>
      <Equation>CH3CHCHCH3 &lt;--&gt; CH3CHCHCH3 </Equation>
      <ID>68400fd9-e4c1-45f9-987e-f732f9882f59</ID>
      <Name></Name>
      <ReactionBasis>MolarConc</ReactionBasis>
      <ReactionHeat>-3600</ReactionHeat>
      <ReactionHeatCO>0</ReactionHeatCO>
      <ReactionPhase>Liquid</ReactionPhase>
      <ReactionType>Kinetic</ReactionType>
      <StoichBalance>0</StoichBalance>
      <A_Forward>3833</A_Forward>
      <A_Reverse>0</A_Reverse>
      <Approach>0</Approach>
      <ConcUnit>kmol/m3</ConcUnit>
      <ConstantKeqValue>0</ConstantKeqValue>
      <E_Forward>0</E_Forward>
      <E_Reverse>0</E_Reverse>
      <Expression></Expression>
      <KExprType>Gibbs</KExprType>
      <Kvalue>0</Kvalue>
      <Rate>0</Rate>
      <RateEquationDenominator></RateEquationDenominator>
      <RateEquationNumerator></RateEquationNumerator>
      <ReactionGibbsEnergy>-2159.99999999999</ReactionGibbsEnergy>
      <Tmax>3000</Tmax>
      <Tmin>0</Tmin>
      <VelUnit>kmol/[m3.s]</VelUnit>
      <ReactionKinFwdType>Arrhenius</ReactionKinFwdType>
      <ReactionKinRevType>Arrhenius</ReactionKinRevType>
      <ReactionKinFwdExpression></ReactionKinFwdExpression>
      <ReactionKinRevExpression></ReactionKinRevExpression>
      <E_Forward_Unit>J/mol</E_Forward_Unit>
      <E_Reverse_Unit>J/mol</E_Reverse_Unit>
      <ReactionKinetics>Expression</ReactionKinetics>
      <ScriptTitle></ScriptTitle>
      <EquilibriumReactionBasisUnits>Pa</EquilibriumReactionBasisUnits>
      <Compounds>
        <Compound Name="Cis-2-butene" StoichCoeff="-1" DirectOrder="1" ReverseOrder="0" IsBaseReactant="true" />
        <Compound Name="Trans-2-butene" StoichCoeff="1" DirectOrder="0" ReverseOrder="0" IsBaseReactant="false" />
      </Compounds>
    </Reaction>
  </Reactions>
  <StoredSolutions />
  <DynamicsManager>
    <Type>DWSIM.DynamicsManager.Manager</Type>
    <Description></Description>
    <CurrentSchedule></CurrentSchedule>
    <ScheduleList />
    <EventSetList />
    <IntegratorList />
  </DynamicsManager>
  <OptimizationCases>
    <OptimizationCase>
      <Type>DWSIM.SharedClasses.Flowsheet.Optimization.OptimizationCase</Type>
      <name>optcase0</name>
      <description></description>
      <stats></stats>
      <solvm>AL_BRENT</solvm>
      <maxits>100</maxits>
      <tolerance>1E-06</tolerance>
      <epsX>0.001</epsX>
      <epsF>0.001</epsF>
      <epsG>0.001</epsG>
      <epsilon>0.001</epsilon>
      <barriermultiplier>0.0001</barriermultiplier>
      <numdevscheme>2</numdevscheme>
      <boundvariables>false</boundvariables>
      <objfunctype>Variable</objfunctype>
      <type>Minimization</type>
      <expression></expression>
      <Variables />
    </OptimizationCase>
  </OptimizationCases>
  <SensitivityAnalysis>
    <SensitivityAnalysisCase>
      <Type>DWSIM.SharedClasses.Flowsheet.Optimization.SensitivityAnalysisCase</Type>
      <iv1>
        <Type>DWSIM.SharedClasses.Flowsheet.Optimization.SAVariable</Type>
        <objectID></objectID>
        <objectTAG></objectTAG>
        <propID></propID>
        <unit></unit>
        <points>5</points>
        <name></name>
        <id></id>
        <currentvalue>0</currentvalue>
      </iv1>
      <iv2>
        <Type>DWSIM.SharedClasses.Flowsheet.Optimization.SAVariable</Type>
        <objectID></objectID>
        <objectTAG></objectTAG>
        <propID></propID>
        <unit></unit>
        <points>5</points>
        <name></name>
        <id></id>
        <currentvalue>0</currentvalue>
      </iv2>
      <dv>
        <Type>DWSIM.SharedClasses.Flowsheet.Optimization.SAVariable</Type>
        <objectID></objectID>
        <objectTAG></objectTAG>
        <propID></propID>
        <unit></unit>
        <points>5</points>
        <name></name>
        <id></id>
        <currentvalue>0</currentvalue>
      </dv>
      <name>SACase0</name>
      <description></description>
      <stats></stats>
      <numvar>1</numvar>
      <depvartype>Variable</depvartype>
      <expression></expression>
      <IV1>
        <Type>DWSIM.SharedClasses.Flowsheet.Optimization.SAVariable</Type>
        <objectID></objectID>
        <objectTAG></objectTAG>
        <propID></propID>
        <unit></unit>
        <points>5</points>
        <name></name>
        <id></id>
        <currentvalue>0</currentvalue>
      </IV1>
      <IV2>
        <Type>DWSIM.SharedClasses.Flowsheet.Optimization.SAVariable</Type>
        <objectID></objectID>
        <objectTAG></objectTAG>
        <propID></propID>
        <unit></unit>
        <points>5</points>
        <name></name>
        <id></id>
        <currentvalue>0</currentvalue>
      </IV2>
      <DV>
        <Type>DWSIM.SharedClasses.Flowsheet.Optimization.SAVariable</Type>
        <objectID></objectID>
        <objectTAG></objectTAG>
        <propID></propID>
        <unit></unit>
        <points>5</points>
        <name></name>
        <id></id>
        <currentvalue>0</currentvalue>
      </DV>
      <Variables />
      <DepVariables />
    </SensitivityAnalysisCase>
  </SensitivityAnalysis>
  <PetroleumAssays />
  <WatchItems />
  <ScriptItems />
  <ChartItems />
  <ParticleSizeDistributions />
  <Spreadsheet>
    <RGFData>{"MAIN":"{\"?xml\":{\"@version\":\"1.0\"},\"grid\":{\"@xmlns:xsd\":\"http://www.w3.org/2001/XMLSchema\",\"@xmlns:xsi\":\"http://www.w3.org/2001/XMLSchema-instance\",\"head\":{\"meta\":{\"culture\":\"id-ID\",\"editor\":\"ReoGrid Core\",\"core-ver\":\"2.1.0.0\"},\"rows\":\"65536\",\"cols\":\"100\",\"default-row-height\":\"20\",\"default-col-width\":\"70\",\"focus-forward-direction\":\"down\",\"settings\":{\"@meta\":\"30475026398\"},\"script\":null},\"style\":{\"@font\":\"Arial\",\"@font-size\":\"10\",\"@align\":\"general\",\"@valign\":\"middle\"},\"rows\":null,\"cols\":null,\"v-borders\":null,\"h-borders\":null,\"cells\":null}}"}</RGFData>
  </Spreadsheet>
  <PanelLayout>&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;!--DockPanel configuration file. Author: Weifen Luo, all rights reserved.--&gt;
&lt;!--!!! AUTOMATICALLY GENERATED FILE. DO NOT MODIFY !!!--&gt;
&lt;DockPanel FormatVersion="1.0" DockLeftPortion="450" DockRightPortion="0.203007518796992" DockTopPortion="0.25" DockBottomPortion="0.152227705943669" ActiveDocumentPane="0" ActivePane="6"&gt;
  &lt;Contents Count="17"&gt;
    &lt;Content ID="0" PersistString="DWSIM.LogPanel" AutoHidePortion="0.152227705943669" IsHidden="False" IsFloat="False" /&gt;
    &lt;Content ID="1" PersistString="DWSIM.MaterialStreamPanel" AutoHidePortion="0.25" IsHidden="False" IsFloat="False" /&gt;
    &lt;Content ID="2" PersistString="DWSIM.WatchPanel" AutoHidePortion="0.152227705943669" IsHidden="True" IsFloat="False" /&gt;
    &lt;Content ID="3" PersistString="DWSIM.FormCharts" AutoHidePortion="0.25" IsHidden="False" IsFloat="False" /&gt;
    &lt;Content ID="4" PersistString="DWSIM.FormDynamicsManager" AutoHidePortion="0.25" IsHidden="False" IsFloat="False" /&gt;
    &lt;Content ID="5" PersistString="DWSIM.FormDynamicsIntegratorControl" AutoHidePortion="0.369804903093313" IsHidden="True" IsFloat="False" /&gt;
    &lt;Content ID="6" PersistString="DWSIM.FormFileExplorer" AutoHidePortion="0.25" IsHidden="False" IsFloat="False" /&gt;
    &lt;Content ID="7" PersistString="DWSIM.FlowsheetSurface_SkiaSharp" AutoHidePortion="0.25" IsHidden="False" IsFloat="False" /&gt;
    &lt;Content ID="8" PersistString="DWSIM.FormNewSpreadsheet" AutoHidePortion="0.25" IsHidden="False" IsFloat="False" /&gt;
    &lt;Content ID="9" PersistString="DWSIM.FormScript" AutoHidePortion="0.25" IsHidden="False" IsFloat="False" /&gt;
    &lt;Content ID="10" PersistString="DWSIM.ProFeatures.FormGHG" AutoHidePortion="0.25" IsHidden="False" IsFloat="False" /&gt;
    &lt;Content ID="11" PersistString="DWSIM.ProFeatures.FormCosting" AutoHidePortion="0.25" IsHidden="False" IsFloat="False" /&gt;
    &lt;Content ID="12" PersistString="DWSIM.FormSimulSettings" AutoHidePortion="0.25" IsHidden="True" IsFloat="True" /&gt;
    &lt;Content ID="13" PersistString="DWSIM.Thermodynamics.MaterialStreamEditor" AutoHidePortion="450" IsHidden="False" IsFloat="False" /&gt;
    &lt;Content ID="14" PersistString="DWSIM.UnitOperations.EditingForm_ReactorCSTR" AutoHidePortion="450" IsHidden="False" IsFloat="False" /&gt;
    &lt;Content ID="15" PersistString="DWSIM.Thermodynamics.MaterialStreamEditor" AutoHidePortion="450" IsHidden="False" IsFloat="False" /&gt;
    &lt;Content ID="16" PersistString="DWSIM.UnitOperations.EditingForm_Adjust" AutoHidePortion="450" IsHidden="False" IsFloat="False" /&gt;
  &lt;/Contents&gt;
  &lt;Panes Count="7"&gt;
    &lt;Pane ID="0" DockState="Document" ActiveContent="7"&gt;
      &lt;Contents Count="9"&gt;
        &lt;Content ID="0" RefID="6" /&gt;
        &lt;Content ID="1" RefID="7" /&gt;
        &lt;Content ID="2" RefID="4" /&gt;
        &lt;Content ID="3" RefID="1" /&gt;
        &lt;Content ID="4" RefID="8" /&gt;
        &lt;Content ID="5" RefID="3" /&gt;
        &lt;Content ID="6" RefID="9" /&gt;
        &lt;Content ID="7" RefID="10" /&gt;
        &lt;Content ID="8" RefID="11" /&gt;
      &lt;/Contents&gt;
    &lt;/Pane&gt;
    &lt;Pane ID="1" DockState="DockBottom" ActiveContent="0"&gt;
      &lt;Contents Count="1"&gt;
        &lt;Content ID="0" RefID="0" /&gt;
      &lt;/Contents&gt;
    &lt;/Pane&gt;
    &lt;Pane ID="2" DockState="DockBottom" ActiveContent="-1"&gt;
      &lt;Contents Count="1"&gt;
        &lt;Content ID="0" RefID="2" /&gt;
      &lt;/Contents&gt;
    &lt;/Pane&gt;
    &lt;Pane ID="3" DockState="Float" ActiveContent="-1"&gt;
      &lt;Contents Count="1"&gt;
        &lt;Content ID="0" RefID="5" /&gt;
      &lt;/Contents&gt;
    &lt;/Pane&gt;
    &lt;Pane ID="4" DockState="DockBottom" ActiveContent="-1"&gt;
      &lt;Contents Count="1"&gt;
        &lt;Content ID="0" RefID="5" /&gt;
      &lt;/Contents&gt;
    &lt;/Pane&gt;
    &lt;Pane ID="5" DockState="Float" ActiveContent="-1"&gt;
      &lt;Contents Count="1"&gt;
        &lt;Content ID="0" RefID="12" /&gt;
      &lt;/Contents&gt;
    &lt;/Pane&gt;
    &lt;Pane ID="6" DockState="DockLeft" ActiveContent="14"&gt;
      &lt;Contents Count="4"&gt;
        &lt;Content ID="0" RefID="13" /&gt;
        &lt;Content ID="1" RefID="14" /&gt;
        &lt;Content ID="2" RefID="15" /&gt;
        &lt;Content ID="3" RefID="16" /&gt;
      &lt;/Contents&gt;
    &lt;/Pane&gt;
  &lt;/Panes&gt;
  &lt;DockWindows&gt;
    &lt;DockWindow ID="0" DockState="Document" ZOrderIndex="1"&gt;
      &lt;NestedPanes Count="1"&gt;
        &lt;Pane ID="0" RefID="0" PrevPane="-1" Alignment="Right" Proportion="0.5" /&gt;
      &lt;/NestedPanes&gt;
    &lt;/DockWindow&gt;
    &lt;DockWindow ID="1" DockState="DockLeft" ZOrderIndex="3"&gt;
      &lt;NestedPanes Count="1"&gt;
        &lt;Pane ID="0" RefID="6" PrevPane="-1" Alignment="Bottom" Proportion="0.5" /&gt;
      &lt;/NestedPanes&gt;
    &lt;/DockWindow&gt;
    &lt;DockWindow ID="2" DockState="DockRight" ZOrderIndex="4"&gt;
      &lt;NestedPanes Count="0" /&gt;
    &lt;/DockWindow&gt;
    &lt;DockWindow ID="3" DockState="DockTop" ZOrderIndex="5"&gt;
      &lt;NestedPanes Count="0" /&gt;
    &lt;/DockWindow&gt;
    &lt;DockWindow ID="4" DockState="DockBottom" ZOrderIndex="2"&gt;
      &lt;NestedPanes Count="3"&gt;
        &lt;Pane ID="0" RefID="1" PrevPane="-1" Alignment="Right" Proportion="0.5" /&gt;
        &lt;Pane ID="1" RefID="4" PrevPane="1" Alignment="Top" Proportion="0.5" /&gt;
        &lt;Pane ID="2" RefID="2" PrevPane="1" Alignment="Right" Proportion="0.261838440111421" /&gt;
      &lt;/NestedPanes&gt;
    &lt;/DockWindow&gt;
  &lt;/DockWindows&gt;
  &lt;FloatWindows Count="2"&gt;
    &lt;FloatWindow ID="0" Bounds="336, 370, 900, 155" ZOrderIndex="0"&gt;
      &lt;NestedPanes Count="1"&gt;
        &lt;Pane ID="0" RefID="3" PrevPane="-1" Alignment="Right" Proportion="0.5" /&gt;
      &lt;/NestedPanes&gt;
    &lt;/FloatWindow&gt;
    &lt;FloatWindow ID="1" Bounds="510, 240, 900, 600" ZOrderIndex="1"&gt;
      &lt;NestedPanes Count="1"&gt;
        &lt;Pane ID="0" RefID="5" PrevPane="-1" Alignment="Right" Proportion="0.5" /&gt;
      &lt;/NestedPanes&gt;
    &lt;/FloatWindow&gt;
  &lt;/FloatWindows&gt;
&lt;/DockPanel&gt;</PanelLayout>
  <MessagesLog>
    <Message>[13/10/2025 23.03.34] Estimated NRTL IP set for Cis-2-butene/Trans-2-butene: -159,52/168,57/0,2</Message>
    <Message>[13/10/2025 23.07.56] Flowsheet berhasil dihitung. [0,5212s]</Message>
    <Message>[13/10/2025 23.08.16] Flowsheet berhasil dihitung. [0,02471s]</Message>
    <Message>[13/10/2025 23.09.01] Flowsheet berhasil dihitung. [0,02196s]</Message>
    <Message>[13/10/2025 23.11.30] Flowsheet berhasil dihitung. [0,2363s]</Message>
    <Message>[13/10/2025 23.11.43] Flowsheet berhasil dihitung. [0,1363s]</Message>
    <Message>[13/10/2025 23.11.59] Flowsheet berhasil dihitung. [0,1385s]</Message>
    <Message>[13/10/2025 23.12.29] 2: Single-compound Stream detected. Switching to PH Flash</Message>
    <Message>[13/10/2025 23.12.29] Flowsheet berhasil dihitung. [0,09131s]</Message>
    <Message>[13/10/2025 23.12.48] 2: Single-compound Stream detected. Switching to PH Flash</Message>
    <Message>[13/10/2025 23.12.48] Flowsheet berhasil dihitung. [0,1432s]</Message>
    <Message>[13/10/2025 23.13.25] 2: Single-compound Stream detected. Switching to PH Flash</Message>
    <Message>[13/10/2025 23.13.25] Flowsheet berhasil dihitung. [0,1053s]</Message>
    <Message>[13/10/2025 23.13.33] 2: Single-compound Stream detected. Switching to PH Flash</Message>
    <Message>[13/10/2025 23.13.33] Flowsheet berhasil dihitung. [0,1091s]</Message>
    <Message>[13/10/2025 23.15.10] Caught unhandled exception: Object reference not set to an instance of an object.</Message>
    <Message>[13/10/2025 23.15.10] Caught unhandled exception: Object reference not set to an instance of an object.</Message>
    <Message>[13/10/2025 23.16.46] 2: Single-compound Stream detected. Switching to PH Flash</Message>
    <Message>[13/10/2025 23.17.04] 2: Single-compound Stream detected. Switching to PH Flash</Message>
    <Message>[13/10/2025 23.17.05] 2: Single-compound Stream detected. Switching to PH Flash</Message>
    <Message>[13/10/2025 23.17.05] Flowsheet berhasil dihitung. [0,1279s]</Message>
    <Message>[13/10/2025 23.17.05] Flowsheet berhasil dihitung. [0,5468s]</Message>
    <Message>[13/10/2025 23.17.49] 2: Single-compound Stream detected. Switching to PH Flash</Message>
    <Message>[13/10/2025 23.17.50] 2: Single-compound Stream detected. Switching to PH Flash</Message>
    <Message>[13/10/2025 23.17.50] Flowsheet berhasil dihitung. [0,1425s]</Message>
    <Message>[13/10/2025 23.17.50] Flowsheet berhasil dihitung. [0,5237s]</Message>
    <Message>[13/10/2025 23.18.17] 2: Single-compound Stream detected. Switching to PH Flash</Message>
    <Message>[13/10/2025 23.18.17] Flowsheet berhasil dihitung. [0,1249s]</Message>
    <Message>[13/10/2025 23.18.17] Flowsheet berhasil dihitung. [0,4846s]</Message>
    <Message>[13/10/2025 23.18.29] 2: Single-compound Stream detected. Switching to PH Flash</Message>
    <Message>[13/10/2025 23.18.29] Flowsheet berhasil dihitung. [0,1205s]</Message>
    <Message>[13/10/2025 23.18.29] Flowsheet berhasil dihitung. [0,4492s]</Message>
    <Message>[13/10/2025 23.20.00] File C:\Users\User\Downloads\CSTR DWSIM.dwxmz saved successfully.</Message>
  </MessagesLog>
  <Results>
    <Type>DWSIM.SharedClasses.DWSIM.Flowsheet.FlowsheetResults</Type>
    <TotalCAPEX>0</TotalCAPEX>
    <TotalOPEX>0</TotalOPEX>
    <ResidualMassBalance>2.22044604925031E-16</ResidualMassBalance>
    <TotalEnergyBalance>-2.75335310107039E-14</TotalEnergyBalance>
    <AdditionalResults />
  </Results>
</DWSIM_Simulation_Data>
