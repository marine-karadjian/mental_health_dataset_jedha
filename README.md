# Mental Health Treatment – Exploratory Data Analysis & Machine Learning  
**JEDHA Essentials – Final Project**

## 📌 Contexte du projet

L’association **Mosaïque Mentale** souhaite lancer une **campagne de prévention en santé mentale**.  
L’objectif est de mieux comprendre **quels profils sont les plus concernés** par les troubles de santé mentale et **quels facteurs influencent le recours au traitement**, afin de cibler plus efficacement les actions de prévention.

La question centrale du projet est la suivante :

> **Quels facteurs influencent le plus la probabilité qu’un individu ait déjà suivi un traitement pour un problème de santé mentale ?**

Ce projet combine :
- une **analyse exploratoire des données (EDA)**,
- la mise en place de **modèles de machine learning**,
- et une **interprétation métier** orientée prévention et santé publique.

---

## 📊 Données

Le dataset contient des informations socio-démographiques et contextuelles, notamment :
- genre,
- pays et continent,
- antécédents familiaux en santé mentale,
- connaissance des options de soins,
- stress ressenti durant la croissance,
- historique personnel de santé mentale,
- statut professionnel.

La variable cible est :

- **`treatment`**
  - `1` → la personne a déjà suivi un traitement
  - `0` → la personne n’a jamais suivi de traitement

---

## 🔍 Exploratory Data Analysis (EDA)

### Biais structurel du dataset

- Forte **surreprésentation masculine** :
  - 82 % d’hommes
  - 18 % de femmes  
→ biais d’échantillonnage majeur.

- Malgré cela, les femmes ont **beaucoup plus souvent suivi un traitement** :
  - 69,4 % des femmes
  - 46,2 % des hommes  

👉 Les femmes consultent significativement plus que les hommes, indépendamment de leur sous-représentation dans le dataset.

---

### Géographie

**Répartition par continent :**
- North America : 65 %
- Europe : 28 %
- Autres continents : très minoritaires

Le dataset reflète majoritairement des **pays occidentaux**.

**Taux de traitement par continent :**
- Oceania : 65,4 %
- North America : 54,2 %
- Europe : 44,1 %
- Africa : 50,9 %
- South America : 22,2 %
- Asia : 13,9 %

👉 Ces écarts reflètent surtout :
- l’accès aux soins,
- la stigmatisation,
- les pratiques de diagnostic,  
et **non la prévalence réelle** des troubles mentaux.

**Country (Top 15)** : forte hétérogénéité  
Exemples :
- New Zealand : 80 %
- United States : 54,2 %
- India : 29,6 %
- Brazil : 33,3 %
- France / Israel : 0 % (effectifs très faibles → résultats à interpréter avec prudence)

---

### Antécédents familiaux

- 39,5 % des individus déclarent un **historique familial**.
- Taux de traitement :
  - Sans antécédents : 35,7 %
  - Avec antécédents : 73,0 %

👉 **Signal le plus fort du dataset**.

---

### Connaissance des options de soins

Taux de traitement selon `care_options` :
- Yes : 71,3 %
- No : 40,9 %
- Not sure : 39,3 %

👉 L’information sur les options de soins est un **levier majeur du passage au traitement**.

---

### Stress et historique personnel

- Répartition quasi équilibrée pour :
  - `Growing_Stress`
  - `Mental_Health_History`

Malgré cela :
- 49,75 % des personnes déclarant un historique de santé mentale **n’ont jamais suivi de traitement**.

👉 Le stress et l’historique personnel sont des **indicateurs de vulnérabilité**, mais **pas des déclencheurs suffisants** du recours aux soins.

---

### Statut professionnel

- Répartition relativement homogène.
- Impact marginal sur le recours au traitement.

---

## 🤖 Modélisation – Machine Learning

### Rôle du modèle

Le modèle de machine learning sert à :
- identifier des **profils à risque de non-recours aux soins**,
- mettre en évidence des **facteurs explicatifs**,
- aider à **prioriser le ciblage** de la campagne de prévention.

Il répond à la question :

> *Compte tenu de ses caractéristiques, cette personne a-t-elle une probabilité plus élevée que la moyenne d’avoir déjà suivi un traitement ?*

---

### Performances du modèle

- Accuracy (train) ≈ **70,97 %**
- Accuracy (test) ≈ **70,72 %**

👉 Environ **7 individus sur 10 correctement classés**.  
Le score est satisfaisant pour un **problème social complexe et multifactoriel**.  
Aucun signe d’overfitting : le modèle généralise correctement.

---

### Analyse par classe (test set)

**Classe 0 – Pas de traitement**
- Precision : 0,72
- Recall : 0,66  
→ Le modèle identifie correctement la majorité des personnes non traitées.

**Classe 1 – Traitement suivi**
- Precision : 0,69
- Recall : 0,75  
→ Bonne capacité à détecter les personnes ayant suivi un traitement.

**Confusion matrix (test set)** :
- Vrais négatifs : 19 083
- Vrais positifs : 21 942
- Faux négatifs : 7 295
- Faux positifs : 9 691

👉 Pour une campagne de prévention :
- Faux positifs = coût faible (message inutile)
- Faux négatifs = coût élevé (personnes à risque non ciblées)

Ce compromis est acceptable.

---

## 📈 Interprétation – Régression Logistique

Principaux facteurs explicatifs :

- **Antécédents familiaux** (+1,43)
- **Connaissance des options de soins** (+1,20)
- **Genre (homme)** (-0,59)
- **Continent** (effet lié à l’accès aux soins)
- Autres variables : impact marginal ou non significatif

👉 Les résultats mettent en évidence :
- le rôle central de l’environnement familial,
- l’importance de l’information,
- des freins culturels et sociaux persistants, notamment chez les hommes.

---

## 🧠 Synthèse globale

Facteurs influençant fortement le recours au traitement :
- antécédents familiaux,
- connaissance des options de soins,
- genre,
- contexte géographique et culturel.

Facteurs ayant peu d’impact :
- occupation,
- stress déclaré,
- historique mental isolé.

---

## 🎯 Recommandations pour la campagne de prévention

**Cibler en priorité :**
- les hommes,
- les personnes sans antécédents familiaux,
- les contextes où le recours au soin est peu normalisé.

**Orienter les messages vers :**
- une information claire et concrète sur les options de soins,
- la déstigmatisation du premier recours,
- la réduction des freins culturels et sociaux.

👉 Le levier principal n’est pas l’intensité du stress, mais **le passage à l’action** :
*quand consulter, comment, et pourquoi même en cas de doute.*

---

## 🚀 Conclusion

Ce projet montre que le machine learning peut être un **outil d’aide à la décision stratégique** pour des problématiques de santé publique, en complément d’une analyse humaine et contextuelle.

Le modèle ne remplace pas l’action sociale, mais permet de **prioriser les publics et les messages** afin de maximiser l’impact des campagnes de prévention.
