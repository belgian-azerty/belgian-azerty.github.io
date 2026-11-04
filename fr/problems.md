<!-- Problèmes et solutions : clavier belge sous Linux | https://belgian-azerty.github.io/fr/problems.html -->

# Problèmes et solutions

Voici les problèmes que nous avons vus et testés nous-mêmes, dans les mots que vous taperiez vous-même. Cela vaut pour
Linux Mint 22.3 et Zorin OS 18.1. Pour d'autres systèmes : [Cinq familles Linux](https://belgian-azerty.github.io/fr/families.md)

## Ctrl+Alt+é ne donne pas @, et Ctrl+Alt+E ne donne pas €

**Cause.** Sous Linux, seule la touche AltGr donne ces caractères. Ctrl+Alt ne le fait pas, alors que sous Windows oui.

**Solution.** Installez keyd et notre paquet keyd-belgian-windows. [Vers l'installation](https://belgian-azerty.github.io/fr/install.md)

**Testé :** dans des émulateurs pour Mint et Zorin, et avec la clé Zorin sur un vrai ordinateur portable (version 0.9.8).

## AltGr+4 et AltGr+5 donnent ¼ et ½ au lieu de { et [

**Cause.** La disposition belge de Linux a d'autres caractères à ces endroits que Windows.

**Solution.** Le même paquet keyd-belgian-windows. [Vers l'installation](https://belgian-azerty.github.io/fr/install.md)

**Testé :** dans l'émulateur sur l'ordinateur de test (0.9.8 et 0.9.9).

## Avec Verr. Maj activé, la rangée du haut ne donne pas les chiffres

Sous Windows, la rangée du haut donne les chiffres 1 2 3 quand Verr. Maj est activé. Sous Linux, non.

**Solution.** Notre paquet belgian-azerty-windows, puis `sudo be-azerty-fix system`. Sur Mint, le Verr. Maj de
Windows est alors activé. Sur Zorin, vous l'activez vous-même avec `sudo CAPS=windows be-azerty-fix system`.

**Attention, sur Zorin :** à cause d'un défaut de GNOME, six touches peuvent s'arrêter après Verr. Maj dans un champ de
mot de passe. Déconnectez-vous puis reconnectez-vous. [Explication dans le README](https://github.com/belgian-azerty/belgian-azerty-linux#caps-lock-on-zorin)

**Testé :** dans des émulateurs.

## L'écran de connexion, un nouvel utilisateur ou une réinitialisation n'a pas le clavier belge

**Cause.** Linux enregistre la disposition à plusieurs endroits. Le belge n'est pas en premier partout.

**Solution.** `sudo be-azerty-fix system` met le belge en premier à tous ces endroits. Vos autres dispositions restent.

**Testé :** dans des émulateurs : écran de connexion, nouveaux utilisateurs, réinitialisation des réglages,
redémarrage et mise à jour complète du système.

## Le pavé numérique tape un point et vous voulez une virgule (ou l'inverse)

**Solution.** `sudo DECIMAL=comma be-azerty-fix system` pour une virgule, `sudo DECIMAL=period be-azerty-fix system`
pour un point. Ou choisissez-le dans l'entrée de menu **Clavier belge**.

**Testé :** dans des émulateurs.

## La mise à niveau vers Ubuntu 26.04, Linux Mint 23 ou Debian 14 s'arrête à mi-chemin

**Cause.** Cette mise à niveau transforme le dossier du clavier en lien. Avec la 0.9.11 ou plus ancienne, deux
fichiers de notre paquet s'y trouvent encore, et la mise à niveau refuse.

**Avant.** Installez d'abord la 0.9.12. Elle met ses fichiers de côté un instant, puis les remet en place.

**Déjà bloqué ?** Tapez :
```
sudo dpkg -r belgian-azerty-windows
sudo apt -f install
sudo apt full-upgrade
```
Installez ensuite la 0.9.12 et tapez `sudo be-azerty-fix system`.

**Testé :** en conteneurs de test (Ubuntu 24.04 vers 26.04, Debian 13 vers la prochaine Debian). Pas avec les
outils de mise à niveau d'Ubuntu ou de Mint eux-mêmes.

## La clé USB live ou l'installateur démarre sans clavier belge

**Cause.** Mint démarre avec un clavier américain. Zorin demande une langue, mais n'a pas de choix belge.

**Solution.** Notre clé, ou vous-même dans le menu de démarrage : appuyez sur `e` et ajoutez
`keyboard-configuration/layoutcode=be` à la ligne qui commence par `linux`. [Vers la clé USB](https://belgian-azerty.github.io/fr/stick.md)

**Testé :** dans des émulateurs (UEFI et BIOS), et sur un vrai ordinateur portable : la clé Zorin (0.9.8) et la clé
Mint (0.9.9, signalé par Younes).

**Pas encore résolu :** au premier démarrage, la fenêtre du mot de passe Wi-Fi de l'installateur a tapé une fois comme
un clavier américain. Plus après un redémarrage.

## Maj+AltGr sur ù, µ et = donne ǎ, ă ou ȧ au lieu de ´, ` ou ~

**Solution.** Depuis la 0.9.9, c'est automatique pour une nouvelle installation. Si vous venez de la 0.9.8, tapez
`sudo ACCENTS=windows be-azerty-fix system`.

**Testé :** dans des conteneurs de test et dans l'émulateur sur l'ordinateur de test.

## ´ puis espace donne ' au lieu de ´

**Solution.** `be-azerty-fix accent-space on` (sans sudo), puis déconnectez-vous et reconnectez-vous.

**Testé :** dans les programmes GTK et dans le Terminal de Mint et de Zorin. Pas testé dans les programmes Qt ni dans
VS Code.

## Le système affiche une disposition américaine en plus (be,us)

Ce n'est pas un défaut de ce projet. Le bureau lui-même l'ajoute dans les sessions en néerlandais et en allemand.
Aucune touche ne bascule vers elle, vous continuez donc à taper en belge.

---

Réalisé avec l'aide de l'IA (Claude). Sans lien avec Linux Mint ni Zorin OS. Un petit projet bénévole.
