# Annexe A — Chapter 2: Key Mathematical Proofs

*Focused mathematical demonstrations for Expected Utility Theory*

**Navigation:**  
[← Chapter 2](chapter2_enhanced.md) • [Annexe B (foundations) →](annexeB_chapter2.md)

---

## A.2.1 — Square Root Utility Calculation

*[Referenced from Chapter 2 - Concrete Example]*

### Step-by-Step Calculation Verification

**Given:**
- Utility function: $U(x) = \sqrt{x}$
- Lottery A: 50% chance of $100, 50% chance of $0
- Lottery B: Certain $49

**Lottery A Expected Utility:**
$$E[U(L_A)] = 0.5 \times U(100) + 0.5 \times U(0)$$

**Substitute utility function:**
$$= 0.5 \times \sqrt{100} + 0.5 \times \sqrt{0}$$

**Calculate square roots:**
- $\sqrt{100} = 10$
- $\sqrt{0} = 0$

**Final calculation:**
$$= 0.5 \times 10 + 0.5 \times 0 = 5 + 0 = 5 \text{ utils}$$

**Lottery B Expected Utility:**
$$E[U(L_B)] = U(49) = \sqrt{49} = 7 \text{ utils}$$

**Decision Rule:** Choose higher expected utility
$$7 > 5 \Rightarrow \text{Choose Lottery B}$$

### Verification of Risk Aversion

**Properties of $U(x) = \sqrt{x}$:**

**First derivative:** $U'(x) = \frac{1}{2\sqrt{x}} > 0$ for $x > 0$
- **Interpretation:** More wealth always increases utility (non-satiation)

**Second derivative:** $U''(x) = -\frac{1}{4x^{3/2}} < 0$ for $x > 0$
- **Interpretation:** Marginal utility decreases with wealth (risk aversion)

**Numerical verification:**
- At $x = 25$: $U'(25) = \frac{1}{2\sqrt{25}} = \frac{1}{10} = 0.1$
- At $x = 100$: $U'(100) = \frac{1}{2\sqrt{100}} = \frac{1}{20} = 0.05$

Indeed, $0.1 > 0.05$, confirming decreasing marginal utility.

---

## A.2.2 — Jensen's Inequality for Risk Aversion

*[Referenced from Chapter 2 - Risk Attitude Classification]*

### Simple Proof of Jensen's Inequality

**Theorem:** For concave function $U$ (where $U''(x) < 0$) and any random variable $W$:
$$U(E[W]) > E[U(W)]$$

**Proof for Two-Outcome Case:**
Let $W$ take values $w_1$ and $w_2$ with probabilities $p$ and $(1-p)$.

**Expected value:** $E[W] = pw_1 + (1-p)w_2$

**Expected utility:** $E[U(W)] = pU(w_1) + (1-p)U(w_2)$

**For concave functions, the definition states:**
$$U(px + (1-p)y) > pU(x) + (1-p)U(y)$$

**Substituting $x = w_1$ and $y = w_2$:**
$$U(pw_1 + (1-p)w_2) > pU(w_1) + (1-p)U(w_2)$$

**This is exactly:**
$$U(E[W]) > E[U(W)]$$

### Economic Interpretation

**Left side:** $U(E[W])$ = utility from certain wealth equal to expected value
**Right side:** $E[U(W)]$ = expected utility from risky gamble
**Inequality direction:** Certainty preferred over risk (when expected values equal)

**This proves:** Concave utility ⇒ Risk aversion

---

## A.2.3 — Expected Utility Maximization

*[Referenced from Chapter 2 - Decision Framework]*

### Optimization Setup

**Problem:** Choose portfolio $\pi$ to maximize expected utility
$$\max_\pi E[U(W(\pi))]$$

**For discrete outcomes:**
$$\max_\pi \sum_{i=1}^n p_i U(W_i(\pi))$$

### First-Order Condition

**Using calculus of variations:**
$$\frac{\partial}{\partial \pi} E[U(W(\pi))] = E\left[U'(W(\pi)) \frac{\partial W(\pi)}{\partial \pi}\right] = 0$$

**Economic interpretation:**
- $U'(W(\pi))$: Marginal utility in each state
- $\frac{\partial W(\pi)}{\partial \pi}$: How wealth changes with portfolio choice
- Zero condition: Marginal utility-weighted wealth changes must sum to zero

### Example: Optimal Risky Asset Allocation

**Setup:**
- Initial wealth: $W_0$
- Fraction $\alpha$ in risky asset with return $\tilde{R}$
- Fraction $(1-\alpha)$ in risk-free asset with return $r_f$
- Final wealth: $W = W_0[\alpha \tilde{R} + (1-\alpha)r_f]$

**First-order condition:**
$$E[U'(W) \cdot W_0(\tilde{R} - r_f)] = 0$$
$$E[U'(W)(\tilde{R} - r_f)] = 0$$

**Economic meaning:** The covariance between marginal utility and excess returns must be zero at the optimum.

---

## A.2.4 — Behavioral Extensions Preview

*[Referenced from Chapter 2 - Limitations]*

### Prospect Theory Basics

**Key Modifications to Expected Utility:**

1. **Reference Point Dependence:** Utility depends on gains/losses from reference point, not absolute wealth levels

2. **Loss Aversion:** Losses hurt more than equivalent gains help
   - $|U(\text{loss})| > U(\text{equivalent gain})$

3. **Probability Weighting:** People don't use objective probabilities
   - Overweight small probabilities (lottery effect)
   - Underweight large probabilities (insurance effect)

### Mathematical Framework

**Value function:** $V(x) = \begin{cases} x^\alpha & \text{if } x \geq 0 \\ -\lambda(-x)^\beta & \text{if } x < 0 \end{cases}$

Where:
- $\alpha, \beta < 1$ (diminishing sensitivity)
- $\lambda > 1$ (loss aversion)

**Weighted expected utility:**
$$\text{Prospect value} = \sum_i w(p_i) V(x_i)$$

Where $w(p_i)$ are decision weights that differ from objective probabilities $p_i$.

### Connection to Standard Theory

**When does expected utility work?**
- Large stakes relative to reference point
- Professional/institutional decision-making
- Repeated decisions with learning

**When do behavioral effects dominate?**
- Small probability events
- First-time decisions
- Emotionally charged contexts

---

## Summary

This annexe provides essential mathematical support for Chapter 2's concepts:

1. **Detailed calculations** verify the square root utility example
2. **Jensen's inequality proof** establishes the concavity-risk aversion connection
3. **Optimization framework** shows how to find optimal decisions
4. **Behavioral extensions** preview modifications to standard theory

The proofs maintain rigor while focusing on key insights rather than exhaustive technical details.

**Return to:** [Chapter 2](chapter2_enhanced.md)