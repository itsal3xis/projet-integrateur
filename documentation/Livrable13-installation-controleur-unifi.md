## Livrable13-installation-controleur-unifi.md

## 1. Objectif

Installer et configurer un contrôleur UniFi Network Server sur une machine virtuelle Linux, afin de permettre la gestion de points d’accès UniFi via une interface web.

---

## 2. Déploiement de la machine virtuelle

**Hyperviseur :** Esxi 
**Nom VM :** vm-s0-03  
**OS installé :** Ubuntu Server 24.04 LTS  
**Adresse IP statique :** 192.168.60.5/24  
**Passerelle :** 192.168.60.1  
**DNS :** 192.168.10.10

---

## 3. Installation du contrôleur UniFi

Le contrôleur UniFi Network Application a été installé en suivant la méthode recommandée par Ubiquiti pour Linux.  
Plutôt que de détailler toutes les commandes, nous avons utilisé le script et la documentation disponibles ici :

https://community.ui.com/questions/UniFi-OS-Server-Installation-Scripts-or-UniFi-Network-Application-Installation-Scripts-or-UniFi-Eas/ccbc7530-dd61-40a7-82ec-22b17f027776

L’installation inclut les dépendances requises et met en place le service UniFi de façon à ce qu’il démarre automatiquement au démarrage de la machine.

### Vérification du service

```bash
sudo systemctl status unifi
sudo systemctl is-enabled unifi
```

---

## 4. Configuration réseau

Les ports nécessaires au fonctionnement du contrôleur UniFi ont été ouverts sur la machine virtuelle :

- TCP 8443 : Interface web UniFi
- TCP 8080 : Adoption des équipements UniFi
- UDP 3478 : STUN (communication AP)
- UDP 10001 : Découverte des AP

L’interface web du contrôleur est accessible via l’URL suivante :
https://192.168.60.5:8443

---

## 5. Capture de l'écran d'accueil du controleur Unifi

![alt text](Controleurunifi.png)