<!-- Belgisch AZERTY op Fedora, openSUSE, Arch en andere Linux | https://belgian-azerty.github.io/nl/families.html -->

# Belgisch AZERTY op vijf Linux-families

Dit project begon bij Linux Mint en Zorin OS. Nu zijn er ook bestanden voor de andere grote families van Linux. Het
staat niet overal even ver. Hieronder zie je per systeem hoe ver.

### Wat betekent de stand?

- **Uitgebracht:** er is een versie om te downloaden. Getest in emulators en op één echte laptop.
- **Pakket op de releasepagina:** kant-en-klare pakketten om te downloaden. Getest in testcontainers en op een
  bureaublad in een virtuele machine, nog niet op een echte pc.
- **Getest in testcontainers:** getest in een afgesloten testsysteem zonder bureaublad. Er is nog niets om te
  downloaden: je bouwt het pakket zelf, met de stappen hieronder. Een test op een echt bureaublad volgt.
- **Script:** geen pakket, maar een klein script. Getest in testcontainers.

### Overal hetzelfde

Dezelfde drie keuzes als op Mint en Zorin: Caps Lock zoals op Windows, de accenten met Shift+AltGr zoals op Windows,
en de indeling voor een Belgisch Apple-toetsenbord. Ctrl+Alt als AltGr komt van keyd, met onze regels.

### Anders dan op Mint en Zorin

- Geen enkel bestand van het systeem verandert. Onze twee bestanden komen in de map `/etc/xkb`.
- De keuzes staan niet in de toetsenbordinstellingen van je bureaublad. Je zet ze aan met één commando (hieronder).
- Een X11-sessie leest `/etc/xkb` niet. Vanaf 0.9.13 laadt het programma `be-azerty-x11-load` onze keuzes daarom bij
  het aanmelden. Getest op Fedora 45 met Xfce in een virtuele machine; andere X11-bureaubladen nog niet. Het
  aanmeldscherm op X11 en de tekstconsole houden het Linux-gedrag.


## Ubuntu en Debian

**Linux Mint 22.3 en Zorin OS 18.1: uitgebracht (0.9.12).** [Naar installeren](https://belgian-azerty.github.io/nl/install.md)

**Ubuntu 24.04 en Debian 13: zelfde pakket, getest in testcontainers.** Ook het typen is getest, op een
GNOME-bureaublad zonder scherm: hetzelfde resultaat als op Mint en Zorin. Je volgt dezelfde stappen als op Mint. Op
Debian zit keyd al in het systeem: typ `sudo apt install keyd` in plaats van de PPA.

**Later naar Ubuntu 26.04, Linux Mint 23 of Debian 14?** Installeer eerst 0.9.12. Met 0.9.11 of ouder stopt de
upgrade halverwege. Getest met een volledige pakketupgrade in testcontainers, niet met de upgradeprogramma's van Ubuntu of
Mint zelf. [Wat als de upgrade al vastzit: Problemen](https://belgian-azerty.github.io/nl/problems.md)

**Op Ubuntu 26.04 (GNOME 50):** verander je een toetsenbordkeuze, bijvoorbeeld Caps Lock of de accenten, meld je dan
af en weer aan. Pas daarna werkt de nieuwe keuze. Gezien in een emulator op de testlaptop.

## Fedora

**Fedora 44 en 45: pakket op de releasepagina. Getest in testcontainers. Fedora 45 ook op een bureaublad in een virtuele machine, met SELinux aan.**

Download de drie bestanden voor jouw Fedora van de [releasepagina van 0.9.13](https://github.com/belgian-azerty/belgian-azerty-linux/releases/tag/v0.9.13) in één map: belgian-azerty-windows,
keyd-belgian-windows en keyd. Fedora heeft zelf geen keyd; dit is keyd 2.6.0, ongewijzigd uit de officiële versie.
De pakketten zijn niet ondertekend. Controleer ze daarom eerst, en installeer ze dan:

```
sha256sum -c --ignore-missing SHA256SUMS-rpm
sudo dnf install ./belgian-azerty-windows-0.9.13-1.fc45.noarch.rpm ./keyd-belgian-windows-0.9.13-1.fc45.noarch.rpm ./keyd-2.6.0-1.belgianazerty.fc45.x86_64.rpm
```

Op Fedora 44 staat er `fc44` in plaats van `fc45`. Zet daarna de keuzes aan (zie "Keuzes aanzetten" hieronder).
Liever zelf bouwen? De stappen staan in [packaging/OTHER-DISTRIBUTIONS.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/packaging/OTHER-DISTRIBUTIONS.md).

**Goed om te weten:** op Fedora staat SELinux standaard aan. Ons pakket voegt daarom een kleine SELinux-regel toe,
zodat de toetsenborddienst onze bestanden mag lezen. Zonder die regel weigerde Fedora 45 elke indeling en bleef het
aanmeldscherm Amerikaans. Met de regel typte het aanmeldscherm Belgisch, met Caps Lock zoals op Windows, en
Ctrl+Alt+E gaf €. Getest in een virtuele machine op één laptop, niet op een echte pc.

## openSUSE

**Tumbleweed en Leap 16.0: pakket op de releasepagina. Getest in testcontainers, en allebei op een bureaublad in een virtuele machine, met SELinux aan.**

Nieuwe installaties van openSUSE gebruiken ook SELinux. Het probleem van Fedora trad op openSUSE niet op, maar ons
pakket voegt dezelfde kleine regel toe, en die werkt er ook. Op Leap 16.0 (GNOME) typte het aanmeldscherm Belgisch,
ook na een herstart. Op Tumbleweed (KDE) werkt het ook, maar op het aanmeldscherm werkt Caps Lock nog op de
Linux-manier: dat scherm draait op X11. Na het aanmelden werkt Caps Lock zoals op Windows.

openSUSE heeft keyd zelf. Download de twee bestanden voor jouw versie van de [releasepagina van 0.9.13](https://github.com/belgian-azerty/belgian-azerty-linux/releases/tag/v0.9.13) in één map.
De pakketten zijn niet ondertekend. Controleer ze daarom eerst, en installeer ze dan:

```
sha256sum -c --ignore-missing SHA256SUMS-rpm
sudo zypper install --allow-unsigned-rpm ./belgian-azerty-windows-0.9.13-1.tumbleweed.noarch.rpm ./keyd-belgian-windows-0.9.13-1.tumbleweed.noarch.rpm
```

Op Leap 16.0 staat er `leap16.0` in plaats van `tumbleweed`. Gebruik je een X11-sessie? Zet dan `--recommends`
achter `zypper install`, zodat de hulpprogramma's voor X11 meekomen. Zet daarna de keuzes aan (zie "Keuzes aanzetten"
hieronder). Liever zelf bouwen? De stappen staan in [packaging/OTHER-DISTRIBUTIONS.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/packaging/OTHER-DISTRIBUTIONS.md).

## Arch

**Arch Linux: getest in testcontainers, bureaubladtest volgt.**

Arch heeft keyd zelf. Typ als gewone gebruiker:

```
sudo pacman -S --needed base-devel git
git clone https://github.com/belgian-azerty/belgian-azerty-linux && cd belgian-azerty-linux/packaging/arch
(cd belgian-azerty-windows && makepkg -si)
(cd keyd-belgian-windows && makepkg -si)
```

Goed om te weten: ons keyd-pakket zet keyd meteen aan, want daarvoor installeer je het. Op Arch is dat ongewoon. Gebruik je een X11-sessie? Installeer dan ook `xorg-xkbcomp` en
`xorg-setxkbmap`.

Zet daarna de keuzes aan (zie hieronder).

## Onafhankelijke systemen: Void, NixOS, Gentoo, Slackware, Solus

**Script: getest in testcontainers, ook voor X11.**

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
- Een X11-sessie leest `/etc/xkb` niet, en veel van deze systemen draaien nog X11 (Slackware 15.0 standaard). Vanaf
  0.9.13 zet het script daarom ook `be-azerty-x11-load` klaar, dat onze keuzes bij het aanmelden laadt. Het heeft
  `xkbcli`, `xkbcomp` en `setxkbmap` nodig. Getest in testcontainers; een echte X11-sessie alleen op Fedora 45, niet
  op deze systemen.
- Het script zet keyd niet op. keyd zit in Void, NixOS en Solus; op Gentoo in de GURU-overlay, op Slackware op
  SlackBuilds.org. De regels voor keyd staan in `keyd/be-winaltgr.conf`. Dat is hier niet getest.
- Op NixOS beheert je configuratie de map `/etc`. Of een rebuild onze bestanden laat staan, is niet nagekeken.

## Keuzes aanzetten (Fedora, openSUSE, Arch en de onafhankelijke systemen)

Voor het hele systeem, ook het aanmeldscherm en nieuwe gebruikers, als je systeem systemd heeft:

```
sudo localectl set-x11-keymap be pc105 "" caps:be_windows,be_azerty:accents
```

Getest in testcontainers. Zonder systemd zet je de keuzes in de toetsenbordinstelling van je bureaublad.

## Nog niet getest buiten Mint en Zorin

- Een bureaublad op Arch en op de onafhankelijke systemen. Het aanmeldscherm is alleen getest op Fedora 45 en
  openSUSE, in een virtuele machine. KDE Plasma alleen op Tumbleweed.
- keyd in dagelijks gebruik.
- De tekstconsole en het ontgrendelscherm van de schijf.
- Een echte installatie of een echte pc.

Alle details: [packaging/OTHER-DISTRIBUTIONS.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/packaging/OTHER-DISTRIBUTIONS.md) en [HOW-WE-TESTED.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/HOW-WE-TESTED.md).

**Werkt het bij jou, of net niet?** Laat het weten op [GitHub Discussions](https://github.com/belgian-azerty/belgian-azerty-linux/discussions). Elke test op een echte computer helpt.

---

Gemaakt met AI-hulp (Claude). Niet verbonden aan Linux Mint of Zorin OS. Een klein vrijwilligersproject.
