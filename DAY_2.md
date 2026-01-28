## 1.Introduction
This project focuses on the design and analysis of CMOS analog test circuits using Cadence Virtuoso Analog Design Environment (ADE-L). The primary objective is to study the DC operating point, transient response, AC behavior, and small-signal gain of PMOS–NMOS based circuits. These analyses are essential for validating proper biasing, stability, and amplification characteristics of analog blocks such as current mirrors, amplifiers, and bias reference circuits (used in BGR and analog front-ends).
## Circuit 2 Overview
<img width="1366" height="768" alt="159b3642f68ca0cfe56a5ebf91f571b4_ckt2" src="https://github.com/user-attachments/assets/228b19f5-55c1-4ca6-9685-af581b3d7457" />
This circuit consists of:
PMOS (PM1) connected to VDD acting as an active load
NMOS (NM2) connected to GND acting as the input-driven device
External DC bias (V4) applied to the PMOS gate
AC + DC input (V3) applied to the NMOS gate
Output taken at Vout3, the common drain node
This configuration represents a basic CMOS common-source amplifier with externally biased PMOS load, commonly used in analog signal amplification and bias testing.
## 2. DC Analysis (Operating Point)
Purpose:
To verify proper biasing and ensure both MOSFETs operate in the saturation region.
Observed DC Parameters (from Cadence):
PMOS (PM1)
Drain current (Id) ≈ 2.64 µA
VGS ≈ −500 mV
VDS ≈ −458 mV
gm ≈ 48.6 µS
NMOS (NM2)
Drain current (Id) ≈ 2.64 µA
VGS ≈ 600 mV
VDS ≈ 541 mV
gm ≈ 34.6 µS

DC Conclusion:
<img width="633" height="686" alt="954784c974b8cc64f588edb045221ee0_Screenshot%20from%202026-01-28%2010-43-25" src="https://github.com/user-attachments/assets/f6a9b062-35fe-450b-96f2-8fcefde5f1f3" />

✔ PMOS and NMOS currents are equal → current continuity satisfied
✔ Both transistors operate in saturation region
✔ Output node Vout3 is correctly biased

## 3. Transient Analysis
Purpose:
To analyze the time-domain response of the circuit when a small AC signal is applied.
Input:
Sinusoidal signal applied at Vin3
Small amplitude to maintain linear operation
Observations:
<img width="775" height="642" alt="5570f574598403f83c588003490838c7_Screenshot%20from%202026-01-28%2011-19-34" src="https://github.com/user-attachments/assets/54ef0910-7962-48a3-8b64-a78e7b6609f5" />

Output waveform at Vout3 is inverted
Output follows input variations smoothly
No oscillations or distortion observed
Transient Conclusion:
✔ Circuit behaves as a stable common-source amplifier
✔ Suitable for small-signal analog processing
<img width="1366" height="768" alt="0abf04fae0db818b8040156eda26f79d_ckt123" src="https://github.com/user-attachments/assets/b3c1e2cf-4549-4864-bad4-effca3a044fd" />

## 5. AC Analysis
Purpose:
To study the frequency response of the amplifier.
Observations:
High gain at low frequencies
Gain decreases as frequency increases
Roll-off due to MOS parasitic capacitances
<img width="1600" height="900" alt="a35fe6fecbb46a296fc4918b4c877158_AC%20analysis" src="https://github.com/user-attachments/assets/d56d6507-f536-4760-83f2-ba8a57614f38" />
AC Conclusion:
<img width="998" height="830" alt="dc5e4c12b75ff773a72616fee02b8c25_Screenshot%20from%202026-01-28%2011-21-17" src="https://github.com/user-attachments/assets/387b02f2-3cd9-4ead-8e39-7b0f92aa3416" />

✔ Circuit provides effective low-frequency amplification
✔ Bandwidth is limited by device capacitances
✔ Dominant pole present at output node

5. Gain Analysis
<img width="998" height="833" alt="cc8e7498882e80635ef3eec907281414_parameter%20analysis" src="https://github.com/user-attachments/assets/517b0eab-a1b3-4e8d-867a-97dfda0e8859" />

Small-Signal Voltage Gain:
## 𝐴𝑣=𝑔𝑚×𝑅𝑜𝑢t
Where:𝑔𝑚 is mainly contributed by NMOS
𝑅𝑜𝑢𝑡 is the parallel output resistance of PMOS and NMOS
From Simulation:
NMOS gm ≈ 34.6 µS
PMOS gm ≈ 48.6 µS
Resulting gain is moderate to high
Gain Conclusion:
✔ Higher gain compared to diode-connected load circuits
✔ External biasing improves output resistance and gain

## 6. Power Consumption
Drain current ≈ 2.64 µA
Operates at 1 V supply
Very low power dissipation
✔ Suitable for low-power analog blocks

## 7. Applications of This Circuit
Analog amplification stage
Bias testing for Bandgap Reference (BGR)
Pre-amplifier in sensor interfaces
Low-power CMOS analog blocks

## 8. Final Conclusion
This circuit demonstrates a well-biased CMOS common-source amplifier with:
Proper DC operating point
Stable transient response
Moderate-to-high AC gain
Low power consumption

## 1. Circuit 3 Overview
The amplifier test circuit is designed to evaluate the performance of an operational amplifier (op-amp) when driven by a biasing network formed using BJTs and resistors. The circuit acts as a signal conditioning and amplification block, commonly used in Bandgap Reference (BGR) systems and precision analog designs.
Major Blocks:
Resistor network (R2, R3, R4) for bias generation
NPN transistors (Q0, Q1) forming current biasing elements
Operational amplifier (I21) with differential inputs
Reference current source (V8)
Output node (Vout) connected to load/measurement point
<img width="1600" height="900" alt="b2445209c0372ac48e6c131269b98ca4_Screenshot%20from%202026-01-28%2014-40-59" src="https://github.com/user-attachments/assets/b5f89797-a6df-44ff-a5dc-8ab99019a1ed" />

## 2. DC Analysis (Operating Point)
Objective:
To verify correct biasing of the amplifier and ensure all devices operate in their intended regions.
Observed DC Parameters:
Resistors carry microampere-level currents
NPN transistors operate in forward-active region
Op-amp inputs (vin_p and vin_n) settle at nearly equal voltages
Output voltage (Vout) stabilizes without saturation

Key DC Observations:
Collector currents of Q0 and Q1 are well matched
Proper voltage drop across resistors confirms correct current flow
Op-amp remains within its linear operating range

DC Conclusion:
✔ Stable operating point achieved
✔ No device in cutoff or saturation
✔ Circuit is suitable for amplification

## 3. Transient Analysis
<img width="1600" height="900" alt="7422afd118696931c7d16898eabadee3_Screenshot%20from%202026-01-28%2015-26-14" src="https://github.com/user-attachments/assets/bca3ec29-6a6c-4aa4-afd8-d5bab1c709f2" />

Objective:
To observe the time-domain response of the amplifier to a varying input signal.
Input Condition:
Small-signal excitation applied through bias/reference node
Input variations kept small to ensure linear behavior
Observations:
Output responds smoothly to input changes
No overshoot or ringing observed
Fast settling time indicates good stability
Transient Conclusion:
✔ Amplifier is stable in time domain
✔ Suitable for low-noise and precision applications

## 4. AC Analysis
<img width="1600" height="900" alt="420e5036a34d51de898fa0f023f29aaf_Screenshot%20from%202026-01-28%2015-24-05" src="https://github.com/user-attachments/assets/b71fee50-858c-4572-92ce-4e9d35bba685" />

Objective:
To analyze the frequency response of the amplifier.
Observations:
High gain at low frequencies
Gain decreases gradually with increasing frequency
Dominant pole behavior observed
Phase margin remains within stable limits
AC Conclusion:
✔ Amplifier exhibits expected low-frequency gain
✔ Bandwidth limited by internal op-amp compensation
✔ Stable frequency response

## 5. Gain Analysis
Small-Signal Gain:
The amplifier gain is determined by the internal op-amp gain and external bias network.
Observations:
High open-loop gain at low frequency
Effective closed-loop gain maintained
Output swing remains within supply limits
Gain Conclusion:
✔ Suitable gain for signal amplification
✔ Bias network ensures stable operation

## 6. Power Analysis
Bias currents are in nanoampere to microampere range
Very low static power dissipation
Efficient for continuous operation
✔ Ideal for low-power BGR and analog front-end circuits

## 7. Applications of This Circuit
Bandgap Reference (BGR) amplification stage
Precision voltage/current reference circuits
Analog signal conditioning
Low-power sensor interfaces
