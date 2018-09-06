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
## Protocols
https://www.raspberrypi.org/forums/viewtopic.php?t=51450
* I2C - Easiest and most expandable bus. Raspberry has two I2C buses, bus 0 and bus 1. Capable of expanding the Rpi to thousands of output ports. Programming is very easy.
* SPI - Only 2 chip select lines so max number of devices is very limited. Bus is faster and can be driven over longer cable runs than I2C. Programming more difficult. Device selection very limited unless you are willing to solder SMD.
* [UART (RS-232)](https://www.raspberrypi.org/documentation/configuration/uart.md)
  * PL011
  * mini UART
* GPIO - Good for turning on/off a few I-O ports. If all that is needed is control of a solid state relay or two for example, this is it. You could bit bang I2C or SPI but why would you when real I2C or SPI is available?

https://electronics.stackexchange.com/questions/37814/usart-uart-rs232-usb-spi-i2c-ttl-etc-what-are-all-of-these-and-how-do-th
