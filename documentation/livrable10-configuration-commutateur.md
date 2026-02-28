# Livrable 10 – Configuration initiale du commutateur

## 1. Informations générales

- **Modèle et version du firmware** : Cisco Catalyst 2960, firmware 15.2
- **Nom du commutateur (hostname)** : SW-S0-01
- **Adresse IP de gestion** : 192.168.60.2 /24 (VLAN Management 60)
- **Passerelle par défaut** : 192.168.60.1
- **Serveurs DNS** : 8.8.8.8, 1.1.1.1
- **Mode d’administration** : Console, SSH

---

## 2. Configuration des VLANs

### Liste des VLANs créés (VLANs du siège social et autres nécessaires)

| VLAN ID | Nom du VLAN       | CIDR             |
|---------|-----------------|----------------|
| 10      | Corpo HQ        | 192.168.10.0/24 |
| 20      | Succursale MTL  | 192.168.20.0/24 |
| 30      | Succursale LVL  | 192.168.30.0/24 |
| 40      | DMZ             | 192.168.40.0/24 |
| 50      | IoT             | 192.168.50.0/24 |
| 60      | Management      | 192.168.60.0/24 |
| 100     | Wi-Fi publique  | 192.168.100.0/24|
| 110     | Wi-Fi corpo     | 192.168.110.0/24|
| 120     | VPN             | 192.168.120.0/24|
| 460     | FAI             | 206.167.46.0/24 |

### Assignation des ports VLAN

| Interface | Mode    | VLAN                                | Description                     |
|-----------|---------|------------------------------------|---------------------------------|
| Gi1/0/1   | Trunk   | 460  | Uplink vers ToR / agrégation    |
| Gi1/0/2   | Trunk   | 10,20,30,40,50,60,100,110,120,460  | Trunk vers hyperviseur / serveurs |
| Gi1/0/3   | Access  | 60                                  | PC de gestion / accès ESXi      |
| Gi1/0/4   | Access  | 10                                  | Poste / service VLAN 10         |
| Gi1/0/5   | Access  | 20                                  | Serveur / VLAN 20               |
| Gi1/0/6   | Access  | 30                                  | Poste / VLAN 30                 |
| Gi1/0/7   | Access  | 40                                  | DMZ / VLAN 40                   |
| Gi1/0/8   | Access  | 50                                  | IoT / VLAN 50                   |
| Gi1/0/9   | Access  | 100                                 | Wi‑Fi publique                  |
| Gi1/0/10  | Access  | 110                                 | Wi‑Fi corpo                     |
| Gi1/0/11  | Shutdown| -                                    | Administratively shutdown      |
| Gi1/0/12  | Shutdown| -                                    | Administratively shutdown      |
| Gi1/0/13  | Shutdown| -                                    | Administratively shutdown      |
| Gi1/0/14  | Shutdown| -                                    | Administratively shutdown      |
| Gi1/0/15  | Shutdown| -                                    | Administratively shutdown      |
| Gi1/0/16  | Shutdown| -                                    | Administratively shutdown      |
| Gi1/0/17  | Shutdown| -                                    | Administratively shutdown      |
| Gi1/0/18  | Shutdown| -                                    | Administratively shutdown      |
| Gi1/0/19  | Shutdown| -                                    | Administratively shutdown      |
| Gi1/0/20  | Shutdown| -                                    | Administratively shutdown      |
| Gi1/0/21  | Shutdown| -                                    | Administratively shutdown      |
| Gi1/0/22  | Shutdown| -                                    | Administratively shutdown      |
| Gi1/0/23  | Shutdown| -                                    | Administratively shutdown      |
| Gi1/0/24  | Shutdown| -                                    | Administratively shutdown      |
| Gi1/0/25  | Shutdown| -                                    | Administratively shutdown      |
| Gi1/0/26  | Shutdown| -                                    | Administratively shutdown      |

---

## 3. Configuration des Trunks

- **Interface Gi1/0/1** : Trunk vers ToR  
  - VLANs autorisés : 10,20,30,40,50,60,100,110,120
- **Interface Gi1/0/2** : Trunk vers Hyperviseur  
  - VLANs autorisés : 10,20,30,40,50,60,100,110,120

---

## 4. Sécurisation et gestion des accès

- **SSH activé**  
  - Utilisateur `admin` avec mot de passe complex
  - Connexion via VTY protégée
  - Mot de passe enable et secret
  - Commandes :
    - SW-S0-01(config)# hostname SW-S0-01
    - SW-S0-01(config)# ip domain-name sw-s0-01.corp.alrian.store
    - SW-S0-01(config)# username admin privilege 15 secret MonMdpSSH
    - SW-S0-01(config)# crypto key generate rsa
    - SW-S0-01(config)# line vty 0 15
    - SW-S0-01(config-line)# login local
    - SW-S0-01(config-line)# transport input ssh
    - SW-S0-01(config-line)# exit
- **Ports inutilisés** : shutdown pour éviter les accès non autorisés
- **STP** : Activé, validé avec la commande : show spanning-tree
- **Serveurs DNS configurés** : `ip name-server 8.8.8.8` et `ip name-server 1.1.1.1`
- **Notes** : L’interface de gestion VLAN 60 est accessible pour l’administration, monitoring et connexion au serveur hyperviseur.

