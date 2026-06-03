# Olist E-Commerce — Audit de la Satisfaction Client

## Contexte Business

Le Directeur Marketing d'Olist, marketplace brésilienne leader en e-commerce,
constate une baisse de satisfaction client sur les 3 derniers mois. La note moyenne
est passée de **4.2 à 3.8 / 5**. Il mandate une analyse complète pour identifier
les causes et formuler des recommandations actionnables avant le prochain comité
de direction.

Ce projet suit une démarche analytique structurée :
**Hypothèses → Données → Test → Recommandations**

## Stack Technique

- **Python** : Pandas · NumPy · Matplotlib
- **Environnement** : Jupyter Notebook / VS Code
- **Dataset** : [Brazilian E-Commerce Public Dataset — Olist (Kaggle)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- **Volume** : 96 361 commandes livrées · 9 tables relationnelles

---

## Key Findings

- **Les retards de livraison sont la cause principale** : note moyenne de **4.29** pour les commandes à l'heure vs **1.71** pour les commandes en retard de plus de 12 jours
- **1 704 commandes** en retard critique (>12 jours) — clients à risque de churner
- **Les transporteurs sont responsables à 82%** des délais : 9 jours en moyenne vs 2 jours côté vendeurs
- **Office_furniture** est la catégorie la plus mal notée (3.52/5) sur 1 664 commandes — produits volumineux, fragiles, exposés aux incidents de transport
- **La satisfaction stagne à 4.1/5** depuis mi-2017 — dans un marché concurrentiel, stagner équivaut à reculer
- **Le retard n'est pas le seul facteur** : des mauvaises notes existent même pour les commandes livrées à l'heure — la qualité produit est un levier distinct

---

## Recommandations

**Court terme :**
- Compenser les 1 704 clients en retard critique (bon de réduction, remboursement partiel)
- Alertes automatiques dès 7 jours de retard pour intervention proactive

**Long terme :**
- Renégocier les contrats transporteurs ou diversifier les partenaires logistiques
- Imposer des SLAs de livraison stricts sur les catégories lourdes (mobilier, bureautique)
- Audit qualité sur les vendeurs des catégories mal notées

---

## Structure du Projet

```
olist_marketplace_analysis/
│
├── olist.ipynb                  # Notebook principal — analyse complète
├── README.md                    # Ce fichier
└── archive/OlistMarket/         # Dataset source (non versionné, à télécharger)
    ├── olist_orders_dataset.csv
    ├── olist_order_reviews_dataset.csv
    ├── olist_order_items_dataset.csv
    ├── olist_products_dataset.csv
    └── olist_product_category_name_translation.csv
```

---

## Analyses Réalisées

| # | Analyse | Méthode | Insight clé |
|---|---------|---------|-------------|
| 1 | Corrélation retard vs satisfaction | Filtres Pandas + comparaison moyennes | 4.29 vs 1.71 selon le retard |
| 2 | Origine des retards | Décomposition chaîne logistique | Transporteurs : 9j vs Vendeurs : 2j |
| 3 | Satisfaction par catégorie | groupby + agg | Office_furniture flop, Books top |
| 4 | Évolution mensuelle satisfaction | Time series + line chart | Stagnation à 4.1 depuis 2017 |

---

## Limites Méthodologiques

- La review est au niveau commande — une commande multi-produits réplique la même note sur chaque produit (biais sur les catégories à fort volume)
- Les données 2016 sont non représentatives (< 10 commandes/mois au lancement)
- Les données de coût d'achat ne sont pas disponibles — impossible de calculer l'impact marge des retards

---

## Lancer le Projet

```bash
git clone https://github.com/votre-github/olist_marketplace_analysis
cd olist_marketplace_analysis
jupyter notebook olist.ipynb
```

Dataset à télécharger sur Kaggle :
→ https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce
