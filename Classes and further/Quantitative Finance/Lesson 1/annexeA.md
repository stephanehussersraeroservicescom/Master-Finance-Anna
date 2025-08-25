# Annexe A — Démonstrations mathématiques (Niveau 2)

Dans cette annexe, nous détaillons pas à pas les démonstrations mathématiques introduites dans la Partie I.  
Chaque démonstration fait appel à des outils de base (voir [Annexe B](annexeB.md)).

---

## A.1 — Concavité et aversion au risque

### Résultat
Une fonction d’utilité concave ($U''(x)<0$) implique une aversion au risque.

### Démonstration
- Soient $W_1$ et $W_2$ deux richesses possibles.  
- Considérons une combinaison linéaire (espérance) :  
  $$
  \kappa W_1 + (1-\kappa) W_2, \quad \kappa \in [0,1]
  $$

- Propriété des fonctions concaves :  
  $$
  U(\kappa W_1 + (1-\kappa) W_2) \geq \kappa U(W_1) + (1-\kappa)U(W_2)
  $$

### Interprétation
- L’utilité de la richesse moyenne est **supérieure** à la moyenne des utilités.  
- Autrement dit, un investisseur préfère un revenu certain équivalent à la moyenne plutôt qu’un pari entre $W_1$ et $W_2$.  

👉 C’est la définition de l’**aversion au risque**.

Voir rappels : [concavité](annexeB.md#b6---concavité-et-convexité).

---

## A.2 — Espérance d’utilité avec distribution normale

### Résultat
Si $R \sim \mathcal{N}(\mu, \sigma^2)$, alors l’espérance d’utilité est :

$$
\mathbb{E}[U(R)] = \int_{-\infty}^{\infty} U(\mu + z\sigma)\,\phi(z)\,dz
$$

### Démonstration
- Densité d’une loi normale :  
  $$
  f_R(r) = \frac{1}{\sqrt{2\pi}\sigma} \exp\!\left(-\tfrac{1}{2}\left(\frac{r-\mu}{\sigma}\right)^2\right)
  $$

- On standardise : $z = \tfrac{r-\mu}{\sigma}$, donc $r = \mu + z\sigma$.  
- Cela transforme l’intégrale en :  
  $$
  \mathbb{E}[U(R)] = \int_{-\infty}^{\infty} U(\mu + z\sigma)\,\phi(z)\,dz
  $$

où $\phi(z)$ est la densité de la loi normale standard.

---

## A.3 — Dérivée par rapport à $\mu$

### Résultat
$$
\frac{\partial}{\partial \mu} \, \mathbb{E}[U(R)] = \int_{-\infty}^{\infty} U'(\mu+z\sigma)\,\phi(z)\,dz > 0
$$

### Démonstration
- On dérive sous le signe intégral (théorème de Leibniz).  
- Règle de la chaîne :  
  $$
  \frac{\partial}{\partial \mu} U(\mu+z\sigma) = U'(\mu+z\sigma)
  $$  
- Donc :  
  $$
  \frac{\partial}{\partial \mu}\mathbb{E}[U(R)] = \int_{-\infty}^{\infty} U'(\mu+z\sigma)\,\phi(z)\,dz
  $$

### Interprétation
Comme $U'(x)>0$ et $\phi(z)>0$, l’intégrale est strictement positive.  
Donc, plus $\mu$ augmente, plus l’utilité espérée croît.

Voir rappels : [espérance](annexeB.md#b1---moyenne-et-espérance), [règle de la chaîne](annexeB.md#b4---dérivée-et-règle-de-la-chaîne).

---

## A.4 — Dérivée par rapport à $\sigma$

### Résultat
$$
\frac{\partial}{\partial \sigma} \, \mathbb{E}[U(R)] = \int_{-\infty}^{\infty} U'(\mu+z\sigma)\, z \,\phi(z)\,dz
$$

### Démonstration
- Règle de la chaîne :  
  $$
  \frac{\partial}{\partial \sigma} U(\mu+z\sigma) = U'(\mu+z\sigma)\cdot z
  $$
- Substituer dans l’intégrale donne le résultat.  

### Interprétation
- Pour $z>0$ : effet positif (scénarios de gains).  
- Pour $z<0$ : effet négatif (scénarios de pertes).  
- Comme $U$ est concave, les pertes pèsent plus lourd → l’intégrale est négative.  

---

## A.5 — Stochastic Discount Factor (SDF)

### Résultat
$$
M_{t+1} = \beta \frac{U'(C_{t+1})}{U'(C_t)}
$$

### Démonstration (intuitive)
- Dans un modèle intertemporel, les prix reflètent l’échange entre **consommer aujourd’hui** et **consommer demain**.  
- Le ratio $\frac{U'(C_{t+1})}{U'(C_t)}$ traduit combien un euro supplémentaire demain vaut comparé à aujourd’hui.  
- $\beta$ est le facteur d’actualisation (préférence pour le présent).  

---

## A.6 — Démonstration du CAPM

### Résultat
$$
\mathbb{E}[R_i] - r = \beta_i (\mathbb{E}[R_M] - r)
$$

### Démonstration (idée générale)
- Partir de la condition d’équilibre :  
  $$
  P_0(X) = \mathbb{E}[M \cdot X]
  $$
- Appliquer à un actif risqué et à l’actif de marché.  
- On obtient que le rendement excédentaire d’un actif est proportionnel à sa covariance avec le marché.  

---
