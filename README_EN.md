# dm7617
[leer en español](https://github.com/teaecetyrannis/pd-dm7617/blob/main/README.md)
<br><br>
fm synth inspired by YM2612 chip, developed in [pure data](https://github.com/pure-data/pure-data)


## installation
download dm7617.zip file from the [last release](https://github.com/teaecetyrannis/pd-dm7617/releases), extract and add the containing folder to pure data path, then it can be started in any patch by creating the `[dm7617~]` object
<br><br>it also depends on the [adsr](https://github.com/teaecetyrannis/pd-adsr) abstraction and the `[selector~]` object from the [cyclone](https://github.com/porres/pd-cyclone) library, so these should necessarily be installed as well


## operation
the synth features:

 1. four operators, each with controls for:
	 - gain (*0-100%*)
	 - attack (*ms*), decay (*ms*), sustain (*0-100%*) and release (*ms*)
	 - fundamental frequency multiplier
	 - fine tuning (*cents*)
	 - amount of lfo that is routed to it (*0-100%*)

	also operator 1 is able to "self-modulate" with an identical copy of itself (op1_self), which has its own gain and lfo controls
	
 2. an lfo with controls for gain and frequency (*hz*)
 3. eight algorithms identical to those of the YM2612
 4. controls for switching between monophonic and polyphonic, **legato**, voice-**stealing** and behaviour of pitch **bend** (*global* applies bending to all active voices of the polyphony and *last* applies it only to the newest voice)
 
WARNING:
- in monophonic mode **bend** should be set to *global*, otherwise pitch bend may have no effect
- in polyphonic mode **legato** should be turned off, otherwise some voices may not sound at all


## documentation, dynamically setting parameters and saving the state of the synth
in the `[pd help]` subpatch inside granola~.pd you will find all this same information and also details on its inlets and outlets and how to set all the parameters from outside via messages, allowing a completely dynamic control of the synth without using the interface
<br>thanks to this it's also possible to fully remember the state of the synthesizer: it only needs a very long message that includes all the current values for each parameter... luckily this function is already built-in and all there is to do is connecting a message (doesn't have to be empty since its content will be replaced) to the third outlet and then send a `[state(` message to the second inlet, this will write all parameters and file paths to the message


## credits
[pure data](https://github.com/pure-data/pure-data) by miller puckette y many others
