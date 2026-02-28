# Livrable 1 – Analyse de l’environnement informatique d’une entreprise  
## Analyse basée sur une offre d’emploi ISR – La Maison Simons Inc.

---

## 1. Informations générales

**Nom de l’entreprise :**  
La Maison Simons Inc. (Simons)

**Secteur d’activité :**  
Commerce de détail (mode, accessoires et articles pour la maison)

**Taille de l’entreprise :**  
Grande entreprise privée canadienne

**Nombre d’employés :**  
Environ 2 500 à 5 000 employés

**Nombre de bureaux/sites :**  
- Siège social : Québec (QC, Canada)  
- Environ 19 à 23 magasins au Canada  
- Centres de distribution  
- Campus Simons – informatique  

**Activités principales :**  
Fondée en 1840, La Maison Simons est une entreprise canadienne spécialisée dans la vente au détail de vêtements, d’accessoires et d’articles pour la maison. L’entreprise exploite des magasins physiques à travers le Canada ainsi qu’une plateforme de commerce électronique. Son environnement informatique soutient les opérations commerciales, la logistique, les systèmes de point de vente (POS), la gestion des employés et les services numériques internes.

---

## 2. Besoins en infrastructure TI

### Réseaux

**Type d’infrastructure réseau :**
- Réseau LAN d’entreprise segmenté par VLAN (administration, magasins, serveurs, invités)
- Réseau Wi-Fi corporatif et Wi-Fi invité
- DMZ pour les services exposés (site web, accès distant)
- Interconnexion des magasins via SD-WAN

**Technologies envisagées :**
- Commutateurs gérés Cisco
- Routeurs SD-WAN
- Points d’accès Wi-Fi professionnels

---

### Virtualisation et serveurs

**Type d’hyperviseur :**
- Nutanix AHV
- Red Hat OpenShift Virtualization

**Nombre de serveurs physiques et virtuels :**
- Environ 6 serveurs physiques
- Environ 20 machines virtuelles (pour la redondance et différents services)

**Services prévus :**
- Active Directory
- DNS et DHCP
- Serveurs de fichiers
- Serveurs applicatifs internes
- Bases de données SQL
- Serveurs Linux et Windows

**Stockage :**
- Infrastructure de stockage SAN
- Stockage centralisé pour les données critiques et les machines virtuelles

---

### Cloud

**Modèle de cloud :**
- Cloud hybride (principalement sur site avec certaines ressources dans le cloud public, utilisation limitée et ciblée)

**Utilisation prévue :**
- **Stockage :** Sauvegardes hors site, réplication et archivage à long terme des données critiques
- **Serveur web :** Hébergement du site transactionnel et/ou utilisation d’un CDN pour assurer haute disponibilité et protection contre les attaques DDoS

---

## 3. Besoins en sécurité

### Protection des données

**Sauvegardes :**
- Sauvegardes automatisées avec Veeam
- Chiffrement des données au repos et en transit
- Tests réguliers de restauration sur l'environnement de test

**Politique de rétention :**
- Sauvegardes régulières des données
- Archivage à long terme pour les données critiques

---

### Accès sécurisé

**VPN :**
- VPN Site-to-Site entre les magasins et le siège social
- VPN pour le télétravail des employés TI

**Authentification :**
- Active Directory avec LDAP
- Authentification multi-facteurs (MFA)
- Gestion centralisée des postes avec MDM et GPO

---

### Supervision et réponse aux incidents

**Outils de supervision :**
- Surveillance des serveurs, réseaux et services critiques
- Alertes automatisées en cas d’incident
- Solution EDR pour la détection et la réponse aux menaces

**Plan de continuité :**
- Tests réguliers de récupération des systèmes
- Redondance des services critiques

---

