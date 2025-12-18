# Mental Health Treatment – Exploratory Data Analysis & Machine Learning  
**JEDHA Essentials – Final Project**

## 📌 Contexte du projet

L’association **Mosaïque Mentale** souhaite lancer une campagne de prévention en santé mentale.  
L’objectif est d’identifier les **facteurs qui influencent le recours au traitement**, afin de mieux cibler les populations à risque de non-recours aux soins.

**Question centrale :**  
> Quels facteurs influencent le plus la probabilité qu’un individu ait déjà suivi un traitement pour un problème de santé mentale ?

---

## 📊 Méthodologie globale

Le projet s’articule en trois grandes étapes :
1. **Exploratory Data Analysis (EDA)** pour comprendre les données et identifier des signaux forts
2. **Pré-processing et encodage** des variables
3. **Modélisation en machine learning** et interprétation métier des résultats

---

## 🔍 Exploratory Data Analysis – Résultats clés

### Biais du dataset
- Forte surreprésentation masculine (82 % hommes, 18 % femmes)
- Malgré cela, les femmes ont nettement plus souvent suivi un traitement :
    - Femmes : 69,4 %
    - Hommes : 46,2 %

Le genre est un facteur structurant du recours aux soins.

---

### Géographie
- Dataset majoritairement occidental (North America + Europe ≈ 93 %)
- Taux de traitement très hétérogènes selon les continents
  - Élevé en Océanie et Amérique du Nord
  - Très faible en Asie et Amérique du Sud

Ces écarts reflètent surtout l’accès aux soins et la stigmatisation, pas la prévalence réelle.

---

### Antécédents familiaux
- 39,5 % déclarent un historique familial
- Taux de traitement :
  - Sans antécédents : 35,7 %
  - Avec antécédents : 73,0 %

Signal le plus fort observé dans l’EDA.

---

### Connaissance des options de soins
- Les personnes connaissant les dispositifs de soin consultent presque deux fois plus.

L’information apparaît comme un levier majeur de prévention.

---

### Stress, historique personnel et occupation
- Stress et historique mental personnel : répartition équilibrée mais faible pouvoir explicatif.
- Occupation : impact marginal

La vulnérabilité perçue seule ne suffit pas à déclencher le passage au soin.

---

## 🤖 Machine Learning

### Pré-processing & encodage

- One-hot encoding des variables catégorielles :
  - `Gender`, `Continent`, `Occupation`
- Conversion manuelle des variables Oui / Non en booléens :
  - `family_history`
  - `treatment` (target)
  - `Mental_Health_History`
  - `care_options`

La variable cible est :
- `Treatment_bool`
  - 1 → traitement déjà suivi
  - 0 → aucun traitement

Le dataset est séparé en train / test (80 % / 20 %) avec stratification sur la target.

---

### Choix du modèle

- **Régression logistique**
  - modèle interprétable
  - adapté à un problème binaire
  - pertinent dans un contexte métier et social où l’explicabilité est clé

---

### Performances du modèle

- Accuracy (train) ≈ **70,97 %**
- Accuracy (test) ≈ **70,72 %**

Bonne capacité de généralisation, pas d’overfitting.

**Lecture métier :**
- Faux positifs : coût faible (message de prévention inutile)
- Faux négatifs : coût élevé (personnes à risque non ciblées)

Le compromis du modèle est donc acceptable pour une campagne de prévention.

---

## 📈 Interprétation des résultats (coefficients)

**Facteurs les plus influents** :
- Antécédents familiaux (+)
- Connaissance des options de soins (+)
- Genre (homme) (−)
- Contexte géographique (+ / − selon régions)

Facteurs à impact faible :
- stress déclaré
- occupation
- historique mental personnel isolé

Le modèle met en évidence des freins culturels et informationnels, plus que des facteurs cliniques.

---

## 🧠 Synthèse & interprétation métier

Le recours au traitement dépend principalement :
- de l’environnement familial,
- de l’accès à l’information,
- des normes sociales et culturelles,
- du genre.

Le stress ou la souffrance perçue ne suffisent pas à expliquer le passage au soin.

---

## 🎯 Recommandations pour la campagne de prévention

**Cibler en priorité :**
- les hommes,
- les personnes sans antécédents familiaux,
- les contextes où le recours au soin est peu normalisé.

**Orienter la communication vers :**
- l’information concrète sur les options de soins,
- la déstigmatisation du premier recours,
- le passage à l’action (quand consulter, comment, pourquoi).

Le modèle est un outil d’aide à la décision stratégique, permettant de prioriser les publics et les messages.

---

## 🚀 Conclusion

Ce projet montre l’intérêt du machine learning interprétable pour éclairer des enjeux de santé publique.  
La valeur principale réside dans la **compréhension des mécanismes sociaux du non-recours aux soins**, afin de concevoir des campagnes de prévention plus efficaces et ciblées.
