## NEC3202-Laboratory-Report-2
Lab Report 2 ( Experiments 9-14 )
________________________________________________________________________________________________________________________________________________________________________________________________________________________
<details>
<summary>EXPERIMENT #9 - Frequency Modulation</summary>

INTRODUCTION:

In analog communication, Frequency Modulation (FM) represents a significant advancement over Amplitude Modulation (AM) schemes. While AM, DSBSC, and SSB systems are highly efficient in terms of bandwidth, they are inherently vulnerable to Atmospheric Noise and Electromagnetic Interference (EMI), which primarily manifest as amplitude fluctuations.
FM overcomes this by encoding the message signal into the instantaneous frequency of a carrier wave. Since the information is stored in the frequency shifts rather than the peak-to-peak voltage, an FM receiver can use "limiters" to clip off noise-induced amplitude spikes without losing the integrity of the original message. This experiment utilizes a Voltage-Controlled Oscillator (VCO) to demonstrate this fundamental shift in modulation theory.

![Image Alt](https://github.com/LechugaKarl/NEC3202-Laboratory-Report-2/blob/main/assets/011370e9-059d-4411-8374-8e4886745089.jpg?raw=true)

________________________________________________________________________________________________________________________________________________________________________________________________________________________

OBJECTIVES:

- To characterize the VCO: Establish the rest frequency ($f_c$) of the Voltage-Controlled Oscillator at a $0\text{V}$ input.
- To demonstrate Frequency Deviation: Observe how the amplitude of a message signal (square wave and speech) directly correlates to the shift in carrier frequency.
- To analyze Signal Integrity: Compare the "flat envelope" of an FM signal against the variable envelopes of AM systems.
- To visualize Spectral Complexity: Observe how even a simple sinusoidal input produces a complex FM signal in the time domain, hinting at the existence of multiple sidebands (Bessel functions).
________________________________________________________________________________________________________________________________________________________________________________________________________________________

BLOCK DIAGRAM : 
![Image Alt](https://github.com/LechugaKarl/NEC3202-Laboratory-Report-2/blob/main/assets/4914a0c2-fe41-40a8-b6ac-e097b227e4f3.jpg?raw=true)

OUTPUT:

![Image Alt](https://github.com/LechugaKarl/NEC3202-Laboratory-Report-2/blob/main/assets/Screenshot%202026-03-08%20230950.jpg?raw=true)

LEARNINGS:

One of the most immediate takeaways from this lab is seeing how the FM signal maintains a perfectly flat envelope. In AM, you can see the message "riding" on top of the carrier, but in FM, the signal looks like a constant-strength wave that just happens to get squashed or stretched. This is the "secret sauce" of FM’s noise immunity; since the demodulator is only looking for frequency shifts, we can technically clip off any noise-induced voltage spikes without losing a single bit of the original audio.
We also get a clear look at how frequency deviation works in a practical sense. It’s not just that the frequency changes, but that the amount of change is tied directly to the message's amplitude. When we swapped a square wave for a speech signal, it became obvious that louder sounds push the carrier further away from its center frequency. This brings Carson’s Rule to life, you realize that while FM sounds better, it pays for that quality by taking up a much wider chunk of the frequency spectrum than an AM signal would.
Finally, observing a modulated sine wave reveals just how complex FM math really is. Unlike AM, which just gives you two neat sidebands, an FM signal is a chaotic-looking mix of multiple frequencies (governed by Bessel functions). Even a simple tone creates a rich spectral signature. Using the VCO module makes this abstract theory feel a lot more tangible, showing that while the hardware is relatively simple, the physics of what's happening inside that wire is incredibly sophisticated.
________________________________________________________________________________________________________________________________________________________________________________________________________________________

CONCLUSION:

The experiment confirms that Frequency Modulation provides a robust alternative to Amplitude Modulation by prioritizing signal quality over bandwidth economy. By using the VCO module, we demonstrated that the carrier's frequency varies in sympathy with the message signal's polarity and magnitude.
While FM requires a more complex mathematical model and generally consumes more bandwidth (as seen in the complex spectral composition of the modulated sine wave), the trade-off is a communication link that is remarkably resilient to environmental noise. This makes FM the preferred choice for applications where high fidelity is non-negotiable, such as professional mobile radio and high-quality broadcasting.

</details>

<details>
<summary>EXPERIMENT #10 - FM Demodulation</summary>

INTRODUCTION:

While FM provides excellent immunity to amplitude-based noise, it introduces a challenge at the receiving end: the information is no longer represented by voltage levels, but by the "timing" of the carrier oscillations. To recover the message, we need a system that acts as a frequency-to-voltage converter.
The Zero-Crossing Detector (ZCD) is a classic, elegant solution for this. By converting the received FM signal into a stream of constant-width pulses, we can use the density of these pulses to recreate the original signal. This experiment explores how to implement this "square-to-pulse" logic using the Emona Telecoms-Trainer 101, ultimately bridging the gap between frequency-modulated carriers and the baseband message we started with.

![Image Alt]()

________________________________________________________________________________________________________________________________________________________________________________________________________________________

OBJECTIVES:
- Understand ZCD Architecture: Trace the signal path through the comparator and the pulse-generator to understand how frequency is mapped to pulse duration.
- Implement FM Demodulation: Successfully set up the ZCD to demodulate an FM signal generated by a Voltage-Controlled Oscillator (VCO).
- Visualize the Conversion: Observe the relationship between the FM frequency, the duty cycle of the resultant pulse train, and the final recovered message.
- Analyze the Filtering Process: Demonstrate how a low-pass filter is essential for extracting the "average" voltage (the original message) from the ZCD's output pulses.

________________________________________________________________________________________________________________________________________________________________________________________________________________________

BLOCK DIAGRAM : 
![Image Alt]()

OUTPUT:

![Image Alt]()

LEARNINGS:

The beauty of the ZCD lies in how it turns a frequency problem into a duty-cycle problem. When you first pass your FM signal through a comparator, you are essentially cleaning it up; by clipping the signal into a strict square wave, you eliminate the amplitude-based noise that AM systems struggle with. The real "a-ha" moment comes when the ZCD generates a pulse of fixed duration every time the signal crosses zero. Since the duration of each pulse is locked, the only thing that changes when the carrier frequency shifts is how often those pulses appear.
This creates a variable duty cycle. When the carrier frequency is high, pulses are bunched together, which increases the average DC level of the signal. When the frequency is low, the pulses are spaced out, which drops that average level. This is where the low-pass filter earns its keep. It acts as an averaging circuit, essentially smoothing out the individual pulses into a continuous, varying DC voltage. Because that DC level perfectly tracks the duty cycle, the filter reconstructs a faithful copy of the original message. It’s a great example of how simple logic gates and basic filtering can perform complex signal processing tasks.
________________________________________________________________________________________________________________________________________________________________________________________________________________________

CONCLUSION:

This experiment demonstrates that while FM systems are more bandwidth intensive, their demodulation can be achieved through highly effective, relatively simple circuits like the Zero-Crossing Detector. By successfully recovering the message signal, we’ve confirmed that FM's robustness is not just theoretical it is a functional reality. The ZCD proves that by manipulating the duty cycle of a signal, we can easily extract information that was hidden in the frequency domain, reinforcing the fundamental engineering principle that if you can convert a signal into a predictable pulse train, you can almost always recover the underlying data.

</details>

<details>
<summary>EXPERIMENT #11 - Sampling and Reconstruction</summary>

INTRODUCTION:



![Image Alt]()

________________________________________________________________________________________________________________________________________________________________________________________________________________________

OBJECTIVES:


________________________________________________________________________________________________________________________________________________________________________________________________________________________

BLOCK DIAGRAM : 
![Image Alt]()

OUTPUT:

![Image Alt]()

LEARNINGS:


________________________________________________________________________________________________________________________________________________________________________________________________________________________

CONCLUSION:




</details>

<details>
<summary>EXPERIMENT #12 - PCM Encoding</summary>

INTRODUCTION:



![Image Alt]()

________________________________________________________________________________________________________________________________________________________________________________________________________________________

OBJECTIVES:


________________________________________________________________________________________________________________________________________________________________________________________________________________________

BLOCK DIAGRAM : 
![Image Alt]()

OUTPUT:

![Image Alt]()

LEARNINGS:


________________________________________________________________________________________________________________________________________________________________________________________________________________________

CONCLUSION:



</details>

<details>
<summary>EXPERIMENT #13 - PCM Decoding</summary>

INTRODUCTION:



![Image Alt]()

________________________________________________________________________________________________________________________________________________________________________________________________________________________

OBJECTIVES:


________________________________________________________________________________________________________________________________________________________________________________________________________________________

BLOCK DIAGRAM : 
![Image Alt]()

OUTPUT:

![Image Alt]()

LEARNINGS:


________________________________________________________________________________________________________________________________________________________________________________________________________________________

CONCLUSION:



</details>

<details>
<summary>EXPERIMENT #14 - Bandwidth limiting and restoring digital signals</summary>

INTRODUCTION:



![Image Alt]()

________________________________________________________________________________________________________________________________________________________________________________________________________________________

OBJECTIVES:


________________________________________________________________________________________________________________________________________________________________________________________________________________________

BLOCK DIAGRAM : 
![Image Alt]()

OUTPUT:

![Image Alt]()

LEARNINGS:


________________________________________________________________________________________________________________________________________________________________________________________________________________________

CONCLUSION:



</details>
