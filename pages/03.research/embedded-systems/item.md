---
taxonomy:
  category: research
  tag: [research, hardware, embedded, raspberrypi, arduino]
---

Research about embedded computing systems

===

# Processes
## New chip learning steps
1. turn an LED on and off
2. input switch controls LED
3. timer controls LED blink
4. switch interrupt controls LED blink
5. establish UART communication with external system
6. establish communication using other protocols (SPI,I2C)
7. create a project

# Lab Essentials

## Equipment
- power supply
- multimeter
- breadboard

## Tools
- wire cutters
- screwdrivers
- tweezers

## ICs
- Voltage regulators
  - LDO: LM2937 / LM2940 / LP2957 / MIC2940A / MIC2954 / TS2937 / TS2940
  - Variable linear: LM317 (positive), LM337 (negative)
  - Voltage reference: TL431, TLV431
  - Switching (buck/boost): MC34063
- Linear
  - Timer: NE555/NE556, TLC551/TLC552
  - LED driver: LM3914 (bar graph)
  - Op-amp: TL082, LM6132, LM324
  - Comparator: LM393, LM311, LM339
  - Opto-isolator: 817C, 4N35, 6N137
- Logic: 74HCxx & 4xxx series (gates, counters, multiplexers, registers)
- I2C-bus
  - EEPROM: 24FC64 / 24FC512
  - I/O Expander: MCP23008 / MCP23017, PCAL6408A / PCAL6416A
  - RTC: various
  - ADC: various
  - DAC: various
  - Environmental sensors: DHT11 / DHT22 (temp/humidity)
  - Voltage translator: NLSX4373
- SPI-bus
  - similar types to I2C
- Microcontrollers & Boards
  - ATmega328P (DIP-28) & ATmega328PB (TQFP-32)
  - ATmega328P (DIP-28) & ATmega328PB (TQFP-32)
  - Arduino NANO clone board in DIP format (cheap from EBAY)
  - Arduino UNO clone board with switch for 3.3V or 5V (Seeeduino v4.2, Iteaduino, ...)
  - Arduino Zero clone board (ARM-based)
  - STM32 NUCLEO-L031K6 and NUCLEO-L432KC boards in DIP format (ARM-based)
  - STM32 Nucleo-64 and Nucleo-144 board families in Arduino UNO format (ARM-based)
  - ESP8266-based & ESP32-based boards
- Transistors
  - PN2222A/PN2907A or 2N4401/2N4403 : generic BJT, TO92 or SMD
  - 2N5551/2N5401 : high voltage BJT, TO92 or SMD
  - MPSA42/MPSA92 : higher voltage BJT, TO92 or SMD
  - BC550B/BC560B : low noise BJT, TO92 or SMD
  - TIP20 : darlington power NPN BJT, TO220
  - 2N7000 : MOSFET, TO92 or SMD
  - AO3400/AO3401 : MOSFET, SOT23-3, higher current than 2N7000, dirt cheap from EBAY
  - IRL530N, IRL540N, IRLZ44N, IRL2203N, IRL2703, IRLB4132, IRLB8721, IRLB8748 : power Nchan MOSFET, logic-level gates, TO220, IRLZ44N is dirt cheap from EBAY
  - Various : power Pchan MOSFET, TO220
  - Various : JFET, TO92 or SMD
- Hardware
  - Heat Sinks : TO220 heats sinks for volt regs and power transistors (cheap on EBAY)
  - M3 stainless steel machine screws : 5mm for threaded heatsinks, other lengths useful too
  - M3 nuts / locking washers / standoffs / spacers : cheap on EBAY
  - M3 nylon threaded-spacers and nuts : cheap on EBAY

## Passive components
- resistors
- capacitors
- inductors
- wire

# Books
- [Mastering STM32](https://leanpub.com/mastering-stm32)

# Links
- [Embedded Systems - Shape The World](http://users.ece.utexas.edu/%7Evalvano/Volume1/E-Book/)
- [LWAN web server](https://lwan.ws)
- [ESPP8266 Deep Sleep with Arduino IDE](https://randomnerdtutorials.com/esp8266-deep-sleep-with-arduino-ide/)
- [The Car Hacker's Handbook](http://opengarages.org/handbook/ebook/)
- [How to Build a Low-tech Website](https://solar.lowtechmagazine.com/2018/09/how-to-build-a-lowtech-website/) - solar-powered Olimex A20 computer running Armbian Stretch
