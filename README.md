Logo of the workshop
Introduction of the workshop
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
In the channel induced charge is directly proportional to Vgs-Vth
Let's take L be effective channel length and consider length of the channel on x-axis and width of the channel on y-axis
V(x) is voltage at point 'x' along channel
SO Vgs-V(x) is effective gate to channel voltage at that point.
Induced charge at point at 'x' is Q(x) is directly proportional to ([Vgs-V(x)]-Vth)
fig 6 
There are two types of current from device point of view:
drift current-current due to potential difference for example due to potential at vds there is voltage of channel difference at source(0) and drain(Vds)
diffusion current- current due to difference in charge carrier concentration
As there is potential difference in channel i.e 0 to Vds there will be drift current
Id = velocity of charge carriers x available charge over channel widht
drift current formulae and drivation
fig7 and fig8 and fig 9
Saturation Region:
Channel voltage=Vgs-Vds
When we increase the potential of Vds gradually we observe the three conditions at this point
fig 10
When there is no channel formed near the drain region then region is called the pinch-off region and the condition is Vgs-Vds<=Vt(paper written)
fig 10
Introduction to spice:
Spice is used to get the characteristics of nmos and pmos as welll as delay of transistor 
Value of model parameters are unique for different respective technology
fig11:model and moderl parameter,model file 
fig12:defining the netlist
fig 13:nodes of the terminal
Lab actvity:
lab1,lab1 spice file ,lab1 -output
There are five different type of corners,they are:
1.tt
2.ff
3.sf
4.ss
5.
we are using different w and l technology
screenshot of w and l file
Day2:
The Id is a linear function of Vds in linear region
The Id is dependent on channel length modulation and Vds in saturation region
fig14
The channel length which is having below 0.25u is referred as short channel
When we are having the same W/L ratio with different width and Length:
1.Id is quadratic dependent on Vgs when it is having long channel 
2.Id is linearly dependent on Vgs when it is having short channel
To observe this situation we are using the same W/L ratio with different width and Length where we are calcualting the Id at constant Vds, the Id is increasing quadratic which is having long channel where as the Id is  quadratic function of Vgs at low gate voltage and linear function of Vgs at high gate voltage which is having short channel and this is occuring due to velocity saturation effect
fig 15 and fig16
There are four regions of operation:
1.
2.
3.
4.
Velocity Saturation effect:
for the lower values of electric field, the velocity of electric field is increases linear with electric field but after critical electric field the velocity of electric field become saturate.
for the both cases the formulae of velocity is 
velocity formulae
here we equate the two conditions and we get the critical electic field 
lets consider the Vgs-Vth=Vgt
For the cutoff region Id=0 as Vgt<0
For the remaining region the equation of Id is submit the vmin and we will get the Id equations
fig17
lab2 vds and vgs
CMOS voltage Transfer characcteristics:
