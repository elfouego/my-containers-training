# 🐳 Docker - Debian 13 Basique

## 📖 Description

Exercice pratique de construction d'une image Docker minimale basée sur **Debian 13 (Trixie)** avec une application **FastAPI** exposant un endpoint de santé `/health`.

## 🎯 Objectifs

- Construire une image Docker fonctionnelle et reproductible
- Installer uniquement les paquets nécessaires
- Réduire la taille de l'image (nettoyage des caches, couches optimisées)
- Appliquer des bonnes pratiques de sécurité (utilisateur non-root)

## 📁 Structure

```
01-debian13-basique/
├── dockerfile
└── app/
    ├── main.py
    └── requirements.txt
```

## 🚀 Installation et utilisation

```bash
# 1. Construire l'image
docker build -t fastapi-auto .

# 2. Lancer le conteneur
docker run -d -p 8000:8000 fastapi-auto

# 3. Tester
curl http://localhost:8000/health
# Réponse : {"status":"ok"}
```

## ⚙️ Commandes utiles

| Commande | Description |
|----------|-------------|
| `docker build -t fastapi-auto .` | Construire l'image |
| `docker run -d -p 8000:8000 fastapi-auto` | Lancer en arrière-plan |
| `docker run -it fastapi-auto bash` | Mode interactif |
| `docker images` | Lister les images |
| `docker ps` | Lister les conteneurs actifs |
| `docker logs <container_id>` | Voir les logs |
| `docker exec -it <container_id> bash` | Exécuter une commande |
| `docker rmi fastapi-auto` | Supprimer l'image |

## 🔍 Analyse avec Dive

```bash
# Installation
sudo snap install dive

# Analyse de l'image
dive fastapi-auto
```

## 💡 Bonnes pratiques appliquées

- ✅ Utilisateur non-root
- ✅ Regroupement des commandes RUN
- ✅ Nettoyage des caches apt
- ✅ `--no-cache-dir` pour pip
- ✅ Image légère et sécurisée

## 🚀 Pistes d'amélioration

- [ ] Passer à une image alpine
- [ ] Ajouter un healthcheck Docker
- [ ] Mettre en place un CI/CD
- [ ] Multi-stage builds

## 📚 Ressources

- [Guide d'origine](https://github.com/stephrobert/containers-training)
