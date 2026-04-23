# 🏦 Analyse de Performance Bancaire – Bankia (Power BI)

Dashboard décisionnel complet pour analyser la performance commerciale
et financière d'une banque fictive multi-agences.

## 🎯 Contexte
Bankia est une banque fictive disposant de plusieurs agences réparties
dans différentes villes. Ce projet simule une mission réelle de
Data Engineer + Data Analyste : construire un système décisionnel
de A à Z, de l'ingestion des données brutes jusqu'au rapport Power BI final.

## 🏗️ Architecture globale
Fichiers sources (XLS, CSV, TXT)
↓
Data Lake (ADLS Gen2)
↓
ODS (bankia_ods_db)
↓
Staging (STG_)
↓
DWH (bankia_dwh_db) → DIM_ + FACT_*
↓
Power BI

## ⚙️ Phase 1 – Data Engineering
- Stockage des fichiers sources dans un **Data Lake**
- Alimentation d'un **Data Warehouse** via un ODS

  ### Rôle des couches
| Couche | Contenu | Utilité |
|--------|---------|---------|
| ODS | Tables proches des sources | Centraliser les données nettoyées |
| STG | Copie locale des lignes détaillées | Préparer les jointures avec les dimensions |
| DWH | Dimensions + Faits | Modèle décisionnel pour Power BI |

### Pipelines ADF
| Pipeline | Rôle |
|----------|------|
| `Master_Pipeline_ODS` | Charge toutes les tables ODS depuis le Data Lake |
| `Master_Pipeline_DWH` | Alimente dimensions, staging et faits |
| `Master_Pipeline` | Orchestre ODS + DWH de bout en bout |

## 📊 Phase 2 – Rapport Power BI

### Pages du rapport
| Page | Contenu |
|------|---------|
| 🔄 Transactions | Volume, valeur, évolution mensuelle/annuelle |
| 💳 Produits | Produits les plus utilisés, clients rentables |
| 💰 Finances | Revenus vs dépenses, marge nette, top agences |

### Mesures DAX clés
- Revenus totaux par produit et par agence
- Marge nette = Revenus – Dépenses
- Cumul des transactions (MTD / YTD)
- Top clients par rentabilité
- Taux d'utilisation par type de produit

### Filtres dynamiques
- Par agence / ville
- Par type de produit
- Par période (mois, trimestre, année)
- Par segment client (Particulier, Professionnel, Entreprise)

## 📁 Sources de données
| Fichier | Description |
|---------|-------------|
| `clients.xls` | Données clients avec segmentation |
| `agences.txt` | Liste des agences par ville |
| `produits_bancaires.csv` | Catalogue des produits (comptes, crédits, cartes, épargne) |
| `transactions.csv` | Opérations clients |
| `depenses.csv` | Charges de fonctionnement par agence |

## 🌟 Fonctionnalités bonus
- Segmentation dynamique des clients (Premium / Réguliers / Inactifs)
- Recommandations pour améliorer la rentabilité

## 🛠️ Outils utilisés
Power BI Desktop · DAX · Power Query · Azure Data Factory · SQL Server

## 📸 Aperçu
<!-- Ajoute tes captures d'écran ici -->
![Dashboard Transactions](screenshots/transactions.png)
![Dashboard Finances](screenshots/finances.png)