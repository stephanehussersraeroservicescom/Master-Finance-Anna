# Annexe B — Enhanced Mathematical Foundations (Level 3)

This annex provides comprehensive coverage of the mathematical concepts underlying expected utility theory. Each section includes definitions, key properties, economic applications, and worked examples.

---

## B.1 — Probability, Expected Value, and Variance

### Expected Value (Mean)

**Definition:** The expected value of a random variable $X$ is the probability-weighted average of all possible outcomes.

**Discrete case:**
$$\mathbb{E}[X] = \sum_{i=1}^n x_i p_i$$
where $x_i$ are the possible outcomes and $p_i$ are their probabilities.

**Continuous case:**
$$\mathbb{E}[X] = \int_{-\infty}^{\infty} x f(x) dx$$
where $f(x)$ is the probability density function.

**Key Properties:**
1. **Linearity:** $\mathbb{E}[aX + bY] = a\mathbb{E}[X] + b\mathbb{E}[Y]$
2. **Constant:** $\mathbb{E}[c] = c$ for any constant $c$
3. **Independence:** If $X$ and $Y$ are independent, $\mathbb{E}[XY] = \mathbb{E}[X]\mathbb{E}[Y]$

**Financial Application:**
The expected return of a portfolio with weights $w_i$ and asset returns $R_i$ is:
$$\mathbb{E}[R_p] = \sum_{i=1}^n w_i \mathbb{E}[R_i]$$

### Variance and Standard Deviation

**Definition:** Variance measures the average squared deviation from the mean.

$$\text{Var}(X) = \mathbb{E}[(X - \mathbb{E}[X])^2] = \mathbb{E}[X^2] - (\mathbb{E}[X])^2$$

**Standard deviation:** $\sigma_X = \sqrt{\text{Var}(X)}$

**Key Properties:**
1. **Scaling:** $\text{Var}(aX) = a^2\text{Var}(X)$
2. **Independence:** If $X$ and $Y$ are independent, $\text{Var}(X + Y) = \text{Var}(X) + \text{Var}(Y)$
3. **Non-negativity:** $\text{Var}(X) \geq 0$

**Portfolio Variance:**
$$\text{Var}(R_p) = \sum_{i=1}^n \sum_{j=1}^n w_i w_j \text{Cov}(R_i, R_j)$$

**Economic Interpretation:**
- Variance measures the **uncertainty** or **risk** in financial returns
- Higher variance means more unpredictable outcomes
- Investors typically require compensation (higher expected return) for bearing higher variance

### Worked Example
**Stock Returns:**
- Bull market (prob = 0.3): Return = 20%
- Normal market (prob = 0.5): Return = 8%  
- Bear market (prob = 0.2): Return = -10%

**Expected return:**
$$\mathbb{E}[R] = 0.3(0.20) + 0.5(0.08) + 0.2(-0.10) = 0.06 + 0.04 - 0.02 = 8\%$$

**Variance calculation:**
$$\mathbb{E}[R^2] = 0.3(0.20)^2 + 0.5(0.08)^2 + 0.2(-0.10)^2 = 0.012 + 0.0032 + 0.002 = 0.0172$$
$$\text{Var}(R) = 0.0172 - (0.08)^2 = 0.0172 - 0.0064 = 0.0108$$
$$\sigma_R = \sqrt{0.0108} = 10.39\%$$

---

## B.2 — Covariance and Correlation

### Covariance

**Definition:** Covariance measures how two random variables move together.

$$\text{Cov}(X,Y) = \mathbb{E}[(X - \mathbb{E}[X])(Y - \mathbb{E}[Y])] = \mathbb{E}[XY] - \mathbb{E}[X]\mathbb{E}[Y]$$

**Properties:**
1. **Symmetry:** $\text{Cov}(X,Y) = \text{Cov}(Y,X)$
2. **Linearity:** $\text{Cov}(aX + b, Y) = a\text{Cov}(X,Y)$
3. **Self-covariance:** $\text{Cov}(X,X) = \text{Var}(X)$

**Signs:**
- $\text{Cov}(X,Y) > 0$: Variables tend to move in same direction
- $\text{Cov}(X,Y) < 0$: Variables tend to move in opposite directions  
- $\text{Cov}(X,Y) = 0$: No linear relationship

### Correlation

**Definition:** Correlation standardizes covariance to lie between -1 and 1.

$$\rho_{X,Y} = \frac{\text{Cov}(X,Y)}{\sigma_X \sigma_Y}$$

**Properties:**
1. **Bounded:** $-1 \leq \rho_{X,Y} \leq 1$
2. **Perfect positive correlation:** $\rho_{X,Y} = 1$ implies $Y = aX + b$ with $a > 0$
3. **Perfect negative correlation:** $\rho_{X,Y} = -1$ implies $Y = aX + b$ with $a < 0$
4. **Independence implies zero correlation:** If $X$ and $Y$ are independent, then $\rho_{X,Y} = 0$

**Financial Applications:**

**1. Diversification:** 
Portfolio risk depends on correlations between assets:
$$\sigma_p^2 = \sum_{i=1}^n \sum_{j=1}^n w_i w_j \sigma_i \sigma_j \rho_{ij}$$

Lower correlations provide better diversification.

**2. Beta coefficient:**
$$\beta_i = \frac{\text{Cov}(R_i, R_M)}{\text{Var}(R_M)} = \rho_{i,M} \frac{\sigma_i}{\sigma_M}$$

**3. Hedging effectiveness:**
Perfect hedge requires $\rho = -1$ between hedged asset and hedge instrument.

### Numerical Example
**Two stocks:**
- Stock A: $\mathbb{E}[R_A] = 10\%$, $\sigma_A = 15\%$
- Stock B: $\mathbb{E}[R_B] = 8\%$, $\sigma_B = 12\%$
- Correlation: $\rho_{A,B} = 0.3$

**Covariance:**
$$\text{Cov}(R_A, R_B) = \rho_{A,B} \sigma_A \sigma_B = 0.3 \times 0.15 \times 0.12 = 0.0054$$

**50-50 Portfolio:**
$$\mathbb{E}[R_p] = 0.5(10\%) + 0.5(8\%) = 9\%$$
$$\sigma_p^2 = (0.5)^2(0.15)^2 + (0.5)^2(0.12)^2 + 2(0.5)(0.5)(0.0054) = 0.0156$$
$$\sigma_p = \sqrt{0.0156} = 12.49\%$$

**Diversification benefit:** Portfolio risk (12.49%) is less than weighted average of individual risks (13.5%).

---

## B.3 — Normal Distribution

### Probability Density Function

**Standard normal:** $Z \sim N(0,1)$
$$\phi(z) = \frac{1}{\sqrt{2\pi}} \exp\left(-\frac{z^2}{2}\right)$$

**General normal:** $X \sim N(\mu, \sigma^2)$  
$$f(x) = \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right)$$

### Key Properties
1. **Symmetry:** Distribution is symmetric around $\mu$
2. **Bell shape:** Single peak at the mean, tails extending to infinity
3. **68-95-99.7 rule:** 
   - 68% of observations within $\mu \pm \sigma$
   - 95% within $\mu \pm 2\sigma$  
   - 99.7% within $\mu \pm 3\sigma$

### Standardization
Any normal random variable can be standardized:
$$Z = \frac{X - \mu}{\sigma} \sim N(0,1)$$

**Reverse transformation:** $X = \mu + \sigma Z$

### Linear Combinations
If $X_1 \sim N(\mu_1, \sigma_1^2)$ and $X_2 \sim N(\mu_2, \sigma_2^2)$, then:
$$aX_1 + bX_2 + c \sim N(a\mu_1 + b\mu_2 + c, a^2\sigma_1^2 + b^2\sigma_2^2 + 2ab\text{Cov}(X_1,X_2))$$

### Financial Applications

**1. Return modeling:**
Stock returns are often assumed normal: $R \sim N(\mu, \sigma^2)$

**2. Portfolio returns:**
If individual assets are normally distributed, portfolio returns are also normal.

**3. Value at Risk (VaR):**
For normal returns, 5% VaR is: $\text{VaR}_{0.05} = \mu - 1.645\sigma$

**4. Option pricing:**
Black-Scholes model assumes log-normal stock prices (normal log-returns).

### Limitations in Finance
1. **Fat tails:** Real returns often have more extreme outcomes than normal distribution predicts
2. **Skewness:** Returns may not be symmetric
3. **Time-varying volatility:** Volatility clusters in real data
4. **Jump risk:** Sudden large moves not captured by normal distribution

### Numerical Example
**Stock with annual return:** $R \sim N(8\%, 15\%^2)$

**Questions:**
1. Probability of positive return?
2. Probability of return above 20%?
3. 5% Value at Risk?

**Solutions:**
1. $P(R > 0) = P\left(\frac{R - 8\%}{15\%} > \frac{0 - 8\%}{15\%}\right) = P(Z > -0.533) = 0.703$

2. $P(R > 20\%) = P\left(Z > \frac{20\% - 8\%}{15\%}\right) = P(Z > 0.8) = 0.212$

3. $\text{VaR}_{0.05} = 8\% - 1.645 \times 15\% = -16.675\%$

---

## B.4 — Calculus: Derivatives and Optimization

### Basic Derivatives

**Power rule:** $\frac{d}{dx} x^n = nx^{n-1}$

**Exponential:** $\frac{d}{dx} e^x = e^x$, $\frac{d}{dx} e^{ax} = ae^{ax}$

**Logarithmic:** $\frac{d}{dx} \ln(x) = \frac{1}{x}$, $\frac{d}{dx} \log_a(x) = \frac{1}{x \ln(a)}$

### Chain Rule
For composite functions: $\frac{d}{dx} f(g(x)) = f'(g(x)) \cdot g'(x)$

**Example:** $\frac{d}{dx} \ln(x^2 + 1) = \frac{1}{x^2 + 1} \cdot 2x = \frac{2x}{x^2 + 1}$

### Product and Quotient Rules
**Product:** $\frac{d}{dx}[f(x)g(x)] = f'(x)g(x) + f(x)g'(x)$

**Quotient:** $\frac{d}{dx}\left[\frac{f(x)}{g(x)}\right] = \frac{f'(x)g(x) - f(x)g'(x)}{[g(x)]^2}$

### Optimization

**First-order condition:** At optimum, $f'(x) = 0$

**Second-order conditions:**
- $f''(x) < 0$: Local maximum
- $f''(x) > 0$: Local minimum
- $f''(x) = 0$: Inconclusive

### Lagrange Multipliers
To optimize $f(x,y)$ subject to constraint $g(x,y) = 0$:

Set up Lagrangian: $L = f(x,y) - \lambda g(x,y)$

**First-order conditions:**
$$\frac{\partial L}{\partial x} = f_x - \lambda g_x = 0$$
$$\frac{\partial L}{\partial y} = f_y - \lambda g_y = 0$$  
$$\frac{\partial L}{\partial \lambda} = -g(x,y) = 0$$

### Financial Applications

**1. Utility maximization:**
Maximize $U(x)$ subject to budget constraint $px \leq I$

**2. Portfolio optimization:**
Maximize $\mathbb{E}[U(W)]$ subject to budget constraint

**3. Firm optimization:**
Maximize profit $\pi(q) = pq - C(q)$ gives $p = C'(q)$ (price equals marginal cost)

### Worked Example: Portfolio Choice
**Problem:** Maximize $U(W) = \ln(W)$ where $W = W_0(1 + wR + (1-w)r_f)$

**Solution:**
$$\frac{dU}{dw} = \frac{1}{W} \cdot W_0(R - r_f) = \frac{W_0(R - r_f)}{W_0(1 + wR + (1-w)r_f)} = \frac{R - r_f}{1 + wR + (1-w)r_f}$$

Setting equal to zero: This only equals zero if $R = r_f$, which contradicts our assumption.

For stochastic returns, we'd use: $\mathbb{E}\left[\frac{R - r_f}{1 + wR + (1-w)r_f}\right] = 0$

---

## B.5 — Integration and Taylor Expansions  

### Basic Integration

**Power rule:** $\int x^n dx = \frac{x^{n+1}}{n+1} + C$ (for $n \neq -1$)

**Special case:** $\int \frac{1}{x} dx = \ln|x| + C$

**Exponential:** $\int e^x dx = e^x + C$

**Trigonometric:** $\int \sin(x) dx = -\cos(x) + C$

### Integration by Parts
$$\int u \, dv = uv - \int v \, du$$

**Example:** $\int x e^x dx$
Let $u = x$, $dv = e^x dx$, then $du = dx$, $v = e^x$
$$\int x e^x dx = xe^x - \int e^x dx = xe^x - e^x + C = e^x(x-1) + C$$

### Fundamental Theorem of Calculus
If $F'(x) = f(x)$, then:
$$\int_a^b f(x) dx = F(b) - F(a)$$

### Taylor Expansions

**General form around point $a$:**
$f(x) = f(a) + f'(a)(x-a) + \frac{f''(a)}{2!}(x-a)^2 + \frac{f'''(a)}{3!}(x-a)^3 + \cdots$

**Maclaurin series** (Taylor series around $a = 0$):
$f(x) = f(0) + f'(0)x + \frac{f''(0)}{2!}x^2 + \frac{f'''(0)}{3!}x^3 + \cdots$

### Common Taylor Series

**Exponential:** $e^x = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots$

**Natural logarithm:** $\ln(1+x) = x - \frac{x^2}{2} + \frac{x^3}{3} - \frac{x^4}{4} + \cdots$ (for $|x| < 1$)

**Sine and cosine:**
- $\sin(x) = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \frac{x^7}{7!} + \cdots$
- $\cos(x) = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \frac{x^6}{6!} + \cdots$

### Financial Applications

**1. Risk premium approximations:**
For small risks, $\mathbb{E}[U(W + \varepsilon)] \approx U(W) + \frac{1}{2}U''(W)\text{Var}(\varepsilon)$

**2. Duration and convexity in bond pricing:**
$P(\Delta y) \approx P_0 - D \cdot P_0 \cdot \Delta y + \frac{1}{2} \cdot C \cdot P_0 \cdot (\Delta y)^2$

**3. Option Greeks:**
Delta, gamma, theta are essentially first, second, and time derivatives from Taylor expansion.

### Worked Example: Utility Approximation
**Given:** $U(W) = \ln(W)$, $W_0 = 100$, small gamble $\varepsilon$ with $\mathbb{E}[\varepsilon] = 0$, $\text{Var}(\varepsilon) = \sigma^2$

**First and second derivatives:**
$U'(W) = \frac{1}{W}, \quad U''(W) = -\frac{1}{W^2}$

**Taylor approximation around $W_0$:**
$\mathbb{E}[U(W_0 + \varepsilon)] \approx U(W_0) + U'(W_0)\mathbb{E}[\varepsilon] + \frac{1}{2}U''(W_0)\mathbb{E}[\varepsilon^2]$
$= \ln(100) + \frac{1}{100}(0) + \frac{1}{2}\left(-\frac{1}{100^2}\right)\sigma^2$
$= \ln(100) - \frac{\sigma^2}{20000}$

**Risk premium:** The certainty equivalent is approximately $W_0 - \frac{\sigma^2}{200}$.

---

## B.6 — Concavity and Convexity

### Definitions

**Concave function:** $f''(x) \leq 0$ for all $x$ in domain
- Graphically: "bends downward" or "caves in"
- Linear combinations lie above the function

**Convex function:** $f''(x) \geq 0$ for all $x$ in domain  
- Graphically: "bends upward" or "bowls up"
- Linear combinations lie below the function

### Mathematical Characterizations

**For concave functions:**
1. **Second derivative test:** $f''(x) \leq 0$
2. **Jensen's inequality:** $f(\lambda x + (1-\lambda)y) \geq \lambda f(x) + (1-\lambda)f(y)$
3. **First-order condition:** $f(y) \leq f(x) + f'(x)(y-x)$ (function lies below its tangent lines)

**For convex functions:** All inequalities reverse.

### Examples

**Concave functions:**
- $f(x) = \ln(x)$ for $x > 0$
- $f(x) = \sqrt{x}$ for $x > 0$  
- $f(x) = x^{1-\gamma}$ for $\gamma > 1, x > 0$

**Convex functions:**
- $f(x) = x^2$
- $f(x) = e^x$
- $f(x) = x^{1-\gamma}$ for $\gamma < 1, x > 0$

### Economic Significance

**Concave utility functions ($U''(x) < 0$):**
1. **Diminishing marginal utility:** Each additional unit provides less satisfaction
2. **Risk aversion:** Prefer certain outcomes to risky ones with same expected value
3. **Insurance demand:** Willing to pay premiums above actuarial value

**Convex utility functions ($U''(x) > 0$):**
1. **Increasing marginal utility:** Each additional unit provides more satisfaction
2. **Risk seeking:** Prefer risky outcomes to certain ones with same expected value
3. **Gambling behavior:** Willing to accept unfair bets

### Risk Attitudes and Curvature

**Absolute risk aversion:** $R_a(x) = -\frac{U''(x)}{U'(x)}$
- Measures curvature relative to slope
- Higher values indicate more risk aversion

**Relative risk aversion:** $R_r(x) = -x\frac{U''(x)}{U'(x)}$
- Risk aversion scaled by wealth level
- Constant relative risk aversion (CRRA) functions have $R_r(x) = \gamma$

### Applications in Portfolio Theory

**Mean-variance analysis relies on:**
1. **Quadratic utility:** $U(x) = x - \frac{b}{2}x^2$ (concave for appropriate $b$)
2. **Or normal distributions:** Any concave utility with normal returns

**Indifference curves in mean-variance space:**
- Risk-averse: Upward sloping and convex (in $\sigma$-$\mu$ space)
- Risk-neutral: Horizontal lines
- Risk-seeking: Downward sloping

### Numerical Examples

**Example 1: Concavity of logarithmic utility**
$U(x) = \ln(x)$, $U'(x) = 1/x$, $U''(x) = -1/x^2 < 0$ ✓ Concave

**Wealth gamble:** 50% chance of $W_1 = 50$, 50% chance of $W_2 = 200$
- Expected wealth: $\mathbb{E}[W] = 125$
- Utility of expected wealth: $U(125) = \ln(125) = 4.828$
- Expected utility: $0.5\ln(50) + 0.5\ln(200) = 0.5(3.912) + 0.5(5.298) = 4.605$
- Risk premium: $125 - e^{4.605} = 125 - 100 = 25$

**Example 2: Convexity check**
$U(x) = x^2$, $U'(x) = 2x$, $U''(x) = 2 > 0$ ✓ Convex

**Same wealth gamble:**
- Expected wealth: $\mathbb{E}[W] = 125$  
- Utility of expected wealth: $U(125) = 15625$
- Expected utility: $0.5(50^2) + 0.5(200^2) = 0.5(2500) + 0.5(40000) = 21250$
- Risk premium: $21250 - 15625 = 5625 > 0$ (risk seeking!)

---

## B.7 — Advanced Probability Concepts

### Conditional Expectation

**Definition:** Expected value of $X$ given information about $Y$
$\mathbb{E}[X|Y = y] = \int x f_{X|Y}(x|y) dx$

**Law of total expectation:**
$\mathbb{E}[X] = \mathbb{E}[\mathbb{E}[X|Y]]$

### Multivariate Normal Distribution

**Bivariate case:** $(X,Y) \sim N(\boldsymbol{\mu}, \boldsymbol{\Sigma})$

Where $\boldsymbol{\mu} = \begin{pmatrix} \mu_X \\ \mu_Y \end{pmatrix}$ and $\boldsymbol{\Sigma} = \begin{pmatrix} \sigma_X^2 & \sigma_{XY} \\ \sigma_{XY} & \sigma_Y^2 \end{pmatrix}$

**Conditional distributions:** If $(X,Y)$ is bivariate normal, then:
$X|Y = y \sim N\left(\mu_X + \rho\frac{\sigma_X}{\sigma_Y}(y - \mu_Y), \sigma_X^2(1-\rho^2)\right)$

### Moment Generating Functions

**Definition:** $M_X(t) = \mathbb{E}[e^{tX}]$

**Properties:**
1. **Uniqueness:** MGF uniquely determines distribution
2. **Moments:** $\mathbb{E}[X^n] = M_X^{(n)}(0)$ (nth derivative at zero)
3. **Independence:** If $X$ and $Y$ independent, $M_{X+Y}(t) = M_X(t)M_Y(t)$

**Normal MGF:** If $X \sim N(\mu, \sigma^2)$, then $M_X(t) = \exp(\mu t + \frac{1}{2}\sigma^2 t^2)$

### Limit Theorems

**Law of Large Numbers:** Sample average converges to population mean
$\frac{1}{n}\sum_{i=1}^n X_i \xrightarrow{p} \mathbb{E}[X]$

**Central Limit Theorem:** Sample average is asymptotically normal
$\sqrt{n}\left(\frac{1}{n}\sum_{i=1}^n X_i - \mathbb{E}[X]\right) \xrightarrow{d} N(0, \text{Var}(X))$

### Financial Applications

**1. Portfolio diversification:**
As number of assets increases, portfolio risk decreases toward systematic risk.

**2. Monte Carlo simulation:**
Law of large numbers ensures simulated expected values converge to theoretical values.

**3. Risk management:**
CLT justifies normal approximations for portfolio returns when many assets are included.

**4. Statistical inference:**
Enables confidence intervals and hypothesis tests for financial parameters.

### Advanced Example: Optimal Portfolio with Short Sales

**Problem:** Maximize $\mathbb{E}[U(W)]$ where $U(W) = -e^{-aW}$ (exponential utility)

**Solution:** With normal returns and exponential utility, optimal weight in risky asset is:
$w^* = \frac{\mathbb{E}[R] - r_f}{a \cdot \text{Var}(R)}$

**Key insights:**
1. **Higher expected excess return** → larger position
2. **Higher risk aversion** ($a$) → smaller position  
3. **Higher variance** → smaller position
4. **Solution independent of wealth** (constant absolute risk aversion)

This demonstrates how mathematical foundations directly connect to practical portfolio management decisions.

---

## Summary of Mathematical Tools

The mathematical foundations covered in this annex provide the analytical framework for modern finance:

**Probability and Statistics:**
- Expected value and variance quantify risk and return
- Normal distribution enables tractable modeling
- Covariance captures asset interactions

**Calculus:**
- Derivatives find optimal solutions
- Taylor expansions provide approximations
- Integration computes expected utilities

**Advanced Concepts:**
- Concavity explains risk aversion
- Conditional expectations model information updates
- Limit theorems justify asymptotic approximations

These tools combine to create the rigorous mathematical foundation underlying expected utility theory and modern portfolio analysis.