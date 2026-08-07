# AfriMarket - Analyse stratégique (E-commerce, Marketing & Clients)

Projet **Data Analyst** : audit qualité → nettoyage → feature engineering → KPIs → analyses business (catégories, villes, marketing, clients) → recommandations actionnables.

## Livrables
- **Notebook d'analyse** : [`notebook/AfriMarket_Analyse_Strategique.ipynb`](notebook/AfriMarket_Analyse_Strategique.ipynb)
- **Rapport complet** : [`reports/Rapport_AfriMarket.pdf`](reports/Rapport_AfriMarket.pdf)
- **Présentation** : [`presentation/AfriMarket_Presentation.pdf`](presentation/AfriMarket_Presentation.pdf)
- **Dashboard Excel interactif** : [`excel/AfriMarket_Dashboard.xlsx`](excel/AfriMarket_Dashboard.xlsx)

## Contexte
AfriMarket est une entreprise e-commerce (cas d'étude) opérant dans plusieurs villes africaines et vendant des produits répartis en **4 catégories** : Électronique, Maison, Mode, Beauté.
Objectif : produire une analyse orientée **aide à la décision** (performance commerciale, efficacité marketing, comportement client) à partir d'un historique de commandes.

## Données
Dataset au format CSV (cas d'étude/formation) contenant des informations de commandes :
- transactions (date, produit, catégorie, quantité, prix, remise)
- géographie (ville)
- marketing (canal, coût marketing)
- opérations (coût livraison, statut commande)
- client (id client, méthode paiement)

### Dictionnaire (principales colonnes)
- `id_commande` : identifiant de commande
- `date_commande` : date de la commande
- `id_client` : identifiant client
- `nom_produit` : libellé produit
- `categorie` : catégorie produit
- `ville` : ville de livraison
- `quantite` : quantité commandée
- `prix_unitaire` : prix unitaire avant remise
- `remise` : taux de remise (ex: 0.10 = 10%)
- `canal_marketing` : canal d'acquisition
- `cout_marketing` : coût marketing imputé
- `cout_livraison` : coût logistique imputé
- `methode_paiement` : moyen de paiement
- `statut_commande` : Livrée / Annulée / Retournée

## Conclusion générale
L'analyse met en évidence **3 leviers prioritaires** :
1) **Réduire les retours sur la catégorie Électronique** (moteur du CA/profit mais principal driver de retours).
2) **Traiter l'anomalie d'annulation sur Douala** (signal opérationnel fort : logistique/paiement/statuts).
3) **Réallouer le budget vers les canaux les plus rentables (ROI) tout en contrôlant la qualité client via la rétention** (Email & Google Ads en tête).

## Objectifs
Le projet couvre :
- **Audit des données** (manquants, doublons, incohérences, valeurs aberrantes)
- **Nettoyage** documenté et reproductible
- **Feature engineering** (CA, marge/profit estimés, variables temporelles, indicateurs retours/annulations)
- **Analyses** :
  - performance globale
  - par **catégorie**
  - par **ville**
  - par **canal marketing** (ROI + rétention)
  - **clients** (Pareto + segmentation RFM)
- **Recommandations** business

## Résultats clés
- **Commandes** : 8 814
- **Clients uniques** : 1 719
- **CA total** : 2 384 892,57
- **Profit net estimé** : 667 401,70
- **Panier moyen** : 275,93
- **Taux d'annulation** : 1,94%
- **Taux de retour** : 8,17%

### Marketing
- **ROI = (CA - coût marketing) / coût marketing**
  - Email : ROI ≈ 231,46
  - Google Ads : ROI ≈ 50,03
  - Instagram Ads : ROI ≈ 24,64
  - Influenceur : ROI ≈ 21,04

- **Rétention (first-touch)** : canal de la 1ère commande ; client retenu si ≥2 commandes (hors annulations)
  - Influenceur : 74,81%
  - Google Ads : 74,09%
  - Instagram Ads : 69,68%
  - Email : 69,25%

### Villes
- **Douala : annulation ≈ 12,94%** → alerte opérationnelle (audit logistique/paiement/statuts)

### Segmentation clients (RFM)
Le poids économique de chaque segment compte davantage que son effectif :

| Segment | Clients | % CA |
|---|---|---|
| VIP | 475 (27,8%) | **73,2%** |
| Fidèles | 323 (18,9%) | 13,6% |
| À réactiver | 597 (35,0%) | 9,1% |
| Occasionnels | 312 (18,3%) | 4,2% |

Les 475 VIP portent près des trois quarts du CA, bien davantage que le segment le plus nombreux ("À réactiver").

## Méthodologie & hypothèses
- Les KPIs et analyses sont réalisés sur un dataset nettoyé `df_clean`.
- Le **profit net estimé** est un indicateur de contribution : **CA - coûts marketing - coûts logistique**.
- Chaque anomalie de données (prix négatifs, remises négatives, quantités nulles) a été corrigée ou supprimée selon que sa valeur absolue est statistiquement plausible ou non ( voir le notebook pour le détail du diagnostic).

## Dashboard Excel
`excel/AfriMarket_Dashboard.xlsx` propose une exploration interactive des données : listes déroulantes (ville, catégorie, canal marketing), cartes KPI, graphiques par catégorie/ville/canal, évolution mensuelle, segmentation clients, top 10 clients et courbe de Pareto.

![Dashboard Excel](excel/Capture_dashboard_excel.png)

## Recommandations (5 actions)
1) **Plan anti-retours** sur Électronique : QA, fiches produits, packaging, SAV.
2) **Task-force Douala** : diagnostic logistique/paiement + suivi hebdo du taux d'annulation.
3) **Réallocation marketing** : scaler Email & Google Ads avec garde-fous (CPA/ROAS).
4) **CRM par segments** (VIP/Fidèles/Occasionnels/À réactiver) + scénarios winback.
5) **Tableau de bord mensuel** : CA / profit estimé / retours / annulations.

---

## Installation
1) Installer les dépendances :
```bash
pip install -r requirements.txt
```

2. Lancer Jupyter :

```bash
jupyter notebook
```

3. Ouvrir le notebook :
   `AfriMarket_Analyse_Strategique.ipynb`

## Auteur
Laté LAWSON
