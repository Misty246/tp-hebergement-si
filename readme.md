bite
# Utiliser l'image officielle Node.js (version LTS recommandée)
FROM node:18-alpine

# Créer le répertoire de l'application
WORKDIR /app

# Télécharger et extraire la dernière version de Wiki.js
RUN wget -O wiki.tar.gz https://github.com/Requarks/wiki/releases/latest/download/wiki-js.tar.gz && \
    tar xzf wiki.tar.gz && \
    rm wiki.tar.gz

# Copier le fichier de configuration par défaut
RUN cp config.sample.yml config.yml

# Exposer le port sur lequel écoute Wiki-JS
EXPOSE 3000

# Démarrer l'application
CMD ["node", "server.js"]
