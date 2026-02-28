# Livrable 4 – Sélection des logiciels

---

## 1. Introduction

Ce document présente les choix logiciels pour l’infrastructure de l’entreprise **Alrian**.  
Les logiciels sélectionnés ont été choisis pour répondre aux besoins suivants : gestion de la virtualisation, conteneurisation, sécurité, supervision, documentation, sauvegarde, services cloud et assistance IA.  

Chaque choix est justifié en fonction de son rôle dans l’infrastructure.

---

## 2. Tableau des besoins logiciels

| Nom du logiciel | Rôle dans l’infrastructure | Justification / Remarques |
|----------------|---------------------------|---------------------------|
| **Bitwarden** | Gestion des accès et mots de passe | Gestion sécurisée des mots de passe pour l’équipe, partage et stockage chiffré. |
| **GitLab / Markdown** | Plateforme de documentation | Documentation centralisée et versionnée du projet. |
| **VMware ESXi** | Hyperviseur | Virtualisation de serveurs physiques pour créer des VM locales et tester l’infrastructure. |
| **Windows Server 2025** | Système d’exploitation serveur | Gestion Active Directory, DNS, DHCP et services internes pour les utilisateurs. |
| **Ubuntu Server 24.04.3 LTS** | Système d’exploitation serveur | Serveur Linux stable pour services web, bases de données et déploiement de conteneurs Docker. |
| **Windows 11 Pro** | Système d’exploitation poste de travail | OS moderne pour les postes des employés, compatible avec AD et applications métiers. |
| **Veeam Backup & Replication** | Sauvegarde des données | Sauvegarde et restauration des VM, serveurs et données critiques. |
| **Zabbix** | Supervision et monitoring | Surveillance des serveurs, VM et équipements réseau, alertes automatiques. |
| **pfSense** | Pare-feu et sécurité réseau | Protection du réseau interne et contrôle des accès Internet. |
| **Ansible** | Gestion et déploiement de configurations | Automatisation du déploiement et de la configuration des serveurs et VM. |
| **Docker** | Virtualisation légère / Conteneurisation | Déploiement d’applications dans des conteneurs isolés, portable et scalable. |
| **Microsoft Azure** | Cloud / VM et services cloud | Hébergement de VM, conteneurs et services cloud, permettant l’extension de l’infrastructure locale et la haute disponibilité. |
| **ChatGPT** | IA d’assistance | Génération de documentation, aide à la résolution de problèmes et automatisation de tâches répétitives. |
| **GitHub Copilot** | IA pour le développement | Assistance à la rédaction de code, complétion intelligente et suggestions pour les scripts et configurations. |

