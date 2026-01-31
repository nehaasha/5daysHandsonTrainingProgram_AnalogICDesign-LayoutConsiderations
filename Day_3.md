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
+ PTAT (Proportional to Absolute Temperature ) = ∂V<sub>BE</sub> = Positive TC.
+ ∂V<sub>BE</sub> =  V<sub>BE1</sub> -  V<sub>BE2</sub>
                   =  V<sub>o1</sub> -  V<sub>o2</sub>

<img width="1600" height="900" alt="Image" src="https://github.com/user-attachments/assets/657ed47d-6f2e-4ee6-92b7-fb3e302f404f" />

**Ectracting the expression:**


<img width="1195" height="644" alt="Image" src="https://github.com/user-attachments/assets/2ce29d05-d1fb-470b-ac8f-704c644606f5" />

**CTAT and PTAT slope calculation:**


<img width="658" height="784" alt="Image" src="https://github.com/user-attachments/assets/83be5ab4-4e51-4be7-8853-d8dd83a69c8a" />

<img width="634" height="770" alt="Image" src="https://github.com/user-attachments/assets/08295ddb-acaa-4b8f-bcd8-1f6c7a9f3d5e" />

+ ∂V<sub>BE</sub>/ ∂T = -1.5mV/Celsious.
+ ∂(delta)V<sub>BE</sub>/ ∂T = 400uV/Celsious.
+ Vref= C<sub>1</sub> V<sub>BE</sub> + C<sub>2</sub>(delta)V<sub>BE</sub>
+ ∂V<sub>ref</sub>/ ∂T= 0.
+ C<sub>1</sub> ∂V<sub>BE</sub>/ ∂T = - C<sub>2</sub>∂(delta)V<sub>BE</sub>
+ C<sub>1</sub>(-1.5mV/Celsious) = - C<sub>2</sub>(400uV/Celsious).
+ Let C<sub>1</sub>=1, C<sub>2</sub>=1.5m/400u = 3.75.

### BGR basic architecture design and anlysis:
<img width="659" height="602" alt="Image" src="https://github.com/user-attachments/assets/c384edc2-ed73-41be-93a8-2e8efe630d2f" />

<img width="1001" height="819" alt="Image" src="https://github.com/user-attachments/assets/c12f17ac-6429-4570-9e2f-5a3f1692e116" />

<img width="995" height="837" alt="Image" src="https://github.com/user-attachments/assets/fd105283-4ff8-4c97-abec-764a973ec4c3" />

+ A basic BJT-based temperature-independent bandgap reference (BGR), also called a first-order/classic BGR, is considered.
+ The reference voltage is given by Vref = V<sub>BE2</sub> + V<sub>T</sub> * ln(n) *c
+ Let R<sub>1</sub>=R<sub>2</sub> = 10kohm
+ For zero temperature coefficient (zero TC), the condition is ln(n) *(1+R<sub>2</sub>/R<sub>3</sub>)= 17.2.
+ taking n= 10, R<sub>2</sub>=10kohm, then R<sub>3</sub> = 1.545kohm.
+ Thus, the resistor values are designed for a temperature-independent BGR.
+ Differentiating V<sub>ref</sub> with respect to temperature gives ∂V<sub>ref</sub>/ ∂T = d(CTAT)/dT + d(PTAT)/dT∂V<sub>ref</sub>/ ∂T.
+ Using the Cadence calculator, the derivatives are obtained as:
+ Using the Cadence calculator, the derivatives are obtained as: deriv(CTAT)= -1.7110^-3 v/celcius and deriv(PTAT)= 202.210^-6 v/celcius.
+ Proper scaling of the PTAT term compensates the CTAT behavior, resulting in a zero-TC reference voltage.

<img width="992" height="826" alt="Image" src="https://github.com/user-attachments/assets/f3d9d26c-eec4-42d3-9040-9fac8c8a2598" />

+ for R<sub>3</sub> = 1.545Kohm , R<sub>2</sub>=10Kohm we got deriv(vref)= -1.9906 *10^-6.
+ so we need to design more accurate one by varying (1+R<sub>2</sub>/R<sub>3</sub>).
+ so to make deriv(vref) = 0,
  0 = deriv(CTAT) + deriv(PTAT) (1+R<sub>2</sub>/R<sub>3</sub>)\
  0= -1.7110^-3 + 202.2*10^-6 * (1+R<sub>2</sub>/R<sub>3</sub>)\
  (1+R<sub>2</sub>/R<sub>3</sub>) = 8.4569\
  So R<sub>2</sub> =10Kohm and R<sub>3</sub>= 1.34102 k ohm
+ Now we get, deriv(vref)=-19.66 uV/celcius

### Conclusion:
The Day 3 session provided practical insight into using the Cadence Calculator and spectrum analysis tools for detailed analog IC performance evaluation. Through spectrum analysis, key dynamic performance metrics such as SNR, SFDR, SINAD, and ENOB were extracted at both input and output, clearly demonstrating how circuit non-idealities affect signal quality. The calculator was effectively used to derive CTAT and PTAT expressions, calculate their temperature slopes, and validate theoretical expectations through simulation.
The Bandgap Reference (BGR) analysis showed how proper scaling of PTAT and CTAT components is essential to achieve temperature independence. Initial resistor values resulted in a small residual temperature coefficient, which was further minimized by adjusting the resistor ratio (1+R<sub>2</sub>/R<sub>3</sub>). By optimizing the resistor values, the temperature drift of the reference voltage was significantly reduced, confirming near zero-TC behavior. Overall, the session reinforced the importance of accurate expression extraction, derivative analysis, and iterative design optimization to achieve robust and reliable analog circuit performance.
  

