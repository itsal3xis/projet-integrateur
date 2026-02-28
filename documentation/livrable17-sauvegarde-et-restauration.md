# Livrable 17 – Sauvegarde et Restauration

## 1. Objectif

Mettre en place une stratégie complète de sauvegarde et de restauration pour l’infrastructure virtualisée, incluant :

- Configuration des sauvegardes
- Stockage sécurisé dans le cloud (mode objet)
- Test de restauration
- Documentation complète

---

# 2. Choix de l’outil de sauvegarde

## Outil sélectionné

Nous avons choisi **Veeam Backup & Replication** installé sur **Windows Server 2022**.

### Justification du choix

- Solution professionnelle utilisée en entreprise
- Compatible avec environnements virtualisés (VMware / Hyper-V)
- Support natif du stockage objet Azure Blob
- Gestion des sauvegardes incrémentielles
- Restauration complète ou instantanée

Ce choix est pertinent et adapté à notre infrastructure.

---

# 3. Architecture mise en place

## Architecture logique

```
        +----------------------+
        |   Machines Virtuelles |
        |      (VMs ESXi)       |
        +-----------+----------+
                    |
                    v
        +----------------------+
        |      SRV-VEEAM       |
        |   Windows Server 2022|
        +-----------+----------+
                    |
                    v
        +----------------------+
        | Microsoft Azure Blob |
        |   Object Storage     |
        |   HTTPS sécurisé     |
        +----------------------+
```
---

# 4. Configuration du stockage Cloud

## Fournisseur Cloud

- Fournisseur : Microsoft Azure
- Service : Azure Blob Storage
- Type : Object Storage
- Connexion : HTTPS via clé API sécurisée

## Étapes réalisées

1. Création d’un Storage Account (StorageV2)
2. Performance : Standard
3. Redondance : LRS
4. Création d’un conteneur nommé : veeam-backups
5. Récupération des Access Keys
6. Configuration du repository Azure Blob dans Veeam

---

# 5. Configuration des sauvegardes

## Type de sauvegarde

- Backup incrémentiel
- Full initial automatique

## Sélection

Toutes les machines virtuelles de l’infrastructure sont incluses.

## Planification

- Fréquence : Quotidienne
- Heure : 22h
- Mode : Automatique

## Politique de rétention

- 14 points de restauration conservés

---

# 6. Exécution des sauvegardes

Les sauvegardes ont été lancées manuellement pour validation initiale.

Résultat :

- Statut : Success
- Fichiers visibles dans Azure Blob Storage
- Connexion sécurisée HTTPS confirmée

## Captures d’écran à inclure

- Configuration du job
- Exécution réussie
- Conteneur Azure avec fichiers de sauvegarde

---

# 7. Test de restauration

## Procédure effectuée

1. Arrêt d’une machine virtuelle test
2. Lancement d’une restauration complète depuis Veeam
3. Sélection du dernier point de restauration
4. Restauration vers l’emplacement d’origine

## Résultat

- Restauration réussie
- VM redémarrée sans erreur
- Services fonctionnels
- Connectivité réseau valide

## Captures d’écran à inclure

- Assistant de restauration
- Processus en cours
- VM restaurée et opérationnelle

---

# 8. Stratégie de sauvegarde retenue

Notre stratégie repose sur :

- Sauvegarde quotidienne automatique
- Stockage hors site sécurisé (Cloud)
- Conservation de 14 points de restauration
- Test de restauration validé

Cette stratégie garantit :

- Protection contre la perte de données
- Protection contre panne matérielle
- Protection contre erreur humaine
- Continuité de service