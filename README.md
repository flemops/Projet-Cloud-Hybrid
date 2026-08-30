# Cloud Hybride — Active Directory, Messagerie & Windows Server

Deux livrables réalisés dans le cadre du cursus Systèmes, Réseaux et Cloud (SUPDEVINCI) : un projet de groupe (architecture hybride pour un client fictif) et un dossier de travaux pratiques individuel sur Windows Server.

## 1. Migration Active Directory & Messagerie — cas client « Malo » (projet de groupe)

Étude de service report (SRD) rédigée pour un cas d'école : la société de conseil fictive Hestia migre l'infrastructure de son client Malo vers une architecture hybride, à l'occasion d'un déménagement.

Équipe de 4, rôles répartis :
- Infrastructure serveur (cloud privé/public) — Jean-Emmanuel Gabriel
- Réseau & sécurité — Mouhamadou Diallo
- **Active Directory & Messagerie — Hamdy Tabsissi** (ce document)
- Gouvernance & supervision — Mugdat Iscen

### Ce qui a été conçu (partie AD & Messagerie)

- **Active Directory hybride** : serveur primaire (MALO-AD1) sur Azure Cloud, serveur secondaire (MALO-AD2) on-premise sur VMware, réplication toutes les 15 min + bascule des rôles FSMO en cas de panne (seizing).
- Rôles configurés : DNS (malo.lan), ADDS (arborescence par service, convention de nommage), ADCS (6 certificats : firewall, Wi-Fi sécurisé, VPN, IPSec, NAP, EFS), ADFS (SSO web).
- GPO de sécurité sur postes et sessions utilisateurs.
- **Messagerie Office 365** : 3 abonnements dimensionnés par profil (Business Premium / Standard / Basic pour ~220 utilisateurs), relayage SMTP, filtre anti-spam, Teams, synchronisation Azure AD Connect.
- Politique de sécurité : rotation mensuelle des mots de passe, 3 profils d'accès (admin / direction / utilisateur).
- Chiffrage détaillé (coûts AD, Office 365, main d'œuvre) et plan de transfert de compétences (formations chiffrées).

`ASI-3-22-SRD_HESTIA_TABSISSI.pdf` — document complet.

## 2. Windows Server — 6 travaux pratiques (individuel)

Dossier de TP réalisé en solo sur une semaine, infrastructure virtualisée sur Azure.

| TP | Sujet |
|---|---|
| 1 | Hyper-V : disques, réseau, management PowerShell |
| 2 | Docker : installation, Dockerfile, exécution de conteneur |
| 3 | ADDS + Azure AD Connect |
| 4 | ADFS, proxy web, IIS |
| 5 | DFS et réplication DFS-R |
| 6 | Sauvegardes |

`TABSISSI_WS_TP1à6.docx.pdf` — document complet.

---
*Projets académiques (Bachelor/cursus cybersécurité SUPDEVINCI) — cas d'étude, pas un déploiement en production.*

