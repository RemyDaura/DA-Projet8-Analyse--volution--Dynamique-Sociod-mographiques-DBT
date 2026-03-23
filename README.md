# DA-Projet8-Analyse--volution--Dynamique-Sociod-mographiques-DBT
# Modélisation de Données avec dbt et Snowflake

![dbt](https://img.shields.io/badge/dbt-FF694B?style=for-the-badge&logo=dbt&logoColor=white)
![Snowflake](https://img.shields.io/badge/Snowflake-29B5E8?style=for-the-badge&logo=snowflake&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)

## Contexte du Projet
Ce projet a été réalisé dans le cadre de mon parcours de Data Analyst. L'objectif était de mettre en place un pipeline de transformation de données moderne (ELT) pour analyser le profil démographique des étudiants d'un organisme de formation, en croisant leurs données avec celles de l'INSEE.

**Mission :** Créer un modèle de données fiable, documenté et testé, servant de source unique de vérité pour les équipes de Business Intelligence.

## Architecture Technique
* **Data Warehouse :** Snowflake (Stockage des données brutes et matérialisation des modèles).
* **Transformation :** dbt (data build tool) pour l'orchestration des requêtes SQL, la documentation et les tests.
* **Contrôle de version :** Git & GitHub.

## Structure du Projet (Workflow dbt)
Le projet respecte les bonnes pratiques de modélisation analytique avec une séparation stricte des couches :

* `models/staging/` : La couche de nettoyage.
  * `stg_students.sql` : Standardisation des régions, gestion des valeurs nulles et dédoublonnage des inscriptions (matérialisé en Vue).
  * `stg_insee.sql` : Préparation des données de population (matérialisé en Vue).
* `models/marts/` : La couche métier.
  * `mart_student_profiling.sql` : Modèle d'agrégation final croisant les étudiants et la population INSEE pour générer les KPI finaux (matérialisé en Table pour des performances d'affichage optimales).

## Qualité et Tests
La qualité des données est garantie via le fichier `schema.yml`. Les tests suivants sont exécutés à chaque run :
* Tests d'unicité (`unique`) sur les clés primaires.
* Tests de non-nullité (`not_null`) sur les champs critiques.
* Tests de valeurs acceptées (`accepted_values`) pour le genre ou les régions.

## Comment exécuter ce projet en local ?

1. Clonez ce dépôt :
   ```bash
   git clone [https://github.com/RemyDaura/nom-de-ton-repo.git](https://github.com/RemyDaura/nom-de-ton-repo.git)
