## Bandgap Reference Circuit Analysis Using Cadence Virtuoso
## 1. Introduction
- A Bandgap Reference (BGR) circuit is a fundamental analog building block used to generate a temperature-independent reference voltage, typically around 1.2 V, which is widely used in ADCs, DACs, voltage regulators, and biasing circuits.
- The principle of a bandgap reference is based on combining:
- CTAT (Complementary To Absolute Temperature) voltage
- PTAT (Proportional To Absolute Temperature) voltage
- By properly scaling and summing these voltages, the temperature dependency cancels out, producing a stable reference voltage.

## 2. Circuit Overview
The schematic consists of:
Circuit 1:
<img width="1009" height="835" alt="0215b72cd96e43b06e80edca69590169_currentsourceproblem" src="https://github.com/user-attachments/assets/b7996ed8-99f0-492a-b5ee-dcdeb5874c17" />

Circuit 2:
<img width="1600" height="900" alt="1d88d15770c494e3ebaffdb05889f739_crt5resistors" src="https://github.com/user-attachments/assets/c3e86540-a92c-4262-885a-13a7066b2ef9" />

- A DC supply (VDD = 2 V)
- Two NPN BJTs (Q0 and Q1) operating at different current densities
- Two current sources (100 µA each)
- Ground reference
- Output nodes labeled VOUT1 and VOUT2
- Although this is shown as a current-source test configuration, it forms the core of a bandgap reference, where PTAT and CTAT voltages are generated across BJTs.

## 3. Operating Principle of Bandgap Reference
The total bandgap reference voltage is given by:
VREF=VBE+k⋅ΔVBE
​Where:VBE → CTAT component, ΔVBE​ → PTAT component, k → scaling factor (set by current ratio / resistor ratio)

## 4. CTAT Voltage Generation 
<img width="658" height="784" alt="currentsourceCTATSlope" src="https://github.com/user-attachments/assets/97725337-1567-47ea-814a-cb4cd5b8624f" />

The base-emitter voltage of a BJT decreases with temperature:
dVBE/dT ≈ −1.5 to −2 mV/°C
Thus, VBE​ is a CTAT voltage.

In the Given Circuit
- Transistor Q0 / Q1 is biased by a constant current source (100 µA)
- The voltage at the base-emitter junction provides VBE
- This voltage is extracted at nodes VOUT1 / VOUT2

Observation:
VBE decreases linearly with temperature → confirms CTAT behavior

## 5. PTAT Voltage Generation 
When two BJTs operate at different current densities:
ΔVBE = VT*ln*n​
Where: VT = kT/q, ΔVBE​ is directly proportional to temperature. Thus, ΔVBE is a PTAT voltage.
<img width="634" height="770" alt="currentSourcePTATSLope" src="https://github.com/user-attachments/assets/05e5746f-806b-4dea-a505-2f4e66abdcfa" />

PTAT Calculation

Assuming:
- Equal collector currents
- Different emitter areas (A₁ ≠ A₂)
- ΔVBE = kT/q*ln⁡(N)

For example, if area ratio 
N=8,
ΔVBE = (26mV)ln⁡(8)≈54mV at 300K,

In the Given Circuit
- Q0 and Q1 operate at equal currents (100 µA)
- Effective area mismatch (model-defined)
- Voltage difference between VOUT1 and VOUT2 gives ΔVBE
- VPTAT = VOUT1 − VOUT2
- Observe slope with temperature

 Observation:
 <img width="995" height="837" alt="81e61730da73a9a662f65767dc4f84c7_crt5case1" src="https://github.com/user-attachments/assets/db9b7a53-b029-433a-a156-b8af0033b36e" />

ΔVBE increases linearly with temperature → confirms PTAT behavior

## 6. Formation of Bandgap Reference Voltage
- The final reference voltage is obtained by summing:
- VREF = VBE + k⋅ΔVBE 
- Where:Scaling factor k is set using resistor ratios or current mirrors
- Proper selection ensures: dVREF/dT ≈ 0
- Typical Result: VREF ≈ 1.2V

## 7. DC Analysis (Cadence ADE-L)
<img width="940" height="797" alt="CurrentSourDC" src="https://github.com/user-attachments/assets/0cfb5b99-44f1-46ed-8acb-a19658873381" />

Purpose:Verify correct biasing,
Ensure all BJTs operate in forward active region.

Steps:
- ADE-L → Analysis → DC
- Run simulation
- Observe:Collector currents,VBE values,Node voltages,Confirms stable DC operating point.

## 8. Transient Analysis
Purpose: Check startup behavior,Verify settling time.

Steps:
- ADE-L → Transient Analysis
- Simulation time: 0 → 10 µs
- Plot VREF vs time

 Observation:Output stabilizes without oscillations, No latch-up condition observed.

## 9. AC Analysis (Small Signal)
Purpose:
- Check PSRR (Power Supply Rejection Ratio)
- Frequency stability

Observation:Low gain at high frequencies, Good supply noise rejection

## 10.Spectrum Analysis of Bandgap Reference Circuit Using Rectangular Window
1. Purpose of Spectrum Analysis in the Bandgap Reference Circuit

Although a bandgap reference is primarily a DC circuit, spectrum analysis is performed to:
- Examine noise components present at the reference output
- Study low-frequency and high-frequency spectral behavior
- Evaluate the effect of device noise and supply ripple
- Verify that no unwanted AC components disturb the DC reference voltage.

In this work, spectrum analysis using a rectangular window is carried out on the VREF (output node) of the bandgap reference circuit using Cadence Virtuoso ADE-L.
<img width="1600" height="900" alt="measurementSpectrumCRT4SYM" src="https://github.com/user-attachments/assets/7f3f8dce-c0ff-4363-b944-ef9a934ec394" />

2. Rectangular Window in Cadence Spectrum Analysis
A rectangular window assumes that the signal is observed over a finite time interval without any edge smoothing. In Cadence, this window is automatically applied when no explicit windowing is selected during FFT or spectrum analysis.
Mathematically, the rectangular window is defined as:
𝑤(𝑡)={1 :	0≤𝑡≤𝑇 , 0 : otherwise
- Where: T is the observation time. The signal is directly truncated at the time boundaries

## 11. Temperature Analysis Summary
<img width="1001" height="819" alt="80015afdafbc86b638d11247afcc3bdc_crt5DCPtat_Ctat" src="https://github.com/user-attachments/assets/6c247a00-15c1-4beb-8ca7-2c30c64a3e62" />

Parameter	Behavior
- VBE	Decreases with temperature (CTAT)
- ΔVBE	Increases with temperature (PTAT)
- VREF	Nearly constant
- Confirms successful bandgap operation

## 12. Advantages of This Bandgap Design
- Low supply voltage operation (2 V)
- Temperature-stable reference
- Simple topology
- Suitable for IC integration

## 13. Applications
- Voltage regulators
- ADC / DAC references
- Biasing circuits
Power management ICs

