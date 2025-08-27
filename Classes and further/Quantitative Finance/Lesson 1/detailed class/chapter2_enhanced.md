# Chapter 2: Expected Utility Theory - The Revolutionary Solution
*[Covers Slides 13-16: Simple Gamble Example and Utility Functions]*

**Navigation:**  
[← Chapter 1](chapter1_enhanced.md) • [Chapter 3 →](chapter3_enhanced.md) • [Annexe A (proofs)](annexeA_chapter2.md) • [Annexe B (math foundations)](annexeB_chapter2.md)

---

## Chapter Objectives and Revolutionary Context

### What Problem Are We Solving?

Expected value cannot explain real-world decision-making under uncertainty. We need a framework that accounts for individual risk preferences while maintaining mathematical rigor.

**The Critical Insight:** Instead of comparing monetary amounts directly, we should compare the **satisfaction** (utility) those amounts provide. This allows us to incorporate risk aversion, wealth effects, and other psychological factors into rigorous mathematical analysis.

### Historical Revolution

**1738:** Daniel Bernoulli proposed utility functions to resolve the St. Petersburg Paradox
**1944:** von Neumann and Morgenstern axiomatized expected utility theory  
**1950s-60s:** Markowitz, Sharpe, and others built modern portfolio theory on this foundation

**Why This Framework Revolutionized Finance:**
- Provides theoretical foundation for portfolio theory
- Explains risk premiums in asset pricing
- Justifies diversification strategies
- Enables rigorous optimization under uncertainty

### Economic Applications

**Portfolio Construction:** Expected utility theory provides the foundation for:
- Modern portfolio theory (Markowitz optimization)
- Capital asset pricing model (CAPM)
- Risk-adjusted performance measures

**Insurance Markets:** Explains why people pay premiums above actuarial value - the utility gained from risk reduction exceeds the expected monetary loss.

**Investment Analysis:** Allows comparison of investments with different risk-return profiles by converting both dimensions into a single utility metric.

---

## The Utility Function Concept

### Core Innovation

**Objective:** Transform monetary outcomes into satisfaction levels that reflect individual preferences and risk attitudes.

**Mathematical Representation:**
$$U : \mathbb{R} \to \mathbb{R}$$
$$U(x) = \text{satisfaction from wealth level } x$$

**Key Properties Required:**
1. **More is Better:** $U'(x) > 0$ (additional wealth increases utility)
2. **Diminishing Satisfaction:** $U''(x) < 0$ for most people (each extra dollar matters less)
3. **Continuity:** Small wealth changes produce small utility changes

### The Expected Utility Decision Rule

**Framework:** When facing uncertain outcomes, choose the option that maximizes:
$$E[U(\text{outcomes})] = \sum_i p_i U(x_i)$$

**Component Analysis:**
- $U(x_i)$: Satisfaction from outcome $i$
- $p_i$: Probability of outcome $i$  
- Sum: Probability-weighted average satisfaction

This replaces expected monetary value with expected satisfaction value.

---

## Concrete Application: The Square Root Example

*[Slide 13 Example]*

### Setup and Utility Function

We demonstrate the framework using **square root utility:** $U(x) = \sqrt{x}$

**Why This Function?**
- $U'(x) = \frac{1}{2\sqrt{x}} > 0$ (more wealth increases utility)
- $U''(x) = -\frac{1}{4x^{3/2}} < 0$ (diminishing marginal utility → risk aversion)
- Simple enough for clear calculations

### Lottery A: The Risky Option

**Structure:** 50% chance of $100, 50% chance of $0

**Expected Monetary Value:**
$$E[L_A] = 0.5 \times 100 + 0.5 \times 0 = 50$$

**Expected Utility Calculation:**
$$E[U(L_A)] = 0.5 \times U(100) + 0.5 \times U(0)$$
$$= 0.5 \times \sqrt{100} + 0.5 \times \sqrt{0}$$
$$= 0.5 \times 10 + 0.5 \times 0 = 5 \text{ utils}$$

### Lottery B: The Safe Option

**Structure:** Certain outcome of $49

**Expected Monetary Value:** $E[L_B] = 49$

**Expected Utility:** $E[U(L_B)] = U(49) = \sqrt{49} = 7$ utils

### The Decision

**Comparison:**
- Expected Value: $E[L_A] = 50 > 49 = E[L_B]$ (Lottery A preferred)
- Expected Utility: $E[U(L_A)] = 5 < 7 = E[U(L_B)]$ (Lottery B preferred)

**Rational Choice:** Lottery B (the safe option)

**Economic Interpretation:**
The certain $49 provides more satisfaction than the risky lottery with expected value $50. The potential loss creates enough disutility to make the certain option preferable despite lower expected monetary value.

➡ **For detailed calculation steps:** [Annexe A §A.2.1](annexeA_chapter2.md#A21)

---

## Risk Attitude Classification Through Curvature

*[Slides 14-15]*

### The Second Derivative Test

**Fundamental Principle:** The shape of the utility function, captured by its second derivative, determines risk attitude.

### Risk-Averse Case: Concave Utility

**Mathematical Condition:** $U''(x) < 0$ (concave function)

**Economic Interpretation:**
- Marginal utility decreases with wealth
- Each additional dollar provides less satisfaction than the previous dollar
- **Behavioral implication:** Prefers certain outcomes to risky ones with same expected value

**Visual Characteristics:**
- Curves downward (like an upside-down bowl)
- Steep at low wealth levels, flatter at high wealth levels
- "Bends away from" the x-axis

**Real-World Examples:**
- Most individuals for large amounts
- Explains insurance purchases
- Justifies diversification strategies

### Risk-Neutral Case: Linear Utility  

**Mathematical Condition:** $U''(x) = 0$ (linear function)

**Economic Interpretation:**
- Marginal utility constant regardless of wealth level
- Each dollar provides same satisfaction
- **Behavioral implication:** Indifferent between certain and risky outcomes with same expected value

**Visual Characteristics:**
- Straight line
- Constant slope
- No curvature

**Real-World Examples:**
- Large institutions making small relative bets
- Theoretical benchmark for analysis

### Risk-Seeking Case: Convex Utility

**Mathematical Condition:** $U''(x) > 0$ (convex function)

**Economic Interpretation:**
- Marginal utility increases with wealth
- Each additional dollar provides more satisfaction
- **Behavioral implication:** Prefers risky outcomes to certain ones with same expected value

**Visual Characteristics:**
- Curves upward (like a bowl)
- Gentle at low wealth levels, steep at high wealth levels
- "Bends toward" the x-axis

**Real-World Examples:**
- Lottery ticket purchases
- Some entrepreneurial ventures
- Gambling behavior

### The Mathematical Connection: Jensen's Inequality

**For Concave Functions (Risk Aversion):**
$$U(E[W]) > E[U(W)]$$

**Economic Translation:**
- Left side: Utility of expected wealth (certainty)
- Right side: Expected utility of risky wealth (gamble)
- Inequality: Certain wealth provides higher utility than risky wealth

This mathematical property directly translates to economic behavior: risk-averse individuals prefer certainty to risk when expected values are equal.

➡ **For rigorous proof of Jensen's inequality:** [Annexe A §A.2.2](annexeA_chapter2.md#A22)
➡ **For concavity mathematical review:** [Annexe B §B.2.1](annexeB_chapter2.md#B21)

---

## The Utility Function Zoo

*[Slide 15: Three Faces of Fortune]*

### Visual Comparison of Risk Attitudes

The three utility function shapes demonstrate how mathematical curvature translates to economic behavior:

**Risk-Averse (Blue/Concave):**
- **Mathematical:** $U''(x) < 0$, curves downward
- **Behavior:** "Prefers certainty" - values guaranteed outcomes
- **Slope:** Steep initially, flattens as wealth increases
- **Real applications:** Most insurance decisions, conservative investing

**Risk-Neutral (Black/Linear):**
- **Mathematical:** $U''(x) = 0$, straight line  
- **Behavior:** "Indifferent to risk" - only cares about expected value
- **Slope:** Constant regardless of wealth level
- **Real applications:** Some institutional decisions, theoretical benchmark

**Risk-Seeking (Red/Convex):**
- **Mathematical:** $U''(x) > 0$, curves upward
- **Behavior:** "Prefers gambles" - attracted to uncertainty
- **Slope:** Gentle initially, steepens as wealth increases  
- **Real applications:** Lottery purchases, speculative investments

### Key Insights from the Comparison

1. **Same Starting Point:** All three curves can intersect at low wealth levels
2. **Divergent Behavior:** Risk attitudes become more pronounced at higher wealth levels
3. **Slope Interpretation:** The steepness indicates how much someone values additional wealth
4. **Practical Implications:** Different people facing identical gambles make different choices

---

## Expected Utility Maximization Framework

### The Decision Rule

**Principle:** Rational decision-makers choose the alternative that maximizes expected utility.

**Mathematical Formulation:**
$$\text{Choose } \pi^* = \arg\max_\pi E[U(W(\pi))]$$

Where:
- $\pi$: Decision alternative (portfolio, investment, etc.)
- $W(\pi)$: Wealth resulting from choice $\pi$
- $E[U(W(\pi))]$: Expected utility from choice $\pi$

### Advantages Over Expected Value

**1. Individual Differences:** Captures varying risk preferences across people

**2. Wealth Effects:** Accounts for how current wealth affects decisions

**3. Realistic Behavior:** Explains observed phenomena like:
- Insurance demand
- Risk premiums  
- Diversification benefits
- Portfolio allocation patterns

**4. Mathematical Tractability:** Enables optimization and comparative analysis

### Practical Application Process

**Step 1:** Identify possible outcomes and their probabilities
**Step 2:** Choose appropriate utility function for decision-maker
**Step 3:** Calculate expected utility for each alternative  
**Step 4:** Select alternative with highest expected utility

➡ **For optimization techniques:** [Annexe A §A.2.3](annexeA_chapter2.md#A23)

---

## Connection to Financial Decision-Making

### Portfolio Theory Foundation

Expected utility theory provides the theoretical foundation for Markowitz's mean-variance optimization:

**Standard Approach:** Maximize expected return subject to risk constraint
**Utility Foundation:** Maximize $E[U(\text{portfolio return})]$

Under specific conditions (quadratic utility or normal returns), these approaches are equivalent.

### Asset Pricing Implications

**Risk Premiums:** Risky assets must offer higher expected returns because:
- Risk reduces expected utility for risk-averse investors
- Higher expected returns compensate for this utility loss
- Equilibrium balances supply and demand

**Market Behavior:** Asset prices adjust so that marginal utilities are equalized across investors, leading to observable risk-return relationships.

### Insurance and Risk Management

**Insurance Demand:** People willingly pay premiums above expected losses because:
- Potential large losses create disproportionate disutility
- Insurance transfers risk to specialized institutions
- Utility gain from risk reduction exceeds expected monetary cost

---

## Limitations and Extensions

### Assumptions Required

1. **Stable Preferences:** Utility functions don't change over time
2. **Rational Calculation:** People can compute expected utilities
3. **Independence:** Preferences satisfy von Neumann-Morgenstern axioms

### Empirical Challenges

**Behavioral Deviations:** Real behavior sometimes contradicts utility theory:
- Allais paradox (violations of independence axiom)
- Probability weighting effects
- Reference point dependence

**Extensions Developed:**
- Prospect theory (Kahneman-Tversky)
- Rank-dependent utility
- Behavioral portfolio theory

### Practical Considerations

**Parameter Estimation:** Requires determining individual utility functions from observed behavior or stated preferences.

**Computational Complexity:** Expected utility calculations can become complex with many outcomes or continuous distributions.

**Model Selection:** Choosing appropriate utility function family affects all subsequent analysis.

➡ **For advanced behavioral extensions:** [Annexe A §A.2.4](annexeA_chapter2.md#A24)

---

## Summary and Transition

Chapter 2 introduced the revolutionary solution to decision-making under uncertainty:

**Key Innovations:**
1. **Utility functions** capture individual satisfaction from wealth
2. **Expected utility maximization** replaces expected value maximization
3. **Curvature** (second derivative) determines risk attitude
4. **Mathematical framework** enables rigorous analysis

**Practical Applications:**
- Explains insurance purchases and risk premiums
- Provides foundation for portfolio theory
- Enables asset pricing and risk management
- Supports financial decision analysis

**What We've Established:**
- Expected utility theory resolves the limitations of expected value
- Different utility function shapes generate different risk attitudes
- The framework is both mathematically rigorous and economically intuitive

**Next Steps:** Chapter 3 will explore the fundamental assumptions underlying utility theory, particularly non-satiation and diminishing marginal utility.

**Next:** [Chapter 3 - Non-Satiation and Marginal Utility](chapter3_enhanced.md)