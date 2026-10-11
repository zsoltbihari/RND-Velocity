RND Velocity – Launcher Script
===============================

FILES
-----
Keep rnd-velocity.sh in the same directory as rnd_velocity.py.

The script launches the program with Python 3. By default, it uses the
python3 command.

SETUP
-----
1. Open a terminal in the directory containing both files.
2. Make the launcher executable:

   chmod +x rnd-velocity.sh

USAGE
-----
Start the program:
   ./rnd-velocity.sh start

Stop the program:
   ./rnd-velocity.sh stop

Stop all detected RND Velocity instances:
   ./rnd-velocity.sh killall

Restart the program:
   ./rnd-velocity.sh restart

Check the status:
   ./rnd-velocity.sh status

Follow the live log:
   ./rnd-velocity.sh log

Running the script without an argument starts the program by default:

   ./rnd-velocity.sh

LOG AND STATE FILES
-------------------
Program log:
   ~/.local/state/rnd-velocity/rnd-velocity.log

Process ID (PID) file:
   ${XDG_RUNTIME_DIR:-$HOME/.local/run}/rnd-velocity/rnd-velocity.pid

The log can help diagnose startup errors in the Python application.

HOW IT WORKS
------------
- Checks that Python and rnd_velocity.py are available.
- Tries to prevent accidental multiple instances.
- Checks whether the process is still running after startup.
- Sends TERM first when stopping the program.
- If the process does not stop within 10 seconds, sends KILL.
- Removes stale PID files when detected.
- The killall command searches for identifiable Python command lines
  containing the full path to this rnd_velocity.py file and attempts to
  stop all matching instances.

IMPORTANT NOTES
---------------
1. The script does not install Python dependencies. Install any required
   packages according to the application's own documentation.
2. Run the script as your normal user, not with sudo, unless the program's
   documentation explicitly requires otherwise.
3. Closing the GUI window will stop the application correctly only if the
   Python program itself handles window closing and exits normally.
4. If the program does not start, inspect the log:

   ./rnd-velocity.sh log

   Or:

   tail -n 50 ~/.local/state/rnd-velocity/rnd-velocity.log

5. Keep rnd-velocity.sh in the same directory as rnd_velocity.py.
6. The script uses python3 by default. To specify another interpreter:

   PYTHON=/usr/bin/python3 ./rnd-velocity.sh start

7. The killall command is intended to target Python command lines containing
   the full path of this rnd_velocity.py file. It does not intentionally
   target unrelated Python programs.

TROUBLESHOOTING
---------------
“Permission denied”:
   Run chmod +x rnd-velocity.sh.

“Program file not found”:
   Check that rnd_velocity.py is in the same directory as the launcher.

The program exits immediately:
   Check the log file and confirm that all required Python dependencies
   are installed.

The program is running, but stop does not stop it:
   Check the status and log. The script only attempts to stop processes
   it identifies as instances of this application.

This launcher is designed for rnd_velocity.py. It does not modify the
Python application's internal code.


MAGYAR ÚTMUTATÓ
================

RND Velocity – indítószkript
=============================

FÁJLOK
------
A rnd-velocity.sh scriptet ugyanabba a könyvtárba tedd, ahol a
rnd_velocity.py található.

A script Python 3-mal indítja a programot. Alapértelmezés szerint a
python3 parancsot használja.

TELEPÍTÉS
---------
1. Nyiss terminált abban a könyvtárban, ahol a két fájl található.
2. Tedd futtathatóvá a scriptet:

   chmod +x rnd-velocity.sh

HASZNÁLAT
---------
Indítás:
   ./rnd-velocity.sh start

Leállítás:
   ./rnd-velocity.sh stop

Az összes azonosítható RND Velocity-példány leállítása:
   ./rnd-velocity.sh killall

Újraindítás:
   ./rnd-velocity.sh restart

Állapot ellenőrzése:
   ./rnd-velocity.sh status

Élő napló megtekintése:
   ./rnd-velocity.sh log

Ha argumentum nélkül futtatod, a script alapértelmezés szerint elindítja
a programot:

   ./rnd-velocity.sh

NAPLÓ- ÉS ÁLLAPOTFÁJLOK
-----------------------
A program naplója:
   ~/.local/state/rnd-velocity/rnd-velocity.log

A folyamat PID-fájlja:
   ${XDG_RUNTIME_DIR:-$HOME/.local/run}/rnd-velocity/rnd-velocity.pid

A napló segíthet a Python-program indulási hibáinak felderítésében.

MŰKÖDÉS
-------
- Ellenőrzi, hogy a Python és a rnd_velocity.py elérhető-e.
- Megpróbálja megakadályozni a program véletlen, többszörös indítását.
- Indítás után ellenőrzi, hogy a folyamat futva maradt-e.
- Leállításkor először TERM jelzést küld.
- Ha a folyamat 10 másodpercen belül nem áll le, KILL jelzést küld.
- Felismeréskor eltávolítja az elavult PID-fájlokat.
- A killall parancs megkeresi azokat a Python-folyamatokat, amelyek
  parancssorában szerepel a rnd_velocity.py fájl teljes elérési útja,
  és megpróbálja leállítani az összes ilyen példányt.

FONTOS MEGJEGYZÉSEK
-------------------
1. A script nem telepíti a Python-függőségeket. A szükséges csomagokat
   a program saját dokumentációja alapján telepítsd.
2. A scriptet normál felhasználóként futtasd, ne sudo-val, kivéve ha a
   program dokumentációja kifejezetten mást ír elő.
3. A grafikus ablak bezárógombja akkor állítja le megfelelően a programot,
   ha maga a Python-program szabályosan kezeli az ablak bezárását.
4. Ha a program nem indul el, nézd meg a naplót:

   ./rnd-velocity.sh log

   vagy:

   tail -n 50 ~/.local/state/rnd-velocity/rnd-velocity.log

5. A rnd-velocity.sh fájl maradjon ugyanabban a könyvtárban, mint a
   rnd_velocity.py.
6. A script alapértelmezés szerint a python3 parancsot használja.
   Másik interpreter megadásához például:

   PYTHON=/usr/bin/python3 ./rnd-velocity.sh start

7. A killall parancs a rnd_velocity.py teljes elérési útját tartalmazó
   Python-parancssorokat célozza. Nem szándékozik más Python-programokat
   leállítani.

HIBAELHÁRÍTÁS
-------------
„Permission denied”:
   Futtasd a chmod +x rnd-velocity.sh parancsot.

„Nem találom a programot”:
   Ellenőrizd, hogy a rnd_velocity.py ugyanabban a könyvtárban van-e.

A program azonnal leáll:
   Ellenőrizd a naplófájlt, és győződj meg róla, hogy minden szükséges
   Python-függőség telepítve van.

A program fut, de a stop parancs nem állítja le:
   Ellenőrizd az állapotot és a naplófájlt. A script csak az általa az
   alkalmazás példányaként azonosított folyamatokat próbálja leállítani.

Ez az indítószkript a rnd_velocity.py programhoz készült. A Python-program
belső kódját nem módosítja.
