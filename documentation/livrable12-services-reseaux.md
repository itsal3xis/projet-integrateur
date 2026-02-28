# Livrable 12 – Installation des serveurs et services réseau

## 1. Informations générales des serveurs

| Serveur / VM | Rôle principal | VLAN associé | Adresse IP | Statut |
|-------------|----------------|-------------|------------|--------|
| VM-S0-01 | Contrôleur de domaine (Active Directory) / DNS interne | Admin | 192.168.10.10 | Installé, opérationnel |
| VM-S0-02 | Serveur Web accessible interne et externe | DMZ | 192.168.40.10 | Installé, opérationnel |

---

## 2. Configuration Active Directory

- **Contrôleur de domaine :** VM-S0-01  
- **Domaine :** corp.alrian.store  
- **Structure des OU (Unités Organisationnelles) :**  
  - Users → comptes utilisateurs  
  - Groups → groupes de sécurité  
  - Computers → postes et serveurs du domaine  

- **Comptes utilisateurs et groupes :**  
  - Admins (droits complets sur le domaine)  
    - a.mindru → administrateur du domaine  
    - a.bernard → administrateur du domaine  
  - Staff (accès limité aux ressources internes)  
    - p.tremblay → utilisateur standard  

- Authentification AD testée et fonctionnelle.

---

## 3. Configuration DNS

- **Serveur DNS interne intégré à AD :** 192.168.10.10  
- **Zones directes :**  
  - corp.alrian.store  
    - www → 192.168.40.10 (VM DMZ interne)  
    - ad → 192.168.10.10  
    - vm-s0-01 → 192.168.10.10
    - vm-s0-02 → 192.168.40.10
    - srv-s0-01 → 192.168.60.3
    - sw-s0-01 →  192.168.60.2
    - rt-s0-01 →  192.168.60.1
- **Zones inverses :**  
  - 192.168.10.0/24 → Corpo_HQ
  - 192.168.40.0/24 → DMZ
  - 192.168.60.0/24 → Management  
- **Résolution DNS interne :** tous les clients utilisent 192.168.10.10 comme DNS principal.  
- **Forwarding DNS :** activé vers 8.8.8.8 et 1.1.1.1 pour les requêtes externes.

---

## 4. Configuration DHCP

- **DHCP activé sur pfSense** pour tous les VLANs internes.  
- **Plages d’adresses par VLAN :**

| VLAN | Plage DHCP | Passerelle |
|------|------------|------------|
| Corpo_HQ | 192.168.10.100-192.168.10.200 | 192.168.10.1 |
| Wi-Fi corporatif | 192.168.110.50-192.168.110.200 | 192.168.110.1 |
| Wi-Fi public | 192.168.100.50-192.168.100.200 | 192.168.100.1 |
| IoT | 192.168.50.50-192.168.50.100 | 192.168.50.1 |
| Management | 192.168.60.50-192.168.60.100 | 192.168.60.1 |
| VPN | 192.168.120.50-192.168.120.200 | 192.168.120.1 |
| Succursale MTL | 192.168.20.50-192.168.20.200 | 192.168.20.1 |
| Succursale LVL | 192.168.30.50-192.168.30.200 | 192.168.30.1 |

- Vérification : tous les clients récupèrent une IP correspondant à leur VLAN.  
- **VM DMZ et serveur Web** : IP statique 192.168.40.10, hors plage DHCP.

---

## 5. Configuration du serveur Web (VM-S0-02)

- **Logiciel :** Apache  
- **Chemin du fichier HTML :** `/var/www/html/index.html`  

### 5.1 Nom de domaine public

- Domaine : `www.alrian.store` (Namecheap)  
- DNS Namecheap configuré : enregistrement A → IP publique WAN pfSense  

### 5.2 Redirection NAT / Port Forward sur pfSense

- Interface : WAN  
- Protocole : TCP  
- Ports : 80 (HTTP: désactivé pour HTTPS) et 443 (HTTPS)  
- IP interne cible : 192.168.40.10  

### 5.3 Certificat HTTPS

- **Let’s Encrypt via Certbot :**  

```bash
sudo apt update
sudo apt install certbot python3-certbot-apache -y
sudo certbot --apache -d alrian.store
