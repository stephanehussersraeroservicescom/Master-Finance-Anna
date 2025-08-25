# Partie I — Cours principal (Niveau 1 enrichi)

---

## Chapitre 1 : Introduction

La finance moderne ne consiste pas seulement à **compter l’argent**, mais à comprendre **comment les gens prennent des décisions en situation d’incertitude**.  

Historiquement, les économistes se sont aperçus que :  
- Les individus ne choisissent pas forcément l’option avec la meilleure **espérance mathématique** (le “gain moyen”).  
- Exemple : dans le paradoxe de Saint-Pétersbourg (Daniel Bernoulli, 1738), une loterie a une valeur attendue infinie, mais aucun joueur ne paierait une somme énorme pour y participer.  

👉 Cela veut dire qu’il fallait une autre notion que la simple “espérance de richesse” pour modéliser les choix.  
C’est ainsi qu’est née la notion d’**utilité**.  

Trois piliers de la théorie moderne :  
1. Rendement espéré (mu) → combien rapporte en moyenne un investissement.  
2. Risque (sigma) → à quel point les résultats sont incertains.  
3. Préférences → comment l’investisseur valorise richesse et risque (via une fonction d’utilité U(x)).  

---

## Chapitre 2 : La fonction d’utilité

### Pourquoi introduire une fonction d’utilité ?

Les gens ne comparent pas seulement des montants d’argent.  
Ils comparent la **satisfaction** (plaisir, sécurité, tranquillité) qu’ils tirent de ces montants.  

C’est ce que capture la fonction :  

`U(x)`

- x : richesse ou consommation  
- U(x) : satisfaction correspondante  

### Exemples de fonctions d’utilité

1. Linéaire : `U(x) = x`  
   - Chaque euro compte autant que le précédent.  
   - Exemple : un joueur neutre au risque (pur calculateur d’espérance).  

2. Logarithmique : `U(x) = ln(x)`  
   - Chaque euro supplémentaire rapporte un peu moins de satisfaction.  
   - Exemple : passer de 1 000 € à 2 000 € est énorme, mais passer de 100 000 € à 101 000 € est négligeable.  

3. CRRA : `U(x) = (x^(1-gamma))/(1-gamma), gamma > 0`  
   - Modèle standard en finance.  
   - gamma = coefficient d’aversion au risque (mesure combien l’investisseur déteste le risque).  

### Ce que ça démontre
- La concavité (U''(x) < 0) formalise l’aversion au risque :  
  l’investisseur préfère un revenu certain à un pari risqué de même espérance.  
- Cela explique pourquoi les gens paient pour s’assurer, ou refusent certaines loteries.  

---

## Chapitre 3 : L’utilité espérée

En situation d’incertitude, on ne connaît pas la richesse finale W_T avec certitude.  
On calcule donc son **utilité espérée** :  

`V(pi) = E[U(W_T)]`

- pi = stratégie choisie (portefeuille, pari, etc.)  
- E = espérance, c’est-à-dire moyenne pondérée par les probabilités  

### Exemple concret
- Investir 100 € :  
  - 50% de chance → 200 €  
  - 50% de chance → 50 €  
- Utilité espérée :  
  `0.5 * U(200) + 0.5 * U(50)`  

Comparons avec un gain certain de 100 € :  
- Si `U(100) > 0.5 * U(200) + 0.5 * U(50)`, l’investisseur préfère la certitude → il est averse au risque.  

---

## Chapitre 4 : Impact du rendement moyen (mu)

On montre que :  

`dE[U(R)]/dmu > 0`

### Interprétation
- Plus le rendement attendu (mu) est élevé, plus l’utilité espérée est grande.  
- Hypothèse clé : `U'(x) > 0` (plus de richesse est toujours mieux).  

### Exemple concret
- Livret A : rendement garanti 3%.  
- Obligation : rendement garanti 5%.  
- Même risque (zéro) → toujours préférée.  

---

## Chapitre 5 : Impact de la volatilité (sigma)

On montre que :  

`dE[U(R)]/dsigma < 0` si `U''(x) < 0`

### Interprétation
- Plus la dispersion (sigma) est grande, plus les résultats extrêmes s’éloignent de la moyenne.  
- Comme U(x) est concave :  
  - les pertes font très mal,  
  - les gains font moins de bien.  

### Exemple concret
- Cas sûr : 105 € garantis.  
- Cas risqué : 50% chance d’avoir 120 €, 50% chance d’avoir 90 € (moyenne = 105 €).  
- Utilité espérée plus faible dans le cas risqué → l’investisseur préfère la certitude.  

---

## Chapitre 6 : Application — CAPM et valorisation

### Formules clés
- CAPM :  
  `E[R_i] - r = beta_i * (E[R_M] - r)`  

- Stochastic Discount Factor (SDF) :  
  `P0(X) = E[M * X], M = beta * U'(C_(t+1)) / U'(C_t)`  

### Exemple
- Une action cyclique (ex : Tesla) chute quand l’économie va mal → forte prime de risque exigée.  
- Une obligation d’État rapporte même en crise → faible prime de risque.  
