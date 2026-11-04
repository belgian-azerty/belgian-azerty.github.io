<!-- Ce qui est testé pour Mint 22.3 et Zorin 18.1 | https://belgian-azerty.github.io/fr/testing.html -->

# Ce qui est testé, et ce qui ne l'est pas

**Testé**
- Linux Mint 22.3 et Zorin OS 18.1, dans des émulateurs et sur un seul ordinateur portable (un Lenovo ThinkPad T14s).
- Les changements des versions 0.9.10, 0.9.11 et 0.9.12 elles-mêmes : uniquement en conteneurs de test. La 0.9.12
  tape la même chose que la 0.9.11.
- Mint 0.9.9 sur clé USB sur le vrai ordinateur portable (signalé par Younes).
- Windows et Linux comparés : avec les deux options d'accents, 306 des 308 caractères belges de Windows correspondent.
  Les deux derniers sont AltGr+4 et AltGr+5, et keyd s'en charge.
- Ubuntu 24.04 et Debian 13 en conteneurs de test, y compris la frappe sur un bureau GNOME sans écran : le même
  résultat que sur Mint et Zorin.
- Une mise à niveau complète des paquets d'Ubuntu 24.04 vers 26.04 et de Debian 13 vers la prochaine Debian, en
  conteneurs de test.
- Fedora, openSUSE, Arch, Void, NixOS, Gentoo, Slackware et Solus : en conteneurs de test, sans bureau.
  [Cinq familles Linux](https://belgian-azerty.github.io/fr/families.md)
- Fedora 45 sur un bureau dans un émulateur : la frappe fonctionne comme sur Mint, mais SELinux bloque le réglage
  clavier du système. Correction à venir.

**Pas encore testé**
- Un vrai clavier Apple.
- Les versions 0.9.10 à 0.9.12, et Zorin 0.9.9, sur du vrai matériel.
- Les outils de mise à niveau d'Ubuntu et de Mint eux-mêmes.
- D'autres systèmes que Mint et Zorin sur un vrai bureau ou un vrai PC.
- Un deuxième clavier USB.

**Situation auprès des projets Linux :** rien n'est encore accepté. Quelle partie revient à quel projet : voir
[MAINTAINERS.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/MAINTAINERS.md).

Tous les détails, avec la version de chaque test : [HOW-WE-TESTED.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/HOW-WE-TESTED.md).

**Envie de participer ?** Testez avec nous ou répondez au sondage sur [GitHub Discussions](https://github.com/belgian-azerty/belgian-azerty-linux/discussions).

---

Réalisé avec l'aide de l'IA (Claude). Sans lien avec Linux Mint ni Zorin OS. Un petit projet bénévole.
