---
license: cc-by-4.0
language:
- fr
- en
pretty_name: Observatoire Point V1 — prix e-commerce et politiques de retour
size_categories:
- n<1K
task_categories:
- tabular-classification
tags:
- e-commerce
- shopify
- prix
- pricing
- politique-de-retour
- return-policy
- france
- europe
configs:
- config_name: prix_par_famille
  data_files: donnees/prix_par_famille.csv
- config_name: prix_par_famille_zone_euro
  data_files: donnees/prix_par_famille_zone_euro.csv
- config_name: politiques_retour_par_langue
  data_files: donnees/politiques_retour_par_langue.csv
---

# Observatoire Point V1 : prix e-commerce et politiques de retour

Ce jeu de données agrège les relevés publics de l'[Observatoire Point V1](https://pointv1.online/guides/observatoire.html). Il porte sur deux sujets : les prix de vente pratiqués par les boutiques Shopify, par famille de produits, et les politiques de retour qu'elles publient.

- **Prix** : 10 733 boutiques et 3 890 482 produits relevés. Le calcul en retient 9 151 boutiques. Mesure du 2026-11-11.
- **Retours** : 7 421 boutiques interrogées, dont 5 476 politiques lisibles en six langues. Mesure du 2026-09-18. Méthode et lecture : [politique de retour en e-commerce](https://pointv1.online/guides/politique-de-retour-ecommerce.html).

Ces chiffres alimentent l'[audit de rentabilité gratuit de Point V1](https://pointv1.online/audit.html), qui dit à un porteur de projet si sa boutique en ligne peut tenir.

## Fichiers

| Fichier | Contenu |
|---|---|
| `donnees/prix_par_famille.csv` | Prix médian, quartiles, intervalle de confiance à 95 % de la médiane, nombre de boutiques et de prix, par famille (univers élargi, converti en EUR) |
| `donnees/prix_par_famille_zone_euro.csv` | Prix médian par famille, boutiques de la zone euro seulement |
| `donnees/politiques_retour_par_langue.csv` | Délai médian de retour, part à 14 jours ou moins, part qui dit qui paie le port, par langue de la politique |
| `donnees/politiques_retour_synthese.csv` | Synthèse du relevé des retours, toutes langues confondues |
| `donnees/mesures.json` | Les mêmes agrégats avec leurs règles d'inclusion, au format lu par le moteur de Point V1 |

## Méthode, en bref

- Les prix viennent des catalogues publics des boutiques (`/products.json`). Les devises hors zone euro sont converties au taux de référence de la BCE, à la date indiquée. Les devises dont le niveau de prix ne se compare pas à la zone euro sont exclues.
- Une famille n'entre que si elle compte au moins 10 boutiques et si l'intervalle de confiance de sa médiane est plus étroit que 75 % de cette médiane.
- Les politiques de retour sont lues à `/policies/refund-policy`, un chemin que Shopify garantit et que son robots.txt autorise. Une requête par boutique. Les champs sont extraits par règles, sans modèle de langue.
- **Limite** : ce relevé mesure ce que les boutiques écrivent, pas ce que leurs clients font. Il ne donne pas le taux de retour réel.
- Aucune boutique n'est nommée. Le jeu ne contient aucune donnée personnelle.

## In English

Aggregated, public figures from the Point V1 Observatory: median selling prices of Shopify stores by product family (EUR, ECB rates) and the return policies those stores publish (return window, who pays return shipping), across six languages. No store is named. CC BY 4.0.

## Citer

Bichard, J. (2026). *Observatoire Point V1 : prix e-commerce et politiques de retour* (version 2026.11.11). Point V1. https://pointv1.online/guides/observatoire.html

## Licence

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Réutilisation libre, avec mention de la source : « Observatoire Point V1, pointv1.online ».
