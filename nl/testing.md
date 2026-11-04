<!-- Wat is getest voor Mint 22.3 en Zorin 18.1 | https://belgian-azerty.github.io/nl/testing.html -->

# Wat is getest, en wat niet

**Getest**
- Linux Mint 22.3 en Zorin OS 18.1, in emulators en op één laptop (een Lenovo ThinkPad T14s).
- De wijzigingen van 0.9.10, 0.9.11 en 0.9.12 zelf: alleen in testcontainers. 0.9.12 typt hetzelfde als 0.9.11.
- Mint 0.9.9 als stick op de echte laptop (door Younes gemeld).
- Windows en Linux vergeleken: met beide accentopties komen 306 van de 308 Belgische Windows-tekens overeen. De
  laatste twee zijn AltGr+4 en AltGr+5, en die regelt keyd.
- Ubuntu 24.04 en Debian 13 in testcontainers, ook het typen op een GNOME-bureaublad zonder scherm: hetzelfde
  resultaat als op Mint en Zorin.
- Een volledige pakketupgrade van Ubuntu 24.04 naar 26.04 en van Debian 13 naar de volgende Debian, in testcontainers.
- Fedora, openSUSE, Arch, Void, NixOS, Gentoo, Slackware en Solus: in testcontainers, zonder bureaublad.
  [Vijf Linux-families](https://belgian-azerty.github.io/nl/families.md)
- Fedora 45 en openSUSE Leap 16.0 op een bureaublad in een virtuele machine, met SELinux aan: het aanmeldscherm typt
  Belgisch, met Caps Lock zoals op Windows.
- openSUSE Tumbleweed met KDE in een virtuele machine, met SELinux aan: het aanmeldscherm typt Belgisch, maar met
  Caps Lock op de Linux-manier (X11). Na het aanmelden zoals op Windows.

**Nog niet getest**
- Een echt Apple-toetsenbord.
- 0.9.10 tot 0.9.12, en Zorin 0.9.9, op echte hardware.
- De upgradeprogramma's van Ubuntu en Mint zelf.
- Andere systemen dan Mint en Zorin op een echt bureaublad of een echte pc.
- Een tweede USB-toetsenbord.

**Stand bij de Linux-projecten:** nog niets aanvaard. Welk deel bij welk project hoort, staat in [MAINTAINERS.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/MAINTAINERS.md).

Alle details, met de versie per test: [HOW-WE-TESTED.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/HOW-WE-TESTED.md).

**Meedoen?** Test mee of beantwoord de enquête op [GitHub Discussions](https://github.com/belgian-azerty/belgian-azerty-linux/discussions).

---

Gemaakt met AI-hulp (Claude). Niet verbonden aan Linux Mint of Zorin OS. Een klein vrijwilligersproject.
