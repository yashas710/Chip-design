# Chip-design
Hands on workshop based on Analog layout
1. Introduction
Analog circuit design plays a crucial role in modern integrated circuits, where stability, frequency response, and robustness against parameter variations are essential. In this project, a Floating Operational Transconductance Amplifier (OTA) based circuit is designed and analyzed using Cadence Virtuoso Analog Design Environment (ADE).
The objective of this work is to:
Design a floating OTA circuit
Analyze its AC response, DC behavior, and Transient performance
Verify frequency stability, gain characteristics, and time-domain response
All simulations are performed using Cadence Virtuoso Schematic Editor and Spectre Simulator, which are industry-standard tools for analog and mixed-signal IC design.
2. Design Tool and Simulation Environment
EDA Tool: Cadence Virtuoso
Analysis Types Used:
AC Analysis
DC Analysis
Transient Analysis
3. Circuit Design and Schematic
Description
The circuit is implemented using a floating OTA architecture, where the OTA operates without a direct ground reference at its input. This improves flexibility and allows differential signal handling.
The schematic includes:
<img width="1600" height="900" alt="11dd1664de43be5d711f39e4028804a9_DC%20analysis" src="https://github.com/user-attachments/assets/98fa141c-1cb5-4561-9cf3-1e255bae5a4d" />
Operational Transconductance Amplifier (OTA)
Biasing resistors to set operating point
NMOS transistor acting as a current-controlling element
Feedback network for stability and gain control
Input and output voltage nodes clearly defined
The design is created in Cadence Virtuoso Schematic Editor, and all components are connected following CMOS analog design rules.
4. AC Analysis – Magnitude Response
Description
AC analysis is performed to evaluate the frequency response of the circuit. A small-signal AC voltage of 1 V is applied at the input, and the output response is observed across a wide frequency range.
<img width="1600" height="900" alt="a35fe6fecbb46a296fc4918b4c877158_AC%20analysis" src="https://github.com/user-attachments/assets/c2b11f79-0a0d-4cb1-b6bf-fed49690f734" />
Observations:
The input voltage (Vin) remains constant across all frequencies
The output voltage (Vout) remains stable at low frequencies
At higher frequencies, the output shows variation due to:
Parasitic capacitances
Internal transistor poles
Bandwidth limitations of the OTA
This confirms the expected small-signal behavior of the circuit.
