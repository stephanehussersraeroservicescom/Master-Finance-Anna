# Chapter 1: Decision Theory - The Foundation of Modern Finance
*[Covers Slides 11-12: Decision Theory and Expected Value]*

**Navigation:**  
[← Prologue](1-prologue_expected_utility.md) • [Chapter 2 →](chapter2_enhanced.md) • [Annexe A (proofs)](annexeA_chapter1.md) • [Annexe B (math foundations)](annexeB_chapter1.md)

---

## Chapter Objectives and Context

### What are we trying to solve?

The fundamental problem in finance: How do people make optimal decisions when the future is uncertain? Traditional economics assumed people simply maximize expected monetary value, but this failed to explain real-world behavior.

Consider these puzzling observations:
- People buy insurance even when premiums exceed expected losses
- Investors demand higher returns for riskier assets beyond what expected value would suggest
- The same person might buy both lottery tickets and insurance policies
- Wealthy individuals often exhibit different risk-taking behavior than poor individuals

### Historical Context

In the 18th century, mathematicians like Daniel Bernoulli noticed that people's choices couldn't be explained by simple expected value calculations. The **St. Petersburg Paradox** showed that even lotteries with infinite expected value weren't infinitely valuable to real people.

**The St. Petersburg Paradox:**
A coin is flipped repeatedly until heads appears. The payout doubles with each additional tail:
- Heads on flip 1: Win $2
- Heads on flip 2: Win $4  
- Heads on flip 3: Win $8
- And so on...

**Mathematical Expected Value:**
$$E[X] = \frac{1}{2}(2) + \frac{1}{4}(4) + \frac{1}{8}(8) + \cdots = 1 + 1 + 1 + \cdots = \infty$$

**The Paradox:** Despite infinite expected value, most people wouldn't pay more than $20-50 to play this game.

This observation launched the field of decision theory and ultimately modern finance.

### Why This Matters for Quantitative Finance

Understanding decision-making under uncertainty is crucial because:

1. **Investment Decisions:** All financial choices involve unknown future returns
2. **Risk Management:** Requires understanding how people value uncertain outcomes  
3. **Asset Pricing:** Depends on how investors collectively evaluate risky securities
4. **Portfolio Optimization:** Must account for individual risk preferences
5. **Market Behavior:** Aggregate individual decisions create market phenomena

**Real-World Applications:**
- Why do risk premiums exist in equity markets?
- How should portfolio managers balance risk and return?
- What drives demand for insurance and derivatives?
- How do we price assets with uncertain payoffs?

---

## Mathematical Framework: Defining Uncertainty

### The Lottery Concept

**Fundamental Innovation:** Instead of analyzing specific investments, we abstract to a general framework where any uncertain situation becomes a "lottery" with known probabilities.

This abstraction allows us to:
- Compare any risky situations using the same mathematical tools
- Develop general theories that apply across all uncertain contexts
- Build rigorous mathematical models of decision-making

### Discrete Lottery Structure

**Mathematical Representation:**
$$L = \{(x_1, p_1), (x_2, p_2), \ldots, (x_n, p_n)\}$$

**Component Analysis:**
- $L$: The lottery (any uncertain situation)
- $x_i$: Specific outcome $i$ (wealth level, return, or any measurable result)
- $p_i$: Probability of outcome $i$ occurring (must be between 0 and 1)
- $n$: Total number of possible outcomes (finite for discrete case)

**Mathematical Constraints:**
These probabilities must satisfy basic axioms of probability theory:

$$p_i \geq 0 \text{ for all } i \quad \text{(probabilities cannot be negative)}$$

$$\sum_{i=1}^n p_i = 1 \quad \text{(probabilities must sum to certainty)}$$

**Practical Examples:**

**Stock Investment Lottery:**
- $x_1 = +20\%$ return with $p_1 = 0.3$ (bull market)
- $x_2 = +5\%$ return with $p_2 = 0.5$ (normal market)  
- $x_3 = -10\%$ return with $p_3 = 0.2$ (bear market)

**Bond Investment Lottery:**
- $x_1 = +4\%$ return with $p_1 = 0.95$ (no default)
- $x_2 = -60\%$ return with $p_2 = 0.05$ (default scenario)

### Continuous Extension

**When We Need Continuous Distributions:**
Many financial variables (stock returns, interest rates, currency movements) can take on virtually any value within a range, making discrete analysis impractical.

**Mathematical Framework:**
For situations with infinitely many possible outcomes, we use a random variable $X$ with probability density function $f(x)$:

$$P(a \leq X \leq b) = \int_a^b f(x)dx$$

**Component Analysis:**
- $X$: Random variable representing uncertain outcome
- $f(x)$: Probability density function (height of distribution at point $x$)  
- $\int_a^b f(x)dx$: Probability that outcome falls between $a$ and $b$

**Mathematical Constraints for Continuous Case:**
$$f(x) \geq 0 \text{ for all } x \quad \text{(density cannot be negative)}$$

$$\int_{-\infty}^{\infty} f(x)dx = 1 \quad \text{(total probability equals certainty)}$$

**Financial Applications:**
- **Stock Returns:** Often modeled as normal distributions
- **Interest Rate Changes:** May follow more complex continuous distributions
- **Currency Fluctuations:** Continuous random variables with fat tails

➡ **For rigorous probability theory foundations:** [Annexe B §B.1 (Probability Theory)](annexeB_chapter1.md#B1)
➡ **For integration techniques:** [Annexe B §B.5 (Integration Methods)](annexeB_chapter1.md#B5)

---

## Expected Value: The First Attempt at Solution

### Theoretical Objective

**What is Expected Value trying to achieve?** Provide a single number that summarizes the "central tendency" of an uncertain outcome, enabling comparison between different risky options.

This represents the **first systematic attempt** to make decisions under uncertainty using mathematical tools rather than pure intuition.

### Mathematical Definitions

**For Discrete Outcomes:**
$$E[L] = \sum_{i=1}^n p_i x_i$$

**For Continuous Outcomes:**
$$E[X] = \int_{-\infty}^{\infty} x f(x) dx$$

**Component Interpretation:**
- Each outcome $x_i$ is weighted by its probability $p_i$
- The sum/integral gives the probability-weighted average outcome
- Represents the "long-run average" if the situation were repeated infinitely

### Practical Calculation Examples

**Stock Investment Expected Return:**
- Bull market: $+20\%$ return × $0.3$ probability = $+6.0\%$
- Normal market: $+5\%$ return × $0.5$ probability = $+2.5\%$  
- Bear market: $-10\%$ return × $0.2$ probability = $-2.0\%$
- **Expected Return:** $E[R] = 6.0\% + 2.5\% - 2.0\% = 6.5\%$

**Bond Investment Expected Return:**
- No default: $+4\%$ return × $0.95$ probability = $+3.8\%$
- Default: $-60\%$ return × $0.05$ probability = $-3.0\%$
- **Expected Return:** $E[R] = 3.8\% - 3.0\% = 0.8\%$

### The Fundamental Problem with Expected Value

**Core Issue:** Expected value alone cannot explain observed human behavior because it completely ignores risk preferences and the distribution of outcomes around the mean.

**Compelling Counter-Example:**
- **Lottery A:** Certain $1,000 (Expected Value = $1,000)
- **Lottery B:** 50% chance of $2,000, 50% chance of $0 (Expected Value = $1,000)

**Expected Value Prediction:** People should be indifferent between these options.
**Reality:** Most people strongly prefer Lottery A (the certain outcome).

### Why Expected Value Falls Short

**1. Ignores Distribution Shape:** Two lotteries with identical expected values can have vastly different risk profiles:
- One might offer steady, predictable outcomes near the mean
- Another might involve extreme outcomes with high uncertainty

**2. Doesn't Account for Individual Differences:** Expected value treats all decision-makers as identical, ignoring:
- Personal risk tolerance variations
- Wealth level effects on decision-making
- Individual utility from different outcomes

**3. Fails to Explain Common Behaviors:**
- **Insurance Purchases:** People pay premiums above expected loss
- **Risk Premiums:** Risky assets must offer higher expected returns
- **Diversification:** People spread risk even when it lowers expected return

**4. Cannot Handle Diminishing Satisfaction:** The assumption that each additional dollar provides the same satisfaction regardless of current wealth level contradicts both intuition and empirical evidence.

➡ **For detailed mathematical analysis of expected value limitations:** [Annexe A §A.1 (Expected Value Critique)](annexeA_chapter1.md#A1)

---

## The Need for a New Framework

### The Core Problem Statement

Given a set of available uncertain choices $\mathcal{L} = \{L_1, L_2, \ldots, L_m\}$, how do we determine which option maximizes an individual's welfare when expected value alone is insufficient?

### Requirements for a Superior Framework

**1. Individual Preference Accommodation:**
- Must capture different risk tolerances across individuals
- Should reflect how satisfaction changes with wealth levels
- Must allow for varying attitudes toward uncertainty

**2. Mathematical Tractability:**
- Enable rigorous optimization and comparative analysis  
- Allow for empirical testing and parameter estimation
- Support building of larger theoretical frameworks

**3. Behavioral Realism:**
- Explain observed phenomena like insurance demand and risk premiums
- Predict actual decision patterns rather than idealized behavior
- Account for wealth effects on risk-taking

**4. Practical Applicability:**
- Support portfolio construction and asset pricing
- Enable risk management and performance evaluation
- Provide foundation for financial market analysis

### The Path Forward

The solution requires **four key innovations:**

1. **Utility Functions:** Mathematical representations of individual satisfaction from different wealth levels
2. **Expected Utility Maximization:** Decision rule that accounts for both probabilities and preferences  
3. **Risk Aversion Measurement:** Quantitative tools to capture and compare risk attitudes
4. **Continuous Analysis:** Extension to realistic probability distributions

This framework—Expected Utility Theory—provides the missing link between human psychology and mathematical finance.

**Preview of Coming Chapters:**
- Chapter 2 introduces utility functions and shows how they resolve expected value problems
- Chapters 3-4 develop risk aversion theory and measurement tools
- Chapters 5-6 analyze specific utility functions used in practice
- Chapters 7-9 extend to advanced applications and graphical analysis

➡ **For probability theory foundations needed for utility analysis:** [Annexe B §B.1 (Advanced Probability)](annexeB_chapter1.md#B1)
➡ **For integration techniques used throughout the course:** [Annexe B §B.5 (Integration Methods)](annexeB_chapter1.md#B5)

---

## Summary and Transition

Chapter 1 established the fundamental inadequacy of expected value analysis for real-world financial decision-making. We demonstrated that:

1. **Expected value ignores risk preferences** - identical expected values can represent completely different risk profiles
2. **Human behavior systematically deviates** from expected value predictions  
3. **Important financial phenomena cannot be explained** without accounting for individual risk attitudes
4. **A new theoretical framework is essential** for rigorous analysis of decision-making under uncertainty

The stage is now set for Expected Utility Theory, which transforms subjective preferences into mathematical functions that can be analyzed and optimized.

**Next:** [Chapter 2 - Expected Utility Theory: The Revolutionary Solution](chapter2_enhanced.md)