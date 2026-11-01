<!-- Live USB that starts with Belgian AZERTY (Mint and Zorin) | https://belgian-azerty.github.io/en/stick.html -->

# Try it on a USB stick first

A normal Mint stick starts with a US keyboard. A normal Zorin stick asks for a language first, but has no Belgian
choice: Nederlands gives you a US keyboard, Français a French one. It stays that way until you have installed Linux.
On our stick, the boot menu first asks for your language (Nederlands, Français, Deutsch, English) and then your
keyboard: Belgian AZERTY with a period or a comma on the numeric keypad. Our packages are already on it. If you install
from the stick, they come along.

**This is a stopgap.** It is needed until Mint and Zorin have a Belgian choice in their own boot menu. It is not our
own version of Mint or Zorin, and we are not affiliated with those projects.

**How do you make it?** You download the official ISO yourself, from linuxmint.com or zorin.com. Our tool changes only
the boot menu, the list of checksums, one extra file with our packages, and the `/belgian/` folder. Everything else is
the original system.

- **On Linux (or with WSL on Windows):** follow the [recipe in the README, under "Live USB"](https://github.com/belgian-azerty/belgian-azerty-linux#live-usb).
- **With Windows and Rufus only:** in preparation. The first test in the emulator passed. A test with a real stick is
  still to be done.

**Rather not use a stick?** That works too. Install Mint or Zorin as usual, then follow the install page. You only miss
the Belgian keyboard during the first few minutes.

---

Built with AI help (Claude). Not affiliated with Linux Mint or Zorin OS. A small volunteer project.
