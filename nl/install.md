<!-- Installeren op Linux Mint 22.3 en Zorin OS 18.1 | https://belgian-azerty.github.io/nl/install.html -->

# Installeren op een systeem dat al draait

Dit is voor Linux Mint 22.3 en Zorin OS 18.1. Je typt drie keer iets in een terminal. Een ander systeem? [Vijf Linux-families](https://belgian-azerty.github.io/nl/families.md)

## Stap 1. Voeg keyd toe.

keyd is het programma dat Ctrl+Alt als AltGr laat werken. Ubuntu 24.04, de basis van Mint 22
en Zorin 18, heeft het niet. De keyd-team PPA heeft het wel. Die PPA wordt onderhouden door de maintainer van Debians
keyd-pakket; ze hoort niet bij het keyd-project zelf.

```
sudo add-apt-repository ppa:keyd-team/ppa
sudo apt update
sudo apt install keyd
```

## Stap 2. Installeer onze twee pakketten.

Download ze van de [releasepagina van 0.9.12](https://github.com/belgian-azerty/belgian-azerty-linux/releases/tag/v0.9.12) in een lege map. Open daar een
terminal en typ:

```
sudo apt install ./keyd-belgian-windows_0.9.12_all.deb ./belgian-azerty-windows_0.9.12_all.deb
sudo be-azerty-fix system
```

Wil je een komma op het numeriek klavier, typ dan `sudo DECIMAL=comma be-azerty-fix system`.

## Stap 3. Meld je af en weer aan.

Met `be-azerty-fix check` zie je wat elke instelling zegt.

**Liever klikken?** Na de installatie staat **Belgisch toetsenbord** in het menu. Daar kies je tussen het
Windows-profiel en het Linux-profiel, met een punt of een komma.

**Goed om te weten**
- De Ctrl+Alt-regels gelden voor elk toetsenbord dat je aansluit, ook voor een extern Amerikaans toetsenbord.
- Op Zorin blijft Caps Lock standaard zoals op Linux. Dat komt door een fout in GNOME met wachtwoordvensters. Je kunt
  de Windows-Caps Lock zelf aanzetten. [Uitleg in de README](https://github.com/belgian-azerty/belgian-azerty-linux#caps-lock-on-zorin)
- Ga je later naar Linux Mint 23 of Ubuntu 26.04? Installeer dan eerst 0.9.12. Met 0.9.11 of ouder stopt de upgrade
  halverwege.
- Alle bekende problemen staan in de [README, onder "Known issues"](https://github.com/belgian-azerty/belgian-azerty-linux#known-issues).

- [Controleer eerst je download](https://belgian-azerty.github.io/nl/verify.md)

---

Gemaakt met AI-hulp (Claude). Niet verbonden aan Linux Mint of Zorin OS. Een klein vrijwilligersproject.
