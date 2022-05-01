# brent_kung_32bit

### Flow

As a part of 32-bit Brent-Kung adder for 2022 IEEE Solid-State Circuits Society (SSCS) Platform for IC Design Outreach (PICO) Open-Source Chipathon, 32-bit Brent-Kung adder will be designed in RTL using Verilog HDL. The RTL will be simulated in Xilinx Vivado Design Suite in the design phase. The test bench including many random test vectors will be utilized to ensure proper operation. Then, the design will be passed through OpenLane flow to obtain GDSII. It will be checked that there is no setup, hold, maximum capacitance, maximum slew violations. DC, LVS, and antenna checks will be done to obtain a clear design. Finally, the output will be simulated at the gate level using Icarus Verilog to see whether the design still works after the IC flow.



### Motivation

Adders are among the basic building blocks constituting many ASIC designs. ALU's, multipliers, and algorithms such as Fast Fourier Transform can be given as examples to show where adders are used [1]. With the inputs containing an increasing number of bits, straightforward adders such as Ripple-Carry Adder (RCA) started to become infeasible due to large delay coming from carry bits "rippled" to the next stage. Therefore, fast adders such as Brent-Kung, Sklansky, and Kogge-Stone started to be used. These tree adders provided great optimization in the computation delay at the expense of additional area consumption. The tree adders differ among themselves in terms of the number of logic levels, routing resource consumption, the number of logic gates, and maximum fanout on each gate [2]. In this work, 32-bit Brent-Kung adder will be designed to be used by the community as a fast adder in different places.



### Description

The block diagram of the design, obtained from [3], can be seen in Figure 1. At the pre-processing stage Generate (G) and Propagate (P) signals are calculated for every input bit pair using the formulas [2],

G(i) = A(i) AND B(i); for i = 0, 1, ... 31,
P(i) = A(i) XOR B(i); for i = 0, 1, ... 31.

Then, black cells and grey cells are used to obtain intermediate values from the G and P values. At the final stage, the values are passed through the post-processing stage to find the overall result.
![Block Diagram](../../tree/main/images/BrentKung_diagram.png)

                                  Figure 1: Block Diagram [3]



### Target Performance

The design will be implemented using SkyWater 130nm Free and Open Source (FOSS) production PDK. Inspecting the results in the literature, Brent-Kung adder 8-bit delay is 1.646 ns, 16-bit delay is 4.112 ns when implemented with 90 nm GPDK using Cadence tools [4]. Thinking 32-bit instead of 16-bit, taking the technology of 130 nm instead of 90 nm into account, and accounting for the optimization capability difference between proprietary and open-source tools, 20 ns would be a fair target. So, the target frequency is 5 MHz. 



### Team Member(s)

Serdar Ünal: Researcher at TUBITAK BILGEM (Integrated Circuit Design and Training Laboratory)



### References

[1] N. U. Kumar, K. B. Sindhuri, K. D. Teja and D. S. Satish, "Implementation and comparison of VLSI architectures of 16 bit carry select adder using Brent Kung adder," 2017 Innovations in Power and Advanced Computing Technologies (i-PACT), 2017, pp. 1-7, doi: 10.1109/IPACT.2017.8244982.

[2] N. Weste and D. Harris, CMOS VLSI design, 3rd ed. Pearson Education, 2005, pp. 651, 661.

[3] M. V and P. N, "Performance Analysis Of Parallel Prefix Adder", International Journal of Electrical Electronics and Data Communication, vol. 3, no. 7, 2015. Available: http://www.iraj.in/journal/journal_file/journal_pdf/1-159-143600590074-77.pdf. [Accessed 1 May 2022].

[4] S. Gauhar, A. Sharif and N. Alam, "Comparison of Parallel Prefix Adders Based on FPGA & ASIC Implementations," 2020 IEEE Students Conference on Engineering & Systems (SCES), 2020, pp. 1-6, doi: 10.1109/SCES50439.2020.9236737.
