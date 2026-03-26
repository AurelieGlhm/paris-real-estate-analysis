# Etude du marché immobilier parisien 

## Contexte
Ce projet a été réalisé dans le cadre de ma formation **Analytics Engineer** chez DataScientest.  
L’objectif principal est de construire une base de données enrichie, fiable et structurée, combinant des données internes issues des Demandes de Valeurs Foncières (DVF), avec des données externes accessibles via des sources ouvertes (données géographiques, économiques, réglementaires, etc.).
- Utilisation de Python (pandas) pour l'extraction des fichiers de vente et l'interrogation de plusieurs APIs publiques, ainsi que le nettoyage, la mise et en forme et la transformation des données.
- Utilisation de SQL (PostgreSQL) pour la création de la base de données, l'insertion et le chargement des données transformées préalablement.
- Création de rapports dynamiques et interactifs via PowerBI, permettant d'avoir une meilleure compréhension des dynamiques du marché immobilier parisien.

---

## Objectif
- Explorer les ventes immobilières à Paris (DVF) sur 2020 à 2024
- Enrichir les données avec des informations contextuelles : zones à risque, établissements scolaires, espaces verts, encadrement des loyers, données cadastrales  
- Construire un **pipeline Python reproductible** pour le traitement et l’intégration des données  
- Produire un tableau de bord Power BI synthétique pour visualiser les insights clés  

---

## Données
Les données utilisées incluent :
- **Ventes immobilières (DVF)** : récupérées via API publique  
- **Zones à risque, établissements scolaires, espaces verts, encadrement des loyers, données cadastrales** : données publiques et fichiers CSV traités par Python  
- **Fichier `adresses_gps.csv`** : fichier de correspondance adresses/coordonnées GPS (non versionné sur GitHub pour des raisons de volume)

> Tous les fichiers générés automatiquement (`OutData/*.csv`) ne sont pas versionnés afin de garantir un repo léger et reproductible.

---

## Structure du projet

```
paris-real-estate-analysis/
├── data/
│   ├── raw/            # Données brutes / intermédiaires (ignorées par GitHub)
│   └── processed/      # Données traitées (ignorées par GitHub)
├── dashboard/          # Fichier Power BI (.pbix)
├── reports/            # Rapport final en PDF
├── sql/                # Script SQL pour créer la BDD
├── src/                # Scripts Python pour le traitement des données
│   ├── constantes.py
│   ├── ET_Bois.py
│   ├── ET_EncadrementLoyer.py
│   ├── ET_Espaces_verts.py
│   ├── ET_EtablissementScolaires.py
│   ├── ET_risque.py
│   ├── ET_ValeursFoncieres.py
│   └── functions.py
├── requirements.txt    # Librairies Python nécessaires
└── README.md
```
---

## Pipeline Python
1. Récupération des données via API et fichiers publics
2. Nettoyage et transformation des données dans les scripts ET_*.py
3. Fonctions réutilisables centralisées dans functions.py
4. Export des fichiers traités dans data/processed/
5. Création de la base de données via init_db.sql (modélisation en flocon)
6. Analyse et visualisation dans Power BI (dashboard/) (modélisation en étoile - plus performant pour la construction de rapports analytiques)

---

## Résultats
Tableau de bord Power BI présentant :
- Répartition des ventes par arrondissement
- Zones à risque
- Proximité aux écoles et espaces verts
- Analyse des prix et tendances du marché
- Par ailleurs, afin d’enrichir l'analyse avec un éclairage sur le contexte économique, il a été décidé d’ajouter deux fichiers complémentaires contenant les taux d’inflation (données mensuelles) et les taux d’intérêt des crédits (données trimestrielles).

---

## Reproduction

Pour reproduire le projet localement :

1. Installer les librairies Python listées dans requirements.txt :
```
pip install -r requirements.txt
```
2. Lancer les scripts Python dans l’ordre souhaité pour générer les fichiers CSV
3. Créer la base de données avec init_db.sql
3. Ouvrir le fichier Power BI pour visualiser le tableau de bord

---

## Remarques
Les CSV intermédiaires et volumineux ne sont pas versionnés pour conserver un repo léger.  
Ce projet met l’accent sur la reproductibilité, la structuration du code et la documentation claire pour un usage professionnel.

---

## Accès rapide
- [Rapport PDF](reports/rapport_immobilier_paris.pdf)
- [Tableau de bord Power BI](dashboard/projet_immobilier_paris.pbix)
- [Scripts Python](src/)
- [Script SQL](sql/init_db.sql)
