# Analyse des ventes d’une PME 

Ce projet a été réalisé dans le cadre de la **préparation à la journée de sélection du parcours Data Engineer chez Simplon**.

Il consiste à concevoir et déployer une **architecture data simple**, permettant d’importer, stocker et analyser des données de ventes fournies par un client fictif (PME de services numériques).

Les données concernent les ventes réalisées sur une période de 30 jours, ainsi que des informations sur les produits et les magasins répartis dans plusieurs villes de France.

---

## Objectifs du projet

- Concevoir une architecture à deux services :
  - Un service pour l’exécution des scripts
  - Un service pour le stockage des données (SQLite)
- Mettre en place l’architecture avec Docker et Docker Compose
- Analyser les jeux de données fournis
- Concevoir un schéma de base de données relationnelle
- Importer les données en base SQLite
- Gérer l’import incrémental des ventes (éviter les doublons)
- Réaliser une première analyse des ventes avec SQL
- Stocker les résultats des analyses en base de données

---

## Architecture

L’architecture repose sur deux services Docker :

### Service Scripts
- Exécute des scripts en Python
- Télécharge les fichiers CSV depuis des URLs via des requêtes HTTP
- Crée la base de données et les tables
- Importe les données
- Lance les requêtes d’analyse SQL

### Service Base de données
- Base de données SQLite
- Stocke les données métiers (ventes, produits, magasins)
- Stocke les résultats des analyses

Les deux services communiquent via un volume partagé.

---

## Données utilisées

Trois fichiers CSV fournis par le client :

- **Produits**
  - ID produit
  - Nom
  - Prix
- **Magasins**
  - ID magasin
  - Ville
  - Région
- **Ventes**
  - ID vente
  - Date
  - Produit
  - Magasin
  - Quantité

Le fichier des ventes étant mis à jour en continu, le script vérifie que les lignes à importer ne sont pas déjà présentes en base de données.

---

## Modélisation des données

La base de données comprend :
- Des tables pour les données métiers (produits, magasins, ventes)
- Des tables dédiées au stockage des résultats d’analyses

Un schéma relationnel (type MCD) est fourni dans les livrables.

---

## Analyses réalisées

Les requêtes SQL permettent de répondre aux questions suivantes :

- Calcul du chiffre d’affaires total
- Analyse des ventes par produit
- Analyse des ventes par région

Les résultats sont enregistrés dans la base de données.

---

## Technologies utilisées

- Python
- SQLite
- Docker
- Docker Compose
- SQL
- HTTP (requêtes pour récupérer les fichiers CSV)

---

## Livrables

- Schéma de l’architecture
- Schéma des données (MCD)
- Dockerfile
- docker-compose.yml
- Scripts Python (collecte, création de la base, import, analyses)
- Fichier SQL des requêtes
- Note de synthèse des résultats d’analyse

---

## Durée estimée

1 à 2 jours

