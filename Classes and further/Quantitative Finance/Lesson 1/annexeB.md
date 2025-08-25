# Annexe B — Rappels mathématiques (Niveau 3)

Cette annexe regroupe les rappels de base nécessaires pour suivre les démonstrations de l’Annexe A.

---

## B.1 — Moyenne et espérance
- **Moyenne (données finies)** :  
  $$
  \bar{x} = \frac{1}{n}\sum_{i=1}^n x_i
  $$
- **Espérance (variable aléatoire)** :  
  $$
  \mathbb{E}[X] = \sum x_i p_i \quad \text{ou} \quad \int x f(x) dx
  $$

---

## B.2 — Variance et écart-type
- Variance :  
  $$
  Var(X) = \mathbb{E}[(X-\mu)^2]
  $$
- Écart-type :  
  $$
  \sigma = \sqrt{Var(X)}
  $$
- Mesure la dispersion autour de la moyenne.

---

## B.3 — Loi normale et variable standardisée $Z$
- Loi normale :  
  $$
  f(x) = \frac{1}{\sqrt{2\pi}\sigma}\exp\!\left(-\frac{(x-\mu)^2}{2\sigma^2}\right)
  $$
- Variable standardisée :  
  $$
  Z = \frac{X-\mu}{\sigma} \sim N(0,1)
  $$

---

## B.4 — Dérivée et règle de la chaîne
- Dérivée : vitesse de variation.  
- Exemple : $f(x)=x^2 \implies f'(x)=2x$.  
- Règle de la chaîne :  
  $$
  (f(g(x)))' = f'(g(x)) \cdot g'(x)
  $$

---

## B.5 — Intégrale et espérance continue
- Intégrale = somme continue.  
- Exemple :  
  $$
  \int_{0}^{1} x dx = \frac{1}{2}
  $$
- En proba :  
  $$
  \mathbb{E}[X] = \int x f(x) dx
  $$

---

## B.6 — Concavité et convexité
- Concave : $f''(x) < 0$ → forme bombée (aversion au risque).  
- Convexe : $f''(x) > 0$ → forme creuse (amour du risque).

---

## B.7 — Covariance et corrélation
- Covariance :  
  $$
  Cov(X,Y) = \mathbb{E}[(X-\mu_X)(Y-\mu_Y)]
  $$
- Corrélation :  
  $$
  \rho = \frac{Cov(X,Y)}{\sigma_X \sigma_Y}
  $$
