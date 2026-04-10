# 4_Stage_Signal_Conditioning_Circuit
I designed and simulated a 4-Stage Signal Conditioning Circuit in LTspice, featuring an Instrumentation Amplifier, a Tow-Thomas Band-Pass Filter, a Programmable Gain Amplifier (PGA) and a Half-Wave Rectifier.
## Stage 1: Instrumentation Amplifier ##
<img width="975" height="530" alt="image" src="https://github.com/user-attachments/assets/2972b558-4638-419b-94e9-5566ba70e800" />

Without RG:Vo|VB=-(R4(R1+R2))/(R3*R1)VB

Vo|VA=(R3+R4)/R3*VA

Vo=Ad(VA-VB)   =>  (R4(R1+R2))/(R3*R1)=(R3+R4)/R3 => R1=R4, R2=R3

=> Vo=(R3+R4)/R3(VA-VB)

With RG connected:
Vo1=R2[(1/R2+1/RG+1/R1)VB-VA/RG]

Vo=R4[(1/R3+1/R4+1/RG)*VA-VB/RG-Vo1/R3]

Vo=(VA-VB)(R4/R3+1+2R4/RG)  => Ad=R4/R3+1+2R4/RG=9 

I chose R3=RG=10kΩ=R2 => R4=R1=26.7kΩ

## Stage 2: Tow-Thomas Band-Pass Filter ##
<img width="975" height="579" alt="image" src="https://github.com/user-attachments/assets/d8aeaf06-7ec3-491e-ae61-a0738de44634" />

H0=R1/R; w0=1√(R2*R4*C1*C2); Q=R1√[C1/C2*1/(R2*R4)]

C1=C2=C

R2=R4

R2=1/w0*C

R1=Q*R2

R=R1/H0

w0=2πf0; f0=BW*Q=707Hz => w0=2π*707 rad/s

I chose C1=C2=100nF and R3=1kΩ => R2=R4=2.2kΩ => R1=1.5kΩ => R=1.5kΩ 

## Stage 3: Programmable Gain Amplifier (PGA) ##

<img width="952" height="565" alt="image" src="https://github.com/user-attachments/assets/4b0376f7-df8f-412b-84fb-f74bc7025395" />

Av[dB]={ -1, 2, 5, 8} => Av[linear]={0.89, 1.26, 1.78, 2.51}

Switch1-ON => |Av|=R0/(R1+R2+R3+R4)=0.89

Switch2-ON => |Av|=(R0+R1)/(R2+R3+R4)=1.26

Switch3-ON => |Av|=(R0+R1+R2)/(R3+R4)=1.78

Switch4-ON => |Av|=(R0+R1+R2+R3)/R4=2.51

Rin>3kΩ=>I chose R4=3.3kΩ => R3=0.825kΩ, R2=0.9kΩ, R1=1kΩ, R0=5.4kΩ

## Stage 4: Half-Wave Rectifier ##

<img width="975" height="579" alt="image" src="https://github.com/user-attachments/assets/d8937c52-490d-432f-999e-0c8241757262" />

Vout=0, Vin>0

Vout=-R2/R1*Vin, Vin<0

R2/R1=1 => I chose R2=R1=1kΩ

## Simulations performed ##

* DCOP

* AC - CMRR, PSRR

* Transient - Slew Rate and Total Harmonic Distortion (THD)


