# Livrable 11 – Installation et configuration du routeur pare-feu virtuel

## 4. Documentation des paramètres du routeur

---

## Informations générales du routeur

- **Nom de la machine** : RT-S0-01.corp.alrian.store
- **Rôle** : Routeur et pare-feu principal de l’entreprise
- **Logiciel** : pfSense Community Edition
- **Version installée** : 2.7.0
- **Type de déploiement** : Machine virtuelle
- **Hyperviseur** : VMware ESXi

---

## Configuration des interfaces réseau

| Interface pfSense | Réseau associé      | Adresse IP          | Passerelle        |
|------------------|--------------------|---------------------|-------------------|
| WAN (vmx2)       | FAI                | 206.167.46.22/24    | 206.167.46.1      |
| LAN (vmx0)       | Corpo HQ           | 192.168.10.1/24     | —                 |
| OPT1 (vmx1)      | Wi-Fi public       | 192.168.100.1/24    | —                 |
| OPT2 (vmx3)      | IoT                | 192.168.50.1/24     | —                 |
| OPT3 (vmx4)      | Wi-Fi corporatif   | 192.168.110.1/24    | —                 |
| OPT4 (vmx5)      | Management (Admin) | 192.168.60.1/24     | —                 |
| OPT5 (vmx6)      | Succursale LVL     | 192.168.30.1/24     | —                 |
| OPT6 (vmx7)      | VPN                | 192.168.120.1/24    | —                 |
| OPT7 (vmx8)      | DMZ                | 192.168.40.1/24     | —                 |
| OPT8 (vmx9)      | Succursale MTL     | 192.168.20.1/24     | —                 |

Chaque réseau est associé à une interface dédiée sur pfSense afin d’assurer une segmentation claire et sécurisée, conforme au plan d’adressage IP.

---

## Configuration des services

### DHCP
- Le service DHCP est activé sur les réseaux suivants :
  - Corpo HQ
  - Succursale MTL
  - Succursale LVL
  - IoT
  - Wi-Fi public
  - Wi-Fi corporatif
  - VPN
- Les plages DHCP respectent le plan d’adressage défini dans le livrable 6.
- Les serveurs et équipements critiques utilisent des adresses IP statiques.

### DNS
- pfSense agit comme **serveur DNS interne et relais** pour les réseaux internes.
- Les requêtes DNS des clients internes sont résolues :
  - Localement par pfSense si des host overrides sont configurés (noms internes testés)
  - Sinon, pfSense relaie les requêtes vers des serveurs DNS publics (ex: 8.8.8.8, 1.1.1.1)
- Les paramètres DNS sont distribués automatiquement aux clients via **DHCP**.
- Forwarding Mode est activé pour permettre la résolution des noms externes.
- Tests de vérification :
  - `www.google.com` → résolu correctement en IPv4 et IPv6
  - Serveur utilisé pour la résolution : pfSense (127.0.0.1)

### Routage inter-VLAN
- Le routage entre les VLANs est assuré par pfSense.
- Les communications inter-réseaux sont contrôlées par des règles de pare-feu.
- Aucune règle autorisant l’accès TCP 80 ou 443 n’est configurée sur l’interface WAN.

---

## Accès distant

- **Interface Web pfSense (HTTPS)** :
  - Accessible uniquement depuis le réseau Management (VLAN 60).
  - Accès sécurisé via HTTPS.
- **SSH** :
  - Activé pour l’administration distante.
  - Accès restreint au réseau Management.

---

## Sauvegarde de la configuration

- Le mot de passe du compte **admin** est sauvegardé dans **Bitwarden**.
- La configuration complète de pfSense est exportée au format **XML**.
- Le fichier d’export est déposé dans le dépôt GitLab, dossier **documentation**.

