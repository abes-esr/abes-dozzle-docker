# abes-dozzle-docker

Dozzle est un visualiseur de logs léger et open source conçu spécifiquement pour surveiller et déboguer les conteneurs Docker.

##  Installation

### 1. Configuration de l'environnement
Ce déploiement utilise des variables pour limiter les ressources allouées au conteneur.

1. Clonez ce dépôt.

2. Utilisez le fichier `.env-dist` mis à disposition ; il contient les variables utiles au bon fonctionnement du conteneur.
```bash
## Resources allocation
DOZZLE_MEM_LIMIT=5g
DOZZLE_MEMSWAP_LIMIT=5g
DOZZLE_CPU_LIMIT=5
``` 

### 3. Lancement
Démarrez le service en arrière-plan à l'aide de Docker Compose :
```bash
docker compose up -d
```

L'interface web de Dozzle est accessible à l'adresse `http://localhost:29999` ou via l'IP de votre serveur en cas de déploiement. 

---

##  Détails de la configuration

Le fichier `docker-compose.yml` configure les éléments clés suivants :

* **Accès au socket Docker :** Le volume `/var/run/docker.sock` permet à Dozzle de détecter automatiquement tous les autres conteneurs présents sur l'hôte et de lire leurs logs en temps réel.
* **Ports exposés :**
* `29999:8080` : Port principal pour accéder au tableau de bord web.
* `2375:2375` : Port exposé pour la communication avec des démons Docker distants (si nécessaire).

---

* **Arrêter le container :**
```bash
docker compose down
```
