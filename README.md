# Nutrition POC

---

## Introduction

Vous êtes missionnés par un client pour réaliser une analyse exploratoire sur les données de nutrition Open Source. En effet ce client souhaiterait développer une application utilisant ces données et souhaiterai connaitre la faisabilité et la plus-value.

## Ressources

---

[](https://static.openfoodfacts.org/data/en.openfoodfacts.org.products.csv)

**Open Data Nutrition**

[](https://world.openfoodfacts.org/data/data-fields.txt)

**MetaData**

---

# Contexte du projet

## *Manger mieux pour vivre mieux*

---

> **Conseils healthy (oranges)**
>

### Part 1

---

- [x]  Stockage de l'ensemble des données dans une BDD
- [x]  Connexion à votre base via un script Python
- [x]  Répondre aux questions SQL en PJ



## Requêtes SQL

```sql
Nombre de produits par nutriscore

SELECT count(*) AS 'products_count', nutriscore_grade FROM nutrition.products
	GROUP by nutriscore_grade;

Quel est le pourcentage de représentation associé?

SELECT nutriscore_grade, COUNT(*) * 100.0 / (SELECT COUNT(*) FROM openfoodfacts.products)
FROM openfoodfacts.products 
GROUP by nutriscore_grade;
```

---

```sql
Les 4 valeurs possibles du Nova_Group

SELECT nova_group FROM nutrition.products
	GROUP BY Nova_group;
```

---

```sql
Quel est la moyenne des fibres par nutriscore ?

SELECT AVG(fiber_100g) AS 'moyenne fibres', nutriscore_grade FROM nutrition.products
	GROUP BY nutriscore_grade;
```

---

```sql
Quels sont le TOP10 des pnns_groups_2 qui comportent le plus d'additif

SELECT pnns_groups_2, MAX(additives_n)
FROM openfoodfacts.products
GROUP BY pnns_groups_2
LIMIT 10;
```

---

```sql
Afficher le taux de sucre/fat moyen et médian des produits avec un nutriscore A ou B

SELECT AVG(sugars_100g) AS 'Moyenne Sucre', product_name
FROM openfoodfacts.products
WHERE nutriscore_grade='a' OR nutriscore_grade='b'
GROUP BY product_name;
```

```sql
Combien avons-nous de produits qui ont un taux de carbohydrates > aux sucres

SELECT COUNT(DISTINCT product_name) AS 'Total des produits'
FROM openfoodfacts.products
WHERE carbohydrates_100g > sugars_100g;
```

---

### Part 2

---

- [x]  Traiter le jeu de données afin de repérer des variables pertinentes pour les traitements à venir.
- [ ]  Automatiser ces traitements pour éviter de répéter ces opérations.
- [ ]  Le programme doit fonctionner si la base de données est légèrement modifiée (ajout d’entrées, par exemple).
- [x]  Tout au long de l’analyse, produire des visualisations dynamiques (avec ++plotly++) afin de mieux comprendre les données.
- [x]  Effectuer une analyse univariée pour chaque variable intéressante, afin de synthétiser son comportement.
- [ ]  Variez les graphiques (boxplots, histogrammes, diagrammes circulaires, nuages de points…) pour illustrer au mieux votre propos.
- [ ]  Confirmer ou infirmer les hypothèses à l’aide d’une analyse multivariée.
- [ ]  Effectuer les tests statistiques appropriés pour vérifier la significativité des résultats.
- [ ]  Élaborer une idée (juste une idée !) d’application.
- [ ]  Identifier des arguments justifiant la faisabilité (ou non) de votre idée d'application à partir des données Open Food Facts et de vos analyses.

[Tasks](https://www.notion.so/9f8dbbc153804e25923c0429429c1ab3)

## **Modalités pédagogiques**

---

Rendus pour mardi 12/10 15h30

Un retroplanning devra être fait de manière détaillé avant de démarrer puis, évidemment, maintenu à jour.

**Groupe** : Véronique, Adil, Cédric

---

## Livrables

---

- Un notebook comprenant vos requêtes relatives à la Part.1 (OK)
- Un notebook du nettoyage des données (OK)
- Un notebook d’exploration comportant une analyse univariée, multivariée ainsi que les différentes questions de recherches associées (in progress)
- Une note méthodologique de réutilisation de vos notebooks (environnement, packages, données, etc)
- **Une présentation, à utiliser en support pour la soutenance, comprenant**
  - La présentation de votre idée d’application.
  - Les opérations de nettoyage effectuées.
  - La description et l'analyse univariée des différentes variables importantes avec les visualisations associées.
  - L’analyse multivariée et les résultats statistiques associés, en lien avec votre idée d’application.
  - 3 observations solidement étayées (graphes et/ou tests statistiques à l’appui au besoin) évaluant la pertinence et la faisabilité de votre application.
  - La synthèse des différentes conclusions sur la faisabilité de votre projet.
- Github ou Drive condensant l'ensemble de ces livrables

---
