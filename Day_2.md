# Day2
## BGR Circuit design in Cadense Tool
# Purpose of the session:
The purpose of today’s session was to understand the fundamentals of analog circuit design using the Cadence tool, with a special focus on Bandgap Reference (BGR) circuits. The session aimed to familiarize participants with schematic design, simulation, and analysis in Cadence, and to study different types of BGR circuits used to generate stable reference voltages that are independent of temperature and supply variations. This knowledge is essential for designing reliable CMOS analog and mixed-signal circuits.
## Circuit 2:
 <img width="261" height="328" alt="Image" src="https://github.com/user-attachments/assets/83376d55-2f1d-4527-9def-2dbb7f9f5f4f" />
<img width="903" height="731" alt="Image" src="https://github.com/user-attachments/assets/ed3f5976-8e78-41f5-b19b-341fdbbf02b1" />


The given circuit is a CMOS inverter / common-source amplifier configuration implemented using NMOS and PMOS transistors in Cadence. It is primarily used to study:
+ DC operating point
+ Voltage transfer behavior
+ Gain characteristics (for AC analysis)
+ Transient response (time-domain behavior)\
**Components and Their Roles:**\
PMOS Transistor (PM0): 
+ Source connected to VDD = 1 V
+ Drain connected to the output node (Vout)
+ Gate connected to a fixed bias / control node
+ Acts as a pull-up device
+ Operates in saturation/linear region depending on input and sizing\
NMOS Transistor (NM0):
+ Source connected to ground
+ Drain connected to Vout
+ Gate driven by the input signal (Vin)
+ Acts as a pull-down device\
**Input Signal:**
+ Vin is a small AC signal source
+ Amplitude: 50 mV
+ Frequency: 1 kHz
+ This input controls the conduction of the NMOS transistor.


### DC Analysis
<img width="996" height="813" alt="Image" src="https://github.com/user-attachments/assets/1e6cde2a-1dcc-4be2-ada5-9a3dd9279266" />

DC analysis determines the steady-state operating point of the circuit by ignoring time variations and AC components.

In this plot:
+ X-axis: PMOS width (w2, in µm)
+ Y-axis: Voltage (mV)
+ Green curve: Vout
+ Red line: Vin (constant DC level)

**Observations from the Plot:**
+ Vin remains constant: The red line is flat, indicating that the input DC voltage does not change during the sweep.
+ Vout increases with PMOS width: As PMOS width (w2) increases: PMOS drive strength increases, More current is supplied to the output node, Vout shifts upward
+ Non-linear behavior: This is due to:
MOSFET saturation effects, Channel-length modulation, Balance between NMOS pull-down and PMOS pull-up currents

### Transient Analysis:
<img width="994" height="794" alt="Image" src="https://github.com/user-attachments/assets/ae335af1-07fb-40db-9075-c6c92a8a8266" />

**Observations from the Transient Plot**

1. Phase Inversion
+ Vout is approximately 180° out of phase with Vin
+ When Vin increases, NMOS conducts more → Vout decreases
+ Confirms inverting amplifier behavior
2. Amplitude Reduction
+ Output amplitude is smaller than input
+ Due to:
Limited transconductance (gm), Load resistance of PMOS, Small-signal operation around bias point
3. DC Offset at Output
+ Vout oscillates around a DC level (~540 mV)
+ This offset is set by the DC operating point obtained from DC analysis
4. Stable and Smooth Waveform
+ No distortion or clipping observed
+ Indicates: Proper biasing, Transistors remain in active/saturation region
  
### AC Analysis:
<img width="1000" height="799" alt="Image" src="https://github.com/user-attachments/assets/6f5e6281-a795-42ac-a374-59ae760c7e03" />

**Observations from the AC Plot**

1. Constant Input Magnitude
+ Vin remains flat across all frequencies
+ Indicates an ideal AC excitation with constant amplitude
2. Mid-Band Gain
+ Vout remains approximately constant at ~0.6 V
+ This corresponds to the mid-band gain of the amplifier
+ Voltage gain ≈ 0.6 V/V
3. Low-Frequency Behavior
+ At low frequencies, coupling and biasing allow full signal transfer
+ No attenuation observed
4. High-Frequency Roll-Off
+ At higher frequencies, Vout magnitude decreases sharply
+ Caused by: Gate-to-drain capacitance (Miller effect), Parasitic junction capacitances, Limited transistor transit frequency
5. Av= -gm1/gm2
  
## Circuit 3
