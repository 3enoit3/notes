# Generalities
## Port vs Bus vs Protocol vs Interface
https://www.quora.com/What-is-the-difference-between-port-bus-protocol-and-interfaces
* Protocol: a set of rules and procedures for transmitting data
* Interface: a shared boundary between two components
  * Bus: a communication system that transfers data
  * Port: a connection point / socket / external bus
## Memory-mapped vs Port-mapped IO
https://www.bogotobogo.com/Embedded/memory_mapped_io_vs_port_mapped_isolated_io.php
# BCM2837
## Designations
* **BCM2835**: https://www.raspberrypi.org/documentation/hardware/raspberrypi/bcm2835/BCM2835-ARM-Peripherals.pdf
* BCM2835 vs **BCM2836**: "The only significant difference is the removal of the ARM1176JZF-S processor and replacement with a quad-core Cortex-A7 cluster" : https://www.raspberrypi.org/documentation/hardware/raspberrypi/bcm2836/README.md 
* BCM2836 vs **BCM2837**: "The only significant difference is the replacement of the ARMv7 quad core cluster with a quad-core ARM Cortex A53 (ARMv8) cluster" : https://www.raspberrypi.org/documentation/hardware/raspberrypi/bcm2837/README.md
On the different designations : https://raspberrypi.stackexchange.com/questions/840/why-is-the-cpu-sometimes-referred-to-as-bcm2708-sometimes-bcm2835
## Protocols
https://www.raspberrypi.org/forums/viewtopic.php?t=51450
* [BSC (I2C)](https://alanbarr.github.io/RaspberryPi-GPIO/i2c.html) - Easiest and most expandable bus. Raspberry has two I2C buses, bus 0 and bus 1. Capable of expanding the Rpi to thousands of output ports. Programming is very easy.
* [UART (RS-232)](https://www.raspberrypi.org/documentation/configuration/uart.md)
  * PL011
  * mini UART
* SPI - Only 2 chip select lines so max number of devices is very limited. Bus is faster and can be driven over longer cable runs than I2C. Programming more difficult. Device selection very limited unless you are willing to solder SMD.
* GPIO - Good for turning on/off a few I-O ports. If all that is needed is control of a solid state relay or two for example, this is it. You could bit bang I2C or SPI but why would you when real I2C or SPI is available?

https://electronics.stackexchange.com/questions/37814/usart-uart-rs232-usb-spi-i2c-ttl-etc-what-are-all-of-these-and-how-do-th
