# Excellia Bourse

<p align="center">
  <img src="https://img.shields.io/badge/Java-17-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java 17" />
  <img src="https://img.shields.io/badge/Spring%20Boot-3.4.3-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" alt="Spring Boot 3.4.3" />
  <img src="https://img.shields.io/badge/Next.js-13-000000?style=for-the-badge&logo=nextdotjs&logoColor=white" alt="Next.js 13" />
  <img src="https://img.shields.io/badge/MySQL-8-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL 8" />
  <img src="https://img.shields.io/badge/Docker-Compose-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker Compose" />
  <img src="https://img.shields.io/badge/Kafka-Message%20Bus-231F20?style=for-the-badge&logo=apachekafka&logoColor=white" alt="Kafka" />
  <img src="https://img.shields.io/badge/Jenkins-CI%2FCD-D24939?style=for-the-badge&logo=jenkins&logoColor=white" alt="Jenkins" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Status-Portfolio%20Project-success" alt="Portfolio Project" />
  <img src="https://img.shields.io/badge/Architecture-Microservices-8A2BE2" alt="Microservices" />
  <img src="https://img.shields.io/badge/Deployment-Docker%20%2B%20Ansible-blue" alt="Deployment" />
</p>

## 🚀 Présentation

Excellia Bourse est une plateforme complète de gestion des bourses d’études, conçue pour digitaliser le parcours complet d’une candidature : publication des offres, recherche de bourses, soumission des dossiers, traitement administratif et notification des étudiants.

Ce projet a été développé comme une solution technique complète, mêlant :

* une architecture backend basée sur des microservices Java/Spring Boot,
* un frontend moderne en Next.js,
* une gestion de messages asynchrones avec Kafka,
* une intégration DevOps avec Docker, Jenkins et Ansible,
* une logique de déploiement orientée environnement réel.

L’objectif principal est de fournir une plateforme fonctionnelle, scalable et facilement extensible pour gérer les demandes de bourses dans un contexte académique ou institutionnel.

---

## 🎯 Objectif du projet

Le projet vise à simplifier et moderniser le processus de gestion des bourses en centralisant les actions suivantes :

* publication et gestion des offres de bourses,
* recherche et filtrage des bourses selon plusieurs critères,
* soumission des candidatures avec pièces jointes,
* validation des dossiers par l’administration,
* notification des étudiants et gestion des échanges,
* suivi des inscriptions et des profils utilisateurs,
* mise en place d’une architecture évolutive et prêtes pour la production.

---

## 🧠 Principe fonctionnel

Le système repose sur un modèle d’écosystème distribué où chaque service métier est responsable d’une partie précise du flux global.

### Flux métier principal

1. Un étudiant s’inscrit et crée son profil..
2. Il consulte les bourses disponibles.
3. Il soumet une candidature avec les documents requis.
4. Le système valide la demande et la stocke.
5. Les notifications et messages sont envoyés via des événements asynchrones.
6. L’administration peut gérer les bourses, dossiers et traitement des demandes.

---

## 🏗️ Architecture globale

```text
┌──────────────────────────────┐
│         Frontend            │
│       Next.js / React       │
└──────────────┬───────────────┘
               │ HTTP / API
               ▼
┌──────────────────────────────┐
│        API Gateway           │
│   Spring Cloud Gateway       │
└───────┬──────────────────────┘
        │
        ├──────────────> inscription-service
        ├──────────────> gestion-bourse-candidature-service
        ├──────────────> messagerie-service
        ├──────────────> notification-service
        │
        └──────────────> discovery-service (Eureka)
                            │
                            └──────────────> config-service (Spring Cloud Config)

                     │
                     │ Kafka
                     ▼
              Event-driven messaging

                     │
                     ▼
              MySQL databases per service
```

---

## 🧩 Composants du projet

### Backend – Microservices Java

* `config-service` : configuration centralisée des microservices.
* `discovery-service` : service de découverte Eureka.
* `gateway-service` : point d’entrée unique et routage des requêtes.
* `inscription-service` : gestion des inscriptions et des utilisateurs.
* `gestion-bourse-candidature-service` : gestion des bourses, candidatures et documents.
* `messagerie-service` : gestion des échanges/messages internes.
* `notification-service` : envoi d’alertes, notifications et updates.
* `utilitiesService` : composants réutilisables cross-services.

### Frontend – Application utilisateur

Le projet frontend est développé avec Next.js et propose une interface moderne pour :

* la création de compte et la connexion,
* la consultation des offres de bourses,
* la soumission de candidature,
* la gestion du profil utilisateur,
* l’accès aux pages de navigation et d’informations institutionnelles.

### CI/CD et déploiement

La partie DevOps du projet comprend :

* `docker-compose.yaml` pour le lancement local / conteneurisé,
* `deployment/jenkins/Jenkinsfile` pour automatiser le build,
* `deployment/ansible/deploy.yml` pour le déploiement automatique sur environnement cible,
* intégration logique de pipelines CI/CD pour exécuter les builds et préparer le déploiement.

---

## 🛠️ Stack technique

### Backend
* Java 17
* Spring Boot 3.4.x
* Spring Cloud Gateway
* Spring Cloud Config
* Spring Cloud Netflix Eureka
* Spring Data JPA
* MySQL
* Kafka
* Maven

### Frontend
* Next.js 13
* React 18
* JavaScript / JSX
* Axios
* CSS Modules / styles globaux

### DevOps
* Docker
* Docker Compose
* Jenkins
* Ansible
* Git / GitHub

---

## ✅ Concepts techniques et bonnes pratiques mis en œuvre

### 1. Architecture microservices

Le projet découpe le système en services autonomes avec des responsabilités bien définies, ce qui favorise :

* la maintenabilité,
* la scalabilité,
* la résilience,
* l’indépendance fonctionnelle des modules.

### 2. Séparation des couches

Le code suit une organisation claire :

* contrôleurs,
* services métier,
* repositories,
* entités JPA,
* DTOs,
* gestion de fichiers et documents.

Cette approche permet de garder le projet propre, lisible et plus facile à faire évoluer.

### 3. Utilisation de DTOs

Les DTOs sont utilisés pour structurer les échanges et éviter d’exposer directement les entités de persistance. Cela améliore la sécurité, la flexibilité et la compréhension du code.

### 4. Gestion de la persistance avec JPA

Les données sont gérées via JPA/Hibernate afin de simplifier les opérations CRUD et la relation entre entités métier.

### 5. Traitement asynchrone avec Kafka

Kafka est utilisé pour déléguer certains événements et processus métier, évitant ainsi les dépendances strictes entre services et améliorant la réactivité globale du système.

### 6. Découverte de services avec Eureka

L’utilisation d’Eureka permet au système de connaître dynamiquement les services disponibles, ce qui est fondamental dans une architecture microservices.

### 7. Configuration externe centralisée

Les paramètres sont externalisés via Spring Cloud Config, ce qui rend le système plus portable et plus facile à gérer selon l’environnement.

### 8. Frontend moderne et orienté UX

Le frontend Next.js apporte une expérience utilisateur plus fluide, rapide et professionnelle, adaptée à une application web de gestion académique.

### 9. Conteneurisation

L’utilisation de Docker Compose facilite la mise en place d’un environnement reproductible pour le développement et les tests.

### 10. Pipeline CI/CD

Le projet affiche une logique de pipeline industrielle avec :

* build automatique des microservices,
* tests et validation,
* déploiement automatisé,
* gestion d’environnement par Ansible.

---

## 📦 Fonctionnalités principales

* gestion des offres de bourses,
* filtrage des bourses par critères,
* soumission de candidatures avec documents,
* gestion des profils utilisateurs,
* validation des dossiers,
* génération de flux de notifications,
* messagerie interne,
* interface utilisateur pour l’étudiant,
* architecture extensible pour nouvelles fonctionnalités.

---

## 🧪 Structure du dépôt

```text
Devops_Pipeline/
├── Excellia_bourse/
│   ├── config-service/
│   ├── discovery-service/
│   ├── gateway-service/
│   ├── gestion-bourse-candidature-service/
│   ├── inscription-service/
│   ├── messagerie-service/
│   ├── notification-service/
│   ├── utilitiesService/
│   ├── ui-tests/
│   ├── src/
│   ├── pom.xml
│   ├── README.md
│   └── ...
├── Excellia_Frontend/
│   ├── src/
│   ├── public/
│   ├── package.json
│   ├── Dockerfile
│   ├── README.md
│   └── ...
├── deployment/
│   ├── ansible/
│   └── jenkins/
├── docker-compose.yaml
├── .gitignore
└── README.md
```

---

## 🚀 Démarrage rapide

### Prérequis

* Java 17+
* Maven
* Node.js 18+
* npm or yarn
* Docker
* Docker Compose

### 1. Démarrer les microservices backend

```bash
cd Excellia_bourse
mvn clean install
```

Puis lancer avec Docker :

```bash
docker-compose up --build
```

### 2. Démarrer le frontend

```bash
cd Excellia_Frontend
npm install
npm run dev
```

### 3. Vérifier l’application

* Frontend : http://localhost:3000
* Gateway : http://localhost:8888
* Eureka : http://localhost:8761

---

## 🔄 Pipeline CI/CD

Le projet inclut un schéma de pipeline automatisé basé sur Jenkins et Ansible.

### Jenkins

Le fichier Jenkins est situé dans :

* `deployment/jenkins/Jenkinsfile`

Il permet de :

* récupérer le code source,
* compiler les microservices Maven,
* créer les artefacts,
* lancer le déploiement sur l’environnement cible.

### Ansible

Le playbook Ansible situé dans :

* `deployment/ansible/deploy.yml`

Il permet de :

* copier le projet sur la machine cible,
* préparer le répertoire de déploiement,
* lancer les conteneurs via Docker Compose.

Cette configuration montre une bonne compréhension des principes DevOps appliqués à une architecture Java/Spring moderne.

---

## 📌 Valeur ajoutée pour votre profil GitHub

Ce projet est particulièrement intéressant à présenter sur GitHub parce qu’il démontre :

* la conception d’une application métier complète,
* la maîtrise de l’architecture microservices,
* la capacité à travailler sur le backend et le frontend,
* les compétences DevOps avec Docker, Jenkins et Ansible,
* la compréhension des bonnes pratiques de développement logiciel,
* la capacité à livrer une solution structurée et prête pour l’environnement réel.

---

## 🏁 Conclusion

Excellia Bourse est bien plus qu’un simple projet académique : c’est une plateforme technique complète qui met en valeur la capacité à concevoir, organiser et déployer une solution logicielle moderne.

---
