# Technical project descriptions

Concise descriptions for a project listing. Repository titles and findings are
used as written; no institutional affiliation, dates, or personal contribution
claims are implied. The linked repositories contain the methods and evidence
behind each summary.

## Can Trading Signals Survive Selection Bias and Transaction Costs?

Python framework for chronological evaluation of 12 industry momentum/reversal
strategies and an annual selector on Kenneth French's 49 Industry Portfolios.
Includes delayed execution, exact self-financing transaction costs, frozen
validation selection, HAC uncertainty, and stationary-bootstrap family inference.
The selected strategy earned −0.18% annualized mean net return over 2015–2025 at
10 bps one-way cost; the family test found no significant positive-return evidence.
A separate 2,000-dataset inference audit reduced short-sample false positives
from 9.3% to 6.0% through bootstrap studentization, while both procedures stayed
near nominal size at the historical sample length. Retains all candidates,
paired audit trials, cost scenarios, and source fingerprints; original empirical
results remain unchanged.

**Skills:** Python · Statistical inference · Portfolio accounting · Time-series analysis · Research design

[Repository](https://github.com/devannshi/alpha-research-lab)

## When Does Market Making Pay After Costs and Inventory Risk?

Event-driven Avellaneda–Stoikov research framework with causal parameter calibration,
order latency, queue proxies, partial fills, fees, risk limits, and explicit
liquidation accounting. Evaluates four policies through 5,632 synthetic policy evaluations and
ETHUSDT/BTCUSDT replay of 12.16 million events across six asset-date samples. Adaptive
quoting reduced average inventory RMS by 74.9% in the reference synthetic study,
while passive quoting earned greater raw profit. Paired path comparisons and a
36-scenario grid expose sensitivity to costs and execution assumptions; historical
replay does not establish a persistent trading edge.

**Skills:** Python · Market microstructure · Event-driven simulation · Execution modeling · Monte Carlo evaluation

[Repository](https://github.com/devannshi/microstructure-market-making)

## Does Modeling Competing Traders Improve Optimal Execution?

Research framework for heterogeneous execution games under latent market regimes.
Combines exact quadratic best responses, direct and iterative mean-field solutions,
causal impact-corrected filtering, and finite-player deviation audits. Implements
an exact terminal-liquidation constraint through a KKT projection and evaluates
seven policies on 512 common-noise paths per main study. Under equal completion,
filtered mean-field execution did not establish an objective improvement over
TWAP. Includes accounting identities, convergence residuals, constrained-optimizer
checks, and explicit limits of certainty-equivalent planning.

**Skills:** Python · Stochastic control · Convex optimization · Mean-field games · Hidden-state filtering

[Repository](https://github.com/devannshi/mean-field-execution)

## Do Hidden Market Regimes Improve Tail-Risk Forecasts?

Original Gaussian and Student-t HMM implementations evaluated through causal
walk-forward forecasting, 400 independent synthetic datasets, and three Federal
Reserve FX series. Compares latent-state models with IID, rolling, and EWMA
baselines using predictive density, quantile loss, and tail-violation diagnostics.
Student-t HMMs improved mean log scores over Gaussian HMMs, while a simpler
Student-t EWMA follow-up achieved higher density scores with worse raw 5% tail
breach rates. Includes numerical-oracle tests, chronological fit audits, and a
past-only quantile controller without claiming conditional coverage guarantees.

**Skills:** Python · Hidden Markov models · Maximum likelihood · Time-series forecasting · Risk calibration

[Repository](https://github.com/devannshi/regime-risk-lab)

## How Reliably Can We Recover Hidden States from Noisy Data?

State-space research framework combining exact Kalman likelihood estimation,
RTS smoothing, and bootstrap/optimal-proposal particle filtering. A 1,000-trial
core experiment measures parameter recovery, state error, and interval coverage;
additional studies examine particle convergence, missing observations, outliers,
and nonlinear stochastic volatility. Demonstrates the observation-loading/state-
scale identifiability ridge and distinguishes filtering from smoothing and oracle
information. Known-parameter Kalman interval coverage was 95.06%, compared with
92.81% after plug-in parameter estimation, exposing uncertainty omitted by
conditional state intervals.

**Skills:** Python · Sequential Monte Carlo · Kalman filtering · Likelihood optimization · Uncertainty quantification

[Repository](https://github.com/devannshi/latent-state-lab)
