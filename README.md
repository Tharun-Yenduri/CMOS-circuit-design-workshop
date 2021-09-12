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
4 terminal device
consists of P-substrate
Isolation Region(SiO2)

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
![lab1 spicefile](https://user-images.githubusercontent.com/90343497/132996341-b03e2f86-ef34-4dd1-b6f2-60882db8f150.png)
![lab1](https://user-images.githubusercontent.com/90343497/132996762-585e5086-f355-46ae-8920-05b1661d90e1.png)
![lab1-output](https://user-images.githubusercontent.com/90343497/132996820-cf972072-a1a1-4f36-8ecd-4ecc1dc0bfba.png)
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
![lab2 vds spice](https://user-images.githubusercontent.com/90343497/132996856-3222012d-4750-4845-8eaa-500db5442cbe.png)
![lab2 vds spice simulation](https://user-images.githubusercontent.com/90343497/132996861-89a48dbf-b89c-4d65-b2d7-3324b3ac0d22.png)
![lab2 vds output](https://user-images.githubusercontent.com/90343497/132996871-f5a8f4ed-ffa4-4391-91ff-812866b2c8f8.png)
Vgs
![lab2 vgs spice](https://user-images.githubusercontent.com/90343497/132996903-5427e994-5f8e-4072-8e82-dcacfdd18cb2.png)
![lab2 vgs simulation](https://user-images.githubusercontent.com/90343497/132996906-91e08918-5bff-42aa-aab5-767ff04a8a31.png)
![lab2 vgs output](https://user-images.githubusercontent.com/90343497/132996910-ccbf68fc-07d9-4d35-a7a4-e5b640c58fee.png)
CMOS voltage Transfer characcteristics:
When Vgs is given to CMOS one of the mosfet will be off and other mosfet will be on so this is called Complementary Mosfet.
MOSFET as switch:
With infinite OFF resistance when |Vgs|<|Vth|
With finite ON resistance when |Vgs|>|Vth|
notes pic
current path
observations
load curve of pmos transistor
voltage transfer characteristics
Day3:
lab3 screenshots
![lab3 spice file vtc](https://user-images.githubusercontent.com/90343497/132996978-0aa7ceb3-6bb7-427f-a645-e3bb7c8a5ef5.png)
![lab 3 simulation vtc](https://user-images.githubusercontent.com/90343497/132996987-16a6d318-de5f-48b8-8b22-85044ad295d9.png)
![lab 3 vtc output](https://user-images.githubusercontent.com/90343497/132997004-5f73393d-137b-4e19-b4c1-1191773fe998.png)
![lab3 tran spice file](https://user-images.githubusercontent.com/90343497/132997019-a840dca0-2c6a-483e-b81e-969984bec8a0.png)
![lab 3 tran spice simulation](https://user-images.githubusercontent.com/90343497/132997033-415ba4dc-6bc7-4e75-9f76-618ce5cc132e.png)
![lab 3 tran output](https://user-images.githubusercontent.com/90343497/132997046-769ca728-1b6c-40c2-8f43-5c1ba8669901.png)
The characteristics that define the CMOS inverter robustness are:
1.Switching threshold voltage
2.Noise Margin
3.Power supply variation
4.Device variations
Switching threshold voltage of CMOS inverter(Vm):
For getting the Swithcing threshold voltage of CMOS Vin=Vout ,the point at pmos and nmos are at saturation region 
Here we are making two observations with one CMOS having w=0.36u,l=0.25u i.e same ascept ratio(W/L) for both pmos and nmos and other CMOS having W=0.9u,l=0.25 for pmos and w=0.36,l=0.25 for nmos then the switching of Voltage is less when pmos and nmos having ascept ratio(W/L) where is switching of voltage is more when widht of pmos is two times more than widht of nmos.
Switching threshold voltage of cmos having same ascept ratio for both pmos and nmos is low compared to cmos having pmos of 2 times the width of nmos.
At switching threshold voltage both pmos and nmos are in saturation region and both the transistors are turn "ON",at this voltage gain is high
As Vin = Vout we can get Vgs = Vdd
Switching threshold voltage formulae
To calculate the rise time delay and fall time delay we will do the transient analysis of CMOS
How to calculate the output rise time delay and fall time delay of an inverter:
output rise time delay = rise time of output - fall time of input at 50% of Vout
output fall time delay = fall time of output - rise time of input at 50% of Vout
table:
observations:
1.When pmos width is 2 times the width of nmos the rise time delay and fall time delay is almost equal which is characterstics of clock inverter/buffer
2.The remaining observations can be used for data path where data arrival time is less than data required time.
3.When pmos width is 4.7 times the nmos then the vm is lies between pmos of widht 4 times the nmos widht and pmos of width 5 times the nmos width
4.On increasing the widht of pmos the rise time delay is decreasing,so more area will be available to charge the capacitor and vm is increasing
Day4:
Noise Margin:Any inverter or any gates can have noise margin i.e cros-talks,glitches and those cross talks and glithces can be handled by handling the noise margin
Screen shot
lab4
![lab 4 noise margin spice file](https://user-images.githubusercontent.com/90343497/132997092-e9254618-ff93-4992-b242-f7bf6a4d9574.png)
![lab4 noise margin simulation](https://user-images.githubusercontent.com/90343497/132997099-9256696b-8298-481c-b423-db2865c2bf72.png)
![lab4 noise margin output](https://user-images.githubusercontent.com/90343497/132997110-93580c48-60fc-4219-bd5c-037bff2279a3.png)
Day5:
power supply variations:In this for the different power supplies how is the CMOS inverter is behaving
lab5:
![lab5 supply variation spice file](https://user-images.githubusercontent.com/90343497/132997200-2ea3267f-17f4-4537-a1c8-080ca00cd363.png)
![lab 5 supply variation simulation](https://user-images.githubusercontent.com/90343497/132997204-58f29c12-90fc-462f-a0e2-fdd410194d7d.png)
![lab 5 supply variation spice output](https://user-images.githubusercontent.com/90343497/132997208-9de9e667-72be-445d-a4ca-b40dac474b7a.png)
![lab 5 device variation spice file](https://user-images.githubusercontent.com/90343497/132997212-50bd1649-e17d-429e-ac1b-61437907af65.png)
![lab 5 device variation spice simulation](https://user-images.githubusercontent.com/90343497/132997218-735d036f-ae66-4940-8305-8db2abf383ef.png)
![lab 5 device output](https://user-images.githubusercontent.com/90343497/132997230-26cbb07f-042b-4953-acbc-390ab1bb5212.png)
