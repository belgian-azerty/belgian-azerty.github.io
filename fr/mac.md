<!-- Clavier Apple belge sur Linux Mint et Zorin OS | https://belgian-azerty.github.io/fr/mac.html -->

# Un clavier Apple belge

Un clavier Apple belge ne porte pas les mêmes caractères qu'un clavier PC, par exemple @ à gauche du 1. Avec la
disposition PC, beaucoup de touches tapent alors autre chose. Si vous utilisez un tel clavier, tapez après
l'installation :

```
sudo APPLE=yes be-azerty-fix system
```

La touche à gauche du 1 et la touche à côté du Maj gauche sont inversées ? Tapez alors aussi :

```
sudo be-azerty-fix apple-iso-keys on
```

**Bon à savoir**
- Option fonctionne comme AltGr. Verr. Maj fonctionne comme sous Linux.
- Le réglage vaut pour tous les claviers de l'ordinateur, aussi sur l'écran de connexion. C'est pourquoi il refuse de
  s'appliquer si aucun clavier Apple n'est branché.
- L'écran texte et l'écran de déverrouillage du disque gardent la disposition PC.
- **Pas encore testé sur un vrai clavier Apple.** Dans un conteneur de test, 333 des 367 caractères de macOS
  correspondaient. La différence vient de Verr. Maj, qui fonctionne autrement sur un Mac.

Retour à un clavier PC : `sudo APPLE=no be-azerty-fix system`.

---

Réalisé avec l'aide de l'IA (Claude). Sans lien avec Linux Mint ni Zorin OS. Un petit projet bénévole.
