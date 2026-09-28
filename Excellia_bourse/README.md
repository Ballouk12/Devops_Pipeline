# Excellia Bourse

<p align="center">
  <img src="https://img.shields.io/badge/Java-17-orange" alt="Java 17" />
  <img src="https://img.shields.io/badge/Spring%20Boot-3.4.3-brightgreen" alt="Spring Boot 3.4.3" />
  <img src="https://img.shields.io/badge/Next.js-13-black" alt="Next.js 13" />
  <img src="https://img.shields.io/badge/MySQL-8-blue" alt="MySQL 8" />
  <img src="https://img.shields.io/badge/Docker-Compose-2496ED" alt="Docker Compose" />
  <img src="https://img.shields.io/badge/Kafka-Message%20Bus-231F20" alt="Kafka" />
</p>

## Objectif du projet

Excellia Bourse est une plateforme de gestion de bourses d’études conçue pour simplifier le processus de recherche, de candidature et de suivi des demandes de financement académique.

Le projet a pour but de centraliser les interactions entre :

- les étudiants qui cherchent des bourses,
- les administrations qui publient et gèrent les offres,
- les utilisateurs qui soumettent leurs candidatures,
- les services internes qui traitent les demandes et les notifications.

Au-delà d’une simple application, ce projet illustre une architecture moderne, scalable et orientée microservices, adaptée à des systèmes complexes qui doivent évoluer sans dépendre d’un monolithe unique.

---

## Principe du projet

Le principe de ce projet repose sur une séparation claire des responsabilités entre plusieurs services métiers, afin de rendre le système :

- modulaire,
- évolutif,
- facile à maintenir,
- robuste et prêt pour un déploiement avec conteneurs,
- adapté à des fonctionnalités métier distinctes.

Chaque service gère une partie précise du système, ce qui permet une meilleure organisation du code et une indépendance fonctionnelle.

### Exemple de logique métier

- Le service de gestion des bourses gère les offres et les candidatures.
- Le service d’inscription gère les comptes et profils utilisateurs.
- Le service de messagerie traite les échanges internes.
- Le service de notification transmet les alertes et mises à jour.
- Le gateway centralise les accès entrants depuis le frontend.

Cette architecture permet de mieux répondre aux besoins d’un système d’information réel avec plusieurs flux et plusieurs bases de données.

---

## Architecture du système

```text
Client Web (Next.js)
        |
        v
  API Gateway
        |
        +----> Service d'inscription
        +----> Service de gestion des bourses / candidatures
        +----> Service de messagerie
        +----> Service de notification
        |
        +----> Service de découverte (Eureka)
        |
        +----> Service de configuration (Spring Cloud Config)

Base de données par service / Kafka / Docker / Jenkins / Ansible
```

### Composants principaux

- Frontend : Next.js
- API Gateway : Spring Cloud Gateway
- Service Discovery : Eureka
- Configuration centralisée : Spring Cloud Config
- Message broker : Kafka
- Bases de données : MySQL
- Conteneurisation : Docker Compose
- Automatisation : Jenkins + Ansible
- Tests : UI automation / tests Java

---

## Concepts techniques mis en œuvre

### 1. Architecture microservices

Le projet est conçu selon une logique de microservices, où chaque service porte une responsabilité métier spécifique. Cela permet :

- d’isoler les évolutions fonctionnelles,
- d’augmenter la scalabilité,
- d’améliorer la résilience du système,
- d’éviter les couplages entre modules.

### 2. API Gateway

Le gateway joue le rôle de point d’entrée unique pour les clients. Il permet :

- de centraliser les appels,
- de protéger l’architecture interne,
- de routage des requêtes vers les bons services,
- d’améliorer la gestion de l’API.

### 3. Service Discovery

L’utilisation d’Eureka permet à chaque microservice de s’enregistrer et de se retrouver automatiquement dans le système. Cela réduit le couplage statique entre services et facilite le déploiement.

### 4. Configuration externe

Le service de configuration permet d’externaliser les paramètres du système pour éviter de dupliquer les configurations dans chaque microservice. Cela rend le projet plus maintenable et plus portable.

### 5. Communication asynchrone avec Kafka

Le système utilise Kafka pour gérer des événements entre services. Cela permet :

- d’éviter les dépendances synchrones fortes,
- d’améliorer la réactivité,
- d’optimiser les flux de notification et de traitement des événements métier.

### 6. Base de données par service

Chaque microservice possède sa propre base de données, ce qui respecte le principe de découpage logique et évite qu’un service soit dépendant du schéma d’un autre service.

### 7. Frontend moderne avec Next.js

Le frontend est développé avec Next.js pour offrir une expérience utilisateur moderne et performante. Il communique avec l’API backend via le gateway.

### 8. Conteneurisation et déploiement

Le projet intègre Docker Compose pour orchestrer le lancement local des services. Cette approche rend le projet plus reproductible et simplifie le déploiement dans différents environnements.

### 9. CI/CD

La structure du projet inclut également des éléments de pipeline CI/CD avec Jenkins et Ansible pour automatiser les étapes de build, déploiement et validation.

---

## Bonnes pratiques implémentées

Ce projet montre plusieurs bonnes pratiques de développement logiciel :

### ✅ Séparation des couches

Le code est organisé selon une logique claire :

- contrôleurs,
- services,
- repositories,
- entités,
- DTOs,
- gestion des fichiers.

Cela favorise la lisibilité et la maintenance du code.

### ✅ Utilisation de DTOs

Les données échangées entre couches sont structurées avec des DTOs pour éviter d’exposer directement les entités de persistence et sécuriser les échanges.

### ✅ Encapsulation de la logique métier

La logique métier n’est pas dispersée dans les contrôleurs ; elle est centralisée dans les services, ce qui améliore la maintenabilité et la testabilité.

### ✅ Gestion des bases de données avec JPA/Hibernate

Le projet exploite JPA pour les opérations CRUD et la persistance des données, avec une modélisation cohérente des relations entre entités.

### ✅ Réduction du code répétitif

L’utilisation de Lombok permet de diminuer la redondance du code Java et de garder les classes plus lisibles.

### ✅ Modularisation du projet

Les services sont séparés en modules distincts, ce qui reflète une architecture professionnelle orientée équipe et évolutivité.

### ✅ Contrôle des dépendances

Le projet utilise des dépendances Spring Boot et Spring Cloud bien structurées, avec une configuration centralisée et un cadre de développement cohérent.

### ✅ Conteneurisation

L’usage de Docker pour exécuter les services apporte une reproductibilité du développement et un meilleur contrôle de l’environnement.

### ✅ Tests et automatisation

Le projet intègre également des mécanismes de validation et de tests (UI tests, services, scripts Jenkins/Ansible), ce qui est un bon signe d’attention qualité et déploiement.

---

## Fonctionnalités principales

- gestion des bourses d’études,
- publication d’offres de financement,
- soumission de candidatures,
- validation des documents requis,
- gestion des profils utilisateurs,
- messagerie interne,
- notifications et alertes,
- recherche et filtres des bourses,
- architecture prête pour l’évolution et l’intégration de nouveaux services.

---

## Stack technologique

### Backend
- Java 17
- Spring Boot 3
- Spring Cloud
- Spring Data JPA
- Spring Kafka
- MySQL
- Eureka
- Spring Cloud Config

### Frontend
- Next.js
- React
- JavaScript / JSX
- Axios

### Outils / DevOps
- Maven
- Docker Compose
- Jenkins
- Ansible
- Git / GitHub

---

## Structure du projet

```text
Excellia_bourse/
├── config-service/
├── discovery-service/
├── gateway-service/
├── gestion-bourse-candidature-service/
├── inscription-service/
├── messagerie-service/
├── notification-service/
├── utilitiesService/
├── ui-tests/
├── src/
├── docker-compose.yaml
├── pom.xml
├── README.md
└── ...
```

---

## Démarrage rapide

### Prérequis

- Java 17+
- Maven
- Docker
- Docker Compose
- MySQL (si vous lancez les services localement)

### Lancer le projet

```bash
docker-compose up --build
```

### Vérifier les services

- Frontend : http://localhost:3000
- Gateway : http://localhost:8888
- Eureka : http://localhost:8761

---

## Conclusion

Excellia Bourse est un projet complet qui montre une bonne maîtrise des principes de l’architecture logicielle moderne : microservices, intégration de services, traitement asynchrone, déploiement conteneurisé et développement orienté produit.

Ce projet est un excellent exemple de travail à présenter sur GitHub pour mettre en valeur :

- la conception d’architecture,
- la gestion de services distribués,
- l’intégration backend/frontend,
- les bonnes pratiques de développement,
- la capacité à concevoir des solutions complètes et évolutives.

---
