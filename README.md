## NEC3202-Laboratory-Report-2
Lab Report 2 ( Experiments 9-14 )
________________________________________________________________________________________________________________________________________________________________________________________________________________________
<details>
<summary>EXPERIMENT #9 - Frequency Modulation</summary>

INTRODUCTION:

In analog communication, Frequency Modulation (FM) represents a significant advancement over Amplitude Modulation (AM) schemes. While AM, DSBSC, and SSB systems are highly efficient in terms of bandwidth, they are inherently vulnerable to Atmospheric Noise and Electromagnetic Interference (EMI), which primarily manifest as amplitude fluctuations.
FM overcomes this by encoding the message signal into the instantaneous frequency of a carrier wave. Since the information is stored in the frequency shifts rather than the peak-to-peak voltage, an FM receiver can use "limiters" to clip off noise-induced amplitude spikes without losing the integrity of the original message. This experiment utilizes a Voltage-Controlled Oscillator (VCO) to demonstrate this fundamental shift in modulation theory.

![Image Alt](https://github.com/LechugaKarl/NEC3202-Laboratory-Report-2/blob/main/assets/exp9.jpg?raw=true)

________________________________________________________________________________________________________________________________________________________________________________________________________________________

OBJECTIVES:

- To characterize the VCO: Establish the rest frequency ($f_c$) of the Voltage-Controlled Oscillator at a $0\text{V}$ input.
- To demonstrate Frequency Deviation: Observe how the amplitude of a message signal (square wave and speech) directly correlates to the shift in carrier frequency.
- To analyze Signal Integrity: Compare the "flat envelope" of an FM signal against the variable envelopes of AM systems.
- To visualize Spectral Complexity: Observe how even a simple sinusoidal input produces a complex FM signal in the time domain, hinting at the existence of multiple sidebands (Bessel functions).
________________________________________________________________________________________________________________________________________________________________________________________________________________________

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

1. Clone the repository
2. Run `npm install`
3. Start with `npm start`

</details>

<details>
<summary>EXPERIMENT #11 - Sampling and Reconstruction</summary>

1. Clone the repository
2. Run `npm install`
3. Start with `npm start`

</details>

<details>
<summary>EXPERIMENT #12 - PCM Encoding</summary>

1. Clone the repository
2. Run `npm install`
3. Start with `npm start`

</details>

<details>
<summary>EXPERIMENT #13 - PCM Decoding</summary>

1. Clone the repository
2. Run `npm install`
3. Start with `npm start`

</details>

<details>
<summary>EXPERIMENT #14 - Bandwidth limiting and restoring digital signals</summary>

1. Clone the repository
2. Run `npm install`
3. Start with `npm start`

</details>
