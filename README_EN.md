# dm7617
[leer en español](https://github.com/teaecetyrannis/dm7617/blob/main/README.md)
<br><br>
fm synth inspired by YM2612 chip, developed in [pure data](https://github.com/pure-data/pure-data) and [camomile](https://github.com/pierreguillot/Camomile)

## installation
download dm7617.zip file from the [last release](https://github.com/teaecetyrannis/dm7617/releases/tag/v1.0) and extract on the folder where vst3 plugins are found (to run with pd just run the dm7617.pd patch)

## operation
the synth features:

 1. four operators, each with controls for:
	 - gain (0-100%)
	 - attack (ms), decay (ms), sustain (0-100%) and release (ms)
	 - fundamental frequency multiplier
	 - fine tuning (cents)
	 - amount of lfo that is routed to it (0-100%)

	also operator 1 is able to "self-modulate" with an identical copy of itself (op1_self), which has its own gain and lfo controls
	
 2. an lfo with controls for gain and frequency (hz)
 3. eight algorithms identical to those of the YM2612
 4. controls for switching between monophonic and polyphonic, legato, voice-stealing and behaviour of pitch bend (*global* applies bending to all active voices of the polyphony and *last* applies it only to the newest voice)
 
	 WARNING: in monophonic mode *bend* should be set to *global* and in polyphonic mode *legato* should be turned off, otherwise some unexpected behaviors may arise (known bugs that i don't know how to fix yet)

## credits
- [pure data](https://github.com/pure-data/pure-data) by miller puckette y many others
- [camomile](https://github.com/pierreguillot/Camomile) by pierre guillot
