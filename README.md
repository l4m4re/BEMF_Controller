# BEMF Controller

The Back EMF Controller is an experimental evolution of the successful [EasyController3](https://github.com/pgrady3/EasyController3). 

This version incorporates an asymmetric bridge topology, which allows for capturing and reusing the energy from the motor's back EMF, which is normally wasted because of the use of freewheeling diodes.

This allows for a more efficient controller, and potentially a longer range for battery-powered applications, as explained on [Wikipedia](https://en.wikipedia.org/wiki/Switched_reluctance_motor#Power_circuitry):

<div style="text-align: center;">
![Asymmetric Bridge](/docs/Asymmetric_Bridge_Converter.png)
</div>


> The phases in an asymmetric bridge converter correspond to the motor phases. If both of the power switches on either side of the phase are turned on, then that corresponding phase is actuated. Once the current has risen above the set value, the switch turns off. The energy now stored within the winding maintains the current in the same direction, the so-called back EMF (BEMF). This BEMF is fed back through the diodes to the capacitor for re-use, thus improving efficiency.

In addition to this, the capacitor that is used to store the energy from the back EMF, is implemented in a bank of 4 capacitors, which are switched between series (BEMF capture) and parallel (coil energizing) by means of a couple of diodes:

<div style="text-align: center;">
![Capacitor Bank](/docs/4CapBank.png)
</div>


[Spice simulations](http://tuks.nl/wiki/index.php/Main/BEMFRecoveryCircuit) have shown that this way the time needed to collapse the magnetic field in the motor is significantly reduced, which might help to further improve the efficiency of the controller:

<div style="text-align: center;">
![Spice simulation of 4 capacitor bank](/docs/BEMF_Capture_4_Caps_Simulation.png)
</div>

At this moment, all of this is still a work in progress, and the controller is still in the design phase. 

## Schematic

At this moment, the schematic is being developed using KiCad, and can be found in the `kicad` folder. The schematic is still a work in progress, but the current version can be found [here](/kicad/BEMF_controller.pdf).

