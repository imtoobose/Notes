# CG: Chapter 1
#cg

## Cathode Ray Tubes
### Working:
- Beam of electrons emitted by electron gun passes through diverting and focusing systems and hits a phosphor coated screen
- The light from the phosphor fades quickly and a redraw is required. This type of CRT is called a  **refresh CRT**

### Primary Components:
- 	**Heated metal cathode**
	- Heat is supplied to the cathode through a coil of wire called the filament inside the cathode 
	- Electrons get “boiled off” the cathode
	- Electrons are accelerated with an accelerating anode
		
- **Control grid**
	- Control grid is a metal cylinder  that fits over the cathode
	- High negative voltage - Reduces number of electrons by stopping them from passing through the small hole in the grid
	- Amount of light is _directly proportional_ to number of electrons. So **control grid controls the brightness.**
		
- **Focusing system** 		
	- Forces electron beam to converge on a singular spot in the centre instead of spreading due to repulsion
	- Achieved through electrostatic or magnetic fields
	- Electron beam passes through a positively charged metal cylinder that forms electrostatic lens
	- Magnetic focusing is more precise

- **Deflection system**
	- Magnetic and electrostatic plates are used to deflect horizontally or vertically. 
	- Two pairs are required, one for horizontal deflection, one for vertical

### Display Mechanism

- Electrons hit the phosphor screen, their kinetic energy is absorbed
	- The energy is lost in some amount through friction and converted to heat
- Phosphor atoms go into a higher quantum state then back, causing a small amount of light energy to be released
- Frequency of light emitted is proportional to energy difference of ground and excited quantum state

### Properties of CRT

#### Phosphor 
- Phosphor can be classified by **color** and **persistence**
	- Persistence is defined as the time it takes the emitted light from the screen to decay to one-tenth of its original intensity
	- Low persistence: good for animation, requires high refresh rate
	- High persistence: good for static pictures

#### Resolution
- _The maximum number of points that can be displayed without overlap on a CRTis referred to as the resolution_
- Two adjacent spots will appear distinct as long as their separation is greater than the diameter at which each spot has an intensity of about 60 percent of that at the center of the spot.
- Spot size also changes with intensity
	- Greater intensity -> Spreads brightness to neighboring phosphor

**Thus resolution depends on:**
- Type of phosphor, 
- Intensity to be displayed,
- focusing and deflection systems	

#### Aspect Ratio
- The ratio of vertical points to horizontal points necessary to produce equal-length lines in both directions on the screen **OR**
- The ratio of horizontal to vertical for the same

## Raster Scan Display
- Electron beam is swept across the screen top to bottom, left to right
- **Refresh buffer / Frame buffer**: memory area that holds set of intensity values for all screen points.
- 
 








		
