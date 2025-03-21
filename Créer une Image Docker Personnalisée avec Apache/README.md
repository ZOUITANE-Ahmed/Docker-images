### **Déploiement d’Apache sur un Conteneur Docker** 🚀  

Dans ce guide, nous allons créer et exécuter un serveur **Apache (HTTPD)** dans un conteneur **Docker** basé sur Fedora ou une autre distribution comme Debian.

---

## **1️⃣ Exécuter un Conteneur avec Apache sans Dockerfile**  
Si vous souhaitez exécuter rapidement **Apache**, vous pouvez utiliser une image officielle comme `httpd` :  

```bash
docker run -d --name apache-container -p 8080:80 httpd:latest
```
- `-d` : Exécute le conteneur en arrière-plan.
- `--name apache-container` : Nom du conteneur.
- `-p 8080:80` : Associe le port **8080** du système hôte au port **80** du conteneur.
- `httpd:latest` : Utilise l’image officielle **Apache HTTPD**.

Une fois exécuté, ouvrez un navigateur et accédez à :  
👉 **http://localhost:8080**  

---

## **2️⃣ Créer une Image Docker Personnalisée avec Apache**  
Si vous voulez une configuration personnalisée, créez votre propre image Docker avec **Fedora** et **Apache**.

### **📌 Étape 1 : Créer un Répertoire de Projet**  
```bash
mkdir apache-fedora && cd apache-fedora
```

### **📌 Étape 2 : Créer un Fichier `Dockerfile`**  
Créez un fichier `Dockerfile` et ajoutez le contenu suivant :  

```dockerfile
# Utiliser Fedora comme image de base
FROM fedora:39

# Installer Apache HTTPD
RUN dnf install -y httpd && \
    dnf clean all

# Copier la page HTML personnalisée
COPY index.html /var/www/html/index.html

# Ouvrir le port 80
EXPOSE 80

# Démarrer Apache en arrière-plan
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
```

---

### **📌 Étape 3 : Ajouter une Page Web Personnalisée**  
Créez un fichier `index.html` dans le même dossier :  

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Serveur Apache sur Docker</title>
</head>
<body>
    <h1>Bienvenue sur Apache dans Docker 🚀</h1>
    <p>Ceci est un serveur web Apache fonctionnant dans un conteneur Docker.</p>
</body>
</html>
```

---

### **📌 Étape 4 : Construire l’Image Docker**  
Lancez la commande suivante pour construire l’image :  
```bash
docker build -t apache-fedora .
```

---

### **📌 Étape 5 : Exécuter le Conteneur Apache**  
Démarrez le conteneur avec :  
```bash
docker run -d -p 8080:80 --name apache-fedora-container apache-fedora
```

- Accédez à **http://localhost:8080** pour voir votre page HTML.  

---

## **3️⃣ Gestion du Conteneur Apache**  
- **Arrêter le conteneur**  
  ```bash
  docker stop apache-fedora-container
  ```
- **Relancer le conteneur**  
  ```bash
  docker start apache-fedora-container
  ```
- **Supprimer le conteneur**  
  ```bash
  docker rm apache-fedora-container
  ```
- **Supprimer l’image personnalisée**  
  ```bash
  docker rmi apache-fedora
  ```

---

### **✅ Conclusion**  
Nous avons vu deux méthodes :  
1. **Utiliser une image Apache prête à l’emploi** (`httpd`).  
2. **Créer une image personnalisée avec Fedora et Apache**.  
