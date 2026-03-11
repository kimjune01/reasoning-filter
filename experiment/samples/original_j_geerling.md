After seeing Oliver Ettlin's 39C3 presentation Excuse me, what precise time is It?, I wanted to replicate the PTP (Precision Time Protocol) clock he used live to demonstrate PTP clock sync.

I pinged him on LinkedIn inquiring about the build, and shortly thereafter, he published Gemini2350/ptp-wallclock, a repository with rough instructions for the build, and his C++ application to display PTP time (if available on the network) on a set of two LED matrix displays, using a Raspberry Pi.

A Pi is useful because it meets the two requirements for a PTP Clock: it's easy to interface with LED matrix displays (via GPIO and a HAT), and its Broadcom NIC has PTP hardware timestamping capabilities.

The required hardware costs around $120-150, depending on what part of the AI bubble we're in: Raspberry Pi 4 model B (the Pi 5 doesn't yet work with the RGB matrix), Adafruit RGB Matrix HAT + RTC for Raspberry Pi, two Waveshare 64x32 pixel LED Matrix Panels, an Adafruit 5V 4A power supply, and a 32GB microSD card. Any Pi 4 should work fine; you don't need a lot of RAM.

And if it isn't obvious, you also need a PTP grandmaster somewhere on your network, which should be broadcasting to the standard PTP multicast IPv4 address, 224.0.1.129. You could also have multiple PTP grandmasters, allowing the Pi to use PTP's Best Master Clock Algorithm (BMCA) to select the best time source.

The Adafruit RGB Matrix HAT requires some soldering. There's a 2x20 female pin header that fits on the Pi's GPIO header, a ribbon cable connector on the top side, and a 5V DC power output screw terminal header to supply power to the two LED matrices. One ribbon cable goes from the HAT to the 'right' LED matrix (when viewed from the front). Then the right matrix plugs into the left matrix using the other ribbon cable.

A dedicated 5V 4A power supply is best, to prevent voltage drop when driving the display (which causes flickering).

The first step is to configure the Pi for optimal performance refreshing the LED matrix. Disable general CPU core scheduling (so threads can better pin themselves to a single core), and disable the built-in audio output. Blacklist the snd_bcm2835 kernel module. Then install the RGB LED Matrix library from hzeller/rpi-rgb-led-matrix — clone it, compile via make, and test with Conway's Game of Life demo.

For the PTP Wallclock application, copy the font file 6x13B.bdf from the RGB LED Matrix project, clone the Gemini2350/ptp-wallclock repo, copy ptp-clock.cpp into the rpi-rgb-led-matrix directory, and compile with g++ linking against librgbmatrix and lpthread.

If you don't see PTP traffic, install tcpdump and check port 319 or 320. If you only see sync messages without follow-up messages, the PTP server may be configured in one-step mode — check that twoStepFlag is set to 1 in the ptp4l configuration.

I designed a 3D printable bracket which attaches the two displays with a tiny bit of wiggle room, to account for manufacturing variances. The mounting bracket keeps the magnetic screws at the same height, so you could mount this to a fridge or other ferrous surface, with the Pi dangling below.

The completed display reveals some interesting timing issues. My GPS-derived time source drifts several seconds from UTC every couple of days. Investigation suggests potential Intel i226 NIC problems with PPS input handling. I'm considering switching to alternative Pi time servers due to driver frustrations.
