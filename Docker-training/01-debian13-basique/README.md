# 01-debian13-basique

## Description du projet

Ce dépôt contient un exercice pratique pour construire une image Docker minimale basée sur Debian 13. L'objectif principal était d'apprendre, par la pratique, les étapes concrètes pour produire une image légère, sécurisée et réutilisable : rédaction d'un Dockerfile, installation minimale de paquets, gestion des couches, nettoyage et tests basiques.

## Objectifs

- Construire une image Docker fonctionnelle et reproductible basée sur Debian 13.
- Installer uniquement les paquets nécessaires et documenter pourquoi ils sont présents.
- Réduire la taille de l'image en limitant les couches et en nettoyant les caches temporaires.
- Appliquer des bonnes pratiques de sécurité (utilisateur non-root, least privilege).
- Donner des commandes claires pour construire, tester et déboguer l'image localement.


## Commandes utilisées (exemples)

- Construire l'image :

	docker build -t mon-image-debian13 .

- Construire en mode nettoyage de cache (recommandé pour tests reproductibles) :

	docker build --no-cache -t mon-image-debian13 .

- Lister les images :

	docker images

- Lancer un conteneur interactif :

	docker run --rm -it mon-image-debian13 /bin/bash

- Lancer en détaché avec restriction de ressources (exemple) :

	docker run -d --name debian13 --memory=256m --cpus=0.5 mon-image-debian13

- Exécuter une commande dans un conteneur existant :

	docker exec -it <container_id> /bin/bash

- Supprimer une image :

	docker rmi mon-image-debian13


## Ce que j'ai appris

- Rédiger un Dockerfile lisible et reproductible : ordre des instructions, utilisation de ARG/ENV et documentation inline.
- Minimiser la taille d'image : combiner RUN quand c'est pertinent, nettoyer apt caches (apt-get clean && rm -rf /var/lib/apt/lists/*), et préférer des images parent légères.
- Sécurité et permissions : créer et utiliser un utilisateur non-root dans l'image, limiter les capacités et éviter d'exposer inutilement des ports.
- Tests basiques : démarrer un conteneur, vérifier que les services et binaires attendus sont présents, valider que l'image fonctionne avec --no-cache.
- Bonnes pratiques supplémentaires : pinning des versions de paquets pour reproductibilité, commentaires expliquant pourquoi chaque paquet est installé, et envisager multi-stage build pour les images contenant des artefacts buildés.


## Remarques et pistes d'amélioration

Pour retrouver la méthodologie suivie, voir aussi le guide d'origine qui m'a aidé : https://github.com/stephrobert/containers-training/blob/main/00-Docker/01-debian12-basique/01-contruction-1ere-image.md

``` 
