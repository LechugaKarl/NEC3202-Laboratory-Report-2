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

- Frequency Modulating a Square Wave: To observe the fundamental behavior of a Voltage-Controlled Oscillator (VCO) and how its output frequency shifts between two distinct states in response to a binary input.
- Generating an FM Signal Using Speech: To demonstrate the application of FM in real-time audio transmission and observe the continuous frequency variations caused by complex, non-periodic waveforms.
- Considering the Spectral Composition of FM Signals: To analyze the time-domain representation of FM signals and acknowledge the existence of multiple sidebands generated even by simple modulating tones.
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

![Image Alt](https://github.com/LechugaKarl/NEC3202-Laboratory-Report-2/blob/main/assets/06b9a1e7-c0d9-44f2-8aad-cb418cfcb01a.jpg?raw=true)

________________________________________________________________________________________________________________________________________________________________________________________________________________________

OBJECTIVES:
- Setting up the FM Modulator: To configure the VCO to establish a stable carrier frequency ($f_c$) as a reference for the demodulation process.
- Setting up the Zero-Crossing Detector: To implement a comparator-based circuit that converts a sinusoidal FM carrier into a squared-up pulse train suitable for timing analysis.
- Investigating the Operation of the ZCD: To verify that the detector generates fixed-duration pulses at every zero-crossing, effectively converting frequency changes into a variable duty cycle.
- Transmitting and Recovering a Sinewave using FM: To validate the end-to-end performance of the FM system by extracting a smooth sinusoidal message from the modulated carrier using a low-pass filter.
- Transmitting and Recovering Speech using FM: To evaluate the fidelity and noise resilience of the Zero-Crossing Detector when processing complex, high-dynamic-range audio signals.

________________________________________________________________________________________________________________________________________________________________________________________________________________________

BLOCK DIAGRAM : 
![Image Alt](https://github.com/LechugaKarl/NEC3202-Laboratory-Report-2/blob/main/assets/7b06c4a4-26c1-40f3-8d06-e254ef271763.jpg?raw=true)

OUTPUT:

![Image Alt](https://github.com/LechugaKarl/NEC3202-Laboratory-Report-2/blob/main/assets/97d6f471-b6d9-4364-a29b-bcc07443aada.jpg?raw=true)

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

The shift from analog to digital communication is driven by the need for data integrity and noise resistance. However, because the world is inherently analog, we must first slice continuous signals into discrete pieces through a process called sampling. This experiment explores the first step of the Analog-to-Digital Conversion (ADC) process. By taking periodic "snapshots" of a signal’s voltage, we can represent a complex waveform as a series of pulses. The challenge for engineers is choosing a sampling method that accurately captures the message without losing the details necessary for high-fidelity reconstruction at the receiver.

![Image Alt]()

________________________________________________________________________________________________________________________________________________________________________________________________________________________

OBJECTIVES:

- Sampling a Simple Message: To observe the basic process of pulse amplitude modulation (PAM) and how periodic snapshots of a sinewave can represent the original signal.
- Reconstructing a Sampled Message: To demonstrate the role of a low-pass filter in smoothing discrete voltage samples back into a continuous analog waveform.
- Aliasing: To investigate the effects of violating the Nyquist Criterion and observe the resulting signal distortion when the sampling rate is too low.
________________________________________________________________________________________________________________________________________________________________________________________________________________________

BLOCK DIAGRAM : 
![Image Alt]()

OUTPUT:

![Image Alt]()

LEARNINGS:

One of the most eye-opening parts of this lab is seeing how much the shape of a sample matters. With Natural Sampling, you can still see the original signal's curve on the top of each pulse, but with sample and hold, the pulses look like a series of flat steps. While the flat steps of Sample-and-Hold might look less accurate to the eye, we learned that this method is actually much better for digital systems because it gives the downstream electronics a steady, unchanging voltage to measure.

We also discovered that the magic of turning these pulses back into music or speech lies entirely in the Low-Pass Filter. By filtering the sampled signal, we essentially remove the high-frequency switching noise of the sampling clock, leaving only the original message behind. It highlights a core engineering principle: as long as you sample fast enough (the Nyquist rate), those discrete pulses contain all the information needed to recreate the original signal perfectly.
________________________________________________________________________________________________________________________________________________________________________________________________________________________

CONCLUSION:

This experiment confirms that sampling is the essential bridge between the analog and digital worlds. We successfully demonstrated that while Natural Sampling preserves the message's contour during the sampling window, Sample-and-Hold is the more robust choice for modern Pulse Code Modulation (PCM) systems. The ability to reconstruct the original sinewave using a simple low-pass filter proves that discrete time-sampling is a valid and efficient way to transport analog information.


</details>

<details>
<summary>EXPERIMENT #12 - PCM Encoding</summary>

INTRODUCTION:

The transformation from analog waveforms to digital strings occurs during encoding. This stage takes samples of a signal and assigns them numerical values. It is the core of modern data systems. By mapping voltage levels to binary words, we create a robust message. This allows data to travel over long distances without losing its original meaning.

![Image Alt]()

________________________________________________________________________________________________________________________________________________________________________________________________________________________

OBJECTIVES:

- Introduction to PCM Encoding Using a Static DC Voltage: To map a constant analog voltage to a specific 8-bit binary word and understand the digital logic levels used in the encoder.
- PCM Encoding of a Variable DC Voltage: To observe how the binary output changes in discrete steps as the input voltage is manually varied across its full dynamic range.
- Quantization: To identify the "rounding error" or difference between the actual analog input and the nearest available digital level, characterizing quantization noise.
- PCM Encoding of Continuously Changing Voltages: To monitor the serial bitstream produced when encoding dynamic signals (like sinewaves) and understand the relationship between signal frequency and data throughput.
________________________________________________________________________________________________________________________________________________________________________________________________________________________

BLOCK DIAGRAM : 
![Image Alt]()

OUTPUT:

![Image Alt]()

LEARNINGS:

Working with the encoder shows how analog precision is traded for digital reliability. The module takes a sample and finds the nearest binary match. This process, called quantization, is where a small amount of detail is lost. This loss is known as quantization noise. When looking at the oscilloscope, the serial output looks like a fast sequence of high and low pulses. Without the frame sync signal, these pulses would be a mystery to the receiver. The sync pulse acts as a marker for the start of each binary word. This ensures the receiver knows which bits belong together.
________________________________________________________________________________________________________________________________________________________________________________________________________________________

CONCLUSION:

The experiment confirms that encoding is the vital bridge for digital data. It proves that binary mapping makes signals resistant to small errors. While quantization adds a tiny amount of noise, the benefit is a clear and manageable stream. This stage is the foundation for all modern phone and internet traffic.

</details>

<details>
<summary>EXPERIMENT #13 - PCM Decoding</summary>

INTRODUCTION:

Decoding is the mirror of encoding. It takes a string of bits and builds back the analog shape. This process must be perfectly timed. If the receiver misses a single bit, the message is ruined. This lab focuses on how a decoder reads binary words and outputs the correct voltage levels. It is the final step in getting a message back to human ears.

![Image Alt]()

________________________________________________________________________________________________________________________________________________________________________________________________________________________

OBJECTIVES:

- Setting up the Encoder: To establish a synchronized digital source by configuring bit-clocks and frame synchronization pulses.
- Decoding the PCM Data: To utilize a PCM Decoder module to interpret serial binary words and convert them back into a staircase-like analog voltage.
- Encoding and Decoding Speech: To test the transparency and latency of a complete PCM link when transmitting real-world audio information.
- Recovering the Message: To apply post-decoding filtration to eliminate high-frequency switching noise and restore the final output to its original analog form.
________________________________________________________________________________________________________________________________________________________________________________________________________________________

BLOCK DIAGRAM : 
![Image Alt]()

OUTPUT:

![Image Alt]()

LEARNINGS:

The decoder creates a staircase version of the original signal. It holds each voltage steady until the next binary word arrives. This creates a jagged waveform that sounds harsh if left alone. To fix this, a low-pass filter is used. This filter smooths out the jumps between levels. It returns the signal to its natural, fluid state. The lab shows that timing is the most critical factor. If the clock or sync signal is lost, the output turns into static. This proves that digital success relies on perfect coordination between both ends of the link.
________________________________________________________________________________________________________________________________________________________________________________________________________________________

CONCLUSION:

This session validates the complete communication cycle. It shows that digital data can accurately represent complex analog sounds. By using a filter, the jagged steps of the decoder become a clean wave again. The lab proves that PCM is a reliable way to move information over any distance.

</details>

<details>
<summary>EXPERIMENT #14 - Bandwidth limiting and restoring digital signals</summary>

INTRODUCTION:

Real channels have limits. Every wire or fiber optic cable acts as a filter. They only let certain frequencies pass. This is known as bandwidth. High-speed digital signals are made of many frequencies. When a channel is too narrow, these frequencies are lost. This causes the signal to smear and lose its shape. This lab investigates how to fix these damaged pulses.

![Image Alt]()

________________________________________________________________________________________________________________________________________________________________________________________________________________________

OBJECTIVES:

- The Effects of Bandwidth Limiting on PCM Decoding: To observe how restricting channel frequencies leads to bit errors and audible distortion in the recovered message.
- The Effects of Bandwidth Limiting on a Digital Signal's Shape: To visualize the loss of high-frequency harmonics, resulting in the rounding of square pulses and potential Inter-Symbol Interference (ISI)
- Restoring Digital Signals: To demonstrate the use of a comparator as a regenerative repeater to clean a distorted signal and recover a sharp, usable digital waveform.
________________________________________________________________________________________________________________________________________________________________________________________________________________________

BLOCK DIAGRAM : 
![Image Alt]()

OUTPUT:

![Image Alt]()

LEARNINGS:

A digital pulse needs high-frequency components to keep its sharp edges. When the channel bandwidth is low, these components disappear. On the scope, the once-square pulses look like rounded bumps. This smearing can lead to errors where the receiver can no longer tell a one from a zero. This is a major hurdle in high-speed engineering. However, a comparator can solve this. It acts as a gate that triggers a new, clean pulse whenever the messy input crosses a certain level. This restorative power is the greatest advantage of digital over analog.
________________________________________________________________________________________________________________________________________________________________________________________________________________________

CONCLUSION:

The study shows that while channels distort data, digital signals can be saved. Bandwidth limits the speed of a system, but restoration tools like comparators keep the data accurate. This balance between speed and clarity is the heart of link design. It confirms that digital systems are built to thrive even in imperfect conditions.

</details>
