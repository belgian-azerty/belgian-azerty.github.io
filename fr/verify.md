<!-- Vérifier votre téléchargement avec SHA256SUMS | https://belgian-azerty.github.io/fr/verify.html -->

# Votre téléchargement est-il correct ?

Chaque version est accompagnée d'un fichier **SHA256SUMS**. Il contient l'empreinte de chaque fichier. Si votre
empreinte correspond, votre fichier n'a pas été modifié en chemin.

**Sous Linux**, dans le dossier qui contient les fichiers :

```
sha256sum -c SHA256SUMS --ignore-missing
```

Chaque fichier doit afficher **OK**.

**Sous Windows** (PowerShell), fichier par fichier :

```
Get-FileHash .\belgian-azerty-windows_0.9.12_all.deb -Algorithm SHA256
```

Comparez le long code avec la ligne de ce fichier dans SHA256SUMS.

**Ça ne correspond pas ?** N'utilisez pas le fichier. Téléchargez-le à nouveau depuis la [page de la version](https://github.com/belgian-azerty/belgian-azerty-linux/releases/latest).

---

Réalisé avec l'aide de l'IA (Claude). Sans lien avec Linux Mint ni Zorin OS. Un petit projet bénévole.
