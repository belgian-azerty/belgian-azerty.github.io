<!-- Problems and fixes: Belgian keyboard on Linux | https://belgian-azerty.github.io/en/problems.html -->

# Problems and fixes

These are the problems we have seen and tested ourselves, in the words you would type yourself. This applies to
Linux Mint 22.3 and Zorin OS 18.1. Nothing has been tested on other systems.

## Ctrl+Alt+é does not give @, and Ctrl+Alt+E does not give €

**Cause.** On Linux, only the AltGr key gives these characters. Ctrl+Alt does not, while on Windows it does.

**Fix.** Install keyd and our keyd-belgian-windows package. [Go to install](https://belgian-azerty.github.io/en/install.md)

**Tested:** in emulators for Mint and Zorin, and with the Zorin stick on one real laptop (version 0.9.8).

## AltGr+4 and AltGr+5 give ¼ and ½ instead of { and [

**Cause.** Linux's Belgian layout has different characters there than Windows.

**Fix.** The same keyd-belgian-windows package. [Go to install](https://belgian-azerty.github.io/en/install.md)

**Tested:** in the emulator on the test laptop (0.9.8 and 0.9.9).

## With Caps Lock on, the top row gives no digits

On Windows, the top row gives the digits 1 2 3 when Caps Lock is on. On Linux it does not.

**Fix.** Our belgian-azerty-windows package, then `sudo be-azerty-fix system`. On Mint the Windows Caps Lock is then
on. On Zorin you switch it on yourself with `sudo CAPS=windows be-azerty-fix system`.

**Watch out, on Zorin:** because of a GNOME bug, six keys can stop working after Caps Lock in a password field. Log
out and back in. [Explained in the README](https://github.com/belgian-azerty/belgian-azerty-linux#caps-lock-on-zorin)

**Tested:** in emulators.

## The login screen, a new user or a settings reset has no Belgian keyboard

**Cause.** Linux stores the layout in several places. Belgian is not first everywhere.

**Fix.** `sudo be-azerty-fix system` puts Belgian first in all of those places. Your other layouts stay.

**Tested:** in emulators: login screen, new users, settings reset, restart and a full system update.

## The numeric keypad types a period and you want a comma (or the other way round)

**Fix.** `sudo DECIMAL=comma be-azerty-fix system` for a comma, `sudo DECIMAL=period be-azerty-fix system` for a
period. Or choose it in the **Belgian keyboard** menu entry.

**Tested:** in emulators.

## The live USB or the installer starts without a Belgian keyboard

**Cause.** Mint starts with a US keyboard. Zorin asks for a language, but has no Belgian choice.

**Fix.** Our stick, or yourself in the boot menu: press `e` and add `keyboard-configuration/layoutcode=be` to the line
that starts with `linux`. [Go to the stick](https://belgian-azerty.github.io/en/stick.md)

**Tested:** in emulators (UEFI and BIOS), and on one real laptop: the Zorin stick (0.9.8) and the Mint stick (0.9.9,
reported by Younes).

**Not fixed yet:** on the first start, the installer's Wi-Fi password window once typed as a US keyboard. Not after a
restart.

## Shift+AltGr on ù, µ and = gives ǎ, ă or ȧ instead of ´, ` or ~

**Fix.** From 0.9.9 this happens by itself on a new install. If you come from 0.9.8, type
`sudo ACCENTS=windows be-azerty-fix system`.

**Tested:** in test containers and in the emulator on the test laptop.

## ´ then space gives ' instead of ´

**Fix.** `be-azerty-fix accent-space on` (no sudo), then log out and back in.

**Tested:** in GTK programs and in the Terminal of Mint and Zorin. Not tested in Qt programs or VS Code.

## The system shows an extra US layout (be,us)

This is not a bug in this project. The desktop itself adds it in Dutch and German sessions. No key switches to it, so
you keep typing Belgian.

---

Built with AI help (Claude). Not affiliated with Linux Mint or Zorin OS. A small volunteer project.
