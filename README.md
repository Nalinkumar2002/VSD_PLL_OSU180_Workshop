# vsd_pll_workshop

![Size](https://img.shields.io/github/repo-size/Nalinkumar2002/vsd_pll_workshop?color=red)
![Last Commit](https://img.shields.io/github/last-commit/Nalinkumar2002/vsd_pll_workshop?color=green)


## 1. Introduction to On-chip clock multiplier
This repository contains simulation files and other relevant files on the On-chip clock multiplier using PLL (Fclkin—5MHz to 12MHz, Fclkout—40MHZ to 100MHZ at 1.8v) IP worked on in the VSD PLL Workshop.
The target is to design a On-chip clock multiplier using the osu180nm technology node. 
The On-chip clock multiplier is present in almost all synchronous processor chips (Integrated circuits).



## Table of Contents
- [1. Introduction to On-chip clock multiplier](#1-introduction-to-On-chip-clock-multiplier)
- [2. Theory](#2-Theory)
- [3. Specification List](#3-specification-list)
- [4. EDA Tools Used](#4-eda-tools-used)
- [5. Pre-layout Simulations](#5-Pre-layout-Simulations)
- [6. Post-layout and Simulations](#6-Post-Layout-Simulations)
- [7. Author](#-Author)
- [8. Acknowledgments](#8-acknowledgments)


## 2. Theory

The clock generator is one of the most crucial part in synchronous processor & probably most susceptible after power lines which can cause failure of entire circuitry if not designed properly.

The phase locked loop or PLL is a circuit block that is widely used in radio frequency or wireless applications.

In view of its usefulness, the phase locked loop or PLL is found in many wireless, radio, and general electronic items from mobile phones to broadcast radios, televisions to Wi-Fi routers, walkie talkie radios to professional communications systems etc.

the circuit simulated here uses PLL block to get desired frequency at it’s output (which is 8 times to that of input frequency provided).
This IP block can be used for clock distribution for processor chip.  

## 3. Specification List

| Parameter| Description| Min | Type | Max | Unit | Condition |
| :---:  | :-: | :-: | :-: | :---:  | :-: | :-: |
|VDD|Digital supply voltage||1.8||V|T=-40 to 150C|
|FCLKREF|Reference clock frequency|5|10|12.5|MHz||	
|FCLKOUT|Output clock frequency|39.7|80.91|99.81|MHz|PLL mode, T=27C, VDD=1.8|
|FCLKOUT|Output clock frequency||||MHz|VCO mode, T=27C, VDD=1.8|
|DC|Duty Cycle|48||52|%|T=-40 to 150C|
|IBCP|Bias current for VCO||||uA||
|VVCO|Oscillatror control input voltage|.557||0.62|V|Vin_vco = 0V at t = 0 (.uic)|
|JRMS|Jitter (rms)||future work||ps|PLL mode, FCLKREF = 10MHz|
|TSET|Settlng Time|5.2|5|4.6|us|start from EN_CP and report 2 values; one at FCLKOUT=40MHz and one at FCLKOUT=100MHz|
|CL|Load Capacitance||||pF||
|IDDA|Analog Supply current||||ua|VVCO=0.8V, VCO mode|
|IDDA|Analog Supply current||||ua|FCLKREF=10MHz, PLL mode|
|IDDA|Analog Supply current||||pa|EN_VCO=0, EN_CP=0, FCLKREF=0|
|IDDD|Digital Supply Current||||uA|VVCO=0.8V, VCO mode|
|IDDD|Digital Supply Current||||uA|FCLKREF=10MHz, PLL mode|
|IDDD|Digital Supply Current||||uA|EN_VCO=0, EN_CP=0, FCLKREF=0|

## 4. EDA Tools Used 
The design has been built using open-source EDA tools. The library used is osu180nm. 

1. [Ngspice](http://ngspice.sourceforge.net/download.html)
2. [Magic](http://opencircuitdesign.com/magic/)

## 5. Pre-layout Simulations
The complete circuit of PLL is built hierarchically using the following subcircuit blocks.

</p>

![Alt Text](Image/blockdiagram.jpg)

</p>

Fig: Block Diagrm of PLL Design.

</p>

</p>


</p>
</p>

**Pre-layout Simulation Results**

</p>

![Alt Text](Images/prelayout_pll.png)

</p>

| Input Frequency | Output Frequency |
| :---:  | :-: |
|5MHz|39.73MHz|
|10MHz|80.91MHz|
|12MHz|96.1MHz|
|12.5MHz|99.81MHz|

## 6. Post-Layout Simulations 

### A. Phase Frequency Detector
![Alt Text](Images/pfd.png)

</p>

Fig: Layout of Phase Frequency Detector (PFD) or Phase Detector (PD)

</p>
</p>

![Alt Text](Images/postlayout_pfd.png)

</p>

Fig: Input-Output waveforms of Phase Frequency Detector (PFD) or Phase Detector (PD) </p>
     Inputs - Fin (Input Frequency) &
              Fvco_8 (Output Frequency divide by 8) </p> </p>
     Outputs - Up Signal &
               Down Signal         </p>

</p>
</p>

### B. Voltage Controlled Oscillator
![Alt Text](Images/vco101.png)


</p>

Fig: Layout of Voltage Controlled Oscillator (VCO).

</p>

</p>

![Alt Text](Images/postlayout_vco_in.png)
![Alt Text](Images/postlayout_vco_out.png)

</p>

Fig: Input-Output waveforms of Voltage Controlled Oscillator (VCO). </p>
Vin - Input Voltage </p>
Fout - Output Frequency

</p>

</p>

### C. Frequency Divider by 2
![Alt Text](Images/freqdiv2.png)

</p>

Fig: Layout of Frequency Divider by 2. </p> 
</p>


![Alt Text](Images/postlayout_freq_div_2.png)

</p>

Fig: Input-Output waveforms of Frequency Divider by 2. </p>
clk - Input Freqency. </p>
q - Output Freqency (Input Freq. by 2). </p>

</p>

### D. Frequency Divider by 8
![Alt Text](Images/freqdiv8.png)

</p>
</p>

Fig: Layout of Frequency Divider by 8. </p> 
</p>


![Alt Text](Images/postlayout_freq_div_8.png)

</p>

Fig: Input-Output waveforms of Frequency Divider by 8. </p>
clk - Input Freqency. </p>
q - Output Freqency (Input Freq. by 8). </p>

</p>

### E. 2:1 MUX
![Alt Text](Images/mux21.png)

</p>
Fig: Layout of 2:1 MUX. </p> 
</p>

![Alt Text](Images/postlayout_mux.png)

</p>
Fig: Input-Output waveforms of of 2:1 MUX. </p> 
i1 - Input 1 </p> 
i2 - Input 2 </p> 
sel - Select </p> 
out - Output </p> 
</p>

### F. Phase lock Loop 
</p>

![Alt Text](Images/PLLv3.png)

</p>
</p>
Fig: Layout of Phase Lock Loop (Combining all the Sub-circuits of PLL). </p> 
</p>

#### a. Input frequency = 5MHz

</p>

![Alt Text](Images/postlayout_pll.png)

</p>
</p>
Fig: Input-Output waveforms of PLL. </p> 
Fin - Input Frequency. </p> 
Fvco_8 - Output Frequency divide by 8. </p> 
up - Up signal </p> 
down - Down signal </p> 
Vcp - Input Voltaage of VCO  </p> 
fout - Output Frequency </p> 
</p>



Note: As there were limitaions for for layout of capacitor in OSU180 tech file, I'm unable to make layout of Low Pass Filter.
However, using more mature & advanced nodes & PDK tech file, it can be made on silicon. 



## 7. Author

🖊️ Nalinkumar S , B.E (Electronics and Communication Engineering), Madras Institute of Technology, Anna University, Tamil Nadu 

## 8. Acknowledgments

 - Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd. - kunalpghosh@gmail.com
 - Paras Gidd, M.Tech.( Microelectronics ), Manipal Institute of Technology,(MAHE), parasgidd@gmail.com


