# Brew Automation Hardware with a STM8S207
This PCB is an evolution of what originally was an Arduino with some added hardware. The current PCB features an STM8S207R8, which comes in a 64 pins LQPF package. It has a maximum of 52 GPIO pins, contains 64K Flash, 1536 bytes EEPROM and 6 KB of RAM.

# Features
The current PCB and firmware have the following features:
- Reading of **6 x temperature sensors**: two in the HLT (one I2C LM92, one One-Wire DS18B20), one in the MLT (I2C), one in the boil-kettle (One-Wire), one at the output of the counterflow-chiller (One-Wire) and one at the MLT return-manifold (One-Wire).
- Reading of **one hardware temperature** by a LM35 temperature sensor: this is used to protect the Solid State Relays (SSR) from overheating. The LM35 is typically mounted to a heatsink of one of the SSRs that switch a heating-element.
- Reading a maximum of **4 x FS300A flowsensors**: between HLT and MLT, between MLT and boil-kettle, one at the output of the counterflow-chiller and one at the entry of the MLT return-manifold.
- Control of **8 x solenoid ball-valves** at 24 V DC.
- **2 x PWM signals (25 kHz, 28 V DC)** for the modulating gasburners (HLT and boil-kettle burners).
- Control of **4 x SSR outputs at 230 V AC**: the pump, a second pump (for the HLT counterflow-chiller), 230 V enable for the HLT gasburner and 230 V enable for the boil-kettle gasburner.
- Control of **6 x SSR outputs at 230 V AC** for the three phase heating-elements in the HLT and the boil-kettle. With this, heating of the HLT is possible with a gas-burner, with 1, 2 or 3 heating-elements of with any combination of these.
- **Synced SSR outputs** for HLT and boil-kettle, so that you only need **one three-phase connection**. The boil-kettle outputs have priority over the HLT outputs, meaning that if (on any phase of 230 V) both HLT and boil-kettle are heating, only the boil-kettle is activated.
  It is also possible to use just one (or two) of the three-phases, depending on the number of heating-elements inside the HLT and/or boil-kettle. The firmware is capable of addressing one, two or three heating-elements per kettle.
- **Ethernet and USB connection** to PC: USB-connection is used for debugging, main connection between PC-program and the firmware is Ethernet.
- **Frontpanel LEDs (24 in total)** that show the status of all actuators. They are controlled by a MAX7219 LED Display Driver, located on a separate PCB, the frontpanel PCB.
