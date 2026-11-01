<!-- Je download controleren met SHA256SUMS | https://belgian-azerty.github.io/nl/verify.html -->

# Klopt je download?

Bij elke versie hoort een bestand **SHA256SUMS**. Daarin staat de vingerafdruk van elk bestand. Komt jouw vingerafdruk
overeen, dan is je bestand onderweg niet veranderd.

**Op Linux**, in de map met de bestanden:

```
sha256sum -c SHA256SUMS --ignore-missing
```

Elk bestand moet **OK** geven.

**Op Windows** (PowerShell), per bestand:

```
Get-FileHash .\belgian-azerty-windows_0.9.10_all.deb -Algorithm SHA256
```

Vergelijk de lange code met de regel voor dat bestand in SHA256SUMS.

**Komt het niet overeen?** Gebruik het bestand dan niet. Download het opnieuw van de [releasepagina](https://github.com/belgian-azerty/belgian-azerty-linux/releases/latest).

---

Gemaakt met AI-hulp (Claude). Niet verbonden aan Linux Mint of Zorin OS. Een klein vrijwilligersproject.
