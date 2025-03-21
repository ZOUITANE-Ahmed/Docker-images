# Docker-images

Docker est une plateforme open-source qui permet de créer, exécuter et déployer des applications dans des conteneurs (Containers). Cette technologie simplifie le développement et le déploiement en garantissant une compatibilité entre les environnements de développement, de test et de production.

## 🔹 **Concepts clés de Docker** :
1. **Conteneur (Container)** : Unité légère et autonome contenant tout ce dont une application a besoin pour fonctionner (librairies, dépendances, etc.).
2. **Image** : Un modèle immuable utilisé pour créer un conteneur.
3. **Dockerfile** : Un fichier contenant les instructions pour construire une image Docker personnalisée.
4. **Docker Compose** : Un outil permettant de gérer des applications multi-conteneurs à l’aide d’un fichier `docker-compose.yml`.
5. **Registry** : Un dépôt pour stocker les images Docker, comme Docker Hub ou un registre privé.

## 🔹 **Commandes Docker essentielles** :
1. **Lancer un conteneur** :  
   ```bash
   docker run -d -p 8080:80 nginx
   ```
   Lance un conteneur basé sur l’image `nginx`, en l’exécutant en arrière-plan et en mappant le port 8080 du système hôte au port 80 du conteneur.

2. **Lister les conteneurs en cours d’exécution** :
   ```bash
   docker ps
   ```

3. **Arrêter un conteneur** :
   ```bash
   docker stop container_id
   ```

4. **Créer une image à partir d’un `Dockerfile`** :
   ```bash
   docker build -t mon_image .
   ```

5. **Exécuter un conteneur en mode interactif** :
   ```bash
   docker run -it ubuntu bash
   ```
   Cela lance un conteneur Ubuntu et ouvre un terminal interactif à l’intérieur.

6. **Supprimer un conteneur** :
   ```bash
   docker rm container_id
   ```

7. **Supprimer une image** :
   ```bash
   docker rmi image_id
   ```

8. **Utiliser `docker-compose`** pour gérer plusieurs conteneurs :
   ```bash
   docker-compose up -d
   ```

## 🔹 **Cas d'utilisation de Docker** :
- Exécuter des applications dans des environnements isolés.
- Simplifier le déploiement et le passage d’une application d’un serveur à un autre.
- Gérer des services multiples dans un environnement de développement unifié.
- Faciliter le déploiement d’applications cloud et distribuées.
