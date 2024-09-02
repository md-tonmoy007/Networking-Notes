---
title: Digital Transmission
tags: 
Chapter: "4"
---
# Digital-to-Digital conversion
 The conversion involves three techniques: line coding, block coding, and scrambling


## Line Codingx

=> Digital data to digital signals.
=> converts sequence of bits to digital signal
![[Pasted image 20240722083109.png]]

### Characteristics

#### 1. Signal Element Versus Data Element
-  A data element is the smallest entity that can represent a piece of information
- A signal element is the shortest unit (time-wise) of a digital signal
-  data elements are what we need to send; signal elements are what we can send. Data elements are being carried; signal elements are the carriers.


#### 2. Data Rate Versus Signal Rate
- The data rate defines the number of data elements (bits) sent in 1s (unit => bps)
- The Signal rate is the  number of signal element sent in 1s. (unit => baud) 
  
  `baud rate determines the requried bandwidth for a digital signal and it is proportional`
  
- One goal in data communications is to increase the data rate while decreasing the signal rate. Increasing the data rate increases the speed of transmission; decreasing the signal rate decreases the bandwidth requirement.
#### 3. Baseline Wandering
- The receiver calculates a running average of the received signal power. This average is called the baseline.
-  A long string of Os or 1s can cause a drift in the baseline (baseline wandering) and make it difficult for the receiver to decode correctly. 
#### 4. DC Components
- When the voltage level in a digital signal is constant for a while, the spectrum creates very low frequencies (results of Fourier analysis). These frequencies around zero, called DC (direct-current) components
#### 5. Self-synchronization
- To correctly interpret the signals received from the sender, the receiver's bit intervals must correspond exactly to the sender's bit intervals. 
#### 6. Built-in Error Detection
#### 7. Immunity to Noise and Interference
#### 8. Complexity


### Schemes

![[Pasted image 20240726075933.png]]

#### 1. Unipolar
>	Positive voltage -> 1
>	Negetive Voltage -> 0

![[Pasted image 20240726080302.png]]

```

It is called NRZ because the signal does not return to zero at
the middle of the bit.

```


#### 2. Polar
##### NRZ-L & NRZ-I

```
NRZ-L => 
1 --> neg voltage
0 --> positive voltage

NRZ-I =>
1 --> Transition
0 --> No transition

```

![[Pasted image 20240726081626.png]]


For NRZ-I if the data doesn't start with 0 (for example $1001101$) it may be confusing where to transition from. The data ($1001101$) is a binary so adding a 0 at the beginning doesn't change a thing. So the data will be $01001101$.
## Block Coding 

Block coding gives us redundancy ( to ensure synchronization and to provide inherent error detecting) and improve performance of line coding.

	
		Block coding is normally referred to as mB/nB coding;it replaces each 
		m~bit group with an n~bit group.
	




# Analog to digital conversion
In this section we describe two techniques,<mark class="hltr-red"> pulse code modulation</mark> and <mark class="hltr-red">delta modulation</mark>

## PCM
![[Pasted image 20240722165142.png]]

Steps of PCM => Sampling -> quantizing -> encoding
### Sampling:
- The analog signal is sampled every $Ts$ s
- $Ts$ is the sample interval or period.
- The inverse of the sampling interval is called the sampling rate or sampling frequency and denoted by $is$
- $is = 1/Ts$
- Three methods => Ideal, natural and flat-top

## Topics to look at:
- Line Coding schemes
	- non-Polar schemes => Non-Return-to-Zero (NRZ)
	- Polar schemes
	- Biphase : Manchester and Differential Manchester
	- AMI and Pseudoternary 



