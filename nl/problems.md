<!-- Problemen en oplossingen: Belgisch toetsenbord op Linux | https://belgian-azerty.github.io/nl/problems.html -->

# Problemen en oplossingen

Hier staan de problemen die we zelf gezien en getest hebben, in de woorden die je zelf zou typen. Dit geldt voor
Linux Mint 22.3 en Zorin OS 18.1. Voor andere systemen: [Vijf Linux-families](https://belgian-azerty.github.io/nl/families.md)

## Ctrl+Alt+é geeft geen @, en Ctrl+Alt+E geeft geen €

**Oorzaak.** Op Linux werkt alleen de AltGr-toets voor die tekens. Ctrl+Alt doet dat niet, zoals op Windows wel.

**Oplossing.** Installeer keyd en ons pakket keyd-belgian-windows. [Naar installeren](https://belgian-azerty.github.io/nl/install.md)

**Getest:** in emulators voor Mint en Zorin, en met de Zorin-stick op één echte laptop (versie 0.9.8).

## AltGr+4 en AltGr+5 geven ¼ en ½ in plaats van { en [

**Oorzaak.** De Belgische indeling van Linux heeft daar andere tekens dan Windows.

**Oplossing.** Hetzelfde pakket keyd-belgian-windows. [Naar installeren](https://belgian-azerty.github.io/nl/install.md)

**Getest:** in de emulator op de testlaptop (0.9.8 en 0.9.9).

## Met Caps Lock aan geeft de bovenste rij geen cijfers

Op Windows geeft de bovenste rij met Caps Lock aan de cijfers 1 2 3. Op Linux niet.

**Oplossing.** Ons pakket belgian-azerty-windows en daarna `sudo be-azerty-fix system`. Op Mint staat de
Windows-Caps Lock dan aan. Op Zorin zet je hem zelf aan met `sudo CAPS=windows be-azerty-fix system`.

**Let op, op Zorin:** door een fout in GNOME kunnen zes toetsen stoppen na Caps Lock in een wachtwoordveld. Meld je
dan af en weer aan. [Uitleg in de README](https://github.com/belgian-azerty/belgian-azerty-linux#caps-lock-on-zorin)

**Getest:** in emulators.

## Het aanmeldscherm, een nieuwe gebruiker of een reset krijgt geen Belgisch toetsenbord

**Oorzaak.** Linux bewaart de indeling op meerdere plaatsen. Niet overal staat Belgisch voorop.

**Oplossing.** `sudo be-azerty-fix system` zet Belgisch voorop op al die plaatsen. Je andere indelingen blijven staan.

**Getest:** in emulators: aanmeldscherm, nieuwe gebruikers, reset van de instellingen, herstart en een volledige
systeemupdate.

## Het numeriek klavier typt een punt en je wilt een komma (of omgekeerd)

**Oplossing.** `sudo DECIMAL=comma be-azerty-fix system` voor een komma, `sudo DECIMAL=period be-azerty-fix system`
voor een punt. Of kies het in het menu-item **Belgisch toetsenbord**.

**Getest:** in emulators.

## De upgrade naar Ubuntu 26.04, Linux Mint 23 of Debian 14 stopt halverwege

**Oorzaak.** Die upgrade maakt van de toetsenbordmap een link. Met 0.9.11 of ouder staan daar nog twee bestanden
van ons pakket, en dan weigert de upgrade.

**Vooraf.** Installeer eerst 0.9.12. Die zet zijn bestanden even opzij en daarna terug.

**Zit de upgrade al vast?** Typ:
```
sudo dpkg -r belgian-azerty-windows
sudo apt -f install
sudo apt full-upgrade
```
Installeer daarna 0.9.12 en typ `sudo be-azerty-fix system`.

**Getest:** in testcontainers (Ubuntu 24.04 naar 26.04, Debian 13 naar de volgende Debian). Niet met de
upgradeprogramma's van Ubuntu of Mint zelf.

## De live-USB of het installatieprogramma start zonder Belgisch toetsenbord

**Oorzaak.** Mint start met een Amerikaans toetsenbord. Zorin vraagt een taal, maar heeft geen Belgische keuze.

**Oplossing.** Onze stick, of zelf in het startmenu: druk op `e` en zet `keyboard-configuration/layoutcode=be` achter de
regel die met `linux` begint. [Naar de stick](https://belgian-azerty.github.io/nl/stick.md)

**Getest:** in emulators (UEFI en BIOS), en op één echte laptop: de Zorin-stick (0.9.8) en de Mint-stick (0.9.9, door
Younes gemeld).

**Nog niet opgelost:** bij de eerste start typte het wifi-wachtwoordvenster van het installatieprogramma één keer als
een Amerikaans toetsenbord. Na een herstart niet meer.

## Shift+AltGr op ù, µ en = geeft ǎ, ă of ȧ in plaats van ´, ` of ~

**Oplossing.** Vanaf 0.9.9 gebeurt dit vanzelf bij een nieuwe installatie. Kom je van 0.9.8, typ dan
`sudo ACCENTS=windows be-azerty-fix system`.

**Getest:** in testcontainers en in de emulator op de testlaptop.

## ´ en dan spatie geeft ' in plaats van ´

**Oplossing.** `be-azerty-fix accent-space on` (zonder sudo), daarna afmelden en weer aanmelden.

**Getest:** in GTK-programma's en in de Terminal van Mint en Zorin. Niet getest in Qt-programma's en VS Code.

## Het systeem toont een extra Amerikaanse indeling (be,us)

Dat is geen fout van dit project. De desktop zelf voegt die toe in Nederlandse en Duitse sessies. Geen enkele toets
schakelt ernaar, dus je blijft Belgisch typen.

---

Gemaakt met AI-hulp (Claude). Niet verbonden aan Linux Mint of Zorin OS. Een klein vrijwilligersproject.
