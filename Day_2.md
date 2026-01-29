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

<img width="215" height="196" alt="Image" src="https://github.com/user-attachments/assets/9344fcfe-7761-49c2-a4c3-f2193eae6e3d" />

<img width="742" height="698" alt="Image" src="https://github.com/user-attachments/assets/b1be918b-93a4-464f-8afc-91d62c472f02" />

**Components and Connections**
1. PMOS Transistor (PM0)
+ Source connected to VDD = 1 V
+ Drain connected to the output node Vout
+ Gate biased using a DC voltage source (V2 = 500 mV)
+ Acts as a constant pull-up load
+ Width (w2) is treated as a swept parameter in DC analysis
2. NMOS Transistor (NM0)
+ Source connected to ground
+ Drain connected to Vout
+ Gate driven by Vin
+ Acts as the pull-down device

**Input and Biasing**
1. Vin (V1)
+ Small AC signal
+ Amplitude = 50 mV
+ Frequency = 1 kHz
2. PMOS Gate Bias (V2)
+ Fixed DC voltage = 500 mV
+ Ensures PMOS remains partially ON for proper biasing

### DC Analysis:
<img width="995" height="830" alt="Image" src="https://github.com/user-attachments/assets/bee6cf49-0109-4a5f-a747-b32a1ef9a678" />

**Plot Description**
+ X-axis: PMOS width (w2, in µm)
+ Y-axis: Voltage (V)
+ Red line: Vin (constant DC level ≈ 0.6 V)
+ Green curve: Vout
**Observations**
1. Vin is constant
+ The flat red line shows that input DC voltage is fixed.
2. Vout increases with PMOS width
+ As w2 increases, PMOS drive strength increases.
+ More current is supplied to the output node.
+ Output voltage rises gradually.
3. Non-linear relationship
+ The rise in Vout is not linear.
+ Caused by MOSFET saturation, channel-length modulation, and current balance between NMOS and PMOS.
  
### Transient Analysis:
<img width="999" height="836" alt="Image" src="https://github.com/user-attachments/assets/7080d3e2-d172-4cf9-aa34-db40d22838d3" />

**Observations from graph**
+ The input (Vin) is a sinusoidal waveform centered around ~600 mV with a small peak-to-peak variation (~100 mV).
+ The output (Vout) is also sinusoidal but with a much larger swing.
+ Vout peak value ≈ 880–900 mV.
+ Vout minimum value ≈ 220–250 mV.
+ The output is 180° out of phase with the input (when Vin is maximum, Vout is minimum).
+ The output waveform is smooth and continuous with no clipping or distortion.
+ The output oscillates symmetrically around a DC level close to ~550–600 mV.
  
### AC Analysis:
<img width="991" height="813" alt="Image" src="https://github.com/user-attachments/assets/f96393e6-8123-4391-851f-0b4abcd33e4e" />

**Observations from graph**
+ The input magnitude (Vin) remains constant at 1 V across all frequencies.
+ The output magnitude (Vout) remains almost constant at ~7.5 V in the low-frequency region.
+ A flat mid-band region is observed up to approximately 10⁸–10⁹ Hz.
+ Beyond this frequency, the output magnitude drops sharply, indicating gain reduction.
+ At very high frequencies (>10¹⁰ Hz), the output magnitude approaches near zero.
+ The response clearly shows a single-pole roll-off characteristic.

