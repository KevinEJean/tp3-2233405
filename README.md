# Description des services
### Portainer
Plateforme cloud pour gérer des opérations dans les environnements Kubernetes, Docker et Podman. Son but est de rendre la gestion de conteneur complexe plus simple. 

### NextCloud
Utilisé pour gérer des fichiers de façon privée. Il offre la synchronisation, partage et collaboration de fichier. 

# Rôle de Traefik
Finalement, le reverse proxy (Traefik) transforme les requêtes 'HTTP' en requêtes 'HTTPS' et demande à Let's Encrypt une certification SSL/TLS. Pour que Let's Encrypt obtienne un certificat, il faut spécifier le dns (duckdns), l'email, nom du domaine, token associé. Son rôle est de sécuriser les sites web en remplaçant les ports avec un nom de domaine (dans ce cas 9000, 8081) et ajoute une couche de sécurité en demandant un certificat. 

# Organisation générale (réseaux, volumes, variables d’environnement)
- <b>RESEAUX</b> : Chaque service communique dans un réseau interne (tp3-2233405_cloud) pour assurer le bon fonctionnement des API.
- <b>VOLUMES</b> : Base de donnee nextclouddb et les données gérées dans Portainer. 
- <b>ENV</b> : Nom du domaine, email et token associé au domaine ainsi que l'utilisateur, nom et mot de passe de la base de donnee.
