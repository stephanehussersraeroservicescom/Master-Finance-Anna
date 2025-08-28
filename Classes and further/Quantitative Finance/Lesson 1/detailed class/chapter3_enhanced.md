# Chapter 3: Portfolio Theory and Risk Assessment
*[Covers Slides 15-18: Portfolio Optimization and Mean-Variance Analysis]*

**Navigation:**  
[← Chapter 2](chapter2_enhanced.md) • [Chapter 4 →](chapter4_enhanced.md) • [Annexe A (proofs)](annexeA_enhanced.md) • [Annexe B (math foundations)](annexeB_enhanced.md)

---

## Chapter Objectives

This chapter takes the expected utility theory we learned in Chapters 1 and 2 and applies it to the real-world problem of choosing between multiple investments. We'll understand:
- How to mathematically describe a portfolio of many assets
- What each symbol in the portfolio optimization equations means
- How risk preferences translate into specific investment decisions
- Why diversification works mathematically

---

## 3.1 From Single Assets to Portfolios
*[Slide 15: Portfolio Selection Framework]*

### What is a Portfolio?

Instead of putting all your money in one investment, a **portfolio** means spreading your money across multiple assets. Think of it like this: instead of buying just Apple stock, you might buy Apple, Google, bonds, and keep some cash.

### The Mathematical Setup

Let's break down the portfolio problem piece by piece:

#### Portfolio Weights: What Fraction Goes Where?

**Portfolio weights:** $w = (w_1, w_2, \ldots, w_n)$ 

**What this means:**
- $w_1$ = fraction of your money invested in asset 1 (e.g., 0.3 means 30% in Apple stock)
- $w_2$ = fraction of your money invested in asset 2 (e.g., 0.2 means 20% in Google stock)
- $w_n$ = fraction of your money invested in asset n (e.g., 0.1 means 10% in Tesla stock)

**Example:** If you have $10,000 and $w_1 = 0.3$, you invest $3,000 in asset 1.

#### The Risk-Free Asset

**Risk-free weight:** $w_f$ = fraction of money in the risk-free asset

**What is the risk-free asset?**
- Government bonds (like U.S. Treasury bills)
- High-grade savings accounts
- Any investment where you know exactly what return you'll get
- **Risk-free return:** $r_f$ = the guaranteed return rate (e.g., 0.03 means 3% per year)

#### The Budget Constraint: All Money Must Be Allocated

$$\sum_{i=1}^n w_i + w_f = 1$$

**Breaking this down:**
- **Left side:** $\sum_{i=1}^n w_i$ = sum of all risky asset weights
- **Plus:** $w_f$ = risk-free asset weight  
- **Equals:** $1$ = 100% of your money

**What this equation says:** Every dollar must go somewhere. You can't invest 120% of your money, and you shouldn't leave money unallocated.

**Example:** If $w_1 = 0.3$, $w_2 = 0.4$, $w_3 = 0.2$, then $w_f = 0.1$ (10% in risk-free asset).

### Terminal Wealth: What You End Up With

#### The Random Returns

**Risky asset returns:** $\tilde{r}_1, \tilde{r}_2, \ldots, \tilde{r}_n$ 

**What the tilde (~) means:** These are **random variables**—you don't know what they'll be! 
- $\tilde{r}_1$ might be +15% if Apple does well, or -10% if it does poorly
- The tilde reminds us this is uncertain

#### Terminal Wealth Formula

$$\tilde{W}_T = W_0\left(w_f r_f + \sum_{i=1}^n w_i \tilde{r}_i\right)$$

**Let's break this down completely:**

**$W_0$** = Your initial wealth (how much money you start with)

**$w_f r_f$** = Return from the risk-free portion
- $w_f$ = fraction in risk-free asset
- $r_f$ = risk-free return rate
- **Example:** If $w_f = 0.2$ and $r_f = 0.03$, this contributes $0.2 \times 0.03 = 0.006$ to your total return

**$\sum_{i=1}^n w_i \tilde{r}_i$** = Return from all risky assets combined
- This is $w_1 \tilde{r}_1 + w_2 \tilde{r}_2 + \ldots + w_n \tilde{r}_n$
- **Example:** $0.3 \times \tilde{r}_1 + 0.4 \times \tilde{r}_2 + 0.2 \times \tilde{r}_3$

**The parentheses:** $(w_f r_f + \sum_{i=1}^n w_i \tilde{r}_i)$ = Your total portfolio return rate

**$W_0 \times (\text{total return})$** = Your final wealth

**Complete example:** 
- Start with $W_0 = \$100,000$
- Portfolio: 30% Apple ($w_1 = 0.3$), 40% Google ($w_2 = 0.4$), 20% bonds ($w_f = 0.2$), 10% Treasury bills ($w_f = 0.1$)
- If Apple returns 10% ($\tilde{r}_1 = 0.1$), Google returns 5% ($\tilde{r}_2 = 0.05$), bonds return 3% ($r_f = 0.03$)
- Total return = $0.1 \times 0.03 + 0.3 \times 0.1 + 0.4 \times 0.05 + 0.2 \times 0.03 = 0.003 + 0.03 + 0.02 + 0.006 = 0.059$
- Final wealth = $\$100,000 \times (1 + 0.059) = \$105,900$

### The Portfolio Selection Problem

Now we can state the investor's problem mathematically:

$$\max_{w} \mathbb{E}[U(\tilde{W}_T)] = \max_{w} \mathbb{E}\left[U\left(W_0\left(w_f r_f + \sum_{i=1}^n w_i \tilde{r}_i\right)\right)\right]$$

**Breaking down the equation:**

**$\max_{w}$** = Choose the portfolio weights $w$ that maximize...

**$\mathbb{E}[\cdot]$** = Expected value (mathematical average over all possible outcomes)

**$U(\tilde{W}_T)$** = Utility of final wealth
- Remember from Chapter 2: utility measures satisfaction, not just dollars
- Higher wealth is better, but with diminishing marginal utility

**$U(W_0(\ldots))$** = Utility applied to the terminal wealth formula we just explained

**What the whole equation means:**
"Choose portfolio weights to maximize the expected satisfaction you'll get from your final wealth, considering all possible market outcomes."

This is much more sophisticated than just "maximize expected return" because it accounts for:
1. **Risk aversion** (through the utility function)
2. **All possible outcomes** (through the expectation)
3. **Diminishing marginal utility** (more money is good, but each extra dollar matters less)

➡️ **Mathematical details:** See [Annexe A §A.3](annexeA_enhanced.md#A3) for the complete optimization techniques.

---

## 3.2 The Mean-Variance Framework
*[Slide 16: Markowitz Model and Return Statistics]*

### Why Mean and Variance Matter

Harry Markowitz discovered something remarkable: under certain conditions, all that matters for portfolio choice is:
1. **Expected return** (how much you expect to make on average)
2. **Variance** (how much the returns bounce around)

This dramatically simplifies the complex optimization problem we just described.

### Expected Portfolio Return: The Average Outcome

$$\mu_p = \mathbb{E}[\tilde{r}_p] = \sum_{i=1}^n w_i \mu_i$$

**Breaking this down:**

**$\tilde{r}_p$** = Your portfolio's random return (what you don't know yet)

**$\mu_p$** = Expected portfolio return (the average you expect)

**$\mu_i$** = Expected return of asset $i$ (e.g., $\mu_1 = 0.08$ means you expect 8% from Apple)

**$w_i \mu_i$** = Contribution of asset $i$ to portfolio expected return
- **Example:** If $w_1 = 0.3$ and $\mu_1 = 0.08$, asset 1 contributes $0.3 \times 0.08 = 0.024$ (2.4%) to total expected return

**The sum:** $\sum_{i=1}^n w_i \mu_i = w_1 \mu_1 + w_2 \mu_2 + \ldots + w_n \mu_n$

**Complete example:**
- 30% Apple (expect 8%): contributes $0.3 \times 0.08 = 0.024$
- 40% Google (expect 6%): contributes $0.4 \times 0.06 = 0.024$  
- 30% Bonds (expect 3%): contributes $0.3 \times 0.03 = 0.009$
- **Total expected return:** $\mu_p = 0.024 + 0.024 + 0.009 = 0.057$ (5.7%)

### Portfolio Variance: Measuring Total Risk

This is where it gets more complex because assets don't move independently!

$$\sigma_p^2 = \text{Var}(\tilde{r}_p) = \sum_{i=1}^n \sum_{j=1}^n w_i w_j \sigma_{ij}$$

**Breaking down this intimidating formula:**

**$\sigma_p^2$** = Portfolio variance (measure of total risk)

**Double sum:** $\sum_{i=1}^n \sum_{j=1}^n$ means we consider every pair of assets (including each asset with itself)

**$w_i w_j$** = Product of weights for assets $i$ and $j$

**$\sigma_{ij}$** = Covariance between assets $i$ and $j$
- When $i = j$: $\sigma_{ii} = \sigma_i^2$ (asset $i$'s own variance)
- When $i \neq j$: $\sigma_{ij} = \text{Cov}(\tilde{r}_i, \tilde{r}_j)$ (how assets $i$ and $j$ move together)

#### Understanding Covariance

**$\sigma_{ij} > 0$**: Assets move together (when one goes up, the other tends to go up)
**$\sigma_{ij} < 0$**: Assets move opposite (when one goes up, the other tends to go down)  
**$\sigma_{ij} = 0$**: Assets move independently

**Why covariance matters for diversification:**
- If all your assets move together ($\sigma_{ij} > 0$ for all pairs), diversification doesn't reduce risk much
- If some assets move opposite ($\sigma_{ij} < 0$), diversification can dramatically reduce risk

#### Matrix Form (More Compact)

$$\sigma_p^2 = w^T \Sigma w$$

**What each piece means:**
- **$w$** = column vector of portfolio weights $\begin{pmatrix} w_1 \\ w_2 \\ \vdots \\ w_n \end{pmatrix}$
- **$w^T$** = row vector (transpose) $\begin{pmatrix} w_1 & w_2 & \cdots & w_n \end{pmatrix}$
- **$\Sigma$** = covariance matrix $\begin{pmatrix} \sigma_1^2 & \sigma_{12} & \cdots \\ \sigma_{21} & \sigma_2^2 & \cdots \\ \vdots & \vdots & \ddots \end{pmatrix}$

**This is the same formula as the double sum—just written more compactly!**

➡️ **Matrix calculation details:** See [Annexe B §B.4](annexeB_enhanced.md#B4) for step-by-step matrix operations.

---

## 3.3 Risk Aversion and Optimal Portfolios
*[Slide 17: Optimal Portfolio Construction]*

### Connecting Risk Preferences to Portfolio Choices

Different people have different comfort levels with risk. The utility function captures this, and it directly determines optimal portfolio choices.

### Example: CRRA Utility and Risk Aversion

**CRRA Utility Function:** $U(W) = \frac{W^{1-\gamma}}{1-\gamma}$

**What each symbol means:**
- **$W$** = Wealth level
- **$\gamma$** = Risk aversion parameter (this is the key!)
- **$1-\gamma$** = Exponent that determines curvature

#### Understanding the Risk Aversion Parameter $\gamma$

**$\gamma = 0$**: Risk neutral (only care about expected return)
- Utility becomes $U(W) = W$ (linear in wealth)
- Put all money in highest expected return asset

**$\gamma = 1$**: Moderate risk aversion  
- Utility becomes $U(W) = \ln(W)$ (logarithmic utility)
- Balanced approach between risk and return

**$\gamma > 1$**: High risk aversion
- $\gamma = 2$: Quite risk averse
- $\gamma = 5$: Very risk averse
- Higher $\gamma$ → more money in safe assets

**$\gamma < 1$ (but $> 0$)**: Low risk aversion
- Willing to take significant risks for higher returns

### The General Optimal Portfolio Formula

Under mean-variance preferences, the optimal portfolio weights are:

$$w^* = \frac{1}{\lambda} \Sigma^{-1}(\mu - r_f \mathbf{1})$$

**Let's decode every symbol:**

**$w^*$** = Vector of optimal portfolio weights (what we're solving for)

**$\lambda$** = Risk aversion coefficient
- Higher $\lambda$ → more risk averse → smaller position in risky assets
- Related to the $\gamma$ parameter in CRRA utility

**$\Sigma^{-1}$** = Inverse of the covariance matrix
- This captures how to optimally weight assets given their risk and correlations
- Assets with low variance get higher weights (all else equal)
- Negatively correlated assets get boosted (diversification benefit)

**$\mu$** = Vector of expected returns $\begin{pmatrix} \mu_1 \\ \mu_2 \\ \vdots \\ \mu_n \end{pmatrix}$

**$r_f \mathbf{1}$** = Risk-free rate times vector of ones $\begin{pmatrix} r_f \\ r_f \\ \vdots \\ r_f \end{pmatrix}$

**$(\mu - r_f \mathbf{1})$** = Vector of excess returns (how much each asset is expected to beat the risk-free rate)
- **Example:** If Apple is expected to return 8% and risk-free rate is 3%, excess return is 5%

#### Economic Intuition

The formula says: "Weight each asset based on":
1. **How much extra return it offers** (higher $\mu_i - r_f$ → higher weight)
2. **How risky it is individually and relative to others** (through $\Sigma^{-1}$)
3. **How risk averse you are** (higher $\lambda$ → smaller overall position in risky assets)

### Practical Example: Two-Asset Case

Let's make this concrete with just two risky assets plus a risk-free asset.

**Given:**
- Asset 1: $\mu_1 = 0.10$ (10% expected), $\sigma_1 = 0.20$ (20% volatility)
- Asset 2: $\mu_2 = 0.08$ (8% expected), $\sigma_2 = 0.15$ (15% volatility)  
- Correlation: $\rho_{12} = 0.3$
- Risk-free rate: $r_f = 0.03$ (3%)
- Risk aversion: $\lambda = 3$

**Step 1: Calculate covariance**
$\sigma_{12} = \rho_{12} \sigma_1 \sigma_2 = 0.3 \times 0.20 \times 0.15 = 0.009$

**Step 2: Build covariance matrix**
$\Sigma = \begin{pmatrix} 0.04 & 0.009 \\ 0.009 & 0.0225 \end{pmatrix}$ (where $0.04 = 0.20^2$ and $0.0225 = 0.15^2$)

**Step 3: Calculate excess returns**
$\mu - r_f \mathbf{1} = \begin{pmatrix} 0.10 - 0.03 \\ 0.08 - 0.03 \end{pmatrix} = \begin{pmatrix} 0.07 \\ 0.05 \end{pmatrix}$

**Step 4: Apply formula**
$w^* = \frac{1}{3} \Sigma^{-1} \begin{pmatrix} 0.07 \\ 0.05 \end{pmatrix}$

The solution tells us exactly how much to invest in each asset based on our risk preferences and the assets' characteristics.

➡️ **Complete calculations:** See [Annexe A §A.4](annexeA_enhanced.md#A4) for the full numerical solution.

---

## 3.4 The Efficient Frontier
*[Slide 18: Efficient Frontier and Capital Market Line]*

### What is the Efficient Frontier?

The **efficient frontier** is the set of all portfolios that give you the maximum possible expected return for each level of risk you're willing to take.

**Mathematical definition:** For each target level of risk $\sigma_p$, find the portfolio that maximizes expected return $\mu_p$.

Alternatively: For each target expected return $\mu_p$, find the portfolio that minimizes risk $\sigma_p$.

### The Mathematical Problem

**Minimize risk for target return:**
$$\min_{w} \frac{1}{2} w^T \Sigma w$$
subject to:
- $w^T \mu = \mu_p$ (return constraint)
- $w^T \mathbf{1} = 1$ (budget constraint)

**Breaking down this optimization problem:**

**Objective function:** $\frac{1}{2} w^T \Sigma w$
- This is portfolio variance (the $\frac{1}{2}$ is just for mathematical convenience)
- We want to minimize this (minimize risk)

**First constraint:** $w^T \mu = \mu_p$
- **$w^T \mu$** = $w_1 \mu_1 + w_2 \mu_2 + \ldots + w_n \mu_n$ (portfolio expected return)
- **$= \mu_p$** = must equal our target return
- **Meaning:** "The portfolio must deliver exactly the return we want"

**Second constraint:** $w^T \mathbf{1} = 1$ 
- **$w^T \mathbf{1}$** = $w_1 + w_2 + \ldots + w_n$ (sum of all weights)
- **$= 1$** = must sum to 100%
- **Meaning:** "All money must be invested somewhere"

### The Two-Fund Theorem

**Remarkable mathematical result:** Every efficient portfolio can be written as:

$$w_{\text{efficient}} = a \times w_{\text{MVP}} + (1-a) \times w_{\text{other}}$$

**What this means:**
- **$w_{\text{MVP}}$** = minimum variance portfolio (the safest efficient portfolio)
- **$w_{\text{other}}$** = any other efficient portfolio  
- **$a$** = mixing parameter between 0 and 1
- **Result:** You only need to find TWO efficient portfolios, then you can create any other efficient portfolio by mixing them!

**Why this is revolutionary:**
Instead of solving complex optimization for every possible target return, you just:
1. Find the minimum variance portfolio
2. Find one other efficient portfolio
3. Mix them in different proportions

### Adding the Risk-Free Asset: The Capital Market Line

When you can also invest in a risk-free asset, something amazing happens: the efficient frontier becomes a straight line!

**Capital Market Line equation:**
$$\mu_p = r_f + \frac{\mu_M - r_f}{\sigma_M} \sigma_p$$

**Breaking this down:**

**$r_f$** = Risk-free return (y-intercept)
- This is where the line starts (zero risk, risk-free return)

**$\frac{\mu_M - r_f}{\sigma_M}$** = Slope of the line (Sharpe ratio of market portfolio)
- **$\mu_M - r_f$** = Market risk premium (extra return for taking risk)
- **$\sigma_M$** = Market risk level
- **Ratio** = "reward per unit of risk"

**$\sigma_p$** = Your portfolio's risk level (x-axis)

**$\mu_p$** = Your portfolio's expected return (y-axis)

#### Economic Interpretation

**The equation says:** "Your expected return equals the risk-free rate plus a risk premium proportional to how much risk you take."

**All optimal portfolios combine:**
1. **Risk-free asset** (Treasury bills, savings account)
2. **Market portfolio** $M$ (the same risky portfolio for everyone!)

**Your choice:** How much of each?
- **Conservative investor:** Mostly risk-free asset, little market portfolio
- **Aggressive investor:** Little (or even borrow against) risk-free asset, mostly market portfolio

➡️ **Geometric visualization:** See [Annexe B §B.5](annexeB_enhanced.md#B5) for graphs and visual intuition.

---

## 3.5 Practical Application: Building Real Portfolios

### Step-by-Step Portfolio Construction

Let's walk through building a real portfolio using everything we've learned.

#### Step 1: Estimate Expected Returns

**Historical average method:**
If Apple stock returned 12%, 8%, 15%, -5%, 10% over the last 5 years:
$$\mu_{\text{Apple}} = \frac{0.12 + 0.08 + 0.15 + (-0.05) + 0.10}{5} = 0.08 \text{ (8%)}$$

**Forward-looking method:**
- Analyst forecasts
- Economic models
- Market indicators

#### Step 2: Estimate the Covariance Matrix

**Sample covariance:**
For two assets with returns $(r_{1t}, r_{2t})$ over $T$ periods:
$$\hat{\sigma}_{12} = \frac{1}{T-1} \sum_{t=1}^T (r_{1t} - \bar{r}_1)(r_{2t} - \bar{r}_2)$$

**What this formula does:**
- Look at each time period $t$
- See how much asset 1's return $(r_{1t})$ differs from its average $(\bar{r}_1)$
- See how much asset 2's return $(r_{2t})$ differs from its average $(\bar{r}_2)$  
- Multiply these deviations together
- Average over all time periods

**Positive result:** Assets tend to move together  
**Negative result:** Assets tend to move opposite  
**Near zero:** Assets move independently

#### Step 3: Choose Risk Aversion Parameter

**Questionnaire approach:**
"Would you rather have:
- A: $1000 for sure
- B: 50% chance of $2200, 50% chance of $0"

If you prefer A, you're risk averse. The degree determines $\lambda$ or $\gamma$.

**Revealed preference:**
Look at someone's existing portfolio. If they hold mostly bonds, they're likely very risk averse.

#### Step 4: Apply the Optimization Formula

$$w^* = \frac{1}{\lambda} \Sigma^{-1}(\mu - r_f \mathbf{1})$$

**Practical challenges:**
- **Matrix inversion:** Need computational software
- **Estimation error:** Small errors in $\mu$ can lead to wildly different portfolios
- **Constraints:** Real investors face limits (no short selling, minimum positions, etc.)

### Real-World Modifications

#### Constraints on Portfolio Weights

**No short selling:** $w_i \geq 0$ for all $i$
- Can't bet against assets
- Changes the math significantly

**Position limits:** $w_i \leq 0.05$ for all $i$  
- No more than 5% in any single asset
- Regulatory or risk management requirement

**Sector limits:** $\sum_{i \in \text{tech}} w_i \leq 0.20$
- No more than 20% in technology stocks
- Diversification requirement

#### Transaction Costs

**Bid-ask spreads:** Cost of buying/selling
**Brokerage fees:** Fixed costs per trade
**Market impact:** Large trades move prices

**Modified objective:**
$$\max E[U(W_T)] - \text{Transaction Costs}$$

### Modern Extensions and Improvements

#### Black-Litterman Model

**Problem:** Historical returns are poor predictors of future returns
**Solution:** Start with market equilibrium, then adjust based on your views

**Formula:**
$$\mu_{\text{BL}} = \tau \Sigma P^T (P \tau \Sigma P^T + \Omega)^{-1} Q + (\tau \Sigma)^{-1} \mu_{\text{market}}$$

**Don't worry about the complexity—the key insight:** Blend market expectations with your personal views.

#### Factor Models

**Instead of estimating full covariance matrix, use factors:**
$$\tilde{r}_i = \alpha_i + \beta_{i1} F_1 + \beta_{i2} F_2 + \ldots + \beta_{ik} F_k + \epsilon_i$$

**Common factors:**
- Market factor (overall stock market movement)
- Size factor (small vs. large companies)
- Value factor (cheap vs. expensive stocks)
- Industry factors

**Advantage:** Much fewer parameters to estimate

---

## 3.6 Why This Matters: From Theory to Practice

### What We've Accomplished

Starting from basic utility theory in Chapter 2, we've built a complete framework for:

1. **Describing portfolios mathematically**
   - Portfolio weights, expected returns, variance calculations
   - Understanding every symbol and what it represents

2. **Optimizing portfolio choice**
   - Connecting risk preferences to investment decisions
   - Solving for optimal weights given constraints

3. **Understanding diversification**
   - Why correlation matters more than individual asset risk
   - Mathematical basis for "don't put all eggs in one basket"

4. **Practical implementation**
   - Real-world constraints and modifications
   - Modern improvements to basic theory

### Connection to Financial Markets

**This theory explains:**
- Why mutual funds exist (diversification benefits)
- How robo-advisors work (automated portfolio optimization)
- Why index funds are popular (market portfolio efficiency)
- How professional managers make decisions

**Real applications:**
- **Target-date funds:** Automatically adjust $\lambda$ (risk aversion) as you age
- **Risk parity:** Weight assets by $\frac{1}{\sigma_i}$ instead of market cap
- **Factor investing:** Use factor models instead of individual assets

### The Mathematical Journey

We started with a simple question: "How should I allocate my money across different investments?"

We ended with a sophisticated framework that:
- Accounts for uncertainty (random returns $\tilde{r}_i$)
- Respects individual preferences (utility function $U$ and risk aversion $\lambda$)
- Handles multiple assets simultaneously (matrix algebra $\Sigma$, $w^T$)
- Provides concrete, implementable solutions ($w^* = \frac{1}{\lambda}\Sigma^{-1}(\mu - r_f\mathbf{1})$)

Every mathematical symbol now has clear economic meaning, and every formula solves a real-world problem.

---

## Chapter Summary

### Key Mathematical Concepts Mastered

**Portfolio representation:**
- Weights $w_i$ (fractions of wealth in each asset)
- Terminal wealth $\tilde{W}_T = W_0(w_f r_f + \sum w_i \tilde{r}_i)$
- Expected return $\mu_p = \sum w_i \mu_i$
- Portfolio variance $\sigma_p^2 = w^T \Sigma w$

**Optimization framework:**
- Objective: $\max E[U(\tilde{W}_T)]$
- Solution: $w^* = \frac{1}{\lambda}\Sigma^{-1}(\mu - r_f\mathbf{1})$
- Constraints: $\sum w_i + w_f = 1$ and others

**Efficient frontier:**
- Mathematical characterization of optimal risk-return tradeoffs
- Two-fund theorem simplification
- Capital market line with risk-free asset

### Economic Insights

**Diversification:** Mathematical proof that correlation reduces risk more than individual asset risk
**Risk preferences:** Direct connection between utility function curvature and portfolio allocation
**Market equilibrium:** How individual optimization leads to market-wide results

### Practical Skills

**Portfolio construction:** Step-by-step process from data to optimal weights
**Risk management:** Understanding and measuring portfolio risk
**Real-world modifications:** Constraints, transaction costs, and modern improvements

This mathematical framework forms the foundation of modern investment management and quantitative finance.

---

**Next:** [Chapter 4: Dynamic Models and Time-Consistent Preferences](chapter4_enhanced.md)

**Supporting Materials:**
- [Annexe A §A.3-A.5](annexeA_enhanced.md) for complete mathematical derivations
- [Annexe B §B.4-B.5](annexeB_enhanced.md) for matrix algebra and geometric interpretations