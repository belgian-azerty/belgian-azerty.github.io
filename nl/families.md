<!-- Belgisch AZERTY op Fedora, openSUSE, Arch en andere Linux | https://belgian-azerty.github.io/nl/families.html -->

# Belgisch AZERTY op vijf Linux-families

Dit project begon bij Linux Mint en Zorin OS. Nu zijn er ook bestanden voor de andere grote families van Linux. Het
staat niet overal even ver. Hieronder zie je per systeem hoe ver.

### Wat betekent de stand?

- **Uitgebracht:** er is een versie om te downloaden. Getest in emulators en op één echte laptop.
- **Getest in testcontainers:** getest in een afgesloten testsysteem zonder bureaublad. Er is nog niets om te
  downloaden: je bouwt het pakket zelf, met de stappen hieronder. Een test op een echt bureaublad volgt.
- **Script:** geen pakket, maar een klein script. Getest in testcontainers. Werkt alleen op bureaubladen met Wayland.

### Overal hetzelfde

Dezelfde drie keuzes als op Mint en Zorin: Caps Lock zoals op Windows, de accenten met Shift+AltGr zoals op Windows,
en de indeling voor een Belgisch Apple-toetsenbord. Ctrl+Alt als AltGr komt van keyd, met onze regels.

### Anders dan op Mint en Zorin

- Geen enkel bestand van het systeem verandert. Onze twee bestanden komen in de map `/etc/xkb`.
- De keuzes staan niet in de toetsenbordinstellingen van je bureaublad. Je zet ze aan met één commando (hieronder).
- Een X11-sessie en de tekstconsole lezen `/etc/xkb` niet. Daar verandert er niets.


## Ubuntu en Debian

**Linux Mint 22.3 en Zorin OS 18.1: uitgebracht (0.9.12).** [Naar installeren](https://belgian-azerty.github.io/nl/install.md)

**Ubuntu 24.04 en Debian 13: zelfde pakket, getest in testcontainers.** Ook het typen is getest, op een
GNOME-bureaublad zonder scherm: hetzelfde resultaat als op Mint en Zorin. Je volgt dezelfde stappen als op Mint. Op
Debian zit keyd al in het systeem: typ `sudo apt install keyd` in plaats van de PPA.

**Later naar Ubuntu 26.04, Linux Mint 23 of Debian 14?** Installeer eerst 0.9.12. Met 0.9.11 of ouder stopt de
upgrade halverwege. Getest met een volledige pakketupgrade in testcontainers, niet met de upgradeprogramma's van Ubuntu of
Mint zelf. [Wat als de upgrade al vastzit: Problemen](https://belgian-azerty.github.io/nl/problems.md)

## Fedora

**Fedora 44 en 45: getest in testcontainers. Fedora 45 ook op een bureaublad in een virtuele machine, met SELinux aan.**

Fedora heeft geen keyd. Daarom bouwen deze stappen ook keyd 2.6.0, ongewijzigd uit de officiële versie. Typ als
gewone gebruiker:

```
sudo dnf install rpm-build rpmdevtools gcc make kernel-headers systemd-rpm-macros git
git clone https://github.com/belgian-azerty/belgian-azerty-linux && cd belgian-azerty-linux
rpmdev-setuptree
for s in packaging/fedora/*.spec; do spectool -g -R "$s" && rpmbuild -ba "$s"; done
R=$(rpm --eval %_rpmdir); sudo dnf install $R/x86_64/keyd-2.6.0-*.rpm $R/noarch/*-0.9.12-*.rpm
```

Daarna, in dezelfde map: `sudo bash be-azerty-fix.sh system`. Dat zet Belgisch voorop voor het hele systeem en voor
de bewaarde GNOME-instellingen van je gebruikers.

**Goed om te weten:** op Fedora staat SELinux standaard aan. Ons pakket voegt daarom een kleine SELinux-regel toe,
zodat de toetsenborddienst onze bestanden mag lezen. Zonder die regel weigerde Fedora 45 elke indeling en bleef het
aanmeldscherm Amerikaans. Met de regel typte het aanmeldscherm Belgisch, met Caps Lock zoals op Windows, en
Ctrl+Alt+E gaf €. Getest in een virtuele machine op één laptop, niet op een echte pc.

## openSUSE

**Tumbleweed en Leap 16.0: getest in testcontainers. Leap 16.0 ook op een bureaublad in een virtuele machine, met SELinux aan.**

Nieuwe installaties van openSUSE gebruiken ook SELinux. Ons pakket voegt dezelfde kleine regel toe als op Fedora. Op
Leap 16.0 typte het aanmeldscherm daarna Belgisch, ook na een herstart. Tumbleweed met SELinux is nog niet getest.

openSUSE heeft keyd zelf. Typ als gewone gebruiker:

```
sudo zypper install rpm-build systemd-rpm-macros git curl
git clone https://github.com/belgian-azerty/belgian-azerty-linux && cd belgian-azerty-linux
SRC=$(rpm --eval %_sourcedir); mkdir -p "$SRC"
curl -L -o "$SRC"/belgian-azerty-linux-0.9.12.tar.gz https://github.com/belgian-azerty/belgian-azerty-linux/archive/refs/tags/v0.9.12.tar.gz
for s in packaging/opensuse/*.spec; do rpmbuild -ba "$s"; done
sudo zypper install --allow-unsigned-rpm $(rpm --eval %_rpmdir)/noarch/*-0.9.12-*.rpm
```

Zet daarna de keuzes aan (zie "Keuzes aanzetten" hieronder).

## Arch

**Arch Linux: getest in testcontainers, bureaubladtest volgt.**

Arch heeft keyd zelf. Typ als gewone gebruiker:

```
sudo pacman -S --needed base-devel git
git clone https://github.com/belgian-azerty/belgian-azerty-linux && cd belgian-azerty-linux/packaging/arch
(cd belgian-azerty-windows && makepkg -si)
(cd keyd-belgian-windows && makepkg -si)
```

Goed om te weten: ons keyd-pakket zet keyd meteen aan, want daarvoor installeer je het. Op Arch is dat ongewoon.

Zet daarna de keuzes aan (zie hieronder).

## Onafhankelijke systemen: Void, NixOS, Gentoo, Slackware, Solus

**Script: getest in testcontainers, X11 nog open.**

Hier is er geen pakket, maar een klein script. Het zet dezelfde twee bestanden in `/etc/xkb` en verandert niets aan
het systeem:

```
git clone https://github.com/belgian-azerty/belgian-azerty-linux && cd belgian-azerty-linux
sudo sh packaging/etc-xkb/be-azerty-etc-xkb.sh install
sh packaging/etc-xkb/be-azerty-etc-xkb.sh status
```

Weer weg: `sudo sh packaging/etc-xkb/be-azerty-etc-xkb.sh remove`. Dat haalt alleen onze twee bestanden weg.

**Goed om te weten**
- Getest met de toetsenbordbibliotheek en de toetsenborddata van elk systeem. Voor Slackware en Solus bestaat geen
  testcontainer: hun eigen pakketten zijn op een ander testsysteem gezet. Op Slackware 15.0 kon één controle niet
  draaien, omdat het testprogramma een nieuwere versie nodig heeft.
- Alleen voor bureaubladen met Wayland. Een X11-sessie leest `/etc/xkb` niet, en veel van deze systemen draaien nog
  X11 (Slackware 15.0 standaard). Een oplossing voor X11 is er nog niet.
- Het script zet keyd niet op. keyd zit in Void, NixOS en Solus; op Gentoo in de GURU-overlay, op Slackware op
  SlackBuilds.org. De regels voor keyd staan in `keyd/be-winaltgr.conf`. Dat is hier niet getest.
- Op NixOS beheert je configuratie de map `/etc`. Of een rebuild onze bestanden laat staan, is niet nagekeken.

## Keuzes aanzetten (openSUSE, Arch en de onafhankelijke systemen)

Voor het hele systeem, ook het aanmeldscherm en nieuwe gebruikers, als je systeem systemd heeft:

```
sudo localectl set-x11-keymap be pc105 "" caps:be_windows,be_azerty:accents
```

Getest in testcontainers. Zonder systemd zet je de keuzes in de toetsenbordinstelling van je bureaublad.

## Nog niet getest buiten Mint en Zorin

- Een bureaublad op Arch en op de onafhankelijke systemen. Het aanmeldscherm van GNOME is alleen getest op Fedora 45
  en Leap 16.0, in een virtuele machine. Voor KDE Plasma weten we het niet.
- keyd in dagelijks gebruik.
- De tekstconsole en het ontgrendelscherm van de schijf.
- Een echte installatie of een echte pc.

Alle details: [packaging/OTHER-DISTRIBUTIONS.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/packaging/OTHER-DISTRIBUTIONS.md) en [HOW-WE-TESTED.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/HOW-WE-TESTED.md).

**Werkt het bij jou, of net niet?** Laat het weten op [GitHub Discussions](https://github.com/belgian-azerty/belgian-azerty-linux/discussions). Elke test op een echte computer helpt.

---

Gemaakt met AI-hulp (Claude). Niet verbonden aan Linux Mint of Zorin OS. Een klein vrijwilligersproject.
