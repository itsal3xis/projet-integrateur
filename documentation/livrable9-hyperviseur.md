# livrable 9: Installation de l'hyperviseur

## Documentation de l’Installation d’un Hyperviseur  

### 1. Informations générales  
- **Nom de l’hyperviseur** : VMware ESXi 8.0
- **Version et build installés** : 8.0.0/20513097  
- **Serveur hôte** : Dell PowerEdge R740

---

### 2. Paramètres d’installation  
- **Médium utilisé** : ISO virtuel avec IDRAC
- **Mode de déploiement** : Installation sur disque local
- **Taille du stockage alloué pour les VM** : 1To
- **Mode de partitionnement** : GPT
- **Configuration du mot de passe administrateur/root** : Bitwarden

---

### 3. Configuration réseau initiale  
- **Adresse IP de gestion** : 192.168.60.3
- **Passerelle par défaut** : 192.168.60.1
- **Serveurs DNS** : 8.8.8.8  
- **Mode d’attribution** : Statique 
- **Nom d’hôte** : `SRV-S0-01`

---

### 4. Configuration matérielle de l’hyperviseur  
- **Processeur** : 8 CPUs x Intel(R) Xeon(R) E E-2468
- **Mémoire vive (RAM)** : 32Go DDR5 
- **Stockage total** : 2x SSD 2 To RAID 1
- **Cartes réseau et configuration** : 	Broadcom NetXtreme Gigabit Ethernet (BCM5720)

---

### 5. Paramétrage post-installation  
- **Activation des accès distants** : Console Web
- **Configuration des datastores** : Stockage local
