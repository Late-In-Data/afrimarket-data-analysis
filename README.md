# AfriMarket — Analyse stratégique (E-commerce, Marketing & Clients)

Projet **Data Analyst** : audit qualité → nettoyage → feature engineering → KPIs → analyses business (catégories, villes, marketing, clients) → recommandations actionnables.

**Livrable :**
- Notebook : `AfriMarket_Analyse_Strategique.ipynb`

## Contexte
AfriMarket est une entreprise e-commerce (cas d’étude) opérant dans plusieurs villes africaines et vendant des produits répartis en **4 catégories** : Électronique, Maison, Mode, Beauté.  
Objectif : produire une analyse orientée **aide à la décision** (performance commerciale, efficacité marketing, comportement client) à partir d’un historique de commandes.

## Données
Dataset au format CSV (cas d’étude/formation) contenant des informations de commandes :
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
- `canal_marketing` : canal d’acquisition  
- `cout_marketing` : coût marketing imputé  
- `cout_livraison` : coût logistique imputé  
- `methode_paiement` : moyen de paiement  
- `statut_commande` : Livrée / Annulée / Retournée

## Conclusion générale
L’analyse met en évidence **3 leviers prioritaires** :
1) **Réduire les retours sur la catégorie Électronique** (moteur du CA/profit mais principal driver de retours).  
2) **Traiter l’anomalie d’annulation sur Douala** (signal opérationnel fort : logistique/paiement/statuts).  
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
  - **clients** (Pareto + segmentation RFM simplifiée)
- **Recommandations** business

## Résultats clés
- **Commandes** : 8 814  
- **Clients uniques** : 1 719  
- **CA total** : 2 384 892,57  
- **Profit net estimé** : 667 401,70  
- **Panier moyen** : 275,93  
- **Taux d’annulation** : 1,94%  
- **Taux de retour** : 8,17%

### Marketing
- **ROI = (CA – coût marketing) / coût marketing**
  - Email : ROI ≈ 233,45  
  - Google Ads : ROI ≈ 50,29  
  - Instagram Ads : ROI ≈ 24,84  
  - Influenceur : ROI ≈ 21,27  

- **Rétention (first-touch)** : canal de la 1ère commande ; client retenu si ≥2 commandes (hors annulations)
  - Influenceur : 75,19%  
  - Google Ads : 74,64%  
  - Email : 70,89%  
  - Instagram Ads : 70,63%  

### Villes
- **Douala : annulation ≈ 12,94%** → alerte opérationnelle (audit logistique/paiement/statuts)

### Segmentation clients (RFM simplifiée)
- À réactiver : 597  
- VIP : 475  
- Fidèles : 323  
- Occasionnels : 312  

## Méthodologie & hypothèses
- Les KPIs et analyses sont réalisés sur un dataset nettoyé `df_clean`.
- Le **profit net estimé** est un indicateur de contribution : **CA – coûts marketing – coûts logistique**.  

## Recommandations (5 actions)
1) **Plan anti-retours** sur Électronique : QA, fiches produits, packaging, SAV.
2) **Task-force Douala** : diagnostic logistique/paiement + suivi hebdo du taux d’annulation.
3) **Réallocation marketing** : scaler Email & Google Ads avec garde-fous (CPA/ROAS).
4) **CRM par segments** (VIP/Fidèles/Occasionnels/À réactiver) + scénarios winback.
5) **Tableau de bord mensuel** : CA / profit estimé / retours / annulations.

---

## Installation (Conda)
1) Créer l’environnement :
```bash
conda env create -f environment.yml
conda activate env_afrimarket
````

2. Lancer Jupyter :

```bash
jupyter notebook
```

3. Ouvrir le notebook :
   `AfriMarket_Analyse_Strategique.ipynb`

## Auteur
Laté LAWSON
