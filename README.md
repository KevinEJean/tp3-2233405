# Description des services
### Portainer
Plateforme cloud pour gérer des opérations dans les environnements Kubernetes, Docker et Podman. Son but est de rendre la gestion de conteneur complexe plus simple. 

### NextCloud
Utilisé pour gérer des fichiers de façon privée. Il offre la synchronisation, partage et collaboration de fichier.

### Paperless
Permet de gérer des documents physique ou non-physique (PDF, images, etc.). Il peut lire, afficher, scanner, formuler des documents et fonctionne de facon autonome. Son but est de retirer le besoin de papier dans l'utilisation de document. Il utilise des images comme "gotenberg" et "tika" pour effectuer ses fonctions.

# Rôle de Traefik
Finalement, le reverse proxy (Traefik) est un outil qui gère le load balancing, certificats SSL/TLS, passerelle API. Dans ce cas, il dirige le trafic sur le port 443/80 vers le port du service demandé (ex.: requête sur portainer:443 ▶️ port:9000), cela pour éviter une congestion de service utilisant les même ports. Avec DuckDNS, il challenge l'utilisateur en lui demandant une preuve en quoi il est titulaire du domaine. Si oui, il est redirigé vers le bon port. Pour des raison de décurité, Traefik cache les ports et ip du domaine.

# Organisation générale
- <b>RESEAUX</b> : Chaque service communique dans un réseau interne (tp3-2233405_cloud) pour assurer le bon fonctionnement des API. Par contre, le service paperless à aussi besoin d'un réseau interne pour communiquer avec ses services (broker, db, tika, gotenberg), ce réseau doit être créer manuellement.
- <b>VOLUMES</b> : Base de donnee nextclouddb, les données gérées dans Portainer et les données des services Paperless.
- <b>ENV</b> : Nom du domaine, email et token associé au domaine ainsi que l'utilisateur, nom et mot de passe de la base de donnee.
