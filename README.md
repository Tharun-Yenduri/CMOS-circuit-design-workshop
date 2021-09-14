# **CMOS Ciruit Design and Spice Simulation using Sky130 Technology**
![image](https://user-images.githubusercontent.com/90343497/132997260-aeda2b04-fa37-4ebd-b032-93007941783f.png)
## Introduction of the workshop:
This workshop is about CMOS Ciruit Design and Spice Simulation using sky130 Technology.This course content is divided for five days having both theory description and labs of Circuit design and Spice simulation.On the first day of workshop the topics covered are Introduction to spice simulation,Nmos resistive and saturation region of operation,introduction to spice.The second day of workshop is about Spice simulation for lower nodes and velocity saturation effect,CMOS voltage transfer characteristics.The third day of workshop is about CMOS voltage transfer characteristics-Spice simulations,Static behaviour-CMOS inverter robustness-Switch threshold voltage.The fourth day of workshop is about CMOS Noise Margin Robustness Evaluation.The fifth day of workshop is about CMOS power supply and device variation robustness evalation.  
## Introdution to Sky130: 
Sky130 is a foundry which is used to built a chip using 130nm technology by providing pdk's(Process Development Kit)
## Day1:
### What is circuit design and why do we need spice?
* Circuit design is basically a way of achieving the required functionality by connecting PMOS and NMOS in certain manner.

 Fig1 illustrates Basic circuit design:

![20210914_014951](https://user-images.githubusercontent.com/90343497/133152317-243e8e80-8464-469b-a2e1-fce553d655c7.jpg)

* Spice will tune the delay of cell by Widht(W) and Length(L) of cell and spice simulation will give the output waveform of CMOS circuits,readymade delay table of sample circuit which will give the delay of circuit by using input slew and output load.

 Fig 2 shows the readymade delay table:

![fig2](https://user-images.githubusercontent.com/90343497/132997730-a0370e4e-3cd0-4cb6-9d15-5c3c702e0149.png)

### Introduction NMOS in ciruit design:

**N type Metal Oxide Semiconductor(NMOS):**
- It is a four terminal device,Isolation region(SiO2) will differentiate the two transistors.

 Fig 3 depicts the cross sectional view of NMOS:

![20210914_015013](https://user-images.githubusercontent.com/90343497/133152380-24a75c8d-0378-4ef6-ab43-3e3cfce09b88.jpg)

- It is a 4 terminal device and the terminals are:
  1. Source(S)
  2. Gate(G)
  3. Drain(D)
  4. Body/substrate/bulk(B)
- Isolation region
- P-Substrate
-  Gate Oxide
- Metal gate
- n+ Diffusion region

### There are three modes of operation:
1. Cutoff region (Vgs<vth)
2. Resistive or Linear Region (Vgs>vth) & (vds<vth)
3. Saturation Region (Vgs>Vth) & (Vds>Vth)

### 1.Cut-off Region:
- Initially when Vgs is  zero there will be no transfer of electrons between source and drain,so resistance of Sd is high.This region is called Cutoff Region.

### Strong Inversion and threshold voltage:
- By applying certain potential there will be formation of depletion region and depletion widht will increase by increasing the potential at Vgs,at some point the part of p-type substrate i.e between source and drain will be converted to n-type material,so electrons will be accumulated between source and drain, this phenomenon is called strong inversion 
- Threshold voltage(Vt):The voltage(Vgs) at which strong inversion occurs is called threshold voltageor It is minimum voltage required for the movement of electrons from source to drain.Spice model will give the threshold voltage of NMOS.

 Fig 4 shows strong inversion:

![fig4(Threshold volatage)](https://user-images.githubusercontent.com/90343497/133072908-56f27654-e1a0-4a89-aef3-854401bf4510.png)

-Body terminal is used to tune the threshold voltage, by applying voltage at Vsb there will be additonal reverse bias which increases the depletion layer width between source and p-substrate will increase as source will accumulate electrons from p-substrate so additional potential is required for strong inversion.

 Fig 5 depicts the body effect in the presence of Vsb:

![fig5(tune Vth using body)_LI](https://user-images.githubusercontent.com/90343497/133082790-dfa7af78-4970-4688-84a1-04410de8b933.jpg)

In the above figure:
1. Additional reverse bias voltage at source and bulk
2. Increase in depletion width due to additional reverse bias voltage

Fig 6 shows derivation of formula for Threshold Voltage:

![WhatsApp Image 2021-09-14 at 2 35 05 AM](https://user-images.githubusercontent.com/90343497/133156418-a861c567-8caa-45a3-8d56-d6e2a72c0d5d.jpeg)

### 2.Resistive Region:
- By increasing the potential beyond the threshold voltage, accumulation of electrons will be more between source and drain and this will leads to increase the channel width and there will be flow of electrons between source and drain.
- Vgs-Vth is the condition where the transistor will be on.
- When there is no potential given at Vds the voltage will be same across the whole channel
-When Vds is given to the transistor the voltage will be vary across the channel as the voltage at source is zero and voltage at drain is Vds,so the voltage acroos the channel is vary from 0 to Vds. 
- In the channel induced charge is directly proportional to Vgs-Vth
  - **Qi(x)∝ -(Vgs-Vt)** 
- Let's take L be effective channel length and consider length of the channel on x-axis and width of the channel on y-axis
- V(x) is voltage at point 'x' along channel
- So **Vgs-V(x)** is effective gate to channel voltage at that point.
- Induced charge at point at 'x' is Q(x) is directly proportional to ([Vgs-V(x)]-Vth)
  - Qi(x)∝ -([Vgs-V(x)]-Vt)
  - Qi(x) = -Cox ([Vgs-V(x)]-Vt)
  - Cox = oxide capacitance
  - Cox = ∈ox/tox
  - ∈ox = Oxide permitivity
        = 3.97x∈o(relative permitivity)
        = 3.5x10e-11 F/m
   - tox = oxide thickness
- There are two types of current from device point of view:
1. drift current-current due to potential difference for example due to potential at vds there is voltage of channel difference at source(0) and drain(Vds)
2. diffusion current- current due to difference in charge carrier concentration
- As there is potential difference in channel i.e 0 to Vds there will be drift current
- **Id = velocity of charge carriers x available charge over channel width**

 Fig 7 and 8 shows the derivation drain current formula:

![20210914_004829](https://user-images.githubusercontent.com/90343497/133157864-aca747b4-7441-4a1f-bfbd-7be87c8cfc25.jpg)
![20210914_005011](https://user-images.githubusercontent.com/90343497/133157894-a4d2e0e4-4c5b-44ab-8dc4-263f867ed153.jpg)

### 3.Saturation Region:
- Channel voltage = Vgs-Vds

 Fig 9 depicts the relative between channel voltage and threshold voltage on increasing the Vds gradually:

![Screenshot (4)](https://user-images.githubusercontent.com/90343497/133107474-df6cd46d-12d8-43a7-a2ba-cc7e26c573ac.png)

- When we increase the potential of Vds gradually from the above table we get three conditions:
  1. Vgs-Vds>Vth 
  2. Vgs-Vds=Vth
  3. Vgs-Vds<Vth
- When Vgs-Vds = Vt so at that point x,the strong inversion is about to happen.  
- When there is no channel formed near the drain region then region is called the pinch-off region and the condition is Vgs-Vds<=Vt

 Fig 10 illustrates the pinch-off region
 
 ![20210914_005213](https://user-images.githubusercontent.com/90343497/133158956-a44dfa6f-0f9b-4d64-a1e6-e683d8f1aeb0.jpg)

- In saturation region for Id equation we will replace the Vds with Vgs-Vt in the Id equation of resistive region
- So the Id equation is
  - Id = Kn/2[(Vgs-Vt)^2(1+λVds)]

 Fig 11 shows about the channel length modulation:
 
![fig10](https://user-images.githubusercontent.com/90343497/133110995-897e5a33-eee6-4f05-95c9-151cb93e23bd.png)

## Introduction to spice:
- Spice is used to get the characteristics of nmos and pmos as welll as delay of transistor and also to sweep the voltages. 
- Value of model parameters are unique for different respective technologies.
- In Model file, all the model parameters are availble provided by foundry.
- Nodes are point which connect the two terminals.
- The first step is to find the nodes of circuit and define the netlist.
- Spice simulations are used to calculate the Id at different Vgs values. It is used to sweep the voltages.

 Fig 12 shows about the steps of spice simulation:

![Capture2](https://user-images.githubusercontent.com/90343497/133159720-9dbba673-09a4-4e3b-82f2-5daf23e5f2b7.PNG)

 Fig 13 depicts the model and model parameters:

![fig11](https://user-images.githubusercontent.com/90343497/133114344-e227babf-dab4-4adb-b896-d09838f3916e.png)

In the above fig 13 the marked values are model parameters 

 Fig 14 shows the nodes of the different components and the netlist description for the circuit:

![fig13](https://user-images.githubusercontent.com/90343497/133114468-da6efa83-4cf2-4593-ad75-c49911597f33.png)

- To run the spice file the command is ngspice filename
- To plot the curve, let say we need Id vs Vds,after running the spice file we need to give plot -vdd#branch
#### Lab actvity-1 :

Below image is spice file of NMOS to get the Id vs Vds curve:

![lab1 spicefile](https://user-images.githubusercontent.com/90343497/132996341-b03e2f86-ef34-4dd1-b6f2-60882db8f150.png)

Below image is spice simulation of NMOS to get the Id vs Vds curve:

![lab1](https://user-images.githubusercontent.com/90343497/132996762-585e5086-f355-46ae-8920-05b1661d90e1.png)

Below image is the output waveform of NMOS Id vs Vds curve:

![lab1-output](https://user-images.githubusercontent.com/90343497/132996820-cf972072-a1a1-4f36-8ecd-4ecc1dc0bfba.png)

- How to check the Id:
  - Left click on the graph where we need to get the value of Id,
  - Some values will be displayed on terminal like x0 and y0,x0 is the value on x-axis and y0 is the value on y-axis,
  - As the above curve is Id vs Vds, y0 is the value of Id in amperes,
  - In spice file, type of corner should be mentioned.
- There are five different type of corners,they are:
  1. tt(typical corner)
  2. sf(slow fast corner)
  3. ff(fast fast corner)
  4. ss(slow slow corner)
  5. fs(fast slow corner)

Below image shows different w and l technologies used in lab

![Screenshot (113)](https://user-images.githubusercontent.com/90343497/132998090-95241ac1-0804-48d8-ae90-a6fe46a00c47.png)

## Day2:
- The Id is a linear function of Vds in linear region
- The Id is dependent on channel length modulation and Vds in saturation region

Fig 15 illustrates the regions of NMOS

![fig 14](https://user-images.githubusercontent.com/90343497/132998124-6371df93-2792-431e-92a0-773bbaebe2e4.png)

- In the above Fig 15 
  - The region before Vds=Vgs-Vt is linear region which is linear function of Vds and 
  - The region after Vds=Vgs-Vt is saturation region which is dependent on channel length modulation and Vds.
- The channel length which is having below 0.25u is referred as short channel
- When we are having the same W/L ratio with different width and Length:
  1.Id is quadratic dependent on Vgs when it is having long channel 
  2.Id is linearly dependent on Vgs at low Vgs and quadratic dependent on Vgs at high Vgs  when it is having short channel

Fig 16 shows the behaviour of NMOS when it is having long channel and short channel

![fig 15](https://user-images.githubusercontent.com/90343497/133208793-5c308208-a4bf-409b-8272-07511dcc99af.png)

- To observe this situation we are using the same W/L ratio with different width and Length where we are calcualting the Id at constant Vds, the Id is increasing quadratic which is having long channel where as the Id is  quadratic function of Vgs at low gate voltage and linear function of Vgs at high gate voltage which is having short channel and this is occuring due to velocity saturation effect

#### There are four regions of operation for short channel:
1. Cut-off region
2. Linear or Resistive region
3. Saturation region
4. Velocity Saturation

- Velocity Saturation effect:
  - Velocity saturation effect says for the lower values of electric field, the velocity of electric field is increases linear with electric field but after critical electric field the velocity of electric field become saturate.

 Fig 17 is the graph between electric charge and its velocity

![Screenshot (140)](https://user-images.githubusercontent.com/90343497/133118185-35b0d014-1c5c-4936-8406-1a9714558362.png)

- As we know formula Velocity = mobility.electric field
  - **Vn(m/s)=μn.∈/(1+(∈/∈c)) for ∈ <= ∈c**
  - **Vsat                     for ∈ >= ∈c**
  - Here we equate the above two conditions and we get the critical electic field,For contunity, put ∈ = ∈c
  - **2Vsat = μn.∈c** 
      - **∈c = (2Vsat/μn)** 
   - when rederiving the drain current using above condition
   - Id=-Vn(x).Qi(x).W
   - **Id = (μn.Cox/1+(Vds/∈c.L)).(W/L).[(Vgs-Vt)Vds-Vds^2/2]** which is too complex while using for calculations.
   - For the cutoff region Id=0 as Vgt<0
   - For the remaining regions,to get the equation of Id submit the vmin and we will get the Id equations for different regions.
   - Let **Id = kn[(Vgt.Vmin)-Vmin^2/2].[1+λVds]** 
     - where Vgt= Vgs-Vt
     - where Vmin=min(Vgt,Vds,Vdsat)
     - Vdsat is one of the model parameter
    - When Vmin is Vdsat the drain current equation in Velocity Saturation region:
      - **Id = kn.[(Vgt.Vdsat)-Vdsat^2/2].[1+λVds]**  
 
 - When Vmin is Vgt we will get the equation for drain current of saturation region as we know Vds>Vgt,
 - When Vmin is Vds we will get the equation for drain current of linear region as it will be linear function of Vds,
 - When Vmin is Vdsat we will get the equation for drain current of Velocity Satuarion region.
- The observation is peak current is low for short channel compared to peak current for long channel.

#### lab2 activity:

Below image is spice file of Id vs Vds curve for the short channel of NMOS

![lab2 vds spice](https://user-images.githubusercontent.com/90343497/132996856-3222012d-4750-4845-8eaa-500db5442cbe.png)

Below image is spice simulation of Id vs Vds for the short channel of NMOS

![lab2 vds spice simulation](https://user-images.githubusercontent.com/90343497/132996861-89a48dbf-b89c-4d65-b2d7-3324b3ac0d22.png)

Below image is output waveform of Id vs Vds curve for short channel of NMOS

![lab2 vds output](https://user-images.githubusercontent.com/90343497/132996871-f5a8f4ed-ffa4-4391-91ff-812866b2c8f8.png)

Below image is spice file of Id vs Vgs where Voltage(Vds) is sweep from 0 to 2.5

![lab2 vgs spice](https://user-images.githubusercontent.com/90343497/132996903-5427e994-5f8e-4072-8e82-dcacfdd18cb2.png)

Below image is simulation of Id vs Vgs curve 

![lab2 vgs simulation](https://user-images.githubusercontent.com/90343497/132996906-91e08918-5bff-42aa-aab5-767ff04a8a31.png)

Below image is output waveform of Id vs Vgs

![lab2 vgs output](https://user-images.githubusercontent.com/90343497/132996910-ccbf68fc-07d9-4d35-a7a4-e5b640c58fee.png)

### CMOS voltage Transfer characcteristics:
- When Vgs is given to CMOS one of the mosfet will be off and other mosfet will be on so this is called Complementary Mosfet.
- MOSFET as switch:
  - With infinite OFF resistance when |Vgs|<|Vth|
  - With finite ON resistance when |Vgs|>|Vth|

Fig 18 shows the behavior of PMOS and NMOS when Vin is changing

![20210914_015850](https://user-images.githubusercontent.com/90343497/133215276-24f79cec-8a3f-46c8-948d-f4777ac1fdf7.jpg)

 Fig 19 illustrates the direction of current path
 - Idsp Drain to source current through PMOS and it will charge the output load Capacitor
 - Idsn Drain to source current throught NMOS and this will discharge the output load Capacitor
 - Idsp=-Idsn
 - Idsp+Idsn=0

![CMOS](https://user-images.githubusercontent.com/90343497/133161606-8cdde982-96af-4748-9c74-9c4ae0c9db17.png)

 Fig 20 is the observations made from the CMOS inverter and load curve of NMOS 
 
![20210914_005636](https://user-images.githubusercontent.com/90343497/133161815-5911eba9-107d-4ee8-ba7c-9127a411156f.jpg)

 Fig 21 depicts changing the PMOS curve in terms of Vin
 
![20210914_005735](https://user-images.githubusercontent.com/90343497/133161827-e47e0360-5d6d-4a20-92c0-0b99d5bba8d8.jpg)

- To change the PMOS curve in terms of Vin and Vout , few observation to made:
 Vgsp | V | Vin=Vgsp+Vdd
 -----|---|-------------
 Vgsp1|   0  |     2      |
 Vgsp1| -0.5 |    1.5     |
 Vgsp1|  -1  |     1      |
 Vgsp1| -1.5 |    0.5     |
 Vgsp1|  -2  |     0      |

- As Vout = Vdd + Vdsp
Load curve of PMOS transistor

 Fig 22 shows that when Vin and Vout of PMOS and NMOS are taken in one graph they are intersecting at some voltages and those intersection points to be plotted on Vin vs Vout which will give the Voltage Transfer Characteristics of CMOS

![20210914_005949](https://user-images.githubusercontent.com/90343497/133161916-cba740fc-0c6b-408d-b7ee-d71956dc98d9.jpg)

Day3:
#### lab3 activity:
- To plot the voltage Transfer Characteristics of CMOS inverter, while simulating the spice file of Voltage transfer characteristics use the below command
  - plot out vs in
 
Below image is spice file of voltage transfer characteristics of CMOS
 
![lab3 spice file vtc](https://user-images.githubusercontent.com/90343497/132996978-0aa7ceb3-6bb7-427f-a645-e3bb7c8a5ef5.png)

Below image is spice simulation of voltage transfer characteristics of CMOS

![lab 3 simulation vtc](https://user-images.githubusercontent.com/90343497/132996987-16a6d318-de5f-48b8-8b22-85044ad295d9.png)

 Below image waveform of voltage transfer characteristics of CMOS
 
![lab 3 vtc output](https://user-images.githubusercontent.com/90343497/132997004-5f73393d-137b-4e19-b4c1-1191773fe998.png)

- To plot the transient analysis of CMOS inverter along with the input curve, while simulating the spice file of Transient analysis use the below command:
  - plot out vs time in
- To get the pulse waveform:In below spice file of transient analysis of CMOS,in the netlist description rise time,fall time,starting,
  - ex:Vin in 0 PULSE(0 1.8 0 0.1ns 0.1ns 2ns 4ns)
    - first value inside pulse is minimum voltage level
    - second value inside pulse is
    - third value inside pulse is initial delay
    - fourth value inside pulse is rise time 
    - fifth value inside pulse is fall time 
    - sixth value inside pulse is pulse width
    - seventh value inside pulse is time period
 
 Below image is spice file of transient analysis of CMOS
 
![lab3 tran spice file](https://user-images.githubusercontent.com/90343497/132997019-a840dca0-2c6a-483e-b81e-969984bec8a0.png)

 Below image is spice simulation of transient analysis of CMOS

![lab 3 tran spice simulation](https://user-images.githubusercontent.com/90343497/132997033-415ba4dc-6bc7-4e75-9f76-618ce5cc132e.png)

 Below image is output waveform of transient analysis of CMOS which give rise time delay and fall time delay
 
![lab 3 tran output](https://user-images.githubusercontent.com/90343497/132997046-769ca728-1b6c-40c2-8f43-5c1ba8669901.png)

- To calculate the rise time delay and fall time delay we will do the transient analysis of CMOS
- How to calculate the output rise time delay and fall time delay of an inverter:
  - output rise time delay = rise time of output - fall time of input at 50% of Vout
  - output fall time delay = fall time of output - rise time of input at 50% of Vout

#### The characteristics that define the CMOS inverter robustness are:
1. Switching threshold voltage
2. Noise Margin
3. Power supply variation
4. Device variations

#### Switching threshold voltage of CMOS inverter(Vm):
- Switching threshold voltage is one of the parameter that define the CMOS inverter robustness
- For getting the Switccing threshold voltage of CMOS Vin=Vout ,the point at where the region of pmos and nmos are at saturation region
 Fig 23 illustrates the change in switching of voltage when PMOS width is 2.5 times greater than width of NMOS
 
![Screenshot (144)](https://user-images.githubusercontent.com/90343497/133135001-d7dd76b1-bcc9-404b-a7bb-e26906bba62e.png)

- Here we are making two observations with one CMOS having Wn=Wp=0.36u,Ln=Lp=0.25u i.e same ascept ratio(W/L) for both pmos and nmos and other CMOS having W=0.9u,l=0.25 for pmos and w=0.36,l=0.25 for nmos then the switching of Voltage is less when pmos and nmos having ascept ratio(W/L) where is switching of voltage is more when widht of pmos is two times more than widht of nmos.
- Switching threshold voltage of cmos having same ascept ratio for both pmos and nmos is low compared to cmos having pmos of 2.5 times the width of nmos.
- At switching threshold voltage both pmos and nmos are in saturation region and both the transistors are turn "ON",at this voltage gain is high.
- As Vin = Vout we can get Vgs = Vdd
- The two ways that are to get the below analytical expressions:
- As we know 
- Idsp=-Idsn
- Idsp+Idsn=0
  1.Analytical expression of Vm as a funtion of (W/L)p and (W/L)n
    - let **Id = μn.Cox.(W/L).[(Vgs-Vt)Vdsat-(Vdsat^2/2)]**
    - Id in terms of Idsn and Idsp
    - **Idsn = kn.[(Vm-Vt)Vdsatn-(Vdsatn^2/2)]**
    - **Idsp = kp.[(Vm-Vdd-Vt)Vdsatp-(Vdsatp^2/2)]**
    - Equating and solving the Idsn and Idsp as per Idsp+Idsn=0
    - **kp.[([Vm-Vdd-Vt].Vdsatp)-Vdsatp^2/2]+kn.[([Vm-Vt].Vdsatn)-Vdsatn^2/2]=0**
    - Solving the above form Vm
    - **Vm=R.Vdd/(1+R)**
        -  where R=(kp.Vdsatp)/(kn.Vdsatn) 
  2.Analytical expression of (W/L)p and (W/L)n as a funtion of Vm
    - As Idsp=-Idsn
    - kn.[(Vm-Vt)Vdsatn-(Vdsatn^2/2)] = -kp.[(Vm-Vdd-Vt)Vdsatp-(Vdsatp^2/2)]
    - **(kp.Vdsatp)/(kn.Vdsatn) =[(Vm-Vt)-(Vdsatn/2)]/[(-Vm+Vdd+Vt)-(Vdsatp/2)]**

- Here few observations from the below table to check the behavior of Vm when width of PMOS is increasing.

 Wp/Lp | x.Wn/Ln | Rise delay | Fall time |   Vm   |
 ------|---------|------------|-----------|--------|
 Wp/Lp | 1.Wn/Ln |    148ps   |   71ps    |  0.99V |
 Wp/Lp | 2.Wn/Ln |    80ps    |   86ps    |  1.2V  |
 Wp/Lp | 3.Wn/Ln |    57ps    |   80ps    |  1.25V |
 Wp/Lp | 4.Wn/Ln |    45ps    |   84ps    |  1.35V |
 Wp/Lp | 5.Wn/Ln |    37ps    |   88ps    |  1.4V  |

- Observations:
  1. When pmos width is 2 times the width of nmos the rise time delay and fall time delay is almost equal which is characterstics of clock inverter/buffer
  2. The remaining observations can be used for data path where data arrival time is less than data required time.
  3. When pmos width is 4.7 times the nmos then the vm is lies between pmos of widht 4 times the nmos widht and pmos of width 5 times the nmos width
  4. On increasing the widht of pmos the rise time delay is decreasing,so more area will be available to charge the capacitor and vm is increasing
### Day4:
- Noise Margin:Any inverter or any gates can have noise margin i.e cros-talks,glitches and those cross talks and glithces can be handled by handling the noise margin

Fig 22 illustrates the ideal I/O characteristics of inverter with Infinite slope and finite slope

![20210914_010425](https://user-images.githubusercontent.com/90343497/133162598-5bac1f25-2b48-4748-86d5-98a6f7be8086.jpg)

Fig 23 depicts the actual I/O characteristics of inverter and the scale from 0 to Vdd to show the noise margin high and noise margin low

![20210914_010521](https://user-images.githubusercontent.com/90343497/133162625-a99cd2ce-c345-46b0-b6b5-080d08dca509.jpg)

- Vil is input voltage which is less than Vdd/2 and it could be nearly Vdd/4
  - Any input voltage lies between 0 and Vil should be considered as logic 0
- Vih is input voltage which is greater than Vdd/2 and it could be nearly 3/4 of Vdd
  - Any input voltage lies between Vih and Vdd should be consider as logic 1
- Vol is output voltage which lies near to 0
  - Any output voltage lies between 0 and Vil should be considered as logic 0 as it may be used as logic 0 for next gate input
- Voh is output voltage which lies near to Vdd
  - Any output voltage lies between Vih and Vdd should be consider as logic 1 as it may be used as logic 1 for next gate input

 Fig 24 shows the Noise Margin summary of bumps
 
![Screenshot (100)](https://user-images.githubusercontent.com/90343497/133162859-10d3dd18-0d01-4c30-b79c-d6470e121335.png)

- From the above image:
  1. If any bump height lies between Vol and Vil can be considered as logic 0
  2. If any bump height lies between Vil and Vih can be considered as undefined logic as bump can go high or low
  3.If any bump height lies between Vih and Voh can be considered as logic 1

 Wp/Lp | x.Wn/Ln |  NMh  | Nml |   Vm   |
 ------|---------|------------|-----------|--------|
 Wp/Lp | 1.Wn/Ln |  0.3  |   71ps    |  0.99V |
 Wp/Lp | 2.Wn/Ln |    0.35    |   86ps    |  1.2V  |
 Wp/Lp | 3.Wn/Ln |    0.4    |   80ps    |  1.25V |
 Wp/Lp | 4.Wn/Ln |    0.42    |   84ps    |  1.35V |
 Wp/Lp | 5.Wn/Ln |    0.42    |   88ps    |  1.4V  |
 
- Based on the observation table:
  1. If the pmos width lies between 1.8 and 2.2 there will be no huge difference in noise margin
  2. On increasing the pmos width the Noise Margin High is increasing  and Noise Margin Low is decreasing
-From the Noise Margin we can conclude the following things:
 1. The area between Voh and Vdd,0 and Vol can be used used as logic 1 and logic 0 for digital design
 2. The undefined region in the curve can be used for amplification for analog design
 
### lab4 actvity:

Below image is the spice file of VtC curve to get the Noise Margin

![lab 4 noise margin spice file](https://user-images.githubusercontent.com/90343497/132997092-e9254618-ff93-4992-b242-f7bf6a4d9574.png)

 Below image is the spice simulation of VtC curve to get the Noise Margin

![lab4 noise margin simulation](https://user-images.githubusercontent.com/90343497/132997099-9256696b-8298-481c-b423-db2865c2bf72.png)

 Below image is the waveform of VtC curve to get the Noise Margin
 
![lab4 noise margin output](https://user-images.githubusercontent.com/90343497/132997110-93580c48-60fc-4219-bd5c-037bff2279a3.png)

- To calculate the noise margin:
  - Left click on the pmos slope then in the terminal two values will be displayed x0 and y0 where x0=Vil and y0=Voh
  - left click on the nmos slope then in the terminal again two values will be displayed x1 and y1 where x1=Vih and y1=Vol
  - To get Noise Margin High(Nmh) subtract y0 and x1 
  - To get Noise Margin low(Nml) subtract x0 and y1
Day5:
- Power supply variation is one of the parameter that define the CMOS inverter Robustness.
- Power supply variations:In this we will check for the different power supplies how is the CMOS inverter is behaving.
- let us sweep the power supply from 2.5V to 0.5V of pmos and nmos having W and L by using the script in under .control in spice file.
- Here we will do two observations:
  1. The gain of curve having 2.5V power supply is nearly 56% lower than the gain of curve having 0.5V power supply
  2. The energy of curve having 2.5V power supply is nearly 96% greater than the gain of curve having 0.5V power supply.
 - Advantages of using 0.5V supply:
   - Increase in Gain(close to 50% improvement)
   - Significant reduction in energy(close to 90% improvement)

### lab5 activity:

- Below image is the spice file for supply variation when voltage is sweeped from 2.5v to 0.5v
 
![lab5 supply variation spice file](https://user-images.githubusercontent.com/90343497/132997200-2ea3267f-17f4-4537-a1c8-080ca00cd363.png)

- Below image is the spice simulation 
 
![lab 5 supply variation simulation](https://user-images.githubusercontent.com/90343497/132997204-58f29c12-90fc-462f-a0e2-fdd410194d7d.png)

- Below image is waveform of different supplies

![lab 5 supply variation spice output](https://user-images.githubusercontent.com/90343497/132997208-9de9e667-72be-445d-a4ca-b40dac474b7a.png)

- To calculate the gain:
  1. Left click on the slope of pmos there will be two values displayed in terminal x0 and y0
  2. Left click on the slope of nmos there will be two values displayed in terminal x1 and y1
  3. Gain is equal to ratio of change in output and change in input i.e y0-y1/x0-x1
- Conclusion from lab:
  1. As power supply voltage decreases the gain is increasing but when the power supply is 1V then the gain cannot be increased as 1V is not sufficient to turn on the pmos and nmos transistor 
### Device variation:
- Device Variation is also one of the variation that defines the CMOS inverter robustness
  1. Etching variation
  2. Oxide thickness variation
 - Etching variation:
   - Etching is one of the fabrication step 
   - It will define the structures in layout of CMOS
   - It will define the structure i.e Width and length
- Let's take the layout of CMOS and we have:
  - P-diffusion region,
  - Poly-silicon area, 
  - Metal layer, 
  - N-diffusion region,
  - Contacts between two layers
- Thickness of poly-silicon layer is the gate length annd it defines at which node we are using like 20nm, 30nm, 45nm, etc..
- Thickness of the P-diffusion layer is the width of the gate of the PMOS and the thickness of the N-diffusion layer is the width of the gate of the NMOS
- While fabricating the mosfet there will be difference in ideal widht,length and actual width and length 
- As we know Id is dependent on W and L,so there will be impact on Id due to etching variation

- Below image shows the difference in ideal and actual etching of CMOS
 
![Screenshot (124)](https://user-images.githubusercontent.com/90343497/133146877-be59e294-d8ef-486b-b494-3b84342d33a9.png)

- Inverter chain:
  - When Inverters are connected side by side in a chain then they are known as Inverter chain as shown in above figure.
  - The inverters that are at head and tail ends are having different structures compared to middle inverters as they may connected to other gates or flipflops,so the distortion of width and length are more at head and tail ends.
- As the middle inverters are sorrounded by first and last inverters they may have same width and length and distortion is less.

- Below image shows the inverter chain and its layout

![Screenshot (123)](https://user-images.githubusercontent.com/90343497/133271938-c6de2d47-0b00-42f0-815c-dab04b4f89ea.png)

- Oxide thickness(Cox):
  - While fabricating the mosfet there will be difference in ideal oxide thickness of gate and actual oxide thickness of gate
  - As we know Id is dependent on Cox,so there will be impact on Id due to Oxide thickness variation.

- Below image shows the difference of ideal and actual oxide thickness

![Screenshot (148)](https://user-images.githubusercontent.com/90343497/133274456-62d0b3a9-d8af-4a95-9451-285dc01e1820.png)

- These two are minimal variations that define the CMOS inverter robustness.
- Lets sweep the width of pmos and nmos as below

![Screenshot (149)](https://user-images.githubusercontent.com/90343497/133274611-7107b0d2-d357-46f3-832f-25a6d52963ba.png)

- Strong Pmos:
  - It is least resistance PMOS i.e it has less resistance path to charge output capacitor
  - It is wider in size
- Weak NMOS:
  - It is high resistance NMOS as area is inversely proportional to resistance
  - It is lower in size 
- Weak PMOS:
  - It is high resistance PMOS 
  - It is lower in size
- Strong NMOS:
  - It is low resistance NMOS
  - It is higher in size
 
 - Below image is spice file where width of PMOS and width of NMOS are sweeped
 
![lab 5 device variation spice file](https://user-images.githubusercontent.com/90343497/132997212-50bd1649-e17d-429e-ac1b-61437907af65.png)

- Below image is spice simulation for device variation
 
![lab 5 device variation spice simulation](https://user-images.githubusercontent.com/90343497/132997218-735d036f-ae66-4940-8305-8db2abf383ef.png)

- Below image is output waveform of device variation

![lab 5 device output](https://user-images.githubusercontent.com/90343497/132997230-26cbb07f-042b-4953-acbc-390ab1bb5212.png)

- Conclusion from lab:
  - As PMOS width is higher than the NMOS,the output of PMOS is staying for long time when compared to NMOS curve.

### Conclusion:

