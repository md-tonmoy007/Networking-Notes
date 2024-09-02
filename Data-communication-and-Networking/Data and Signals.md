---
title: Data and Signals
tags:
  - "#physical-layer"
  - "#analog-signal"
  - digital-signal
Chapter: "3"
---
`To be transmitted, data must be transformed to electromagnetic signals`

## Analog and DIGITAL Data:

analog => continuous
digital => discontinuous/discrete

**periodic and non-periodic signals**:
A periodic signal completes a pattern within a measurable time frame, called a
period, and repeats that pattern over subsequent identical periods. The completion of one full pattern is called a cycle. A non-periodic signal changes without exhibiting a pattern or cycle that repeats over time.

><mark class="hltr-red">In data communications, we commonly use periodic
  analog signals and nonperiodic digital signals.</mark>


- If a signal does not change at all, its frequency is zero.
- If a signal changes instantaneously, its frequency is infinite.

**Phase:** Phase describes the position of the waveform relative to time 0.
#### Composite signal 

>
> If the composite signal is periodic, the decomposition gives a series of signals with 
> discrete frequencies; if the composite signal is nonperiodic, the decomposition
> gives a combination of sine waves with continuous frequencies.
> 


#### Bandwidth:

```
The bandwidth of a composite signal is the difference between the
highest and the lowest frequencies contained in that signal.
```


#### Baseband Transmission

```
Baseband transmission means sending a digital signal over a channel without changing the digital signal to an analog signal.

```

`A digital signal is a composite analog signal with an infinite bandwidth.`


```
Low-Pass Channel with Wide Bandwidth:

Baseband transmission of a digital signal that preserves the shape of the digital signal is possible only if we have a low-pass channel with an infinite or very wide bandwidth.
```


## Transmission Impairment
![[Pasted image 20240720123734.png]]

- Attenuation means loss of energy. amplify used to amplify signal
- Distortion means the changes of signal
- Noises: thermal noise, induced noise, crosstalk and impulse noise.


## Data Rate Limits

### Nyquist Bit Rate

				BitRate = 2 x bandwidth x 10g2 L

```
bandwidth is the bandwidth of the channel, L is the number of signal
levels used to represent data, and BitRate is the bit rate in bits per second.
```


### Shannon Capacity

				Capacity = bandwidth X log2 (1 + SNR)


```
In this formula, bandwidth is the bandwidth of the channel, SNR is the signal-to-noise ratio, and capacity is the capacity of the channel in bits per second.
```

>
>The Shannon capacity gives us the upper limit;
>the Nyquist formula tells us how many signal levels we need.
>

## Performance

1. Bandwidth
	- Bandwidth in hertz:  the range of frequencies contained in a composite signal or the range of frequencies a channel can pass
	- Bandwidth in bits/second:  the number of bits per second that a channel, a link, or even a network can transmit. 
2. Throughput: The throughput is a measure of how fast we can actually send data through a network.
3. Latency: The latency or delay defines how long it takes for an entire message to completely arrive at the destination from the time the first bit is sent out from the source
	> **Latency = propagation time + transmission time + queuing time + processing delay**



## Topics to look at:
- Bandwidth-Delay Product
- Digital Signal as Composite analog signal
- Frequency-domain representation
- 