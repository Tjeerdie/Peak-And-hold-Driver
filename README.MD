# Project PWM peak and hold injector driver
Project peak and hold became in excistance because I could not find a open source PWM peak and hold injector driver for low-Z injectors. This one is specifically tailored for LPG injectors but could be used for any other low-Z injectors like throttle body injectors and other high flow injectors. 

## Simulation	
A LTspice simulation of PWM peak and hold drivers is also in the LTspice folder. It is interresting to see the wave forms used and the current thru the coil. This also shows the maximum voltage level expected on the mosfets. This can be significant voltage levels depdending on the clamping voltage.  

## Photos
Check out the PeakHoldPWMDriver_V0.1\photos folder to see the real thing! 

## Getting Started
Well there is no getting started because this board is not fully tested and debugged yet. Current status of design still some mistake in V0.1 so after confirming it works as designed with some preliminary chances and wiring version V0.2 should work as expected. When it is ready a getting started will be introduced. 

## License
This project is licensed under the GNU GENERAL PUBLIC LICENSE - see the [LICENSE.md](LICENSE.md) file for details