### **Développement d'un Conteneur Fedora avec Docker**  

Si vous souhaitez créer et personnaliser un conteneur **Fedora** avec **Docker**, voici les étapes à suivre.  

---

## **1. Exécuter un conteneur Fedora simple**  
Si vous voulez simplement lancer une instance **Fedora** sans personnalisation, utilisez la commande suivante :  
```bash
docker run -it fedora /bin/bash
```
- `-it` : mode interactif (terminal).
- `fedora` : utilise la dernière version officielle de Fedora.
- `/bin/bash` : démarre le shell Bash à l’intérieur du conteneur.

Si vous souhaitez une version spécifique de **Fedora**, utilisez :  
```bash
docker run -it fedora:39 /bin/bash
```
(Ce qui lancera Fedora 39, par exemple).

---

## **2. Créer une Image Fedora Personnalisée avec un Dockerfile**  
Si vous souhaitez un environnement Fedora personnalisé, créez une image à partir d’un `Dockerfile`.  

### **Étapes pour créer l’image personnalisée**  

1. **Créer un répertoire de projet**  
   ```bash
   mkdir fedora-container && cd fedora-container
   ```
2. **Créer un fichier `Dockerfile`**  
   Créez un fichier `Dockerfile` et ajoutez le contenu suivant :  

   ```dockerfile
   # Utilisation de Fedora comme image de base
   FROM fedora:39

   # Passer en mode super-utilisateur
   USER root

   # Mettre à jour le système et installer des paquets essentiels
   RUN dnf update -y && dnf install -y \
       nano \
       git \
       curl \
       wget \
       vim \
       python3 \
       python3-pip && \
       dnf clean all

   # Définir un répertoire de travail dans le conteneur
   WORKDIR /app

   # Commande exécutée par défaut
   CMD ["/bin/bash"]
   ```

3. **Construire l’image Docker**  
   Exécutez la commande suivante pour construire l’image :  
   ```bash
   docker build -t my-fedora .
   ```

---

## **3. Exécuter le Conteneur Fedora Personnalisé**  
Après la construction de l’image, démarrez un conteneur basé sur celle-ci :  
```bash
docker run -it --name fedora-container my-fedora
```
- `-it` : mode interactif.
- `--name fedora-container` : nom du conteneur.
- `my-fedora` : nom de l’image construite précédemment.

---

## **4. Exécuter le Conteneur en Mode Détaché**  
Si vous souhaitez exécuter le conteneur en arrière-plan :  
```bash
docker run -d --name fedora-container my-fedora
```
Puis, pour y accéder :  
```bash
docker exec -it fedora-container /bin/bash
```

---

## **5. Gestion des Conteneurs Fedora**  
- **Arrêter un conteneur Fedora :**  
  ```bash
  docker stop fedora-container
  ```
- **Redémarrer le conteneur :**  
  ```bash
  docker start fedora-container
  ```
- **Supprimer un conteneur :**  
  ```bash
  docker rm fedora-container
  ```
- **Supprimer l’image Docker Fedora personnalisée :**  
  ```bash
  docker rmi my-fedora
  ```

---

## **6. Partager l’Image sur Docker Hub (Facultatif)**  
Si vous souhaitez partager votre image sur **Docker Hub**, suivez ces étapes :  

1. **Se connecter à Docker Hub :**  
   ```bash
   docker login
   ```
2. **Taguer l’image Docker pour Docker Hub :**  
   ```bash
   docker tag my-fedora yourusername/my-fedora:latest
   ```
3. **Pousser l’image sur Docker Hub :**  
   ```bash
   docker push yourusername/my-fedora:latest
   ```

---

### **💡 Résumé**
1. Exécuter Fedora avec `docker run fedora`.
2. Créer une image personnalisée avec un `Dockerfile`.
3. Installer des paquets essentiels avec `dnf`.
4. Gérer le conteneur Fedora (`start`, `stop`, `rm`).
5. Partager l’image sur **Docker Hub** si nécessaire.

🚀 Si vous avez besoin de plus de personnalisation, dites-moi ! 😊
