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
Data Lake (Azure Blob Storage)
↓
ODS (Staging)
↓
Data Warehouse (modèle en étoile)
↓
Power BI Report
## ⚙️ Phase 1 – Data Engineering
- Stockage des fichiers sources dans un **Data Lake**
- Alimentation d'un **Data Warehouse** via un ODS
- Pipelines **Azure Data Factory** :
  - `Master_Pipeline_ODS` → chaîne ODS
  - `Master_Pipeline_DWH` → chaîne DWH
  - `Master_Pipeline` → ODS + DWH complet

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