Projet 5 — Créez et utilisez une base de données immobilière avec SQL (DATAImmo)




Contexte — Laplace Immo (réseau national d’agences). Projet DATAImmo pour mieux prévoir les prix via une base unifiée des transactions immobilières (DVF), enrichie par le référentiel géographique et la démographie INSEE.

Ce dépôt rassemble la modélisation 3NF, l’implémentation SQL, le chargement des données et les requêtes d’analyse.

🧭 Résumé exécutif

Concevoir un schéma relationnel 3NF robuste.

Créer les tables et importer les CSV en respectant types et contraintes.

Assurer la conformité RGPD (minimisation, anonymisation, traçabilité).

Analyser le marché (requêtes SQL avec agrégations, jointures, classements).

Présenter la démarche et les résultats (support de soutenance).

📦 Livrables

docs/dictionnaire_donnees.xlsx — Dictionnaire complété (DVF / INSEE / Référentiel).

schema/schema_relationnel.jpg — Schéma relationnel normalisé (3NF).

schema/ddl_create_tables.sql — DDL (création des tables, PK/FK, contraintes, index).

db/screenshots/ — Captures prouvant la création des tables & volumes chargés.

analyses/requetes.sql — Requêtes d’analyse (avec alias).

slides/presentation_DATAImmo.pptx — Support (≤ 10 slides, ≤ 7 éléments/slide).

reports/rgpd_conformite.md — Mesures RGPD et stratégie de sauvegarde.

🔍 Modèle de données (3NF)

Entités & clés (indicatif, alignées sur le dictionnaire)

region(code_region PK, nom_region)

commune(id_dep_commune PK, code_departement, nom_commune, code_region FK→region)

bien(Id_bien PK, id_dep_commune FK→commune, type_local, surfaces…, adresse…)

vente(id_vente PK, Id_bien FK→bien, date, valeur)

Contraintes suggérées

NOT NULL sur les clés et champs critiques ;

CHECK (bornes réalistes : surfaces ≥ 0, pièces 0–50, valeurs ≥ 0) ;

Index sur date, code_region, code_departement, type_local.

👤 Auteur & licence

Auteur : David Fernandes — David.Fernandes.data@gmail.com

Licence : CC BY‑NC‑SA 4.0
