 Livrable 3 – Définition d’une convention de nommage

---

## 1. Description de l’entreprise

**Nom choisi :**  
Alrian

**Description de l’entreprise :**  
Alrian est une entreprise de vente au détail de vêtements opérant principalement en magasin physique. Elle propose des produits vestimentaires de **luxe**. L’entreprise possède deux succursales ouvertes au public ainsi qu’un siège social qui centralise l’administration, la gestion des systèmes informatiques et les opérations.

**Nombre de succursales :**  
2 succursales + 1 siège social

**Nombre d’employés :**  
Environ 60 employés

---

## 2. Nom de domaine interne et internet

**Nom de domaine interne :**  
corp.alrian.store

**Nom de domaine externe :**  
alrian.store

**Fournisseur DNS :**  
Namecheap

---

## 3. Convention de nommage

### 3.1 Structure générale de nommage

TYPE-LOCALISATION-NUMÉRO


---

### 3.2 Étiquetage des câbles CAT6 RJ45

### Format

-ENTREPRISE - NOM DE L'ÉQUIPEMENT BRANCHÉ


### Exemple

alrian-SRV-S0-01


**Justification :**  
Cette convention permet d’identifier rapidement l’origine et la destination d’un câble réseau, facilitant ainsi la maintenance et les interventions techniques.

---

### 3.3 Abréviations utilisées

**Types d’équipements :**
- SRV : Serveur physique
- VM : Machine virtuelle locale
- VMC : Machine virtuelle dans le cloud
- SW : Commutateur
- RT : Routeur
- AP : Point d’accès Wi-Fi
- PC : Poste de travail

**Localisations :**
- S0 : Siège social
- S1 : Succursale 1 (Montréal)
- S2 : Succursale 2 (Laval)

**Numérotation :**
- Numérotation séquentielle (01, 02, 03…)

---

## 4. Tableau de la convention de nommage

| Type d’équipement | Convention de nommage | Justificatif |
|------------------|----------------------|--------------|
| Serveurs physiques | `SRV-S0-01` | Permet d’identifier clairement le serveur physique, sa localisation et son ordre d’installation. |
| Machines virtuelles (locales) | `VM-S0-01` | Distingue les machines virtuelles locales des serveurs physiques tout en restant cohérent. |
| Machines virtuelles dans le cloud | `VMC-S1-01` | Facilite la distinction entre les ressources locales et celles hébergées dans le cloud. |
| Commutateurs | `SW-S1-01` | Indique la succursale où le commutateur est installé, facilitant la gestion réseau. |
| Routeurs | `RT-S0-01` | Permet une identification rapide des équipements assurant la connectivité réseau. |
| Points d’accès Wi-Fi | `AP-S2-01` | Permet de localiser rapidement la zone couverte par le point d’accès Wi-Fi. |
| Postes de travail | `PC-S1-01` | Identifie le poste utilisateur selon sa localisation et son numéro. |
| Noms d’utilisateurs | `p.nom` | Convention simple, uniforme et professionnelle facilitant la gestion des comptes. |
| Câbles CAT6 RJ45 | `-ENTREPRISE - NOM DE L'ÉQUIPEMENT BRANCHÉ` | Simplifie le repérage physique des câbles et accélère le dépannage réseau. |

---