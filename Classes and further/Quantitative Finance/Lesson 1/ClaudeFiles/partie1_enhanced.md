# Partie I — Expected Utility Theory: Complete Guide (Enhanced Multi-Level)

**Navigation rapide :**  
[Annexe A (detailed proofs)](annexeA_chapter1.md) • [Annexe B (mathematical foundations)](annexeB_chapter1.md)

---

## Chapter 1: Why Expected Utility Theory Matters

### The Core Problem
Modern finance isn't just about counting money—it's about understanding **how people make decisions when they can't predict the future**.

**Historical Context:** In 1738, Daniel Bernoulli observed something puzzling about human behavior. Consider this famous example:

**The St. Petersburg Paradox:**
- A coin is flipped until it comes up heads
- If heads appears on the first flip, you win $2
- If heads appears on the second flip, you win $4  
- If heads appears on the third flip, you win $8
- And so on, doubling each time...

**The Mathematical Expected Value:** $E[X] = \frac{1}{2} \cdot 2 + \frac{1}{4} \cdot 4 + \frac{1}{8} \cdot 8 + \ldots = 1 + 1 + 1 + \ldots = \infty$

**The Paradox:** Even though this lottery has infinite expected value, most people wouldn't pay more than $20-50 to play it. Why?

**Bernoulli's Insight:** People don't evaluate money amounts directly—they evaluate the **satisfaction** (utility) that money brings them.

### The Three Pillars of Modern Finance

Understanding any investment decision requires three components:

1. **Expected Return ($\mu$)** - What do we expect to earn on average?
   - Mathematical representation: the mean of possible outcomes
   - Economic meaning: the reward for investing
   - Why it matters: higher expected returns attract investors

2. **Risk ($\sigma$)** - How uncertain is that return?
   - Mathematical representation: standard deviation of outcomes  
   - Economic meaning: the price of uncertainty
   - Why it matters: most investors dislike uncertainty

3. **Preferences ($U(x)$)** - How does an individual trade off risk vs. return?
   - Mathematical representation: utility function
   - Economic meaning: personal taste for risk-taking
   - Why it matters: different people make different choices facing identical opportunities

---

## Chapter 2: The Utility Function - Quantifying Satisfaction

### What is Utility?
When you have $100, getting an extra $100 feels great. But when you have $10,000, getting an extra $100 feels much less significant. **Utility functions capture this diminishing satisfaction from additional wealth.**

The utility function $U(x)$ maps wealth levels to satisfaction levels:

$$U(x) = \text{satisfaction from having wealth level } x$$

### Key Properties

**1. More is Better (Non-Satiation):**
$$U'(x) > 0$$
- The first derivative is positive
- **Economic meaning:** Additional wealth always increases satisfaction
- **Why this matters:** Ensures people prefer higher expected returns

**2. Diminishing Marginal Utility:**
$$U''(x) < 0$$  
- The second derivative is negative (concave function)
- **Economic meaning:** Each additional dollar provides less extra satisfaction than the previous dollar
- **Why this matters:** This creates risk aversion - the pain of losing $100 exceeds the joy of gaining $100

### Common Utility Functions

**1. Linear Utility (Risk Neutral):**
$$U(x) = x$$
- $U'(x) = 1$ (constant marginal utility)
- $U''(x) = 0$ (no diminishing marginal utility)
- **Meaning:** Each dollar provides the same satisfaction regardless of current wealth
- **Implication:** Only expected return matters, risk is irrelevant

**2. Logarithmic Utility (Moderate Risk Aversion):**
$$U(x) = \ln(x)$$
- $U'(x) = \frac{1}{x}$ (decreasing marginal utility)
- $U''(x) = -\frac{1}{x^2} < 0$ (concave)
- **Meaning:** Marginal utility decreases proportionally to wealth level
- **Implication:** Moderate risk aversion that decreases with wealth

**3. Power Utility (CRRA - Constant Relative Risk Aversion):**
$$U(x) = \frac{x^{1-\gamma}}{1-\gamma} \text{ for } \gamma > 0, \gamma \neq 1$$

Where $\gamma$ is the **risk aversion parameter**:
- $\gamma = 0$: Risk neutral (linear utility)
- $\gamma = 1$: Logarithmic utility  
- $\gamma > 1$: Higher risk aversion
- $\gamma < 1$: Lower risk aversion

**Why CRRA is Popular:** The risk aversion doesn't change as wealth changes, making it mathematically convenient for modeling.

➡ **For detailed mathematical proofs:** See [Annexe A §A.1](annexeA_chapter1.md#A1)  
➡ **For concavity review:** See [Annexe B §B.6](annexeB_chapter1.md#B6)

---

## Chapter 3: Expected Utility - Making Decisions Under Uncertainty

### The Expected Utility Formula
When outcomes are uncertain, we evaluate choices using **expected utility**:

$$V(\pi) = \mathbb{E}[U(W_T)]$$

**Breaking this down:**
- $\pi$ = the investment strategy or portfolio choice
- $W_T$ = final wealth (random variable)  
- $U(\cdot)$ = utility function
- $\mathbb{E}[\cdot]$ = expected value (probability-weighted average)
- $V(\pi)$ = expected utility of strategy $\pi$

### Step-by-Step Example
**Investment Choice:** You have $1,000 and can either:
- **Option A:** Keep it safe (certain $1,000)
- **Option B:** Invest with 50% chance of $1,200, 50% chance of $800

**Using Logarithmic Utility $U(x) = \ln(x)$:**

**Option A Expected Utility:**
$$V(A) = U(1000) = \ln(1000) = 6.908$$

**Option B Expected Utility:**
$$V(B) = 0.5 \times U(1200) + 0.5 \times U(800)$$
$$= 0.5 \times \ln(1200) + 0.5 \times \ln(800)$$  
$$= 0.5 \times 7.090 + 0.5 \times 6.685 = 6.888$$

**Decision:** Since $V(A) > V(B)$, choose the safe option despite both having the same expected monetary value ($1,000).

**Economic Insight:** The **concavity** of the utility function makes losses hurt more than equivalent gains help, leading to risk-averse behavior.

### Why Expected Value Alone Isn't Enough
- **Expected Value of A:** $E[W_A] = 1000$
- **Expected Value of B:** $E[W_B] = 0.5(1200) + 0.5(800) = 1000$  

Both options have the same expected monetary return, but **expected utility** accounts for the investor's risk preferences, showing why someone might prefer certainty.

➡ **For integral construction:** See [Annexe A §A.2](annexeA_chapter1.md#A2)  
➡ **For probability review:** See [Annexe B §B.1](annexeB_chapter1.md#B1)

---

## Chapter 4: How Expected Return Affects Utility

### The Core Result
$$\frac{\partial}{\partial \mu} \mathbb{E}[U(R)] > 0$$

**In Plain English:** Increasing the expected return always increases expected utility (assuming non-satiation).

### The Mathematical Logic

Starting with the expected utility integral for normally distributed returns:
$$\mathbb{E}[U(R)] = \int_{-\infty}^{\infty} U(\mu + z\sigma)\phi(z)dz$$

Where:
- $\mu$ = expected return
- $\sigma$ = standard deviation (risk)  
- $z$ = standardized normal variable
- $\phi(z)$ = standard normal density function

**Taking the derivative with respect to $\mu$:**
$$\frac{\partial}{\partial \mu} \mathbb{E}[U(R)] = \int_{-\infty}^{\infty} U'(\mu + z\sigma)\phi(z)dz$$

**Why is this positive?**
- $U'(\mu + z\sigma) > 0$ for all $z$ (non-satiation assumption)
- $\phi(z) > 0$ for all $z$ (probability densities are positive)
- Therefore, the entire integral is positive

### Economic Intuition

**What this means:** Imagine shifting the entire distribution of possible returns to the right by increasing $\mu$. Every possible outcome becomes better, so:
- In good scenarios, you do better than before
- In bad scenarios, you still do better than before  
- Your expected utility must increase

**Practical Example:**
- **Bond A:** Expected return 3%, risk 1%
- **Bond B:** Expected return 5%, risk 1% (same risk!)
- **Conclusion:** Everyone prefers Bond B regardless of risk preferences

This explains why higher expected returns are always good, all else equal.

➡ **For complete proof:** See [Annexe A §A.3](annexeA_chapter1.md#A3)  
➡ **For chain rule review:** See [Annexe B §B.4](annexeB_chapter1.md#B4)

---

## Chapter 5: How Risk Affects Utility

### The Core Result  
$$\frac{\partial}{\partial \sigma} \mathbb{E}[U(R)] < 0 \quad \text{if } U''(x) < 0$$

**In Plain English:** For risk-averse investors (concave utility), increasing risk decreases expected utility.

### Understanding the Mathematical Intuition

**The derivative with respect to risk:**
$$\frac{\partial}{\partial \sigma} \mathbb{E}[U(R)] = \int_{-\infty}^{\infty} U'(\mu + z\sigma) \cdot z \cdot \phi(z)dz$$

**Key insight:** The term $z \cdot \phi(z)$ in the integral creates asymmetry:
- When $z > 0$ (good outcomes): $z \cdot \phi(z) > 0$  
- When $z < 0$ (bad outcomes): $z \cdot \phi(z) < 0$

**For risk-averse investors with $U''(x) < 0$:**
- $U'(\mu + z\sigma)$ is **lower** when $z > 0$ (marginal utility decreases with wealth)
- $U'(\mu + z\sigma)$ is **higher** when $z < 0$ (marginal utility increases with wealth)

**The asymmetric impact:**
- **Bad outcomes** ($z < 0$): High marginal utility $\times$ negative weight = large negative contribution
- **Good outcomes** ($z > 0$): Low marginal utility $\times$ positive weight = small positive contribution
- **Net effect:** Negative (increased risk hurts expected utility)

### Concrete Example with Numbers

**Scenario:** Expected return $\mu = 10\%$, comparing $\sigma = 5\%$ vs $\sigma = 20\%$

**With logarithmic utility $U(x) = \ln(x)$ and initial wealth $W_0 = 100$:**

**Low Risk ($\sigma = 5\%$):**
- 95% of outcomes between $100 \times (1.05) = 105$ and $100 \times (1.15) = 115$
- Expected utility ≈ $\ln(110) = 4.700$

**High Risk ($\sigma = 20\%$):**  
- 95% of outcomes between $100 \times (0.70) = 70$ and $100 \times (1.50) = 150$
- Expected utility ≈ $4.650$ (lower despite same expected return)

**Why the difference?** The **pain** from the possibility of losing $30 (going from 100 to 70) outweighs the **joy** from the possibility of gaining $40 (going from 110 to 150), due to diminishing marginal utility.

### Economic Implications

1. **Risk Premiums:** Investors demand higher expected returns to accept higher risk
2. **Diversification Value:** Reducing risk without sacrificing return increases utility  
3. **Insurance Demand:** People pay to reduce risk even when it lowers expected wealth

➡ **For detailed proof:** See [Annexe A §A.4](annexeA_chapter1.md#A4)  
➡ **For variance concepts:** See [Annexe B §B.2](annexeB_chapter1.md#B2)

---

## Chapter 6: Applications - CAPM and Stochastic Discount Factors

### The Capital Asset Pricing Model (CAPM)

**The Formula:**
$$\mathbb{E}[R_i] - r = \beta_i \cdot (\mathbb{E}[R_M] - r)$$

**Component by component:**
- $\mathbb{E}[R_i]$ = expected return on asset $i$
- $r$ = risk-free rate (Treasury bill rate)  
- $\mathbb{E}[R_M]$ = expected return on market portfolio
- $\beta_i = \frac{\text{Cov}(R_i, R_M)}{\text{Var}(R_M)}$ = beta coefficient

**What beta measures:**
$$\beta_i = \frac{\text{Cov}(R_i, R_M)}{\text{Var}(R_M)}$$

- **$\beta > 1$:** Asset is more volatile than the market (amplifies market movements)
- **$\beta = 1$:** Asset moves exactly with the market  
- **$\beta < 1$:** Asset is less volatile than the market (dampened market movements)
- **$\beta = 0$:** Asset is uncorrelated with the market

**Economic Interpretation:**
The **risk premium** an investor demands for holding asset $i$ is proportional to how much systematic (market) risk that asset contributes to a diversified portfolio.

**Example:**
- Risk-free rate: $r = 2\%$
- Market expected return: $\mathbb{E}[R_M] = 8\%$  
- Stock with $\beta = 1.5$

**Required return:** $\mathbb{E}[R_i] = 2\% + 1.5 \times (8\% - 2\%) = 11\%$

**Why 11%?** This stock moves 50% more than the market, so investors demand 50% more risk premium.

### The Stochastic Discount Factor (SDF)

**The Formula:**
$$P_0(X) = \mathbb{E}[M \cdot X]$$

Where the stochastic discount factor is:
$$M = \beta \frac{U'(C_{t+1})}{U'(C_t)}$$

**Breaking this down:**
- $P_0(X)$ = today's price of an asset that pays $X$ tomorrow
- $M$ = stochastic discount factor (pricing kernel)
- $\beta$ = time preference parameter (impatience factor)
- $\frac{U'(C_{t+1})}{U'(C_t)}$ = ratio of marginal utilities between tomorrow and today

**The Economic Logic:**
1. **When are future dollars most valuable?** When marginal utility is high
2. **When is marginal utility high?** When consumption is low (bad times)
3. **Therefore:** Assets that pay off in bad times are more valuable

**Practical Implications:**
- **Insurance:** Pays off when you need money most (high $U'$) → worth paying for
- **Bonds:** Provide steady income regardless of economic conditions → valuable in downturns  
- **Growth stocks:** Pay off mainly in good times (low $U'$) → require higher expected returns

**Example with recession:**
- **Normal times:** $C_t = 50,000$, $U'(C_t) = 0.01$
- **Recession:** $C_{t+1} = 30,000$, $U'(C_{t+1}) = 0.02$ 
- **SDF:** $M = 0.95 \times \frac{0.02}{0.01} = 1.9$

An asset paying $1,000 in recession is worth $P_0 = 1.9 \times 1,000 = 1,900$ today!

**Why so valuable?** That $1,000 provides enormous marginal utility when consumption is low.

➡ **Detailed SDF theory:** [Annexe A §A.5](annexeA_chapter1.md#A5)  
➡ **Complete CAPM derivation:** [Annexe A §A.6](annexeA_chapter1.md#A6)  
➡ **Covariance review:** [Annexe B §B.7](annexeB_chapter1.md#B7)

---

## Summary: The Big Picture

Expected Utility Theory provides the foundation for modern finance by:

1. **Explaining risk aversion** through concave utility functions
2. **Showing why higher expected returns are always better** (positive marginal utility)
3. **Demonstrating why risk typically reduces welfare** for risk-averse investors  
4. **Providing the basis for asset pricing models** like CAPM
5. **Explaining insurance and investment behavior** through the SDF framework

**Key Mathematical Insights:**
- Concavity ($U'' < 0$) creates risk aversion
- Expected utility integrates both return and risk preferences  
- Marginal utility determines how much we value payoffs in different states

**Practical Applications:**
- Portfolio optimization balances expected return against risk
- Asset pricing reflects both systematic risk and investor preferences
- Financial products are designed around utility-maximizing behavior

This framework underlies virtually all modern financial theory and practice.