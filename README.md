# <h1 align="center">Soup Pico</h1>

<p align="center">I made Soup from fallout with RP2040 board because I think rectangles are boring. The Soup Pico is what I came up with.</p>

<p align="center">

<img src="https://github.com/user-attachments/assets/10cdbeb2-b130-40f6-b05e-e0af3bb90407" width="500">

</p>

## Why did I make the Soup Pico?

I was tired of looking at the old rectangular dev boards. So I decided to learn how to design my RP2040 hardware. This includes the USB, flash memory and all that stuff. I thought, why not make it look like a cat? That is how the Soup Pico was born. It has been a way to learn about routing on printed circuit boards. Now I have a cat-shaped computer that is really cool.

## What the Soup Pico can do

- The Soup Pico has an RP2040 chip with two cores that can go up to 133 MHz
- It has a USB-C port for power and programming
- The Soup Pico has 4 MB of flash memory
- It has boot and reset buttons so I do not have to short any pins
- All the GPIO pins are accessible
- The best part is that the Soup Pico is shaped like a cat

### Schematics

- I mostly followed the RP2040 hardware guide and made a few changes:
- I used a USB-C port with the usual resistors on the CC lines
- I added a 3.3V regulator to power everything
- The flash chip is connected to the dedicated QSPI pins
- The buttons and headers are arranged to fit inside the cat outline

<img align="center" width="600" src="https://github.com/user-attachments/assets/8017d7af-cc13-4ea1-a253-2fc4ed8d9633" />

### PCB layout

The Soup Pico has a two-layer printed circuit board with a cat-shaped outline. I tried to keep the USB and crystal traces short. I also made sure to add a lot of ground and put capacitors to the RP2040 chip.

<h1 align="center">Layers</h1>



<img width="500" alt="Screenshot 2026-05-27 232959" src="https://github.com/user-attachments/assets/c993e542-13e3-4911-9841-940b14cb5d56" />

<img width="480" alt="image" src="https://github.com/user-attachments/assets/d40c4f7c-70b7-4134-b079-250ac37e706d" />

</div>

## What you'll need to build one

| Component          | Part / value               | How many |
|--------------------|----------------------------|----------|
| RP2040             | QFN56                      | 1        |
| Flash chip         | W25Q32 (4 MB)              | 1        |
| USB-C connector    | 16-pin receptacle          | 1        |
| Crystal            | 12 MHz, 20pF               | 1        |
| Voltage regulator  | 3.3V, 500 mA (RT9013 etc.) | 1        |
| Capacitors         | 0.1 µF, 1 µF, 10 µF        | ~10      |
| Resistors          | 1k, 5.1k, 27 ohm           | ~8       |
| Tactile switches   | 6x6 mm                     | 2        |
| Pin headers        | 1x40 male (snap to size)   | 1        |


## Getting firmware onto the Soup Pico

Flashing the Soup Pico is the same as any RP2040 board:

- Hold down **BOOTSEL**
- Plug in the USB cable
-  a drive called `RPI-RP2` pops up
- Drag and drop a `.uf2` file. That is it.

### GPIO pins on the Soup Pico

All the RP2040 pins are accessible. A few special ones are:

| Pin     | What it does               | Where to find it   |
|---------|----------------------------|--------------------|
| GP0      | UART0 TX, or anything really | Left ear header  |
| GP1      | UART0 RX                   | Left ear           |
| 3V3_EN   | Turn the regulator on/off  | Near the USB port  |
| VBUS     | 5V straight from USB       | Power header       |
| 3V3      | Regulated 3.3V output      | Power header       |


## Example firmwarefor the Soup Pico
``` diff
#define LED_PIN 25

void setup() {
  pinMode(LED_PIN, OUTPUT);
}

void loop() {
  digitalWrite(LED_PIN, HIGH);
  delay(500);

  digitalWrite(LED_PIN, LOW);
  delay(500);
}
```


# Zine Page
<img width="600" alt="zine4" src="https://github.com/user-attachments/assets/b22fac3d-c55e-4787-99ba-d6c0f9264736" />
