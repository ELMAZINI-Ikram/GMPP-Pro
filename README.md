# GMPP Pro — Gestion de Maintenance Préventive Planifiée

**Plateforme de GMAO (Gestion de Maintenance Assistée par Ordinateur) qui organise la maintenance préventive et corrective d'un parc machines** : planification des interventions, suivi des pannes, gestion des pièces de rechange et pilotage de la performance par les indicateurs de fiabilité (MTBF, MTTR, TRS / OEE).

![Java](https://img.shields.io/badge/Java-17-red)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.2-6DB33F)
![React](https://img.shields.io/badge/React-18-61DAFB)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-336791)
![Docker](https://img.shields.io/badge/Docker-Compose-2496ED)

> 🇬🇧 *Computerized maintenance management system (CMMS) for planned preventive maintenance: machine registry with QR codes, maintenance scheduling, corrective failure workflow, spare parts inventory, reliability KPIs (MTBF, MTTR, OEE, Pareto analysis), real-time notifications and multilingual interface. Built with Spring Boot, React and PostgreSQL, fully containerized with Docker.*

---

## Sommaire

- [Contexte et problématique](#contexte-et-problématique)
- [Solution](#solution)
- [Aperçu](#aperçu)
- [Modules](#modules)
- [Indicateurs de performance maintenance](#indicateurs-de-performance-maintenance)
- [Gestion des rôles](#gestion-des-rôles)
- [Architecture technique](#architecture-technique)
- [Installation](#installation)
- [Compétences mobilisées](#compétences-mobilisées)
- [Équipe](#équipe)

---

## Contexte et problématique

Dans de nombreux ateliers, la maintenance reste majoritairement corrective : on répare quand la machine tombe en panne. Les plannings préventifs sont suivis sur papier ou sur tableur, l'historique des interventions est difficile à exploiter et les pièces de rechange manquent au moment où on en a besoin. Conséquence : arrêts de production imprévus, coûts élevés et fiabilité des équipements mal mesurée.

**Enjeu :** passer à une maintenance préventive planifiée, tracer chaque intervention et piloter le parc machines à partir d'indicateurs fiables.

## Solution

```
Parc machines (fiche + QR code + compteur horaire)
        ─► Points de maintenance (périodicités, consommables)
        ─► Planning des interventions préventives ─► Exécution et validation
        ─► Déclaration et traitement des pannes correctives
        ─► Consommation des pièces de rechange (stock, alertes de seuil)
        ─► Indicateurs MTBF, MTTR, TRS / OEE, Pareto ─► Rapports PDF / Excel / CSV
```

## Aperçu

<!-- Ajouter les captures d'écran dans un dossier docs/ puis décommenter :
![Tableau de bord](docs/dashboard.png)
![Planning des interventions](docs/planning.png)
![Indicateurs KPI](docs/kpi.png)
-->

*Captures d'écran à venir.*

## Modules

| Module | Contenu |
|--------|---------|
| **Tableau de bord** | Indicateurs en direct, alertes, graphiques temps réel |
| **Machines** | Gestion complète du parc, compteur horaire, génération de QR codes (PNG) |
| **Points de maintenance** | Périodicités, fréquences, consommables associés |
| **Interventions préventives** | Workflow complet : planification → confirmation → validation |
| **Planning** | Calendrier semaine / mois / liste avec création rapide |
| **Pannes correctives** | Workflow visuel : déclaration → résolution → validation |
| **Stock de pièces** | Inventaire, mouvements d'entrée et de sortie, alertes de seuil |
| **KPI et performance** | MTBF, MTTR, TRS / OEE, Pareto des pannes, diagramme radar |
| **Rapports** | Exports PDF, Excel et CSV |
| **Notifications** | Centre de notifications en temps réel (WebSocket) |
| **Journal d'audit** | Traçabilité complète des actions (réservé à l'administrateur) |

**Interface :** multilingue (français, anglais, arabe), mode clair / sombre.

## Indicateurs de performance maintenance

| Indicateur | Signification |
|------------|---------------|
| **MTBF** (Mean Time Between Failures) | Temps moyen de bon fonctionnement entre deux pannes — mesure la fiabilité |
| **MTTR** (Mean Time To Repair) | Temps moyen de réparation — mesure la maintenabilité |
| **TRS / OEE** | Taux de rendement synthétique — combine disponibilité, performance et qualité |
| **Pareto des pannes** | Identifie les machines ou causes responsables de la majorité des arrêts |

## Gestion des rôles

| Rôle | Périmètre |
|------|-----------|
| **Administrateur** | Accès complet, gestion des utilisateurs, journal d'audit |
| **Responsable maintenance** | Pilotage, planification, indicateurs |
| **Chef d'équipe** | Organisation et validation des interventions |
| **Technicien** | Exécution des interventions et déclaration des pannes |

Authentification sécurisée par **Spring Security** et **JWT**.

## Architecture technique

| Couche | Technologies |
|--------|--------------|
| **Backend** | Java 17, Spring Boot 3.2, Spring Security, JWT, Spring WebSocket |
| **Frontend** | React 18, Recharts, Lucide Icons |
| **Base de données** | PostgreSQL 15 |
| **Exports** | iText7 (PDF), Apache POI (Excel), OpenCSV |
| **QR codes** | Google ZXing |
| **Documentation API** | Swagger / OpenAPI |
| **Déploiement** | Docker, Docker Compose |
| **Sauvegarde** | `pg_dump` quotidien automatique |

## Installation

**Prérequis :** Docker et Docker Compose.

```bash
git clone https://github.com/ELMAZINI-Ikram/GMPP-Pro.git
cd GMPP-Pro

cp .env.example .env          # Linux / macOS
# copy .env.example .env      # Windows

docker-compose up --build
```

| Service | Adresse |
|---------|---------|
| Application | http://localhost:3000 |
| Documentation API (Swagger) | http://localhost:8080/api/swagger-ui.html |
| pgAdmin | http://localhost:5050 |

<details>
<summary><b>Comptes de démonstration</b></summary>

| E-mail | Mot de passe | Rôle |
|--------|--------------|------|
| admin@gmpp.ma | Admin@2024 | Administrateur |
| responsable@gmpp.ma | Resp@2024 | Responsable maintenance |
| chef@gmpp.ma | Chef@2024 | Chef d'équipe |
| tech1@gmpp.ma | Tech@2024 | Technicien |
| tech2@gmpp.ma | Tech@2024 | Technicien |

Ces comptes sont destinés uniquement aux tests locaux.
</details>

## Compétences mobilisées

| Domaine | Compétences |
|---------|-------------|
| **Maintenance industrielle** | Maintenance préventive planifiée, maintenance corrective, gestion des pièces de rechange |
| **Performance et fiabilité** | MTBF, MTTR, TRS / OEE, analyse de Pareto |
| **Digitalisation industrielle** | Conception d'une GMAO couvrant le cycle complet de maintenance |
| **Développement full-stack** | Java / Spring Boot, React, API REST, WebSocket |
| **Sécurité** | Authentification JWT, contrôle d'accès par rôles, journal d'audit |
| **DevOps** | Conteneurisation Docker, orchestration Docker Compose, sauvegardes automatisées |
| **Travail en équipe** | Projet collaboratif réalisé à cinq |

## Équipe

Projet réalisé par cinq élèves ingénieur(e)s en Transformation Digitale Industrielle — ENSA Béni Mellal :

- **Ikram ELMAZINI** — [@ELMAZINI-Ikram](https://github.com/ELMAZINI-Ikram)
- **[Prénom NOM]** — [@pseudo-github](https://github.com/pseudo-github)
- **[Prénom NOM]** — [@pseudo-github](https://github.com/pseudo-github)
- **[Prénom NOM]** — [@pseudo-github](https://github.com/pseudo-github)
- **[Prénom NOM]** — [@pseudo-github](https://github.com/pseudo-github)
