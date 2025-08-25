# Partie I — Cours principal (Niveau 1 enrichi)

**Navigation rapide :**  
[Annexe A (démonstrations)](annexeA.md) • [Annexe B (rappels)](annexeB.md)

---

## Chapitre 1 : Introduction

La finance moderne ne consiste pas seulement à **compter l’argent**, mais à comprendre **comment les gens prennent des décisions en situation d’incertitude**.

Historiquement, les économistes se sont aperçus que :
- Les individus ne choisissent pas forcément l’option avec la meilleure **espérance mathématique** (le “gain moyen”).
- Exemple : paradoxe de Saint-Pétersbourg (Bernoulli, 1738) : une loterie peut avoir une valeur attendue très élevée, sans que les gens veuillent y mettre une fortune.

👉 D’où l’idée d’**utilité** : on compare la **satisfaction** tirée de la richesse/consommation, pas seulement les montants.

Trois piliers :
1. **Rendement espéré** $\mu$ — combien rapporte en moyenne un investissement.  
2. **Risque (écart-type)** $\sigma$ — incertitude autour de ce rendement.  
3. **Préférences** (via une fonction d’utilité $U(x)$) — aversion au risque, etc.

---

## Chapitre 2 : La fonction d’utilité

### Pourquoi une utilité ?
Les gens ne comparent pas que des montants : ils comparent la **satisfaction** (plaisir, sécurité, sérénité) qu’ils en tirent. C’est ce que capture la fonction
$$
U(x),
$$
où $x$ est la richesse (ou la consommation) et $U(x)$ la satisfaction associée.

### Exemples usuels
- Linéaire (neutre au risque) : $U(x)=x$.
- Logarithmique (avers au risque modéré) : $U(x)=\ln(x)$.
- **CRRA** (aversion relative constante) : $U(x)=\dfrac{x^{1-\gamma}}{1-\gamma}$, avec $\gamma>0$.

**Ce que ça montre :** la **concavité** ($U''(x)<0$) formalise l’**aversion au risque** : on préfère un revenu **certain** à une loterie de même espérance.  
➡ Démo : [Annexe A §A.1](annexeA.md#A1). • Rappel concavité : [Annexe B §B.6](annexeB.md#B6).

---

## Chapitre 3 : L’utilité espérée

Quand le résultat est incertain, on évalue une stratégie $\pi$ via l’**utilité espérée** :
$$
V(\pi)=\mathbb{E}[U(W_T)].
$$

- $\pi$ : portefeuille/choix ;  
- $\mathbb{E}[\cdot]$ : moyenne **pondérée par les probabilités**.

### Exemple concret
- **Investir 100 € :**
  - $50\%$ de chance $\rightarrow$ 200 €  
  - $50\%$ de chance $\rightarrow$ 50 €
- **Utilité espérée :**  
  $$0.5\,U(200)+0.5\,U(50).$$

Comparons avec un **gain certain** de 100 € :
$$
\text{si } U(100) \;>\; 0.5\,U(200)+0.5\,U(50), \text{ alors l’investisseur préfère la certitude } \Rightarrow \text{ il est averse au risque.}
$$

➡ Construction de l’intégrale sous normale : [Annexe A §A.2](annexeA.md#A2). • Rappel espérance : [Annexe B §B.1](annexeB.md#B1).

---

## Chapitre 4 : Impact du rendement moyen $\mu$

**Résultat clé :**
$$
\frac{\partial}{\partial \mu}\,\mathbb{E}[U(R)]>0.
$$

**Idée :** augmenter $\mu$ décale toute la distribution vers la droite ; avec $U'(x)>0$, l’utilité espérée augmente.

**Exemple :** Livret 3 % vs Obligation 5 % (même risque) $\Rightarrow$ on préfère 5 %.

➡ Démo : [Annexe A §A.3](annexeA.md#A3). • Règle de la chaîne : [Annexe B §B.4](annexeB.md#B4).

---

## Chapitre 5 : Impact de la volatilité $\sigma$

**Résultat clé :**
$$
\frac{\partial}{\partial \sigma}\,\mathbb{E}[U(R)]<0 \quad \text{si } U''(x)<0.
$$

**Idée :** plus de dispersion = plus d’extrêmes ; avec une utilité concave, **la douleur des pertes domine** le plaisir des gains.

**Exemple :** 105 € certain vs loterie $(120,\,90)$ à 50/50 (même moyenne 105)  
$\Rightarrow$ utilité espérée plus faible pour la loterie.

➡ Démo : [Annexe A §A.4](annexeA.md#A4). • Rappel variance/écart-type : [Annexe B §B.2](annexeB.md#B2).

---

## Chapitre 6 : Application — CAPM et facteur d’actualisation stochastique

### Formules clés (corrigées)

- **CAPM :**
$$
\mathbb{E}[R_i]-r \;=\; \beta_i\,\big(\mathbb{E}[R_M]-r\big),
$$
où $\beta_i=\dfrac{\operatorname{Cov}(R_i,R_M)}{\operatorname{Var}(R_M)}$ mesure la sensibilité de l’actif $i$ au marché $M$.

- **Stochastic Discount Factor (SDF) :**
$$
P_0(X)=\mathbb{E}\!\big[M\,X\big],\qquad
M=\beta\,\frac{U'(C_{t+1})}{U'(C_t)}.
$$

**Intuition :** un actif qui paie **dans les mauvaises périodes** (quand $U'$ est élevé) vaut plus cher $\Rightarrow$ plus faible prime de risque.

➡ Liens : [Annexe A §A.5 (SDF)](annexeA.md#A5) • [Annexe A §A.6 (CAPM)](annexeA.md#A6).  
Rappels utiles : [covariance/corrélation §B.7](annexeB.md#B7) • [normale et variable $Z$ §B.3](annexeB.md#B3).
