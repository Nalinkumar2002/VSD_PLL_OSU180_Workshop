# PLL_OSU180nm_VSD

![vsdopentutorial](Images/vsd.png)

![Size](https://img.shields.io/github/repo-size/Nalinkumar2002/vsd_pll_workshop?color=red)
![Last Commit](https://img.shields.io/github/last-commit/Nalinkumar2002/vsd_pll_workshop?color=green)


## 1. Introduction to On-chip clock multiplier

 This repository focuses on design of On-Chip clock multiplier / PLL for VSD Open 2021 PLL Workshop.
 In this repository we are going to cover a brief description on PLL and also its pre-layout and post-layout simulations. 
 PLL is found in many wireless, radio, and general electronic items from mobile phones to broadcast radios, televisions to Wi-Fi routers, walkie talkie radios to professional   communications systems etc.
The On-chip clock multiplier is present in almost all synchronous processor chips (Integrated circuits).



## Table of Contents
- [1. Introduction to On-chip clock multiplier](#1-introduction-to-On-chip-clock-multiplier)
- [3. EDA Tools Used](#3-eda-tools-used)
- [4. Pre-layout Simulations](#4-Pre-layout-Simulations)
- [5. Post-layout and Simulations](#5-Post-Layout-Simulations)
- [6. Author](#6-Author)
- [7. Acknowledgments](#7-acknowledgments)
- [8. References](#8-References)


## 4. EDA Tools Used 
The design has been built using open-source EDA tools. The library used is osu180nm. 

1. [Ngspice](http://ngspice.sourceforge.net/download.html)
2. [Magic](http://opencircuitdesign.com/magic/)

## 5. Pre-layout Simulations
The complete circuit of PLL is built hierarchically using the following subcircuit blocks.

</p>

![Alt Text](Images/blockdiagram.jpg)

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

## 9. References

- https://github.com/parasgidd/avsdpll_3v3.git


