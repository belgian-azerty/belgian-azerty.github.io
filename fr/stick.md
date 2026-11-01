<!-- Clé USB live qui démarre en AZERTY belge (Mint et Zorin) | https://belgian-azerty.github.io/fr/stick.html -->

# Essayer d'abord sur une clé USB

Une clé Mint ordinaire démarre avec un clavier américain. Une clé Zorin ordinaire demande d'abord une langue, mais n'a
pas de choix belge : avec Nederlands, vous obtenez un clavier américain, avec Français un clavier français. Cela reste
ainsi jusqu'à ce que vous ayez installé Linux. Sur notre clé, le menu de démarrage demande d'abord votre langue
(Nederlands, Français, Deutsch, English), puis votre clavier : AZERTY belge avec un point ou une virgule sur le pavé
numérique. Nos paquets sont déjà dedans. Si vous installez depuis la clé, ils sont installés aussi.

**C'est une solution provisoire.** Elle est nécessaire jusqu'à ce que Mint et Zorin aient eux-mêmes un choix belge dans
leur menu de démarrage. Ce n'est pas une version à nous de Mint ou de Zorin, et nous ne sommes pas liés à ces projets.

**Comment la créer ?** Vous téléchargez vous-même l'ISO officielle, sur linuxmint.com ou zorin.com. Notre outil ne
change que le menu de démarrage, la liste des sommes de contrôle, un fichier supplémentaire avec nos paquets et le
dossier `/belgian/`. Le reste est le système d'origine.

- **Sous Linux (ou avec WSL sous Windows) :** suivez la [recette du README, sous « Live USB »](https://github.com/belgian-azerty/belgian-azerty-linux#live-usb).
- **Uniquement avec Windows et Rufus :** en préparation. Le premier test dans l'émulateur a réussi. Un test avec une
  vraie clé reste à faire.

**Vous préférez sans clé ?** C'est possible aussi. Installez Mint ou Zorin comme d'habitude, puis suivez la page
d'installation. Vous n'aurez alors pas le clavier belge pendant les premières minutes, c'est tout.

---

Réalisé avec l'aide de l'IA (Claude). Sans lien avec Linux Mint ni Zorin OS. Un petit projet bénévole.
