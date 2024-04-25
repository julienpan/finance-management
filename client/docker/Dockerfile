# Utiliser l'image Node.js
FROM node:alpine as build

# Définir le répertoire de travail
WORKDIR /app

# Copier les fichiers du projet dans le répertoire de travail
COPY ./ /app

# Installer les dépendances et construire l'application
RUN npm install
RUN npm run build

# Utiliser une image légère pour servir l'application
FROM nginx:alpine

# Copier les fichiers de build de l'application dans le répertoire de travail de Nginx
COPY --from=build /app/build /usr/share/nginx/html

# Exposer le port 80
EXPOSE 80

# Commande de démarrage pour Nginx
CMD ["nginx", "-g", "daemon off;"]
