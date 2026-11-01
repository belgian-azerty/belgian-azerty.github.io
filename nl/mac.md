<!-- Belgisch Apple-toetsenbord op Linux Mint en Zorin OS | https://belgian-azerty.github.io/nl/mac.html -->

# Een Belgisch Apple-toetsenbord

Op een Belgisch Apple-toetsenbord staan andere tekens dan op een pc-toetsenbord, bijvoorbeeld @ links van de 1. Met de
pc-indeling typen veel toetsen dan iets anders. Als je zo'n toetsenbord gebruikt, typ dan na de installatie:

```
sudo APPLE=yes be-azerty-fix system
```

Zijn de toets links van de 1 en de toets naast de linker Shift omgewisseld? Typ dan ook:

```
sudo be-azerty-fix apple-iso-keys on
```

**Goed om te weten**
- Option werkt als AltGr. Caps Lock werkt zoals op Linux.
- De instelling geldt voor elk toetsenbord op de computer, ook op het aanmeldscherm. Daarom weigert ze als er geen
  Apple-toetsenbord aangesloten is.
- Het tekstscherm en het ontgrendelscherm van de schijf houden de pc-indeling.
- **Nog niet getest op een echt Apple-toetsenbord.** In een testcontainer kwamen 333 van de 367 macOS-tekens overeen.
  Het verschil is Caps Lock, dat op een Mac anders werkt.

Terug naar een pc-toetsenbord: `sudo APPLE=no be-azerty-fix system`.

---

Gemaakt met AI-hulp (Claude). Niet verbonden aan Linux Mint of Zorin OS. Een klein vrijwilligersproject.
