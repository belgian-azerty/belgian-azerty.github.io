<!-- Installer sur Linux Mint 22.3 et Zorin OS 18.1 | https://belgian-azerty.github.io/fr/install.html -->

# Installer sur un système qui fonctionne déjà

Pour Linux Mint 22.3 et Zorin OS 18.1. Vous tapez trois fois quelque chose dans un terminal.

## Étape 1. Ajoutez keyd.

keyd est le programme qui fait fonctionner Ctrl+Alt comme AltGr. Ubuntu 24.04, la base de
Mint 22 et de Zorin 18, ne l'a pas. Le PPA keyd-team l'a. Ce PPA est tenu par le mainteneur du paquet keyd de Debian ;
il ne fait pas partie du projet keyd lui-même.

```
sudo add-apt-repository ppa:keyd-team/ppa
sudo apt update
sudo apt install keyd
```

## Étape 2. Installez nos deux paquets.

Téléchargez-les depuis la [page de la version 0.9.10](https://github.com/belgian-azerty/belgian-azerty-linux/releases/tag/v0.9.10) dans un dossier vide.
Ouvrez un terminal dans ce dossier et tapez :

```
sudo apt install ./keyd-belgian-windows_0.9.10_all.deb ./belgian-azerty-windows_0.9.10_all.deb
sudo be-azerty-fix system
```

Vous voulez une virgule sur le pavé numérique ? Tapez alors `sudo DECIMAL=comma be-azerty-fix system`.

## Étape 3. Déconnectez-vous et reconnectez-vous.

Avec `be-azerty-fix check`, vous voyez ce que dit chaque réglage.

**Vous préférez cliquer ?** Après l'installation, le menu contient **Clavier belge**. Vous y choisissez entre le profil
Windows et le profil Linux, avec un point ou une virgule.

**Bon à savoir**
- Les règles Ctrl+Alt valent pour tout clavier que vous branchez, aussi pour un clavier américain externe.
- Sur Zorin, Verr. Maj reste par défaut comme sous Linux. C'est dû à un défaut de GNOME dans les fenêtres de mot de
  passe. Vous pouvez activer vous-même le Verr. Maj de Windows. [Explication dans le README](https://github.com/belgian-azerty/belgian-azerty-linux#caps-lock-on-zorin)
- Tous les problèmes connus sont dans le [README, sous « Known issues »](https://github.com/belgian-azerty/belgian-azerty-linux#known-issues).

- [Vérifiez d'abord votre téléchargement](https://belgian-azerty.github.io/fr/verify.md)

---

Réalisé avec l'aide de l'IA (Claude). Sans lien avec Linux Mint ni Zorin OS. Un petit projet bénévole.
