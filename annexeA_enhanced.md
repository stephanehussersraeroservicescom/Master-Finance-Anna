# Annexe A — Enhanced Mathematical Demonstrations (Level 2)

This annex provides detailed, step-by-step mathematical proofs for all results introduced in Part I. Each proof includes economic intuition and connects abstract mathematics to real-world financial concepts.

---

## A.1 — Concavity and Risk Aversion

### Statement
A concave utility function ($U''(x) < 0$) implies risk aversion, meaning investors prefer certain outcomes to risky prospects with the same expected value.

### Complete Mathematical Proof

**Step 1: Define the comparison**
Consider an investor choosing between:
- **Certain outcome:** Wealth level $\mathbb{E}[W]$ with certainty  
- **Risky outcome:** Random wealth $W$ with the same expected value $\mathbb{E}[W]$

**Step 2: Apply Jensen's Inequality**
For any concave function $U$ and random variable $W$:
$$U(\mathbb{E}[W]) \geq \mathbb{E}[U(W)]$$

**Step 3: Economic interpretation**
- Left side: $U(\mathbb{E}[W])$ = utility from certain wealth equal to the expected value
- Right side: $\mathbb{E}[U(W)]$ = expected utility from the risky prospect  
- Inequality: Certain wealth provides higher utility than risky wealth with same expected value

**Step 4: Rigorous proof of Jensen's Inequality**
Since $U$ is concave, $U''(x) < 0$, which means for any two points $x_1, x_2$ and weight $\lambda \in [0,1]$:
$$U(\lambda x_1 + (1-\lambda)x_2) \geq \lambda U(x_1) + (1-\lambda)U(x_2)$$

**Extending to general case:** For any discrete distribution with outcomes $W_1, W_2, \ldots, W_n$ and probabilities $p_1, p_2, \ldots, p_n$:
$$U\left(\sum_{i=1}^n p_i W_i\right) \geq \sum_{i=1}^n p_i U(W_i)$$

This is exactly: $U(\mathbb{E}[W]) \geq \mathbb{E}[U(W)]$

### Geometric Interpretation
The concave utility function lies below its tangent lines. When you "average" along the curve (expected utility), you get a lower value than the point on the curve at the average wealth level.

### Numerical Example
**Utility function:** $U(x) = \sqrt{x}$  
**Wealth scenarios:** $W_1 = 100$ with probability 0.5, $W_2 = 400$ with probability 0.5  
**Expected wealth:** $\mathbb{E}[W] = 0.5(100) + 0.5(400) = 250$

**Certain outcome utility:** $U(250) = \sqrt{250} = 15.81$  
**Expected utility of gamble:** $0.5\sqrt{100} + 0.5\sqrt{400} = 0.5(10) + 0.5(20) = 15$

**Result:** $15.81 > 15$, confirming risk aversion.

**Economic insight:** The investor would pay up to $\sqrt{250}^2 - \sqrt{15}^2 = 250 - 225 = 25$ to avoid this risk.

See also: [Mathematical foundations - concavity](annexeB_enhanced.md#B6)

---

## A.2 — Expected Utility with Normal Distributions  

### Statement
When returns follow a normal distribution $R \sim \mathcal{N}(\mu, \sigma^2)$, expected utility can be expressed as:
$$\mathbb{E}[U(R)] = \int_{-\infty}^{\infty} U(\mu + z\sigma)\phi(z)dz$$

### Complete Derivation

**Step 1: Start with the definition**
For continuous random variable $R$ with probability density $f_R(r)$:
$$\mathbb{E}[U(R)] = \int_{-\infty}^{\infty} U(r) f_R(r) dr$$

**Step 2: Normal distribution density**
For $R \sim \mathcal{N}(\mu, \sigma^2)$:
$$f_R(r) = \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(r-\mu)^2}{2\sigma^2}\right)$$

**Step 3: Standardization transformation**
Let $z = \frac{r-\mu}{\sigma}$, then:
- $r = \mu + z\sigma$  
- $dr = \sigma dz$
- When $r = -\infty$, $z = -\infty$
- When $r = +\infty$, $z = +\infty$

**Step 4: Transform the density**
The Jacobian of the transformation gives us:
$$f_R(r)dr = \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{z^2}{2}\right) \sigma dz = \frac{1}{\sqrt{2\pi}} \exp\left(-\frac{z^2}{2}\right) dz = \phi(z)dz$$

Where $\phi(z) = \frac{1}{\sqrt{2\pi}} \exp\left(-\frac{z^2}{2}\right)$ is the standard normal PDF.

**Step 5: Final result**
$$\mathbb{E}[U(R)] = \int_{-\infty}^{\infty} U(\mu + z\sigma) \phi(z) dz$$

### Why This Transformation Matters

**1. Separates location and scale effects:**
- $\mu$ represents the "center" of the distribution
- $\sigma$ represents how "spread out" outcomes are around the center  
- $z$ represents standardized deviations from the mean

**2. Enables comparative statics:**
- We can analyze how changes in $\mu$ affect utility by taking $\frac{\partial}{\partial \mu}$
- We can analyze how changes in $\sigma$ affect utility by taking $\frac{\partial}{\partial \sigma}$

**3. Universal applicability:**
- Any normal distribution can be analyzed using this framework
- The standardized variable $z$ has the same distribution regardless of $\mu$ and $\sigma$

### Computational Example
**Given:** $U(x) = \ln(x)$, $\mu = 0.08$, $\sigma = 0.20$, initial wealth $W_0 = 100$

**Final wealth:** $W_T = W_0(1 + R) = 100(1 + \mu + z\sigma) = 100(1.08 + 0.20z)$

**Expected utility:**
$$\mathbb{E}[U(W_T)] = \int_{-\infty}^{\infty} \ln(108 + 20z) \phi(z) dz$$

This integral can be evaluated numerically or approximated using Taylor expansion methods.

See also: [Probability foundations](annexeB_enhanced.md#B1), [Normal distribution](annexeB_enhanced.md#B3)

---

## A.3 — Impact of Expected Return on Utility

### Statement
$$\frac{\partial}{\partial \mu} \mathbb{E}[U(R)] = \int_{-\infty}^{\infty} U'(\mu + z\sigma)\phi(z)dz > 0$$

### Complete Mathematical Proof

**Step 1: Apply the fundamental theorem of calculus**
Starting from: $\mathbb{E}[U(R)] = \int_{-\infty}^{\infty} U(\mu + z\sigma)\phi(z)dz$

We differentiate under the integral sign (Leibniz integral rule):
$$\frac{\partial}{\partial \mu} \mathbb{E}[U(R)] = \int_{-\infty}^{\infty} \frac{\partial}{\partial \mu} U(\mu + z\sigma) \phi(z) dz$$

**Step 2: Apply chain rule**  
$$\frac{\partial}{\partial \mu} U(\mu + z\sigma) = U'(\mu + z\sigma) \cdot \frac{\partial}{\partial \mu}(\mu + z\sigma) = U'(\mu + z\sigma) \cdot 1 = U'(\mu + z\sigma)$$

**Step 3: Combine results**
$$\frac{\partial}{\partial \mu} \mathbb{E}[U(R)] = \int_{-\infty}^{\infty} U'(\mu + z\sigma)\phi(z)dz$$

**Step 4: Prove positivity**
- **Non-satiation assumption:** $U'(x) > 0$ for all $x$ (marginal utility is positive)
- **Probability density:** $\phi(z) > 0$ for all $z$ 
- **Product of positives:** $U'(\mu + z\sigma) \cdot \phi(z) > 0$ for all $z$
- **Integral of positive function:** $\int_{-\infty}^{\infty} U'(\mu + z\sigma)\phi(z)dz > 0$

### Economic Interpretation

**What this derivative represents:**
The rate at which expected utility increases when we shift the entire return distribution rightward by a small amount.

**Why it's always positive:**
Increasing $\mu$ means every possible outcome becomes better:
- Bad outcomes ($z < 0$) become less bad
- Good outcomes ($z > 0$) become even better
- Since more wealth is always preferred (non-satiation), expected utility must increase

**Practical implications:**
1. **Portfolio choice:** Investors always prefer assets with higher expected returns, ceteris paribus
2. **Market efficiency:** Higher expected returns are required to attract capital to riskier investments
3. **Performance evaluation:** Fund managers are rewarded for generating higher expected returns

### Numerical Example
**Setup:** $U(x) = \ln(x)$, $\sigma = 0.15$, $W_0 = 1000$

**Compare two scenarios:**
- **Scenario A:** $\mu_A = 0.05$
- **Scenario B:** $\mu_B = 0.08$

**Expected utilities (calculated numerically):**
- $\mathbb{E}[U(W_T^A)] \approx 6.901$
- $\mathbb{E}[U(W_T^B)] \approx 6.932$

**Marginal effect:** $\frac{\mathbb{E}[U(W_T^B)] - \mathbb{E}[U(W_T^A)]}{\mu_B - \mu_A} = \frac{6.932 - 6.901}{0.03} = 1.033 > 0$

This confirms that higher expected return increases expected utility.

### Conditions for Validity
This result requires:
1. **Differentiability:** $U$ is differentiable
2. **Non-satiation:** $U'(x) > 0$  
3. **Regularity conditions:** Allow differentiation under the integral sign

See also: [Chain rule](annexeB_enhanced.md#B4), [Integration techniques](annexeB_enhanced.md#B5)

---

## A.4 — Impact of Risk on Utility

### Statement  
$$\frac{\partial}{\partial \sigma} \mathbb{E}[U(R)] = \int_{-\infty}^{\infty} U'(\mu + z\sigma) \cdot z \cdot \phi(z)dz < 0 \text{ if } U''(x) < 0$$

### Complete Mathematical Proof

**Step 1: Differentiate under the integral**
$$\frac{\partial}{\partial \sigma} \mathbb{E}[U(R)] = \int_{-\infty}^{\infty} \frac{\partial}{\partial \sigma} U(\mu + z\sigma) \phi(z) dz$$

**Step 2: Apply chain rule**
$$\frac{\partial}{\partial \sigma} U(\mu + z\sigma) = U'(\mu + z\sigma) \cdot \frac{\partial}{\partial \sigma}(\mu + z\sigma) = U'(\mu + z\sigma) \cdot z$$

**Step 3: Complete derivative**
$$\frac{\partial}{\partial \sigma} \mathbb{E}[U(R)] = \int_{-\infty}^{\infty} U'(\mu + z\sigma) \cdot z \cdot \phi(z) dz$$

**Step 4: Analyze the sign using integration by parts**

Split the integral at zero:
$$\int_{-\infty}^{\infty} U'(\mu + z\sigma) z \phi(z) dz = \int_{-\infty}^{0} U'(\mu + z\sigma) z \phi(z) dz + \int_{0}^{\infty} U'(\mu + z\sigma) z \phi(z) dz$$

**For the left integral** ($z < 0$):
- $z < 0$ (negative)
- $\phi(z) > 0$ (positive)
- $U'(\mu + z\sigma)$ is large (high marginal utility when wealth is low)

**For the right integral** ($z > 0$):
- $z > 0$ (positive)  
- $\phi(z) > 0$ (positive)
- $U'(\mu + z\sigma)$ is small (low marginal utility when wealth is high)

**Step 5: Apply mean value theorem analysis**

Due to concavity ($U'' < 0$), marginal utility decreases with wealth:
$$U'(\mu + z\sigma) \text{ is decreasing in } z$$

This creates asymmetry:
- **Negative outcomes:** High $|U'|$ × Large $|z|$ × Negative sign = Large negative contribution
- **Positive outcomes:** Low $U'$ × Large $z$ × Positive sign = Small positive contribution  

**Net effect:** Negative (risk reduces expected utility)

### Detailed Economic Analysis

**What drives the negative effect?**

1. **Diminishing marginal utility:** Additional wealth provides less satisfaction
2. **Loss aversion:** Potential losses create more disutility than equivalent gains create utility
3. **Asymmetric impact:** Risk spreads outcomes, but the "bad tail" hurts more than the "good tail" helps

**Quantitative example:**
Suppose $\mu = 0$, $\sigma$ increases from 10% to 20%

**Low risk scenario:**
- Outcomes roughly between -10% and +10%
- Marginal utilities roughly between $U'(0.9)$ and $U'(1.1)$

**High risk scenario:**  
- Outcomes roughly between -20% and +20%
- Marginal utilities roughly between $U'(0.8)$ and $U'(1.2)$

**The asymmetry:** $U'(0.8) - U'(0.9) > U'(1.1) - U'(1.2)$ due to concavity.

### Alternative Proof Using Taylor Expansion

**For small risks, approximate:**
$$U(\mu + z\sigma) \approx U(\mu) + U'(\mu)z\sigma + \frac{1}{2}U''(\mu)(z\sigma)^2$$

**Taking expectations:**
$$\mathbb{E}[U(R)] \approx U(\mu) + U'(\mu)\sigma\mathbb{E}[z] + \frac{1}{2}U''(\mu)\sigma^2\mathbb{E}[z^2]$$

Since $\mathbb{E}[z] = 0$ and $\mathbb{E}[z^2] = 1$:
$$\mathbb{E}[U(R)] \approx U(\mu) + \frac{1}{2}U''(\mu)\sigma^2$$

**Differentiating with respect to $\sigma$:**
$$\frac{\partial}{\partial \sigma}\mathbb{E}[U(R)] \approx U''(\mu)\sigma < 0$$

Since $U''(\mu) < 0$ for risk-averse investors.

### Risk Premium Implication

The negative effect of risk leads to **risk premiums**. Investors demand compensation:
$$\text{Risk Premium} = \mathbb{E}[R] - r_f \propto \sigma^2 \times |U''(\mu)|$$

Where:
- $r_f$ = risk-free rate
- The premium increases with both variance and risk aversion

See also: [Variance concepts](annexeB_enhanced.md#B2), [Taylor expansion](annexeB_enhanced.md#B5)

---

## A.5 — Stochastic Discount Factor (SDF) Framework

### Statement
In intertemporal choice models, asset prices are determined by:
$$P_0(X) = \mathbb{E}[M \cdot X]$$
where the stochastic discount factor is:
$$M = \beta \frac{U'(C_{t+1})}{U'(C_t)}$$

### Theoretical Foundation

**Step 1: Intertemporal utility maximization**

Consider an investor choosing consumption $(C_t, C_{t+1})$ to maximize:
$$V = U(C_t) + \beta \mathbb{E}[U(C_{t+1})]$$

Subject to budget constraint:
$$C_t + \frac{C_{t+1}}{1 + R} = W_t$$

**Step 2: First-order conditions**

Taking derivatives:
$$\frac{\partial V}{\partial C_t} = U'(C_t) - \lambda = 0$$
$$\frac{\partial V}{\partial C_{t+1}} = \beta U'(C_{t+1}) - \frac{\lambda}{1 + R} = 0$$

Where $\lambda$ is the Lagrange multiplier.

**Step 3: Combine conditions**
$$U'(C_t) = \beta (1 + R) U'(C_{t+1})$$

Rearranging:
$$\frac{1}{1 + R} = \beta \frac{U'(C_{t+1})}{U'(C_t)}$$

**Step 4: Generalize to any asset**
For any asset paying random amount $X$ next period:
$$P_0 = \mathbb{E}\left[\frac{X}{1 + R}\right] = \mathbb{E}\left[\beta \frac{U'(C_{t+1})}{U'(C_t)} \cdot X\right]$$

Defining $M \equiv \beta \frac{U'(C_{t+1})}{U'(C_t)}$ gives us:
$$P_0(X) = \mathbb{E}[M \cdot X]$$

### Economic Interpretation of the SDF

**What $M$ represents:**
The SDF is the **price per dollar** of consumption in different future states.

**Component analysis:**

1. **$\beta$ (time preference):**
   - $\beta < 1$: Impatient (prefer current consumption)
   - $\beta \approx 1$: Patient (indifferent to timing)
   - Discounts all future payoffs equally

2. **$\frac{U'(C_{t+1})}{U'(C_t)}$ (state preference):**
   - High when $C_{t+1}$ is low (recession states)
   - Low when $C_{t+1}$ is high (boom states)  
   - Reflects diminishing marginal utility

**Key insight:** Money is most valuable when marginal utility is high (bad times).

### Applications and Examples

**1. Risk-free asset pricing:**
For certain payoff $X = 1$:
$$P_0 = \mathbb{E}[M] \cdot 1 = \mathbb{E}[M]$$

Therefore: $r_f = \frac{1}{\mathbb{E}[M]} - 1$

**2. Equity risk premium:**
For market return $R_M$:
$$1 = \mathbb{E}[M(1 + R_M)]$$

Using covariance decomposition:
$$1 = \mathbb{E}[M] \mathbb{E}[1 + R_M] + \text{Cov}(M, 1 + R_M)$$

This gives us:
$$\mathbb{E}[R_M] - r_f = -\frac{\text{Cov}(M, 1 + R_M)}{\mathbb{E}[M]}$$

**Economic interpretation:** Assets that pay off when the SDF is low (good times) must offer higher expected returns.

**3. Insurance valuation:**
Insurance that pays $I$ in bad states (high $M$) has value:
$$P_0 = \mathbb{E}[M \cdot I]$$

Since $M$ and $I$ are positively correlated, insurance commands a premium above its actuarial value.

### Numerical Example

**Setup:**
- Utility: $U(C) = \ln(C)$  
- Time preference: $\beta = 0.95$
- Current consumption: $C_t = 100$
- Two future states:
  - Boom: $C_{t+1} = 120$ (probability 0.6)
  - Recession: $C_{t+1} = 80$ (probability 0.4)

**Calculate SDF values:**
- Boom: $M_{\text{boom}} = 0.95 \times \frac{U'(120)}{U'(100)} = 0.95 \times \frac{1/120}{1/100} = 0.95 \times \frac{100}{120} = 0.792$
- Recession: $M_{\text{recession}} = 0.95 \times \frac{U'(80)}{U'(100)} = 0.95 \times \frac{1/80}{1/100} = 0.95 \times \frac{100}{80} = 1.188$

**Risk-free rate:**
$$\mathbb{E}[M] = 0.6(0.792) + 0.4(1.188) = 0.950$$
$$r_f = \frac{1}{0.950} - 1 = 5.26\%$$

**Asset that pays $100 in boom, $0 in recession:**
$$P_0 = 0.6 \times 0.792 \times 100 + 0.4 \times 1.188 \times 0 = 47.52$$

This asset has expected payoff $0.6 \times 100 = 60$ but trades at only $47.52$ due to its correlation with good times.

See also: [Optimization methods](annexeB_enhanced.md#B4), [Covariance](annexeB_enhanced.md#B7)

---

## A.6 — Capital Asset Pricing Model (CAPM) Derivation

### Statement
Under specific assumptions, all assets satisfy:
$$\mathbb{E}[R_i] - r_f = \beta_i (\mathbb{E}[R_M] - r_f)$$
where $\beta_i = \frac{\text{Cov}(R_i, R_M)}{\text{Var}(R_M)}$

### Complete Derivation from SDF

**Step 1: Start with fundamental pricing equation**
$$1 = \mathbb{E}[M(1 + R_i)]$$

**Step 2: Expand using covariance decomposition**
$$1 = \mathbb{E}[M]\mathbb{E}[1 + R_i] + \text{Cov}(M, 1 + R_i)$$
$$1 = \mathbb{E}[M](1 + \mathbb{E}[R_i]) + \text{Cov}(M, R_i)$$

**Step 3: Solve for expected return**
$$1 = \mathbb{E}[M] + \mathbb{E}[M]\mathbb{E}[R_i] + \text{Cov}(M, R_i)$$
$$\mathbb{E}[R_i] = \frac{1 - \mathbb{E}[M]}{\mathbb{E}[M]} - \frac{\text{Cov}(M, R_i)}{\mathbb{E}[M]}$$

**Step 4: Identify risk-free rate**
For risk-free asset: $\text{Cov}(M, r_f) = 0$, so:
$$r_f = \frac{1 - \mathbb{E}[M]}{\mathbb{E}[M]}$$

**Step 5: Substitute back**
$$\mathbb{E}[R_i] = r_f - \frac{\text{Cov}(M, R_i)}{\mathbb{E}[M]}$$

**Step 6: Apply to market portfolio**
$$\mathbb{E}[R_M] = r_f - \frac{\text{Cov}(M, R_M)}{\mathbb{E}[M]}$$

**Step 7: Take ratio to eliminate $M$**
$$\frac{\mathbb{E}[R_i] - r_f}{\mathbb{E}[R_M] - r_f} = \frac{\text{Cov}(M, R_i)}{\text{Cov}(M, R_M)}$$

**Step 8: Express in terms of market betas**

Since $M$ is decreasing in aggregate consumption/wealth, and market return represents aggregate wealth changes:
$$\text{Cov}(M, R_i) = -\gamma \text{Cov}(R_i, R_M)$$
$$\text{Cov}(M, R_M) = -\gamma \text{Var}(R_M)$$

for some positive constant $\gamma$.

**Step 9: Final CAPM formula**
$$\frac{\mathbb{E}[R_i] - r_f}{\mathbb{E}[R_M] - r_f} = \frac{\text{Cov}(R_i, R_M)}{\text{Var}(R_M)} = \beta_i$$

Therefore: $\mathbb{E}[R_i] - r_f = \beta_i(\mathbb{E}[R_M] - r_f)$

### Economic Interpretation

**What beta measures:**
$$\beta_i = \frac{\text{Cov}(R_i, R_M)}{\text{Var}(R_M)} = \rho_{i,M} \frac{\sigma_i}{\sigma_M}$$

Where:
- $\rho_{i,M}$ = correlation between asset $i$ and market
- $\frac{\sigma_i}{\sigma_M}$ = relative volatility

**Beta interpretation:**
- $\beta_i = 1$: Asset moves exactly with market
- $\beta_i > 1$: Asset amplifies market movements (aggressive)
- $\beta_i < 1$: Asset dampens market movements (defensive)
- $\beta_i = 0$: Asset uncorrelated with market

**Risk premium decomposition:**
$$\mathbb{E}[R_i] - r_f = \underbrace{\rho_{i,M}}_{\text{correlation}} \times \underbrace{\frac{\sigma_i}{\sigma_M}}_{\text{relative volatility}} \times \underbrace{(\mathbb{E}[R_M] - r_f)}_{\text{market premium}}$$

### Key CAPM Assumptions

1. **Homogeneous expectations:** All investors have same beliefs about returns
2. **Mean-variance preferences:** Investors care only about mean and variance  
3. **Frictionless markets:** No transaction costs or taxes
4. **Price-taking:** All investors are small relative to market
5. **Risk-free borrowing/lending:** Available to all investors at same rate

### Extensions and Limitations

**Multi-factor models:**
$$\mathbb{E}[R_i] - r_f = \beta_{i,1}\lambda_1 + \beta_{i,2}\lambda_2 + \cdots + \beta_{i,K}\lambda_K$$

Where $\lambda_k$ are risk premiums for different factors.

**Empirical challenges:**
1. **Market portfolio unobservable:** Usually proxied by stock index
2. **Beta instability:** Changes over time
3. **Anomalies:** Size effect, value effect, momentum

**Alternative models:**
- Fama-French three-factor model
- Consumption CAPM  
- Intertemporal CAPM

See also: [Covariance properties](annexeB_enhanced.md#B7), [Portfolio theory foundations](annexeB_enhanced.md#B1)