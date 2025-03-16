# linux fedora dns-http-dhcp-......-package-downlaod-commandes-
Configuration de base et DNS sous Linux Fedora
1. Configuration du réseau
Modifier les fichiers de configuration du réseau :


vi /etc/sysconfig/network
Ajouter le nom d’hôte :


hostname=baitam
Configurer l’interface réseau :


vi /etc/sysconfig/network-scripts/ifcfg-eth0
Exemple de configuration :


ONBOOT=YES
IPADDR=192.168.10.10
NETMASK=255.255.255.0
GATEWAY=192.168.10.11
DNS1=8.8.8.8
DNS2=8.8.4.4
2. Installation de Bind
Vérifier si Bind est installé :


rpm -qa | grep bind
Si ce n’est pas le cas, installer Bind :


rpm -ivh bind-****
3. Configuration du serveur DNS
Modifier le fichier de configuration principal


vi /etc/named.conf
Définir les zones DNS :


zone "formation.ma" IN {
    type master;
    file "formation.dir";
};

zone "5.168.192.in-addr.arpa" IN {
    type master;
    file "formation.inv";
};
Configurer la zone directe


vi /var/named/formation.dir
Exemple de configuration :


$TTL 86400
@   IN  SOA server.formation.ma. root.formation.ma. (
        01 ; Serial
        10800 ; Refresh
        3600  ; Retry
        604800 ; Expire
        38400 ; Minimum
)
@   IN  NS  server.formation.ma.
Server  IN  A   192.168.5.2
Configurer la zone inverse


vi /var/named/formation.inv
Exemple de configuration :



$TTL 86400
@   IN  SOA server.formation.ma. root.formation.ma. (
        01 ; Serial
        10800 ; Refresh
        3600  ; Retry
        604800 ; Expire
        38400 ; Minimum
)
@   IN  NS  server.formation.ma.
2   IN  PTR server.formation.ma.
4. Redémarrer le service Bind


service named restart
