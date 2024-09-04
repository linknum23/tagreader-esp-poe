# Tag Reader for Home Assistant modified to work with ESP32-POE

The tag reader is a simple to build/use NFC tag reader, specially created for [Home Assistant](https://www.home-assistant.io). It is completely based on [adonno/tagreader](https://github.com/adonno/tagreader) but uses a ESP32-POE in place of a D1 Mini to avoid using wireless. The firmware is built using [ESPhome](https://www.esphome.io).

![Photos of the final product](docs/cases.jpg)

## Building the tag reader

To build your own modified tag reader, you need the following components:

- [ESP32-POE](https://www.olimex.com/Products/IoT/ESP32/ESP32-POE/open-source-hardware)
- [PN532 NFC Reader](https://s.click.aliexpress.com/e/_dZNORIJ)
- [WS2812](https://s.click.aliexpress.com/e/_d82GRqr)
- [Buzzer](https://s.click.aliexpress.com/e/_dZ5F5yj)

The 3D models are not yet available for combining the ESP32-POE and PN532 NFC Reader. This was made for a demo.

### Connecting the components

NOTE: this schematic needs to be updated to show the ESP32-POE and its pins. Instead of this weird fritzig software, use graphviz images.

![Photo of schematics](Schematics/tag_reader_schematics_v3.2.png)

There are not too many components to connect, but it does require soldering. You will need the following:

- [Solder](https://s.click.aliexpress.com/e/_dT3S62j)
- [Soldering iron with a fairly thin tip](https://s.click.aliexpress.com/e/_dXaI6nz)
- [About 40cm of thin wire (at least 5 different colors)](https://s.click.aliexpress.com/e/_dZvoYoB)


Also, make sure that you have set the switches on the PN532 to the following:

- Switch 1: On (up)
- Switch 2: Off (down)

This enables the PN532 module to communicate with the D1 over I2C, and is required for the modules to work together!

To flash the reader firmware to your ESP32-OPE you point ESPHome at [tagreader.yaml](tagreader.yaml).
> :warning: The tag reader requires ESPHome `1.16.0`.

If you're new to ESPHome, we recommend that you use the [ESPHome Home Assistant add-on](https://esphome.io/guides/getting_started_hassio.html).

![Open Case](docs/inside-case-completed.jpg)

## Configuring for use with Home Assistant

The tag reader requires [Home Assistant](https://www.home-assistant.io) 0.115 or later.

The tag reader will be automatically discovered by Home Assistant once the tag reader is connected to the same network. You can follow the instructions in the UI to set it up.

## Usage

Scanned tags can be managed from the tags interface in Home Assistant. You can find it under config -> tags.

![Screenshot of the Home Assistant tag UI](docs/tag-ui.gif)

## Disclamer

We use aliexpress affiliate links for the components and the tools. Some Ad-blockers might block these links and thus they seem to appear broken. You will have to temporarily disable the ad-blocker to open these links.
