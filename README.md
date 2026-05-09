# Description des services
### Portainer
Attribuer les donnes (portainer_data) dans la section 'volumes'.

### NextCloud
Creer le service nextcloud et nextclouddb, puis ajouter cette base de donne dans la section 'volumes'.

# Rôle de Traefik
Finallement, le reverse proxy (Trafeik) transforme les requetes 'HTTP' en requettes 'HTTPS' et demande a <i>Lets Encrypt</i> une certification SSL/TLS. Pour que <i>Lets Encrypt</i> obtient un certificats il faut specifier le dns (duckdns) et l'email, nom du domaine, token associer. Son role est de securiser les sites web en remplacent les ports avec un nom de domaine (dans ce cas 9000, 8081) et ajoutent une couche de securiter en demandant un certificat.

# Organisation générale (réseaux, volumes, variables d’environnement)
- RESEAUX : Chaque service communique dans un reseaux interne (tp3-2233405_cloud) pour assurer le bon fonctionnement des API. 
- VOLUMES : Base de donnee nextclouddb et les donnees gere dans Portainer.
- ENV : Nom du domaine, email et token associer au domaine ainsi que l'utilisateur, nom et mot de passe de la base de donnee.
