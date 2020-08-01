# Project PWM peak and hold injector driver
The peak and hold project started because I could not find an open-source PWM peak and hold injector driver for low-Z injectors. For low-z injectors normally series resistors are used. But resistors create a lot of heat and are not very adjustable. But i do encourage everyone to use resistors if possible because the results are great and resistors can not break<br/>
<br/>
This design is specific to work with LPG injectors but could be used for any other low-Z injectors like TBI type and other high flow injectors. It could even be used for any coil type actuator like relays or valves <br/>

The design is Kicad. So to see the schematic or to adjust the deisgn to your liking open the Kicad project.<br/>

Latest release is V0.3.<br/>
 __IMPORANT NOTE: Board V0.3 is not tested yet!! Order on your own risk__ <br/>

__specifications:__
- Max peak current 6A<br/>
- Max continuous hold current 3A<br/>
- Hold PWM duty cycle 5%-60%<br/>
- PWM frequency 20khz<br/>
- 4 Individual injector channels<br/>

## Getting Started
This section explains all we need to do to setup the board

### Get all the parts
1. Order the PCB. For example use https://www.pcbway.com/ Upload the PeakHoldPWMDriver_V0.3.zip located in the gebers folder and order the design.<br/>
2. Get all the parts from you favorite supplier. A BOM list is included in the geber folder<br/>
3. Assemble the PCB, hand soldering is possible.<br/>

### Connect the board
The board is intended to be connected to any ECU that uses a switch to ground for each injector channel. This is the case for most types of ECU. Further down this readme there is a description how to use microcontroller pins to drive the injectors directly. <br/>

__Connector J1__
1. injector channel 1 IN<br/>
2. injector channel 2 IN<br/>
3. injector channel 3 IN<br/>
4. injector channel 4 IN<br/>
5. Power - <br/>
6. Power + (14.8V switched with ignition switch)<br/>

__Connector J2__
1. inj channel 1 +<br/>
2. inj channel 1 -<br/>
3. inj channel 2 +<br/>
4. inj channel 2 -<br/>
5. inj channel 3 +<br/>
6. inj channel 3 -<br/>
7. inj channel 4 +<br/>
8. inj channel 4 -<br/>

Power on the board. Led must be lit when powered.<br/>

### Set the PEAK current
1. Measure __TP1__ and use __RV2__ to set to value needed. 100mv = 1A<br/>
2. Make sure this PEAK current is not too close to the maximum current. If that is the case you run the risk the peak current is never reached and the HOLD current is never set. Max peak current = 10.0[V] / R-inj[Ohm]<br/>

### Set the HOLD current
1. Measure the resistance of the injector(s) per channel (R-inj)[Ohm]. <br/>
2. Find the hold current needed for the injector in the datasheet. Usually about 50% to 25% of the peak current would be enough<br/>
3. Calculate the duty cycle needed using: ((R-inj + 0.20)* HoldCurrent)/2,4<br/>
4. Measure __TP2__ and use __RV1__ to set it to voltage calculated in step 3.<br/>
5. If it is possible in your setup or on a bench, connect __injector channel 1 IN__ to the __Power -__ use a multi-meter in series with your connected injector on channel 1 to measure the current. This must be close the the set current. If this is not correct adjust __RV1__ accordingly <br/>

### Direct microcontroller input
It is possible to use the board directly with an microcontroller. (non inverted inputs) The board inputs are 3.3V and 5V safe.<br/> 

To do this, with a sharp object scratch the bridge between __pin 1__ and __pin 2__ of __JP1__ to __JP4__ on the back of the board. Use a multi-meter to double check the connection is broken.<br/>

<br/>Use a soldering iron and a bit of solder to connect __pin 3__ and __pin 2__ for __JP1__ to __JP4__.<br/> 
       

## Simulation	
An LTspice simulation of PWM peak and hold drivers is also in the LTspice folder. It is a good learning experience to see the wave forms and the current thru the coil. This also shows the maximum voltage level expected on the mosfets. This can be significant voltage levels depdending on the clamping voltage of the main driver. <br/>


## License
This project is licensed under the GNU GENERAL PUBLIC LICENSE - see the [LICENSE.md](LICENSE.md) file for details<br/>

