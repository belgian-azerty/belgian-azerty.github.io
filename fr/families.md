<!-- AZERTY belge sur Fedora, openSUSE, Arch et d'autres Linux | https://belgian-azerty.github.io/fr/families.html -->

# L'AZERTY belge sur cinq familles Linux

Ce projet a commencé avec Linux Mint et Zorin OS. Il y a maintenant aussi des fichiers pour les autres grandes familles
de Linux. Tout n'en est pas au même point. Vous voyez ci-dessous où en est chaque système.

### Que veut dire la situation ?

- **Publié :** il y a une version à télécharger. Testé dans des émulateurs et sur un seul vrai ordinateur portable.
- **Paquet sur la page de la version :** des paquets prêts à télécharger. Testé en conteneurs de test et sur un
  bureau dans une machine virtuelle, pas encore sur un vrai PC.
- **Testé en conteneurs de test :** testé dans un système de test isolé, sans bureau. Il n'y a encore rien à
  télécharger : vous construisez le paquet vous-même, avec les étapes ci-dessous. Un test sur un vrai bureau suivra.
- **Script :** pas de paquet, mais un petit script. Testé en conteneurs de test.

### Partout pareil

Les trois mêmes choix que sur Mint et Zorin : Verr. Maj comme sous Windows, les accents avec Maj+AltGr comme sous
Windows, et la disposition pour un clavier Apple belge. Ctrl+Alt comme AltGr vient de keyd, avec nos règles.

### Différent de Mint et Zorin

- Aucun fichier du système ne change. Nos deux fichiers vont dans le dossier `/etc/xkb`.
- Les choix n'apparaissent pas dans les réglages du clavier de votre bureau. Vous les activez avec une seule commande
  (ci-dessous).
- Une session X11 ne lit pas `/etc/xkb`. À partir de la 0.9.13, le programme `be-azerty-x11-load` charge donc nos
  choix à la connexion. Testé sur Fedora 45 avec Xfce dans une machine virtuelle ; pas encore sur d'autres bureaux
  X11. L'écran de connexion sous X11 et la console texte gardent le comportement de Linux.


## Ubuntu et Debian

**Linux Mint 22.3 et Zorin OS 18.1 : publié (0.9.12).** [Vers l'installation](https://belgian-azerty.github.io/fr/install.md)

**Ubuntu 24.04 et Debian 13 : le même paquet, testé en conteneurs de test.** La frappe aussi a été testée, sur un
bureau GNOME sans écran : le même résultat que sur Mint et Zorin. Vous suivez les mêmes étapes que sur Mint. Debian a
keyd lui-même : tapez `sudo apt install keyd` au lieu d'utiliser le PPA.

**Plus tard vers Ubuntu 26.04, Linux Mint 23 ou Debian 14 ?** Installez d'abord la 0.9.12. Avec la 0.9.11 ou plus
ancienne, la mise à niveau s'arrête à mi-chemin. Testé avec une mise à niveau complète des paquets en conteneurs de
test, pas avec les outils de mise à niveau d'Ubuntu ou de Mint. [Si la mise à niveau est déjà bloquée : Problèmes](https://belgian-azerty.github.io/fr/problems.md)

**Sur Ubuntu 26.04 (GNOME 50) :** si vous changez un choix du clavier, par exemple Verr. Maj ou les accents,
déconnectez-vous puis reconnectez-vous. Ce n'est qu'après que le nouveau choix fonctionne. Vu dans un émulateur sur
l'ordinateur portable de test.

## Fedora

**Fedora 44 et 45 : paquet sur la page de la version. Testé en conteneurs de test. Fedora 45 aussi sur un bureau dans une machine virtuelle, avec SELinux activé.**

Téléchargez les trois fichiers pour votre Fedora depuis la [page de la version 0.9.13](https://github.com/belgian-azerty/belgian-azerty-linux/releases/tag/v0.9.13) dans un même dossier :
belgian-azerty-windows, keyd-belgian-windows et keyd. Fedora n'a pas keyd lui-même ; c'est keyd 2.6.0, inchangé par
rapport à la version officielle. Les paquets ne sont pas signés. Vérifiez-les donc d'abord, puis installez-les :

```
sha256sum -c --ignore-missing SHA256SUMS-rpm
sudo dnf install ./belgian-azerty-windows-0.9.13-1.fc45.noarch.rpm ./keyd-belgian-windows-0.9.13-1.fc45.noarch.rpm ./keyd-2.6.0-1.belgianazerty.fc45.x86_64.rpm
```

Sur Fedora 44, c'est `fc44` au lieu de `fc45`. Activez ensuite les choix (voir « Activer les choix » ci-dessous).
Vous préférez construire vous-même ? Les étapes sont dans [packaging/OTHER-DISTRIBUTIONS.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/packaging/OTHER-DISTRIBUTIONS.md).

**Bon à savoir :** sur Fedora, SELinux est activé par défaut. Notre paquet ajoute donc une petite règle SELinux qui
permet au service clavier de lire nos fichiers. Sans cette règle, Fedora 45 refusait toute disposition et l'écran de
connexion restait en américain. Avec la règle, l'écran de connexion a tapé en belge, avec Verr. Maj comme sous Windows,
et Ctrl+Alt+E a donné €. Testé dans une machine virtuelle sur un seul ordinateur portable, pas sur un vrai PC.

## openSUSE

**Tumbleweed et Leap 16.0 : paquet sur la page de la version. Testé en conteneurs de test, et les deux sur un bureau dans une machine virtuelle, avec SELinux activé.**

Les nouvelles installations d'openSUSE utilisent aussi SELinux. Le problème de Fedora ne s'est pas produit sur
openSUSE, mais notre paquet ajoute la même petite règle, et elle y fonctionne aussi. Sur Leap 16.0 (GNOME), l'écran de
connexion a tapé en belge, aussi après un redémarrage. Sur Tumbleweed (KDE), cela fonctionne aussi, mais sur l'écran
de connexion, Verr. Maj fonctionne encore à la manière de Linux : cet écran tourne sous X11. Après la connexion,
Verr. Maj fonctionne comme sous Windows.

openSUSE a keyd lui-même. Téléchargez les deux fichiers pour votre version depuis la [page de la version 0.9.13](https://github.com/belgian-azerty/belgian-azerty-linux/releases/tag/v0.9.13)
dans un même dossier. Les paquets ne sont pas signés. Vérifiez-les donc d'abord, puis installez-les :

```
sha256sum -c --ignore-missing SHA256SUMS-rpm
sudo zypper install --allow-unsigned-rpm ./belgian-azerty-windows-0.9.13-1.tumbleweed.noarch.rpm ./keyd-belgian-windows-0.9.13-1.tumbleweed.noarch.rpm
```

Sur Leap 16.0, c'est `leap16.0` au lieu de `tumbleweed`. Vous utilisez une session X11 ? Ajoutez alors
`--recommends` après `zypper install`, pour que les outils X11 soient installés aussi. Activez ensuite les choix (voir « Activer les choix »
ci-dessous). Vous préférez construire vous-même ? Les étapes sont dans [packaging/OTHER-DISTRIBUTIONS.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/packaging/OTHER-DISTRIBUTIONS.md).

## Arch

**Arch Linux : testé en conteneurs de test, test sur bureau à venir.**

Arch a keyd lui-même. Tapez en tant qu'utilisateur normal :

```
sudo pacman -S --needed base-devel git
git clone https://github.com/belgian-azerty/belgian-azerty-linux && cd belgian-azerty-linux/packaging/arch
(cd belgian-azerty-windows && makepkg -si)
(cd keyd-belgian-windows && makepkg -si)
```

Bon à savoir : notre paquet keyd active keyd tout de suite, car c'est pour cela que vous l'installez. Sur Arch, c'est
inhabituel. Vous utilisez une session X11 ? Installez alors aussi `xorg-xkbcomp` et `xorg-setxkbmap`.

Activez ensuite les choix (voir ci-dessous).

## Systèmes indépendants : Void, NixOS, Gentoo, Slackware, Solus

**Script : testé en conteneurs de test, aussi pour X11.**

Ici, pas de paquet, mais un petit script. Il met les deux mêmes fichiers dans `/etc/xkb` et ne change rien au
système :

```
git clone https://github.com/belgian-azerty/belgian-azerty-linux && cd belgian-azerty-linux
sudo sh packaging/etc-xkb/be-azerty-etc-xkb.sh install
sh packaging/etc-xkb/be-azerty-etc-xkb.sh status
```

Pour l'enlever : `sudo sh packaging/etc-xkb/be-azerty-etc-xkb.sh remove`. Cela n'enlève que nos deux fichiers.

**Bon à savoir**
- Testé avec la bibliothèque de clavier et les données de clavier de chaque système. Pour Slackware et Solus, il
  n'existe pas de conteneur de test : leurs propres paquets ont été mis sur un autre système de test. Sur Slackware
  15.0, un contrôle n'a pas pu tourner, car l'outil de test a besoin d'une version plus récente.
- Une session X11 ne lit pas `/etc/xkb`, et beaucoup de ces systèmes tournent encore sous X11 (Slackware 15.0 par
  défaut). À partir de la 0.9.13, le script installe donc aussi `be-azerty-x11-load`, qui charge nos choix à la
  connexion. Il a besoin de `xkbcli`, `xkbcomp` et `setxkbmap`. Testé en conteneurs de test ; une vraie session X11
  seulement sur Fedora 45, pas sur ces systèmes.
- Le script n'installe pas keyd. keyd se trouve dans Void, NixOS et Solus ; sur Gentoo dans l'overlay GURU, sur
  Slackware sur SlackBuilds.org. Les règles pour keyd sont dans `keyd/be-winaltgr.conf`. Cela n'a pas été testé ici.
- Sur NixOS, votre configuration gère le dossier `/etc`. Nous n'avons pas vérifié si une reconstruction laisse nos
  fichiers en place.

## Activer les choix (Fedora, openSUSE, Arch et les systèmes indépendants)

Pour tout le système, y compris l'écran de connexion et les nouveaux utilisateurs, si votre système a systemd :

```
sudo localectl set-x11-keymap be pc105 "" caps:be_windows,be_azerty:accents
```

Testé en conteneurs de test. Sans systemd, réglez les choix dans les réglages du clavier de votre bureau.

## Pas encore testé en dehors de Mint et Zorin

- Un bureau sur Arch et sur les systèmes indépendants. L'écran de connexion n'est testé que sur Fedora 45 et openSUSE,
  dans une machine virtuelle. KDE Plasma uniquement sur Tumbleweed.
- keyd au quotidien.
- La console texte et l'écran de déverrouillage du disque.
- Une vraie installation ou un vrai PC.

Tous les détails : [packaging/OTHER-DISTRIBUTIONS.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/packaging/OTHER-DISTRIBUTIONS.md) et [HOW-WE-TESTED.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/HOW-WE-TESTED.md).

**Ça marche chez vous, ou pas tout à fait ?** Dites-le sur [GitHub Discussions](https://github.com/belgian-azerty/belgian-azerty-linux/discussions). Chaque test sur un vrai ordinateur
aide.

---

Réalisé avec l'aide de l'IA (Claude). Sans lien avec Linux Mint ni Zorin OS. Un petit projet bénévole.
