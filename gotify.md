# Découverte de Gotify

Gotify est une application de serveur de notification open source qui permet aux développeurs de mettre en place leur propre serveur de notifications pour envoyer des messages à des clients ou des applications. Il offre une alternative autohébergée aux services de notification cloud tiers.

Lien vers le site web : <https://gotify.net/>

## Installation

Lien vers la vidéo Youtube : <https://>

### Prérequis : création du répertoire NFS dans lequel nous stockerons les data de l'application

On se connecte sur notre serveur NFS en SSH et on execute les commandes suivantes :

```bash
sudo mkdir -p /srv/raid/nfs/docker/docker/gotify/data
```

### Configuration du conteneur

Le fichier docker-compose est accessible ici : <https://github.com/lucduke/portainer/blob/main/stack/gotify.yml>

Les paramètres correspondants aux variables employées dans le fichier docker-compose sont les suivantes :

```env
port=4080
username=admin
password=azerty1234@
address=nas.home
path_nfs_data=":/srv/raid/nfs/docker/docker/gotify/data"
```

## Lancement de l'application

Pour se connecter à Gotify, il suffit d'ouvrir le lien suivant sur votre navigateur : <http://VOTRE-IP:4080>

## Exemple d'intégration dans un script bash

```bash
#!/bin/bash

GOTIFY_URL="http://votre-serveur-gotify"
GOTIFY_TOKEN="votre-token"

MESSAGE="Ceci est un exemple de notification Gotify depuis un script Bash."

# Utilisation de curl pour envoyer la notification
curl -X POST "$GOTIFY_URL/message?token=$GOTIFY_TOKEN" \
     -F "title=Titre de la notification" \
     -F "message=$MESSAGE"
```
