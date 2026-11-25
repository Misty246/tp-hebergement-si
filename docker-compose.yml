version: '3.8'

services:
  # ---------------------------------------------------------------------------
  # Service de Base de Données (MySQL) requis par WordPress
  # ---------------------------------------------------------------------------
  db:
    image: mysql:5.7
    container_name: wp_db
    restart: always
    # Variables d'environnement pour configurer l'accès à la base de données
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wpuser
      MYSQL_PASSWORD: wppassword
    # Volume persistant pour s'assurer que les données de la BDD ne sont pas perdues
    volumes:
      - db_data:/var/lib/mysql

  # ---------------------------------------------------------------------------
  # Service WordPress (Application Web)
  # ---------------------------------------------------------------------------
  wordpress:
    image: wordpress:latest
    container_name: wp_app
    restart: always
    # Redirection du port 80 de la machine hôte vers le port 80 du conteneur
    ports:
      - "80:80"
    # Configuration de la connexion entre WordPress et le conteneur de base de données
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_NAME: wordpress
      WORDPRESS_DB_USER: wpuser
      WORDPRESS_DB_PASSWORD: wppassword
    # Volume pour assurer la persistance des fichiers du site WordPress
    volumes:
      - wp_data:/var/www/html

# -----------------------------------------------------------------------------
# Déclaration des volumes nommés pour la persistance des données
# -----------------------------------------------------------------------------
volumes:
  db_data:
  wp_data:
