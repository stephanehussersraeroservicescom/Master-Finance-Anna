# Annexe A — Mathematical Proofs and Detailed Derivations

This annex provides rigorous mathematical demonstrations for all results introduced in the main chapters. Each proof includes complete derivations, technical conditions, and connections to economic interpretations.

**Navigation:**  
[← Chapter 1](chapter1_enhanced.md) • [Main Course](partie1_enhanced.md) • [Annexe B (foundations) →](annexeB_chapter1.md)

---

## A.1 — Expected Value Analysis and Limitations

*[Referenced from Chapter 1]*

### Formal Definition and Properties

**Theorem A.1.1:** For a discrete lottery $L = \{(x_1, p_1), (x_2, p_2), \ldots, (x_n, p_n)\}$ with probabilities satisfying $\sum_{i=1}^n p_i = 1$ and $p_i \geq 0$, the expected value is:

$$E[L] = \sum_{i=1}^n p_i x_i$$

**Proof of Basic Properties:**

**Linearity Property:**
For any constants $a, b$ and lotteries $L_1, L_2$:
$$E[aL_1 + bL_2] = aE[L_1] + bE[L_2]$$

**Proof:**
Let $L_1 = \{(x_i, p_i)\}$ and $L_2 = \{(y_j, q_j)\}$. Then:
$$E[aL_1 + bL_2] = \sum_{i,j} p_i q_j (ax_i + by_j) = a\sum_i p_i x_i + b\sum_j q_j y_j = aE[L_1] + bE[L_2]$$

### Mathematical Critique of Expected Value Decision-Making

**Theorem A.1.2 (Inadequacy of Expected Value):** There exist lotteries $L_1$ and $L_2$ with $E[L_1] = E[L_2]$ such that rational decision-makers consistently prefer one over the other.

**Proof by Construction:**

**Example 1 - St. Petersburg Paradox:**
Consider lottery $L_{SP}$: Win $2^n$ with probability $2^{-n}$ for $n = 1, 2, 3, \ldots$

$$E[L_{SP}] = \sum_{n=1}^{\infty} 2^{-n} \cdot 2^n = \sum_{n=1}^{\infty} 1 = \infty$$

Despite infinite expected value, empirical evidence shows people won't pay more than modest finite amounts to play this lottery.

**Example 2 - Risk Aversion Demonstration:**
- $L_1$: Certain payoff of $100
- $L_2$: $50\%$ chance of $200, 50\%$ chance of $0

Both have $E[L_1] = E[L_2] = 100$, yet survey data consistently shows preference for $L_1$.

**Mathematical Implication:** Expected value maximization fails as a descriptive theory of decision-making under uncertainty.

### Continuous Case Analysis

**Theorem A.1.3:** For continuous random variable $X$ with probability density function $f(x)$, expected value exists if and only if:

$$\int_{-\infty}^{\infty} |x|f(x)dx < \infty$$

**Proof of Existence Conditions:**

**Sufficient Condition:** If the integral of the absolute value converges, then:
$$E[X] = \int_{-\infty}^{\infty} xf(x)dx$$

exists and is finite.

**Counterexample (Cauchy Distribution):**
$$f(x) = \frac{1}{\pi(1+x^2)}$$

The integral $\int_{-\infty}^{\infty} |x|f(x)dx$ diverges, so the expected value doesn't exist despite the distribution being well-defined.

**Economic Interpretation:** Even mathematically well-defined probability distributions may not have expected values, further limiting the expected value framework.

➡ **Mathematical foundations:** See [Annexe B §B.1 (Measure Theory)](annexeB_chapter1.md#B1) for rigorous integration theory

---

## A.2 — Utility Functions and Expected Utility Theory

*[Referenced from Chapters 2-3]*

### Formal Axiomatization

**Von Neumann-Morgenstern Axioms:**

**Axiom 1 (Completeness):** For any lotteries $L_1, L_2$, either $L_1 \succeq L_2$, $L_2 \succeq L_1$, or both.

**Axiom 2 (Transitivity):** If $L_1 \succeq L_2$ and $L_2 \succeq L_3$, then $L_1 \succeq L_3$.

**Axiom 3 (Continuity):** If $L_1 \succeq L_2 \succeq L_3$, then there exists $p \in (0,1)$ such that $L_2 \sim pL_1 + (1-p)L_3$.

**Axiom 4 (Independence):** If $L_1 \succeq L_2$, then $pL_1 + (1-p)L_3 \succeq pL_2 + (1-p)L_3$ for all $p \in (0,1]$ and any $L_3$.

**Theorem A.2.1 (Von Neumann-Morgenstern Representation):** If preferences satisfy the four axioms above, then there exists a utility function $U$ such that $L_1 \succeq L_2$ if and only if $E[U(L_1)] \geq E[U(L_2)]$.

**Proof Outline:** 
1. Normalize utility by setting $U(\text{best outcome}) = 1$ and $U(\text{worst outcome}) = 0$
2. For any outcome $x$, find probability $p$ such that decision-maker is indifferent between $x$ for certain and lottery giving best outcome with probability $p$
3. Set $U(x) = p$
4. Show this assignment is consistent and represents preferences

**Technical Note:** The proof requires substantial measure-theoretic arguments beyond the scope of this course. See Fishburn (1982) for complete details.

### Concavity and Risk Aversion

**Definition A.2.1:** A function $U: \mathbb{R} \to \mathbb{R}$ is strictly concave if:
$$U(\lambda x + (1-\lambda)y) > \lambda U(x) + (1-\lambda)U(y)$$
for all $x \neq y$ and $\lambda \in (0,1)$.

**Theorem A.2.2 (Concavity ⇒ Risk Aversion):** If utility function $U$ is strictly concave, then the decision-maker is strictly risk-averse.

**Proof:**
Let $\tilde{X}$ be any random variable with $E[\tilde{X}] = \mu$. By Jensen's inequality for concave functions:

$$U(E[\tilde{X}]) = U(\mu) > E[U(\tilde{X})]$$

This means the utility of the expected value exceeds the expected utility, which is the definition of strict risk aversion.

**Converse Direction:**

**Theorem A.2.3:** If a decision-maker with differentiable utility function is risk-averse for all possible gambles, then $U$ is concave.

**Proof:**
Suppose $U$ is not concave. Then there exist $x < y$ and $\lambda \in (0,1)$ such that:
$$U(\lambda x + (1-\lambda)y) < \lambda U(x) + (1-\lambda)U(y)$$

Consider the lottery that gives $x$ with probability $\lambda$ and $y$ with probability $(1-\lambda)$. Its expected value is $\lambda x + (1-\lambda)y$, and its expected utility is $\lambda U(x) + (1-\lambda)U(y)$.

But then:
$$U(\text{expected value}) < \text{expected utility}$$

This contradicts risk aversion, so $U$ must be concave.

### Second Derivative Characterization

**Theorem A.2.4:** For twice-differentiable utility functions:
- $U''(x) < 0$ for all $x$ ⟺ strict risk aversion
- $U''(x) = 0$ for all $x$ ⟺ risk neutrality  
- $U''(x) > 0$ for all $x$ ⟺ risk seeking

**Proof for Risk Aversion Case:**

**Direction 1:** $U''(x) < 0$ ⟹ risk aversion
If $U''(x) < 0$, then $U$ is strictly concave. By Theorem A.2.2, this implies risk aversion.

**Direction 2:** Risk aversion ⟹ $U''(x) < 0$
Suppose there exists some point $x_0$ where $U''(x_0) \geq 0$. 

For small gambles around $x_0$, Taylor expansion gives:
$$E[U(x_0 + \tilde{\varepsilon})] \approx U(x_0) + U'(x_0)E[\tilde{\varepsilon}] + \frac{1}{2}U''(x_0)E[\tilde{\varepsilon}^2]$$

For a fair gamble with $E[\tilde{\varepsilon}] = 0$ and $E[\tilde{\varepsilon}^2] > 0$:
$$E[U(x_0 + \tilde{\varepsilon})] \approx U(x_0) + \frac{1}{2}U''(x_0)E[\tilde{\varepsilon}^2] \geq U(x_0)$$

This means the decision-maker prefers the gamble to certainty, contradicting risk aversion.

➡ **For Taylor series and approximation theory:** See [Annexe B §B.5 (Taylor Expansions)](annexeB_chapter1.md#B5)

---

## A.3 — Arrow-Pratt Risk Aversion Measures

*[Referenced from Chapters 4-5]*

### Absolute Risk Aversion

**Definition A.3.1:** The Arrow-Pratt coefficient of absolute risk aversion is:
$$R_a(W) = -\frac{U''(W)}{U'(W)}$$

**Theorem A.3.1:** For small fair gambles $\tilde{\varepsilon}$ with $E[\tilde{\varepsilon}] = 0$ and variance $\sigma^2$, the risk premium $\pi_a$ satisfies:
$$\pi_a \approx \frac{1}{2}\sigma^2 R_a(W)$$

**Proof:**
The risk premium $\pi_a$ is defined by:
$$U(W - \pi_a) = E[U(W + \tilde{\varepsilon})]$$

**Left side Taylor expansion:**
$$U(W - \pi_a) \approx U(W) - \pi_a U'(W)$$

**Right side Taylor expansion:**
$$E[U(W + \tilde{\varepsilon})] \approx U(W) + U'(W)E[\tilde{\varepsilon}] + \frac{1}{2}U''(W)E[\tilde{\varepsilon}^2]$$

Since $E[\tilde{\varepsilon}] = 0$ and $E[\tilde{\varepsilon}^2] = \sigma^2$:
$$E[U(W + \tilde{\varepsilon})] \approx U(W) + \frac{1}{2}U''(W)\sigma^2$$

**Equating both sides:**
$$U(W) - \pi_a U'(W) = U(W) + \frac{1}{2}U''(W)\sigma^2$$

$$-\pi_a U'(W) = \frac{1}{2}U''(W)\sigma^2$$

$$\pi_a = -\frac{1}{2}\sigma^2 \frac{U''(W)}{U'(W)} = \frac{1}{2}\sigma^2 R_a(W)$$

### Relative Risk Aversion

**Definition A.3.2:** The Arrow-Pratt coefficient of relative risk aversion is:
$$R_r(W) = -W\frac{U''(W)}{U'(W)} = W \cdot R_a(W)$$

**Theorem A.3.2:** For small proportional gambles, the relative risk premium $\pi_r$ satisfies:
$$\pi_r \approx \frac{1}{2}\sigma_\eta^2 R_r(W)$$

where $\sigma_\eta^2$ is the variance of the proportional gamble.

**Proof:**
Consider a gamble of the form $W(1 + \tilde{\eta})$ where $E[\tilde{\eta}] = 0$.

The relative risk premium satisfies:
$$U(W(1 - \pi_r)) = E[U(W(1 + \tilde{\eta}))]$$

**Left side expansion:**
$$U(W(1 - \pi_r)) \approx U(W) - \pi_r W U'(W)$$

**Right side expansion:**
$$E[U(W(1 + \tilde{\eta}))] \approx U(W) + WU'(W)E[\tilde{\eta}] + \frac{1}{2}W^2U''(W)E[\tilde{\eta}^2]$$

Since $E[\tilde{\eta}] = 0$ and $E[\tilde{\eta}^2] = \sigma_\eta^2$:
$$E[U(W(1 + \tilde{\eta}))] \approx U(W) + \frac{1}{2}W^2U''(W)\sigma_\eta^2$$

**Equating:**
$$-\pi_r W U'(W) = \frac{1}{2}W^2U''(W)\sigma_\eta^2$$

$$\pi_r = -\frac{1}{2}W\sigma_\eta^2 \frac{U''(W)}{U'(W)} = \frac{1}{2}\sigma_\eta^2 R_r(W)$$

### Comparative Risk Aversion

**Theorem A.3.3:** Individual A is more risk-averse than individual B if and only if $R_a^A(W) \geq R_a^B(W)$ for all $W$.

**Proof:**
**Direction 1:** $R_a^A(W) \geq R_a^B(W)$ ⟹ A more risk-averse than B

For any fair gamble $\tilde{\varepsilon}$, the risk premiums satisfy:
$$\pi_a^A \approx \frac{1}{2}\sigma^2 R_a^A(W) \geq \frac{1}{2}\sigma^2 R_a^B(W) \approx \pi_a^B$$

So A demands higher compensation for risk.

**Direction 2:** A more risk-averse ⟹ $R_a^A(W) \geq R_a^B(W)$

If A is more risk-averse, then for any small fair gamble, $\pi_a^A \geq \pi_a^B$.
Since $\pi_a \approx \frac{1}{2}\sigma^2 R_a(W)$, this implies $R_a^A(W) \geq R_a^B(W)$.

➡ **For rigorous treatment of approximation errors:** See [Annexe B §B.5 (Approximation Theory)](annexeB_chapter1.md#B5)

---

## A.4 — Specific Utility Functions

*[Referenced from Chapter 6]*

### Exponential Utility

**Function:** $U(W) = -e^{-aW}$ for $a > 0$

**Derivatives:**
- $U'(W) = ae^{-aW} > 0$
- $U''(W) = -a^2e^{-aW} < 0$

**Risk Aversion Measures:**
$$R_a(W) = -\frac{U''(W)}{U'(W)} = -\frac{-a^2e^{-aW}}{ae^{-aW}} = a$$

$$R_r(W) = W \cdot R_a(W) = aW$$

**Theorem A.4.1:** Exponential utility exhibits constant absolute risk aversion (CARA).

**Proof:** $R_a(W) = a$ is independent of wealth level $W$.

### Power Utility (CRRA)

**Function:** $U(W) = \frac{W^{1-\gamma}}{1-\gamma}$ for $\gamma > 0, \gamma \neq 1$

**Special Case:** When $\gamma = 1$, $U(W) = \ln W$

**Derivatives:**
- $U'(W) = W^{-\gamma}$
- $U''(W) = -\gamma W^{-(\gamma+1)}$

**Risk Aversion Measures:**
$$R_a(W) = -\frac{U''(W)}{U'(W)} = -\frac{-\gamma W^{-(\gamma+1)}}{W^{-\gamma}} = \frac{\gamma}{W}$$

$$R_r(W) = W \cdot R_a(W) = \gamma$$

**Theorem A.4.2:** Power utility exhibits:
1. Decreasing absolute risk aversion (DARA): $\frac{dR_a}{dW} = -\frac{\gamma}{W^2} < 0$
2. Constant relative risk aversion (CRRA): $R_r(W) = \gamma$

**Proof:**
1. Direct differentiation of $R_a(W) = \gamma/W$ gives $\frac{dR_a}{dW} = -\gamma/W^2 < 0$
2. $R_r(W) = W \cdot \frac{\gamma}{W} = \gamma$ is constant

### Quadratic Utility

**Function:** $U(W) = W - \frac{b}{2}W^2$ for $b > 0$

**Domain Restriction:** Valid only for $W < \frac{1}{b}$ (satiation point)

**Derivatives:**
- $U'(W) = 1 - bW$ (positive only if $W < 1/b$)
- $U''(W) = -b < 0$

**Risk Aversion Measures:**
$$R_a(W) = -\frac{U''(W)}{U'(W)} = \frac{b}{1-bW}$$

**Theorem A.4.3:** Quadratic utility exhibits increasing absolute risk aversion (IARA):
$$\frac{dR_a}{dW} = \frac{b^2}{(1-bW)^2} > 0$$

**Economic Problems:**
1. **Satiation Point:** Utility is maximized at $W = 1/(2b)$ and decreases thereafter
2. **IARA Property:** Contradicts empirical evidence about wealth effects on risk aversion
3. **Unbounded Risk Aversion:** $R_a(W) \to \infty$ as $W \to 1/b$

➡ **For advanced function analysis techniques:** See [Annexe B §B.6 (Function Properties)](annexeB_chapter1.md#B6)

---

## A.5 — Normal Returns and Expected Utility

*[Referenced from Chapter 7]*

### Setup and Transformation

**Assumption:** Returns follow normal distribution $\tilde{R} \sim N(\mu, \sigma^2)$

**Standardization:** Let $\tilde{Z} = \frac{\tilde{R} - \mu}{\sigma} \sim N(0,1)$

Then $\tilde{R} = \mu + \sigma\tilde{Z}$

**Expected Utility Integral:**
$$E[U(\tilde{R})] = \int_{-\infty}^{\infty} U(\mu + \sigma z) \phi(z) dz$$

where $\phi(z) = \frac{1}{\sqrt{2\pi}}e^{-z^2/2}$ is the standard normal PDF.

### Impact of Expected Return

**Theorem A.5.1:**
$$\frac{\partial}{\partial \mu} E[U(\tilde{R})] = \int_{-\infty}^{\infty} U'(\mu + \sigma z) \phi(z) dz > 0$$

**Proof:**
Using the dominated convergence theorem (conditions verified below):

$$\frac{\partial}{\partial \mu} E[U(\tilde{R})] = \frac{\partial}{\partial \mu} \int_{-\infty}^{\infty} U(\mu + \sigma z) \phi(z) dz$$

$$= \int_{-\infty}^{\infty} \frac{\partial}{\partial \mu} U(\mu + \sigma z) \phi(z) dz$$

$$= \int_{-\infty}^{\infty} U'(\mu + \sigma z) \phi(z) dz$$

**Positivity:** Since $U'(x) > 0$ (non-satiation) and $\phi(z) > 0$, the integrand is always positive, making the integral positive.

**Technical Conditions:** For the interchange of differentiation and integration, we need:
1. $U'$ exists and is continuous
2. $|U'(\mu + \sigma z)| \leq g(z)$ for some integrable function $g$

These hold for standard utility functions under reasonable growth conditions.

### Impact of Risk

**Theorem A.5.2:**
$$\frac{\partial}{\partial \sigma} E[U(\tilde{R})] = \int_{-\infty}^{\infty} U'(\mu + \sigma z) \cdot z \cdot \phi(z) dz$$

For risk-averse investors ($U'' < 0$), this derivative is negative.

**Proof of Derivative:**
$$\frac{\partial}{\partial \sigma} E[U(\tilde{R})] = \int_{-\infty}^{\infty} \frac{\partial}{\partial \sigma} U(\mu + \sigma z) \phi(z) dz$$

$$= \int_{-\infty}^{\infty} U'(\mu + \sigma z) \cdot z \cdot \phi(z) dz$$

**Proof of Negative Sign for Risk Aversion:**

**Step 1:** Split the integral:
$$\int_{-\infty}^{\infty} U'(\mu + \sigma z) z \phi(z) dz = \int_{-\infty}^{0} U'(\mu + \sigma z) z \phi(z) dz + \int_{0}^{\infty} U'(\mu + \sigma z) z \phi(z) dz$$

**Step 2:** Change variables in the first integral. Let $y = -z$:
$$\int_{-\infty}^{0} U'(\mu + \sigma z) z \phi(z) dz = -\int_{0}^{\infty} U'(\mu - \sigma y) y \phi(y) dy$$

**Step 3:** Combine integrals:
$$\frac{\partial}{\partial \sigma} E[U(\tilde{R})] = \int_{0}^{\infty} [U'(\mu + \sigma z) - U'(\mu - \sigma z)] z \phi(z) dz$$

**Step 4:** Apply risk aversion. For $z > 0$:
- $\mu + \sigma z > \mu - \sigma z$ 
- $U'' < 0$ implies $U'$ is decreasing
- Therefore: $U'(\mu + \sigma z) < U'(\mu - \sigma z)$
- So: $U'(\mu + \sigma z) - U'(\mu - \sigma z) < 0$

**Step 5:** Since $z \phi(z) > 0$ for $z > 0$, the integrand is negative, making the entire integral negative.

➡ **For rigorous integration theory:** See [Annexe B §B.5 (Measure Theory)](annexeB_chapter1.md#B5)

---

## Summary

Annexe A provides the mathematical foundation underlying Expected Utility Theory through rigorous proofs and detailed derivations. Key results include:

1. **Axiomatic foundation** of utility representation
2. **Equivalence** between concavity and risk aversion  
3. **Risk aversion measures** and their economic interpretations
4. **Properties** of specific utility functions
5. **Continuous analysis** with normal distributions

Each proof maintains mathematical rigor while connecting to economic interpretations developed in the main chapters.

**Navigation:**  
[← Return to Main Course](partie1_enhanced.md) • [Mathematical Foundations →](annexeB_chapter1.md)