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
+ Av=-gm3(ro3||ro4)

## Circuit 4- Differential Amplifier
<img width="269" height="235" alt="Image" src="https://github.com/user-attachments/assets/a8b438eb-4cb4-4c72-973b-e525e9051cc4" />
<img width="902" height="710" alt="Image" src="https://github.com/user-attachments/assets/ab1c2521-c679-4d5e-af58-66774a29b555" />

+ The circuit is a CMOS differential amplifier designed using 45 nm CMOS technology.
+ It consists of an NMOS differential input pair, a PMOS active load, and an NMOS tail current source.
+ The circuit operates with a supply voltage of 2 V.
+ Differential input signals Vinp and Vinn are applied to the NMOS input transistors.
+ A fixed bias voltage (Vbias) is used to set the tail current.
+ The PMOS transistors act as a current mirror load, converting differential current into a single-ended output.
+ The output voltage (Vout1) is taken from one side of the PMOS load.
+ The circuit amplifies the difference between Vinp and Vinn.

### Transient analysis
<img width="992" height="790" alt="Image" src="https://github.com/user-attachments/assets/e8db4862-5db4-492e-976c-12ebf2411fd4" />

+ Transient analysis is performed to study the time-domain response of the circuit.
+ Differential sinusoidal inputs (Vinp and Vinn) are applied with equal amplitude and opposite phase.
+ Vinp and Vinn are centered around ~1.2 V with a peak-to-peak swing of ~100 mV.
+ The output Vout1 is a sinusoidal waveform with a larger amplitude.
+ Vout1 swings approximately from ~0.9 V to ~1.6 V.
+ The output peak-to-peak swing is ~600–650 mV, indicating amplification.
+ The output waveform is smooth and continuous.
+ No clipping or distortion is observed in the output signal.
+ The output remains centered around a stable DC operating point.
+ The circuit shows proper differential amplification behavior in the time domain.
### AC analysis
<img width="995" height="810" alt="Image" src="https://github.com/user-attachments/assets/5070466d-1ab6-4215-9441-4a56b9f1ece3" />

+ Frequency sweep range: ~10⁻¹ Hz to 10¹¹ Hz
+ Input magnitudes:
+ Vinp ≈ 1 V (flat across all frequencies)
+ Vinn ≈ 1 V (flat across all frequencies)
+ Output magnitude (Vout1) at low frequencies: ≈ 13–14 V
+ Mid-band gain remains constant at ≈ 13–14 V/V
+ Flat gain region observed up to approximately 10⁸–10⁹ Hz
+ Gain roll-off begins around ~10⁹ Hz

## To Create a New Symbol
1. Create Cell View and Schematic
+ Go to Create → Cell View, open a new schematic, and design the required circuit.
+ Remove all the power supply sources from the schematic.
2. Create Pins
+ Click Create Pin or press B.
+ In the pop-up window, enter the pin name, select the direction (input/output/ground), set Usage as Schematic, and Signal Type as Signal.
+ For VDD, select Signal Type as Power; for VSS, select Ground; for VOUT, set Direction as Output and Signal Type as Signal.
3. Generate Symbol View
+ Go to Create → Cell View → Run Cell View.
+ Ensure the library name and cell name match the schematic and click OK.
+ Assign pins to left, right, top, and bottom as required.
4. Modify Symbol Shape
+ Use the Create Polygon option to change the shape of the pins or symbol if needed.
5. Test the Symbol
+ Open a new schematic cell view, add the created symbol, connect power supplies, and run simulations such as DC, Transient, and AC analysis.

<img width="895" height="726" alt="Image" src="https://github.com/user-attachments/assets/32282416-c363-41ff-8cf0-6199d7af7b43" />

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/b7dacfcd-def2-4bc5-b551-2d91cf3e18d5" />

<img width="898" height="723" alt="Image" src="https://github.com/user-attachments/assets/e83062d3-5d8d-42b3-8151-1c95cf2434e2" />

**Testing Symbol**


**Transient Analysis**

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/01818939-e6c9-474b-a4c0-aab75a31ea10" />

+ Two sinusoidal input signals vin1 and vin2 are applied to the OTA.
+ Both inputs have:
+ Frequency ≈ 1 kHz
+ Small amplitude (around ±50 mV)
+ DC level ≈ 1.2–1.3 V
+ vin1 and vin2 are out of phase, representing differential input operation.
+ The output voltage (vout) is a sinusoidal waveform.
+ Output DC level ≈ 1.38–1.40 V.
+ Output peak value ≈ 1.41 V.
+ Output minimum value ≈ 1.38 V.
+ Output peak-to-peak swing ≈ 30–40 mV.
+ Output waveform is smooth and periodic.
+ No clipping or distortion is observed.
+ Output follows the difference between vin1 and vin2, confirming differential amplification.
+ The output frequency matches the input frequency, indicating stable time-domain operation.

**AC Analysis**
<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/83124d44-4c5e-4d86-8ad9-55555b109448" />

+ Frequency sweep range: 10⁻¹ Hz to 10¹¹ Hz.
+ Input magnitudes:vin1 ≈ 1 V, vin2 ≈ 1 V
+ Both remain constant across frequency.
+ Output magnitude (vout) at low frequency ≈ 13–14 V.
+ Mid-band gain ≈ 13–14 V/V.
+ Gain remains flat from low frequency up to approximately 10⁸–10⁹ Hz.
+ High-frequency roll-off starts around 10⁹ Hz.
+ Beyond roll-off, output magnitude decreases rapidly.

## Conclusion:
The Day 2 session effectively enhanced understanding of CMOS analog circuit design using the Cadence tool through hands-on implementation and analysis. DC analysis helped in identifying proper biasing and operating points, while transient analysis verified correct time-domain behavior such as phase inversion and stable amplification. AC analysis provided insight into gain, bandwidth, and high-frequency limitations due to parasitic effects. The differential amplifier study demonstrated accurate differential operation with good gain and stability. Additionally, creating and testing custom symbols improved practical design workflow skills. Overall, the session established a strong base for advanced analog blocks, especially Bandgap Reference (BGR) circuits and mixed-signal IC design.
