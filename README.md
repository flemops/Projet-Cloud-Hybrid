# Cloud hybride — Active Directory, messagerie et Windows Server

> **Statut : ACADÉMIQUE** — deux livrables de cursus (SUPDEVINCI, filière Systèmes, Réseaux et Cloud). Cas client **fictif** pour le premier ; travaux pratiques individuels pour le second. Pas de la production.

## 1. DAT « Hestia / Malo » — Active Directory et messagerie (projet de groupe, juin 2022)

**Contexte.** Une ESN fictive (Hestia) migre l'infrastructure d'un client fictif (Malo, ~220 utilisateurs) vers une architecture hybride à l'occasion d'un déménagement. Équipe de 4, chacun un périmètre : infrastructure serveur, réseau et sécurité, gouvernance et supervision, et **Active Directory + messagerie : Hamdy Tabsissi** (attribution écrite dans le document, p. 5 ; rédaction à la première personne).

**Contribution de Hamdy (périmètre AD et messagerie uniquement).**
- Annuaire hybride : contrôleur principal sur une VM Azure (Windows Server 2022, paramètres de VM chiffrés dans le document), contrôleur secondaire sur site sous VMware ; réplication toutes les 15 minutes ; procédure de reprise des rôles FSMO (*seizing*).
- Services : DNS, AD DS (arborescence par service), AD CS (6 certificats : pare-feu, Wi-Fi sécurisé, VPN, IPSec, NAP, EFS), AD FS (SSO web), GPO de sécurité.
- Messagerie Microsoft 365 : trois niveaux d'abonnement selon les profils (5 / 6 / 209 utilisateurs, soit 220), relais SMTP, antispam, Teams, synchronisation Azure AD Connect.
- Politique de mots de passe (renouvellement mensuel), trois profils d'accès, chiffrage et plan de formation.

**Compromis argumentés** : annuaire principal dans le cloud avec réplique sur site (reprise et sauvegarde) ; Microsoft 365 retenu pour les mises à jour de sécurité automatiques et l'évolutivité ; abonnements différenciés par profil pour limiter le coût.

**Ce que le document est et n'est pas.** Un dossier de conception (DAT) documenté. Le texte décrit des éléments configurés, mais **aucun test de réplication ni de bascule n'y est présenté** : ne pas le lire comme une mise en production. Hestia et Malo n'existent pas. Les autres parties du dossier appartiennent aux autres membres.

**Preuve** : [`ASI-3-22-SRD_HESTIA_TABSISSI.pdf`](ASI-3-22-SRD_HESTIA_TABSISSI.pdf).

## 2. Dossier de 6 travaux pratiques Windows Server (individuel, 6–12 décembre 2021)

Réalisé seul sur une semaine, machines virtuelles sur Azure.

| TP | Sujet | Ce que le dossier montre |
|---|---|---|
| 1 | Hyper-V | Installation et création de machines en PowerShell, commutateur virtuel, points de contrôle, disque virtuel |
| 2 | Docker | Images Windows Server Core / Nano Server, Dockerfile, build et exécution |
| 3 | AD DS + Azure AD Connect | Domaine, unités d'organisation, utilisateurs (interface et `New-ADUser`), jonction d'un poste, synchronisation vers Microsoft 365 |
| 4 | AD FS, proxy web, IIS | Certificat auto-signé, fédération, Web Application Proxy, publication d'un site, test depuis un poste |
| 5 | DFS et DFS-R | Espace de noms, réplication multidirectionnelle, test de réplication ; limites de DFS-R rappelées (ce n'est pas une sauvegarde) |
| 6 | Sauvegardes | Windows Server Backup, coffre Recovery Services (agent MARS) |

**Preuve** : [`TABSISSI_WS_TP1à6.docx.pdf`](TABSISSI_WS_TP1à6.docx.pdf) (captures et commandes).

## Limites

- Exercices de formation sur des environnements jetables ; niveau « bachelor / master », pas une expérience d'exploitation.
- Le DAT ne contient pas de preuve de test de bascule ; les TP 3 à 6 sont surtout des procédures guidées.
- Les PDF sont des documents d'origine non retravaillés : des mots de passe de travaux pratiques d'environnements détruits y figurent, sans lien avec un système actuel.
