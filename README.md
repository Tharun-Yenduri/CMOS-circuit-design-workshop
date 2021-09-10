**cmos ciruit design and spice simulation using sky130 Technology**
Introdution to Sky130:Sky130 is a foundry which is used to built a chip using 130nm technology by providing pdk's(Process Development Kit)
Day1:
What is circuit design and why do we need spice?
Circuit design is basically a way of achieving the required functionality by connecting PMOS and NMOS in certain manner.
Fig1 illustrates,depicts Basic circuit design
Spice will tune the delay of cell by Widht(W) and Length(L) of cell and spice simulation will give the output waveform of CMOS circuits
Fig 2 shows the readymade delay table of sample circuit which will give the delay of circuit by using input slew and output load
Introduction NMOS in ciruit design:
N type Metal Oxide Semiconductor(NMOS):It is a four terminal device,Isolation region(SiO2) will differentiate the two transistors
Fig 3
There are three modes of operation:
1.Cutoff region (Vgs<vth)
2.Resistive or Linear Region (Vgs>vth) & (vds<vth)
3.Saturation Region (Vgs>Vth) & (Vds>Vth)
Initially when Vgs is  zero there will be no transfer of electrons between source and drain,so resistance of Sd is high.This region is called Cutoff Region.
Strong Inversion and threshold voltage:
By applying certain potential there will be formation of depletion region and depletion widht will increase by increasing the potential at Vgs,at some point the part of p-type substrate i.e between source and drain will be converted to n-type material,so electrons will be accumulated between source and drain, this phenomenon is called strong inversion 
Threshold voltage(Vt):The voltage(Vgs) at which strong inversion occurs is called threshold voltageor It is minimum voltage required for the movement of electrons from source to drain.Spice model will give the threshold voltage of NMOS
Body terminal is used to tune the threshold voltage, by applying voltage at Vsb there will be additonal reverse bias which increases the depletion layer width between source and p-substrate will increase. 
Threshold volatage formulae
fig4 and fig5
2.Resistive Region:
By increasing the potential beyond the threshold voltage accumulation of electrons will be more between source and drain and this will leads to increase the channel widht and there will be flow of electrons between source and drain.
Vgs-Vth is the condition when the transistor will be on.
Accumulation Charges will be directly proportional to Vgs-Vth
When there is no potential given at Vds the voltage will be same across the whole channel
When Vds is given to the transistor the voltage will be vary across the channel as the voltage at source is zero and voltage at drain is Vds,so the voltage acroos the channel is vary from 0 to Vds. 
