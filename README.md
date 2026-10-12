# RND Velocity

**RND Velocity** is a Python/PySide6 MIDI velocity randomizer and JACK MIDI patchbay for Linux. It provides a graphical interface for configuring velocity randomization and monitoring MIDI activity. It connects to the system's JACK-compatible MIDI server, including setups that provide JACK through PipeWire.

## Features

- Graphical interface built with PySide6.
- JACK MIDI input and output ports.
- Configurable velocity range and randomization behavior, including distribution, bias, maximum change, interval shift, and width.
- Preferences for display customization.
- Optional terminal debug output and an in-app log panel.
- Window layout and appearance options.

## Requirements

- Linux with a working JACK-compatible MIDI server (for example, JACK or PipeWire with JACK support).
- Python 3.
- PySide6.
- The Python `jack` module provided by JACK-Client.

The MIDI server must be running and accessible to the user before starting the application.

## Run

From a terminal in the directory containing `rnd_velocity.py`:

```bash
python3 rnd_velocity.py
```

If the application cannot connect, check that the JACK/PipeWire audio server is running and that its MIDI ports are available.

## Configuration

The application exposes its settings through **Preferences**. The program may create a local `midi-randomize-preferences.json` file to store preferences. Keep personal settings and machine-specific files out of public commits unless you intend to share them.

## Status

This project is under active development. Hardware, distribution, and MIDI-server configurations can differ, so test it with your own setup before relying on it in a live performance.

---

# RND Velocity – magyarul

Az **RND Velocity** egy Linuxon futó, Python és PySide6 alapú MIDI-velocity-randomizer és JACK MIDI patchbay. Grafikus felületet biztosít a velocity véletlenszerű módosításának beállításához és a MIDI-forgalom megfigyeléséhez. A rendszer JACK-kompatibilis MIDI-szerveréhez csatlakozik, beleértve a PipeWire JACK-kompatibilitást biztosító konfigurációkat is.

## Funkciók

- PySide6-alapú grafikus felület.
- JACK MIDI-bemenet és -kimenet.
- Beállítható velocity-tartomány és randomizálási viselkedés, többek között eloszlás, bias, maximális változás, intervallumeltolás és szélesség.
- A megjelenés testreszabásának lehetőségei.
- Opcionális terminálos hibakeresési kimenet és beépített naplóablak.
- Ablakelrendezési és megjelenési lehetőségek.

## Követelmények

- Linux működő JACK-kompatibilis MIDI-szerverrel (például JACK-kel vagy JACK-támogatást biztosító PipeWire-rel).
- Python 3.
- PySide6.
- A JACK-Client csomag által biztosított Python `jack` modul.

Az alkalmazás indítása előtt a MIDI-szervernek futnia kell, és a felhasználó számára elérhetőnek kell lennie.

## Indítás

Terminálban, abban a könyvtárban, ahol a `rnd_velocity.py` található:

```bash
python3 rnd_velocity.py
```

Ha az alkalmazás nem tud csatlakozni, ellenőrizd, hogy fut-e a JACK/PipeWire audioszerver, és elérhetők-e a MIDI-portjai.

## Beállítások

A beállítások a **Preferences** ablakban érhetők el. A program létrehozhat egy helyi `midi-randomize-preferences.json` fájlt a beállítások tárolására. Személyes beállításokat és gépspecifikus fájlokat csak akkor tölts fel nyilvánosan, ha szándékosan meg akarod osztani őket.

## Állapot

A projekt fejlesztés alatt áll. A hardverek, a Linux-disztribúciók és a MIDI-szerverek konfigurációja eltérhet, ezért élő előadás előtt a saját rendszereden is teszteld.
