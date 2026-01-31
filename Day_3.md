# Day 3
## Exploring Cadence Calculator and BGR Circuit Analysis
### Purpose of the session:
On Day 3 of the workshop, we learned how to perform calculations using the built-in calculator, configure calculator settings, and extract mathematical expressions. The session also covered spectrogram analysis, including how to use available plugins to analyze signal characteristics effectively and also analysing the BGR circuits.
### Circuit Measurement in Cadense using Spectrum analysis:
In analog IC design, circuit measurements such as Signal-to-Noise Ratio (SNR), Spurious-Free Dynamic Range (SFDR), and Total Harmonic Distortion (THD) are critical to evaluate the performance of a circuit. These metrics quantify how well a circuit preserves the input signal while minimizing noise, distortion, and spurious components. The input signal plays a major role in these measurements—its amplitude, frequency, and waveform directly affect the observed performance. Such analysis ensures circuits are linear, noise-resilient, and suitable for their intended applications, with typical target ranges like SNR > 60 dB, SFDR > 70–80 dB, and THD < 1% depending on design requirements, though exact values depend on the application and design specifications. Proper measurement and analysis ensure that the circuit meets its intended performance in real-world operation.
**Steps:**Measurements>Spectrum>select the waves for which you want the spectrum.
<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/8a91503e-0bf0-43e8-b74c-e8e37505aa5e" />
**Results:**
1. Vin:
+ ENOB = 9.88
+ SINAD = 61.30098dB
+ SNR = 61.89dB
+ SFDR = 70.55dB
2. Vout:
+ ENOB = 3.0047
+ SINAD = 19.85dB
+ SNR = 58.97dB
+ SFDR = 19.88dB
this is the spectrum of circuit 4 that is ota being designed in the previous session and in the outputs we can observe the different measurement at output panel.
### Calculator Performance in Cadence:
In Cadence, the Calculator Window is a powerful analysis tool used to derive custom measurements from simulation data. It enables designers to form mathematical expressions using node voltages, branch currents, and other simulation results to evaluate circuit performance. Common uses include computing voltage or current ratios, performing arithmetic operations, and applying mathematical functions such as differentiation and integration. For instance, expressions like V(out)/V(in) are used to determine gain, while d(V(out))/dt helps estimate slew rate during transient analysis. The calculator also supports advanced operations such as FFT, RMS, peak detection, and min/max evaluation. Overall, the Cadence calculator provides flexibility in extracting detailed performance parameters, making it an essential component for accurate and in-depth circuit verification.
**Steps in Cadense**
+ Open the Calculator from Tools → Calculator and select Wave.
+ From the Plot window, choose Vout1 and Vout2, then use the Subtract operation to form the expression.
+ Go to the ADE (ADEL) window, select Outputs → Setup, click Get Expression, name it CTAT/PTAT based on the requirement, and click Add.
+ Return to the Calculator, enable Function Panel to 'all', select Derivative, and click Evaluate to obtain the slope of the waveform.
### Example Problem:
<img width="1009" height="835" alt="Image" src="https://github.com/user-attachments/assets/80767d8f-72c6-4168-afda-2b8b364acba4" />
**DC Analysis:**

<img width="940" height="797" alt="Image" src="https://github.com/user-attachments/assets/3a2734a1-e9ed-4d0a-8f9b-97659b68b1f9" />

+ CTAT ( Complementary to Absolute Temperature) = V<sub>BE</sub> = Negative TC.
+ PTAT (Proportional to Absolute Temperature ) = 
