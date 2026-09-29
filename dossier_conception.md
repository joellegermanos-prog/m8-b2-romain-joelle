# Fiche de décision — <votre cas> (À COMPLÉTER)

**Client :** <nom, rôle> · **Groupe :** <prénoms> · **Cas <A/C/D>**

> **Livrable principal — 3-4 pages au maximum** (un plafond, pas une cible).
> Lisible par un architecte technique. Renommez en `dossier_conception.md`.
> Tout s'écrit **ici, une seule fois** : décisions, arbitrages, schéma et
> questions prévues. Tableaux plutôt que paragraphes.

---

## 1. Décisions de groupe (mardi 15h30-16h45)

> 3-5 points où vos cadrages M8-B1 divergeaient. Pas de compromis mou : un
> choix tranché et argumenté.

| Divergence | Positions (qui pensait quoi) | Décision retenue | Pourquoi |
| --- | --- | --- | --- |
| Prise en compte de la demande nocturne | Joëlle indique qu'aucune nouvelle contrainte n'a été communiquée et maintient une décision humaine, Romain rapporte la demande de la direction : arrêt automatique la nuit au-delà de 90 %, avec un seul chef d'équipe. | Considérer la demande comme une évolution réelle (exclure l'arrêt automatique du pilote en lecture seule). | Information manquante dans le cadrage de Joëlle. |
| Valeur probante de l'extrait capteurs | Joëlle observe une dérive sur les 48 h qui pourrait signaler des précurseurs, Romain précise que l'extrait BAIN-02 n'est associé à aucune panne et ne permet pas de valider une prédiction. | Utiliser l'extrait pour explorer les tendances, pas comme preuve de prédictibilité. | Sans panne étiquetée, les 48 mesures ne permettent pas de vérifier une anticipation. |
| Qualité des historiques | Joëlle juge les mesures horaires sur deux ans de qualité apparente bonne, Romain signale des lacunes lors de redémarrages, une sonde du bain 3 décalée de 2–3 °C et des causes de panne incertaines. | Auditer et fiabiliser les historiques avant entraînement et évaluation. | Environ 50 pannes sur deux ans, des biais de mesure ou des labels incertains peuvent fausser les résultats. |
| Approche de modélisation | Joëlle recommande l'analyse de séries temporelles, en ML classique ou détection d'anomalies, Romain propose une référence règles/tendances et une régression logistique supervisée si les pannes sont reliables. | Évaluer d'abord une référence simple, puis le modèle supervisé si les données le permettent, écarter le deep learning à ce stade. | Les quelque 50 pannes et quatre bains ne justifient pas une complexité accrue sans gain mesuré. |
| KPI et seuils de réussite | Joëlle fixe notamment 70 % de pannes détectées à 48 h, un seuil minimal de 60 %, un horizon minimal de 24 h et une réduction des arrêts de 20 %, Romain retient 70 % à 48 h et ajoute 1–2 alertes par semaine ainsi que des objectifs économiques à confirmer. | Garder 70 % à 48 h comme cible à tester, suivre séparément charge d'alertes et résultats métier, et confirmer les seuils d'acceptation avec les équipes. | Les critères ne sont pas tous équivalents, la limite de 1–2 alertes hebdomadaires doit notamment être précisée avant de juger le pilote. |

## 2. Les 5 arbitrages

> Pour chacun : **choix + raisons (≥ 1 chiffrée) + condition de changement
> d'avis** — ou « non applicable » en une ligne justifiée (+ ce qui ferait se
> poser la question). Répondre « SLM » ou « RAG » sur un cas sans texte pour
> remplir la grille est un signal de tropisme.

| Arbitrage | Choix — ou « non applicable » | Raisons (≥ 1 chiffrée) | On changerait d'avis si… |
| --- | --- | --- | --- |
| ML classique vs deep learning |  |  |  |
| SLM vs LLM |  |  |  |
| RAG oui / non |  |  |  |
| Agents oui / non |  |  |  |
| Zero-shot suffit ? |  |  |  |

## 3. Architecture finale et sobriété

```mermaid
flowchart LR
    A[Source] --> B[Traitement] --> C[Modèle] --> D[Sortie / humain]
```

<!-- Chaque brique découle d'un arbitrage. Commentez en 3-4 lignes. -->

**Ce qu'on n'a PAS mis (obligatoire)** : <!-- brique écartée + raison, ex. « pas de vector DB : RAG = non » -->

## 4. Évaluation

<!-- Comment on saura que ça marche AVANT la mise en service :
     baseline simple à battre, découpage des données (temporel si le temps compte),
     métriques alignées sur le KPI métier du cadrage. -->

## 5. Déploiement et monitoring (héritage M5 / M6)

<!-- Où et comment ça tourne, rollback. Puis : -->

| Question | Métrique | Seuil | Alerte vers |
| --- | --- | --- | --- |
| En vie ? |  |  |  |
| Prédit bien ? |  |  |  |
| Données qui dérivent ? |  |  |  |

<!-- Quand réentraîner, et qui décide. -->

## 6. Conformité et sécurité

<!-- Qualification AI Act et base légale RGPD reprises des cadrages (raisonnement,
     pas étiquette), en tenant compte de l'imprévu client de mardi 14h30.
     Chaque menace de sécurité retenue → sa réponse d'architecture + le risque résiduel. -->

## 7. Coûts (ordres de grandeur, sur VOTRE volumétrie)

<!-- ressources/fiche_chiffrage.md — à recalculer, pas à recopier. -->

| Poste | Estimation | Hypothèse |
| --- | --- | --- |
|  |  |  |

---

## ⭐ Optionnel — Pseudo-code du composant critique

```text
fonction <nom>(<entrées>):
    # 10-20 lignes : cas nominal, cas limite (donnée manquante, confiance basse…),
    # ce qui est journalisé.
```

## Annexe — 5 questions prévues (hors pagination)

| # | Question probable | Réponse préparée (2-3 lignes) | Qui répond |
| --- | --- | --- | --- |
| 1 |  |  |  |
| 2 |  |  |  |
| 3 |  |  |  |
| 4 |  |  |  |
| 5 |  |  |  |
