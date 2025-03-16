# linux fedora dns-http-dhcp-......-package-downlaod-commandes-
Configuration DNS sous Linux Fedora
Introduction
Ce projet décrit la mise en place d’un serveur DNS sur Linux Fedora en utilisant Bind. Il inclut la configuration du réseau, l’installation des paquets nécessaires et la configuration des zones DNS, aussi bien directes qu’inverses.

Configuration du Réseau
La configuration réseau commence par la définition du nom d’hôte et des paramètres IP. L’interface réseau est paramétrée avec une adresse IP statique, un masque de sous-réseau, une passerelle et des serveurs DNS publics.

Installation de Bind
L’installation du service DNS se fait en vérifiant d’abord sa présence dans le système. Si nécessaire, Bind est installé depuis les paquets RPM. Une fois installé, il peut être configuré pour gérer les zones DNS.

Configuration des Zones DNS
Deux types de zones sont définis :

La zone directe, qui associe des noms de domaine à des adresses IP.
La zone inverse, qui permet la résolution inverse, en associant des adresses IP à des noms de domaine.
Les fichiers de configuration contiennent les informations sur le serveur DNS, les enregistrements SOA (Start of Authority), les serveurs de noms (NS) et les correspondances entre noms et adresses IP.

Redémarrage et Test du Serveur DNS
Après la configuration, le service Bind est redémarré pour appliquer les modifications. La résolution DNS peut être testée en interrogeant le serveur avec des outils comme nslookup ou dig.

Conclusion
Cette configuration permet d’héberger un serveur DNS fonctionnel sous Linux Fedora, facilitant la gestion des noms de domaine au sein d’un réseau local ou d’une infrastructure plus large
