# Arduino-Based Busch 2090 Microtronic Emulators 
## Arduino-based Emulators of the Vintage Busch 2090 Microtronic Computer System from 1981 
#### Authors: 
- [Michael Wessel](http://www.michael-wessel.info/): Original Emulators & Next Generation Emulator 
- Frank de Jaeger: 2nd Generation Microtronic PCB 
- Manfred Henf: 2nd Generation Microtronic 3D Design & Printing 
- Martin Sauter: Busch 2095 Cassette Interface Protocol Reengineering & Research
- Lilly (https://github.com/ducatimaus/Busch-2090): Breakpoint & Single Stepping Integration for Uno R3 Version 

#### License: GPL 3
#### [YouTube Videos](https://www.youtube.com/playlist?list=PLvdXKcHrGqhekyx81EoCwQij1Lqylp0dB) 

## Abstract

This repository contains a number of Arduino-based emulators of the 
Busch 2090 Microtronic Computer System. 

The Microtronic was an educational 4bit single-board computer system of
the early 1980s, manufactured by the company Busch Modellbau in
Germany: 

![Microtronic Prospekt](./images/microtronic-prospekt.png) 

This is the Microtronic of the author; on the left you see
the 2095 Cassette Interface (the breadboard & Arduino R3 contraption 
connected to the Microtronic is an Arduino-based speech synthesizer
for the the 2090, utilizing the Emic-2 speech board): 

![Microtronic 1](./images/microtronic-emic-2-speech-3.jpg) 
![Microtronic 2](./images/microtronic-emic-2-speech-1.JPG) 

There is [some information about the Busch 2090 Microtronic available
on the official Busch website here, including PDFs of the original
manuals in
German](https://www.busch-model.info/service/historie-microtronic/.)

The designer of the original Busch Microtronic, **Mr. Jörg Vallen of Busch**, 
was also so kind to grant permission to include a full copy of the
manual set in the [`manuals`](./manuals/) directory of this project. 

The latest PCB version - "The Microtronic Next Generation" - also
povides an emulation of the Busch 2095 Cassette Interface that plugs
into a real Microtronic to provide SD-card based file storage. The
2095 Cassette Interface implementation was made possible by Martin
Sauter's ingenious reverse engineering of the 2095 protocol. Martin
also implemented a Python-based prototype of a 2095 emulator.

Recently, the latest iteration of this project, "The Microtronic Next
Generation", was featured on the Hackaday front page:

![Hackaday 1](./hackaday/microtronic-hackaday-1.jpg) 
![Hackaday 2](./hackaday/microtronic-hackaday-2.jpg) 
![Hackaday 3](./hackaday/microtronic-hackaday-3.jpg) 

## History 

The project started in January 2016 and is still active in January 
2021. In that time, the number of contributers increased from 1 to 6. 
See below for the different versions using different Arduino
variants and form factors. 

## Emulator Versions 

### The "Microtronic Next Generation" Project 

The current version of the Microtronic Emulator is called the "Micotronic Next Generation", and it comes as a PCB: 

![Busch 2090 Microtronic Next Generation - SH1106 SPI OLED Version](./microtronic-nextgen-sh1106-spi/nextgen-spi-5.jpg) 

![Busch 2090 Microtronic Next Generation - SH1106 SPI OLED Version](./microtronic-nextgen-sh1106-spi/nextgen-spi-1.jpg) 

![Busch 2090 Microtronic Next Generation - Nokia Version Front](./microtronic-nextgen-nokia/pcb1.jpg) 

![Busch 2090 Microtronic Next Generation - Nokia Version Back](./microtronic-nextgen-nokia/pcb2.jpg) 

![Busch 2090 Microtronic Next Generation - Nokia Version](./microtronic-nextgen-nokia/pcb1.jpg) 

![Busch 2090 Microtronic Next Generation - 2095 Emulation](./microtronic-nextgen-nokia/2095-1.jpg) 

![Busch 2090 Microtronic Next Generation - 2095 Emulation](./microtronic-nextgen-nokia/2095-2.jpg) 

### The "Microtronic 2nd Generation" Sister Project  

The "sister project", created by **Frank de Jaeger from Belgium and Manfred Henf from Germany,** ist called the **"Microtronic 2nd Generation"**. Please consider this great project if you wish to create a more professional Microtronic emulator that neatly and professionally installs into an original Busch electronics console, including a 3D-printed keyboad that mounts onto the console hole raster on the top! 

The project uses the same firmware as the "Microtronic Next Generation" presented here, but has a slightly different pin layout (i.e., requires some slight adjustments to the `hardware.h` pin configuration file). The firmware can be found in the [`microtronic-2nd-generation`](./microtronic-2nd-generation/) folder. The 2nd Generation version uses the Nokia 5110, does not support the real time clock (RTC), and does not have a 1Hz output port. The loudspeaker can be
added between A0 and GND over a 75 Ohm resistor as an "after market"
hack / mod (it wasn't anticipated in the original 2nd Generation design). 

**Thanks to Frank and Manfred for this great piece of engineering.** They also *exactly replicated the input and output transistor-stages of the original Microtronic,* so the 2nd Generation project is electrically maximally compatible with the original. It is hence the best choice for a fully compatible  Microtronic emulator that blends perfectly with the Busch electronics system, and for conducting the plenty electronics experiments described in the original Microtronic Busch manuals. 

More details about this great project can be found on the [homepage of the Microtronic 2nd Generation project.](https://www.rigert.com/ee-forum/viewtopic.php?t=2497)

*The following pictures are courtesy of Frank de Jaeger:* 

![Microtronic 2nd Generation Pic 1](./microtronic-2nd-generation/pic1.jpg)
![Microtronic 2nd Generation Pic 2](./microtronic-2nd-generation/pic2.jpg)
![Microtronic 2nd Generation Pic 3](./microtronic-2nd-generation/pic3.jpg)
![Microtronic 2nd Generation Pic 4](./microtronic-2nd-generation/pic4.jpg)


### The 2021 Arduino Uno R3 Version  

This is a new take on the 2016 Arduino Uno R3 version with some improvements over the 2016 version. 

In a nutshell, it offers: 

- High-speed Microtronic emulation with an authentic retro user experience (LED 7segment display etc.)
- Extended PGM program library in AVR ``PGMSPACE``, e.g. Blackjack, Prime Numbers, Lunar Lander, and the Nim Game. Unlike previous versions of the R3 emulator, the PGM programs are now no longer stored in the AVR's EEPROM; hence, more and longer programs can be accessed with the push of a PGM button - more fun! Note that the ``PGM-EEPROM.INO`` loader is no longer required with that version and is considered obsolete by now. 
- PGM 2 & PGM 1 functionality: the EEPROM is now used to store & restore the Microtronic memory contents! Before powering down the emulator, simply dump the current memory contents into the EEPROM via ``PGM 2``, and resume your work with ``PGM 1``. Better than a 2095 Cassette Interface! 
- Soft reset functionaliy; either via an extra push button, or the ``RUN + CCE`` key combination. 
- CPU Speed Control / Throttle: go turbo Microtronic (Prime Numbers have never been computed faster on a Microtronic!), or experience the cozy processing speed of the original Microtronic. You can either use a 10 kOhm potentiometer to dial in the speed, or use the ``RUN + <HEXKEY>`` key combination. 
- Four digital inputs for ``DIN``, and either 3 or 4 digital outputs for ``DOT`` *(note: for 4 outputs, the soft reset button has to be sacrificed).* 
- 1 Hz clock output as required for certain experiments *(note: then, the CPU speed potentiometer has to be sacrificed).* 
- Breakpoint (``BKP``) and Single Step (``STEP``) functionality: **Thanks much to Lilly (https://github.com/ducatimaus/Busch-2090) for integrating & refactoring this functionality! Great job!** 
- A simple build - you can set this up in 30 minutes.

![Busch 2090 Microtronic Emulator for Arduino Uno R3 2021 Version - Pic 1](https://github.com/lambdamikel/Busch-2090/blob/master/images/2090-2021-1.jpg)

![Busch 2090 Microtronic Emulator for Arduino Uno R3 2021 Version - Pic 2](https://github.com/lambdamikel/Busch-2090/blob/master/images/2090-2021-2.jpg)

![Busch 2090 Microtronic Emulator for Arduino Uno R3 2021 Version - Pic 3](https://github.com/lambdamikel/Busch-2090/blob/master/images/2090-2021-3.jpg)

![Busch 2090 Microtronic Emulator for Arduino Uno R3 2021 Version - Pic 4](https://github.com/lambdamikel/Busch-2090/blob/master/images/2090-2021-input-board-1.jpg)

![Busch 2090 Microtronic Emulator for Arduino Uno R3 2021 Version - Pic 5](https://github.com/lambdamikel/Busch-2090/blob/master/images/2090-2021-input-board-2.jpg)

**Thanks to Lilly (Germany) for pointing out that the R3 version was
still compiling and working (which motivated me to resurrect this
project), and for integrating & refactoring the ``BKP`` and ``STEP``
functionality!** In fact, Lilly built her own 2090 R3 emulator:
embracing the true hacker spirit, she used an old Agfa photo box and
recycled it as the emulator case! This is her emulator; it certainly
has the words "retro" and "vintage" written all over it. For more
details about her projects and the Agfa box emulator, check out her
Github [https://github.com/ducatimaus](https://github.com/ducatimaus)
that also contains a fork of the 2090 project:

![Lilly Pic 1](https://github.com/lambdamikel/Busch-2090/blob/master/images/lilly-1.jpg)

![Lilly Pic 3](https://github.com/lambdamikel/Busch-2090/blob/master/images/lilly-3.jpg)

Lilly has added external pulldown resistors to the digital inputs so that the logic-levels are non-inverted and hence compatible with Busch electronics kits & experiments. See below for a discussion of pulldown vs. (internal) pullup resistors. 

![Lilly Pic 2](https://github.com/lambdamikel/Busch-2090/blob/master/images/lilly-2.jpg)

I also love how the documentation (IPad PDF manual) is much more modern than the computer - back in the 80s, it used to be the other way around :-) 

#### Hardware Requirements

You will need: 

- An Arduino Uno R3 
- A TM1638 module with 8 7segment digits, 8 push buttons, and 8 LEDs 
- A 4x4 keypad with matrix encoding for hexadecimal input
- Optional: A 10k Ohm potentiometer for CPU speed / throttle control 
- Optional: A reset push button for Soft Reset 

#### Hardware Setup / Wiring 

For the Uno version:

    //
    // Uncomment this if you want 4 DOT outputs instead of 3: 
    //

    // #define RESET_BUTTON_AT_PIN_0 

    //
    // Uncomment this to use A5 for CPU speed potentiometer; ELSE this is used for 1 Hz clock output: 
    //

    // #define USE_CPU_THROTTLE_POT_AT_PIN_A5 

    //
    // TM1638 module
    //

    TM1638 module(14, 15, 16);

    //
    // Keypad 4 x 4 matrix
    //

    byte colPins[COLS] = {5, 6, 7, 8}; // columns
    byte rowPins[ROWS] = {9, 10, 11, 12}; // rows

    //
    // These are the digital input pins used for DIN instructions
    // Uncomment this if you want non-inverted inputs (INPUT vs. INPUT_PULLUP):

    #define INVERTED_INPUTS 
    
    #define DIN_PIN_1 1
    #define DIN_PIN_2 2
    #define DIN_PIN_3 3
    #define DIN_PIN_4 4

    //
    // these are the digital output pins used for DOT instructions
    // (in addition to the TM1638 LEDs)
    //

    #define DOT_PIN_1 13
    #define DOT_PIN_2 17
    #define DOT_PIN_3 18
    // only used if RESET_BUTTON_AT_PIN_0 is not defined: 
    #define DOT_PIN_4 0 

    // only used if USE_CPU_THROTTLE_POT_AT_PIN_A5 is not defined: 
    #define CLOCK_1HZ A5 

    //
    // reset Microtronic (not Arduino) by pulling this to GND
    // only used if RESET_BUTTON_AT_PIN_0 is defined: 
    //

    #define RESET_PIN 0

    //
    // CPU throttle 
    // only used if USE_CPU_THROTTLE_POT_AT_PIN_A5 is defined: 
    // 

    #define CPU_THROTTLE_ANALOG_PIN A5 // center pin of 10k Ohm potentiometer
    #define CPU_THROTTLE_DIVISOR 10 
    #define CPU_MIN_THRESHOLD 10 // if smaller than this, CPU delay = 0

    // standard delay (~ original Microtronic speed) 
    int cpu_delay = 12;

    // predefined delays in ms: RUN + <HEX> 
    //                    0  1  2  3   4   5   6   7   8   9  10  11   12   13   14  15
    int cpu_delays[16] = {0, 3, 6, 9, 12, 15, 18, 21, 30, 40, 50, 80, 120, 150, 200, 500 }; 

	
#### Description 

The TM1638 "Led & Key" module is being used.  The **eight push buttons
of the TM1638 are the function keys of the Microtronic**, in this
order of sequence, from left to right: ``HALT, NEXT, RUN, CCE, REG,
STEP, BKP, PGM``:

    #define HALT  1 
    #define NEXT  2 
    #define RUN   4
    #define CCE   8
    #define REG  16
    #define STEP 32
    #define BKP  64
    #define PGM 128 

The 4x4 keypad keys are hex from `0` to `F`, in bottom-left to
top-right order. You might consider to relabel the keys on the pad 
(I haven't done that):

    7 8 9 A       C D E F 
    4 5 6 B  ==>  8 9 A B
    1 2 3 C  ==>  4 5 6 7
    * 0 # D       0 1 2 3

Unlike the original, you can use **``HALT + CCE``** (pressed
simultaneously) to **soft-reset the emulator.** Memory contents gets
preserved, unlike with the Arduino reset button.

In addition, the CPU speed ("throttle") can be set to 1 of 16 
pre-defined speeds (see ``cpu_delays[16]`` array).  To select the
**emulation speed**, use **``RUN + <HEXKEY>``** (pressed
simultaneously); speed 3 or 4 roughly corresponds to original
Microtronic speed. At slower emulation speeds, you might have to hold
these buttons pushed down for up to a second or two in order to be
effective.

Microtronic's **Carry** and **Zero** flag are the LEDs 1 and 2 of the
TM1638, the 1 **Hz clock LED** is LED 3 (from left to right). The LEDs
5 to 8 are used as **DOT outputs** (set by the data out op-code
``FEx``). 

There are also three PINs for DOT outputs: ``13``, ``A3`` and ``A4``
are used for the first 3 bits of the DOT outputs. For the 4th bit, you 
can use pin ``0``, but then the ``RESET`` button (see next paragraph) 
will have to be sacrificed (due to a shortage of R3 pins). 

The Arduino Uno pins ``D1`` to ``D4`` are read by the emulator data in
instruction ``FDx (DIN)``. Connecting these pins to ground (GND) will
set the corresponding bit to one (high). See ``PGM D``. Note that the
Microtronic uses positive logic, i.e. *HIGH = 3.5 to 5 V = 1,* and
*LOW = GND (0 V) = 0*.  If an input is left unconnected ("floating"),
then it also reads as LOW = 0.  **Note that unlike the original
Microtronic, the emulator is using inverted logic by default:
``pinMode(DIN_PIN_x, INPUT_PULLUP)``.** It is possible to use
non-inverted logic like the original Microtronic, but you will then
need to add external pulldown (4.7 kOhm typical) resistors, else
floating inputs will not quickly and reliably respond to HIGH -> LOW
transitions (floating inputs always have to be avoided). In addition
to the pulldown resistors, ``#define INVERTED_INPUTS`` needs to be
commented out, i.e., not defined. If flag ``#define INVERTED_INPUTS``
is defined, the inputs are configured via ``pinMode(DIN_PIN_x,
INPUT_PULLUP)``, and the **internal pullup resistors** are used,
resulting in **inverted logic** levels. If you wish to use **external
pulldown resistors** for **non-inverted logic** (like in the real
Microtronic), then ensure ``#define INVERTED_INPUTS`` is commented
out, i.e., not defined. Consequently, inputs will then be configured via
``pinMode(DIN_PIN_x, INPUT)``.

The emulator also features 3 or 4 digital outputs for ``DOT`` on pins
``13, 17 (A3), 18 (A4)``, and ``0``.  Pin ``0`` is used for ``DOT``
bit 4 only if ``#define RESET_BUTTON_AT_PIN_0`` is NOT defined, i.e., 
commented out from the source code. 

Due to a shortage of GPIO pins on the R3, pin ``0`` is then used as a
soft reset pin to which you can connect a physical push
button. Connecting this to GND will reset the emulator and keep the
memory contents, unlike the reset button on the Arduino. However, you
can always preserve memory contents via ``PGM 2`` and reload via ``PGM
1``. **Note that the physical reset button is not required, as you now
also use ``HALT + CCE`` (pressed simultaneously) to soft-reset the
emulator.** It is hence suggested to use ``PIN 0`` for ``DOT`` bit 4,
and hence leave ``#define RESET_BUTTON_AT_PIN_0`` commented out, i.e.,
not defined.

Due to even more severe GPIO pin-shortage, the ``A5`` pin is either
used as a CPU speed throttle to which you can connect a potentiometer
to dial in the emulator speed, or you can use it as the ``1 Hz`` clock
output. **The latter is required for certain experiments; i.e., on page
38 in Vol. 1 of the Manual ("Timer - Der Computer als Zeitschaltuhr"),
where the ``1 Hz`` Clock Output is connected to ``DIN 4`` to provide a
1 Hz clock signal to the program.** To use ``A5`` as 1 Hz clock output,
leave ``#define USE_CPU_THROTTLE_POT_AT_PIN_A5`` commented out, i.e.,
not defined.

However, if ``#define USE_CPU_THROTTLE_POT_AT_PIN_A5`` is defined,
then analog pin ``A5`` on the Uno is used as a CPU speed
throttle. Then, connect a potentiometer to adjust the speed of the
CPU.  **Important: All three pins of the potentiometer need to be
connected!  The center pin of the potentiometer goes to ``A5``
(``CPU_THROTTLE_ANALOG_PIN``), and the outer remaining two pins
connect to ``5V (VCC)`` and ``GND``.** Otherwise, the analog input is
left "floating" and no analog value can be read. The ``analogRead``
should return a value between 0 and 1023; adjust the
``CPU_THROTTLE_DIVISOR 10`` if required. I am using a 10 kOhm
potentiometer; don't use values smaller than 1 kOhm because of the VCC
-> GND current leakage over the potentiometer.

Please note that the CPU throttle potentiometer is no longer required, 
because the emulation speed can also be specified by using the 
key combination ``RUN + <HEXKEY>`` (``0`` = fastest, ``F`` = slowest). The 
CPU throttle delay times are specified in the source code in the array
``int cpu_delays[16] = {0, 3, 6, 9, 12, 15, 18, 21, 30, 40, 50, 80, 120, 150, 200, 500 }``
(times in milliseconds). 

Unlike the original Microtronic, this emulator uses the leftmost digit
of the 8digit FM1638 to display the **current system status**; the
original Microtronic only featured a 6digit display. Currently, the
**status codes** are:

- ``H``: stopped 
- ``A``: enter address 
- ``P``: enter op-code 
- ``r``: running program
- ``?``: keypad input from user requested  
- ``i``: entering / inspecting register via ``REG``  
- ``t`` : entering clock time (``PGM 3``) 
- ``C`` : showing clock time (``PGM 4``) 

Moreover, unlike the original Microtronic, the emulator uses blinking
digits to indicate cursor position. The ``CCE`` key works a little bit
differently, but editing should be comfortable enough.

Typical operation sequences such as ``HALT-NEXT-00-RUN`` and
``HALT-NEXT-00-F10-NEXT-510-NEXT-C00-NEXT`` etc. will work as
expected.  Also, try to load a demo program: ``HALT-PGM-7-RUN``.

Note that programs can be entered manually, using the keypad and
function keys, or you can load a fixed ROM program specified in the
Arduino sketch via the ``PGM`` button. These ROM programs are defined
in the ``busch2090.ino`` sketch and are stored in the ``PGMSPACE``.
The ROM programs ``PGM 7`` to ``PGM F`` are defined:

The following PGM programs from ``PGM 7`` to ``PGM F`` are stored in
the sketch using ``PGMSPACE`` strings.  Note that ``PGM 1`` to ``PGM
6`` are built-in special functions that do not correspond to
``PGMSPACE`` programs. If you wish, you can exchange these ``7`` to
``F`` programs with you own:

- ``PGM 1`` : restore Microtronic memory from EEPROM ("core restore") 
- ``PGM 2`` : store / dump Microtronic memory to EEPROM  ("core dump") 
- ``PGM 3`` : set clock 
- ``PGM 4`` : show clock 
- ``PGM 5`` : clear memory
- ``PGM 6`` : load ``F01`` (NOPs) into memory 
- ``PGM 7`` : Nim Game 
- ``PGM 8`` : Crazy Counter 
- ``PGM 9`` : the Electronic Dice, from Microtronic Manual Vol. 1, page 10
- ``PGM A`` : the Three Digit Counter from Microtronic Manual Vol. 1, page 19 
- ``PGM B`` : moving LED Light from the Microtronic Manul Vol. 1, page 48  
- ``PGM C`` : digital input DIN Test Program
- ``PGM D`` : Lunar Lander (Moon Landing) from the Microtronic Manual Vol. 1, page 23 
- ``PGM E`` : Prime Numbers, from the "Computerspiele 2094" book, page 58
- ``PGM F`` : Game 17+4 BlackJack, from the "Computerspiele 2094" book, page 32

Have fun! 

## Current Arduino Sketches & Gerbers 

Please check the sub-directories
- [`microtronic-nextgen-nokia`](./microtronic-nextgen-nokia/) for the Nokia 5510 Display version, 
- [`microtronic-nextgen-sh1106-spi`](./microtronic-nextgen-sh1106-spi/) for the SH1106 SPI OLED version, 
- [`microtronic-2nd-generation`](./microtronic-2nd-generation/) for the Nokia 5110-based Microtronic 2nd Generation project, and 
- [`busch2090`](./busch2090/) for the 2021 Arduino Uno R3 version. 

The *SH1106 SPI OLED is the latest version* and we have identified this
display as the best option for the project. The Nokia 5510 is a good
choice too, but it is less reactive and gets blurry with very fast
screen updates. 

The 2nd Generation version does not support the real time clock (RTC),
and does not have a 1Hz output port. Note that the loudspeaker can be
added between A0 and GND over a 75 Ohm resistor (as an "after market"
hack / mod).

The SH1106 I2C SPI OLED was also experimented with; see
[`microtronic-nextgen-sh1106-i2c`](./obsolete/microtronic-nextgen-sh1106-i2c/).
It is **no longer supported** because it is **significantly slower than
both the Nokia 5110 and the SH1106 SPI OLED.**

Only the
[`microtronic-nextgen-sh1106-spi`](./microtronic-nextgen-sh1106-spi/)
and the [`busch2090`](./busch2090/) 2021 Arduino Uno R3 version will
be continued.  The PCB Gerbers will follow shortly.


## 2016 Versions - DEPRECATED and NOT RECOMMENDED 

**Please note that these version have note been tested recently (they
are from 2016, and Arduino has changed since then).  I strongly
recommend to use the "Micotronic Next Generation" version given above 
instead.**

![Busch 2090 Microtronic Emulator for Arduino Mega 2560 Version 3](https://github.com/lambdamikel/Busch-2090/blob/master/images/img-mega-v3-1-small.jpg)

![Busch 2090 Microtronic Emulator for Arduino Mega 2560 Version 3](https://github.com/lambdamikel/Busch-2090/blob/master/images/img-mega-v2-5-small.jpg)

![Busch 2090 Microtronic Emulator for Arduino Uno](https://github.com/lambdamikel/Busch-2090/blob/master/images/img4-small.jpg)

![Busch 2090 Microtronic Emulator for Arduino Mega](https://github.com/lambdamikel/Busch-2090/blob/master/images/img-mega-v1-1-small.jpg)

![Busch 2090 Microtronic Emulator for Arduino Mega](https://github.com/lambdamikel/Busch-2090/blob/master/images/img-mega-v1-6-small.jpg)

[More info about these 2016 Microtronic emulator projects can be found here.](./README.old.md) 

## Required Third-Party Libraries 

Please check the [`libraries.zip`](./libraries/libraries.zip) that contains everything needed (and more) for the different Arduino emulator versions discussed here. 