# Découverte de Dockge

Dockge est une application disponible sous forme de conteneur Docker qui vous permet de gérer vos conteneurs ou convertir des commandes `docker run` en fichier `docker-compose`.

Lien vers le Githhub du développeur : <https://github.com/louislam/dockge?tab=readme-ov-file>

## Installation

Lien vers la vidéo Youtube : <https://youtu.be/9eiJ1azxrto>

### Prérequis : création des répertoires NFS dans lesquels nous stockerons les data de l'application ainsi que les stacks

On se connecte sur notre serveur NFS en SSH et on execute les commandes suivantes :

```bash
sudo mkdir -p /srv/no-raid/nfs1/docker/dockge/data
sudo mkdir -p /srv/raid/nfs/docker/docker/dockge/stacks
```

### Configuration du conteneur

Le fichier docker-compose est accessible ici : <https://github.com/lucduke/portainer/blob/main/stack/dockge.yml>

Les paramètres correspondants aux variables employées dans le fichier docker-compose sont les suivantes :

```env
port=5001
address=nas.home
path_nfs_data=":/srv/no-raid/nfs1/docker/dockge/data"
path_nfs_stacks=":/srv/raid/nfs/docker/docker/dockge/stacks"
```

## Lancement de l'application

Pour se connecter à Dockge, il suffit d'ouvrir le lien suivant sur votre navigateur : <http://VOTRE-IP:5001>

Lors de la 1ère connexion, vous devez choisir votre langue, un nom d'utilisateur et un mot de passe.
