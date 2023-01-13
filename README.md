# UE-DEP
This is the official GitHub repository for the UE-DEP project, where all the code and schematics of the will be tracked and hosted.
This is the capstone project for my bachelor's degree in electrical engineering. 

# Project goals
- Design and implement a real-time audio DSP hardware unit in a "guitar pedal" form factor
  - Provide a practical "black box" to allow a musician to use audio plugins as effect pedals in live settings 
  - Must at least be able to take input from one guitar and output to an amplifier or guitar pedal. 
  - Must have external controls to allow effects to be modulated by a performer
  - Must have a bypass control
- Foster a software ecosystem that respects the user's freedom to compute as they wish
  - Utilize *free* and *open source* software as much as possible
  - Create a platform that facilitates the development of original audio processing software 
  - Must be, "out of the box", capable of running a large subset of audio plugins
  - Must also be capable of extension by the user to use original algorithms or extraneous programs to add functionality to their device 
  - Towards this end, all my schematics and necessary code will be licensed under an appropriate FOSS license 

# Definitions and Acronyms
Most of these are generic DSP terms, but they have been repeated here for convenience and to comment on how they will be applied to this project.
- UE-DEP 
  - **U**ser **E**xtensible-**D**igital **E**ffects **P**edal.
  - Tentatively pronounced "yoo dehp"
  - Name of this project and its Git repo.
<!-- Grammatically, it should be User**-**Extensible Digital Effects Pedal, or U-EDEP, but then we would lose the pronunciation suggested by the UE-DEP acronym. -->
- DSP
  - digital signal processing
  - In this project, the DSP will mostly be audio signal processing where the signal is assumed to have negligible bandwidth below 20Hz and above 20kHz.
<!-- For now, I am assuming that the main input type is electric guitar or *any signal derived from it.* 
For example, a guitar playing its lowest note followed by a heavy distortion pedal may very well have non-negligible signal energy around 8kHz, far higher than the fundamental.
Such a use case is very practical and likely. For example, a user might choose to replace a speaker cabinet for an
impulse response plugin for recording, because it's so much easier to set up compared to micing up a cabinet. -->
- Discrete time
  - Used to describe a signal that is only defined for integer time values or at times t = nT, where T is a fixed sample rate and n is any integer.
- Digital
  - Used to describe a signal that is Discrete in both time and *allowed values.* The latter is typically expressed by saying the signal is "quantized".
  - All audio signals are represented on computers as digital signals where the allowed values are quantized to be one of 2<sup>N</sup> values, where N is the bit depth (usually 16, 24, or 32).
  - A control history of the on-off state of a push-button switch is represented as a digital signal where the allowed values are 1 or 0; or, the signal can be one of 2<sup>1</sup> = 2 values, which can be represented with 1 bit. 
- RPi
  - Raspberry Pi
  - Although in my project I will be using the Raspberry Pi 4, the hardware schematics should work for any Raspberry Pi with i2S capability and possibly control pin remappings. 
- OS
  - Operating system 
- Real-time
  - [Firm real-time](https://en.wikipedia.org/wiki/Real-time_computing#Criteria_for_real-time_computing)
<!-- I think a general Linux (like RPi OS) isn't capable of hard real time. One needs a RTOS like a RT-patched Linux or FreeRTOS. The former will be looked into. -->
- FOSS 
  - free and open source software using the [GNU Free Software Definition](https://www.gnu.org/philosophy/free-sw.html.en#fs-definition).
- DAW
  - A digital audio workstation (DAW) is a class of software that allows a user to manipulate digital audio streams, usually using real-time digital effects. 
  - Most DAWs operate based on a multi-track tape "metaphor": several tracks of audio are displayed on the screen as their waveforms, and the contributions of each track, usually one (or more) per instrument, are digitally summed and played to the user.
- Audio plugin
  - A piece of software designed to extend the signal processing functionality of a DAW.
  - Practically, music is produced by processing tracks and MIDI with chains of plugins.
  - To this end, many plugins attempt to emulate the sound of classic analog gear by modeling the circuit in discrete time. 
- Plugin host
  - Any program capable of running at least one format of standard audio plugins
  - For the purpose of this project, an "audio plugin host" will refer to a DAW that is not designed to record input or output to a file. 
