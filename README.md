# Quantitative Research Portfolio

**Five reproducible studies of signals, execution, latent states, and model risk.**

The common question is whether a model's apparent advantage survives realistic
information, accounting, uncertainty, and baseline checks. Each repository includes
original Python implementations, executed experiments, retained results, tests,
and a mathematical explanation. The studies report failures alongside improvements.

## Evidence

Full source, mathematical reports, executed notebooks, raw trial tables, tests,
and experiment manifests are included in each project. Inspecting the
published artifacts requires no private market-data subscription. Each repository
explains how to reproduce its simulations and retrieve any public source data.

## Choose a starting point

| Research focus | Suggested reading order |
| --- | --- |
| Systematic strategy research | **Alpha Research** → Regime Risk → Market Making → Latent States → Mean-Field Execution |
| Execution and market microstructure | **Market Making** → Mean-Field Execution → Alpha Research → Regime Risk → Latent States |
| Statistical and probabilistic modeling | **Latent States** → Regime Risk → Alpha Research → Mean-Field Execution → Market Making |

These orders emphasize different research skills; the projects answer different
questions and their performance numbers are not directly comparable.

## The projects

### 1. [Can Trading Signals Survive Selection Bias and Transaction Costs?](https://github.com/devannshi/alpha-research-lab) [![Tests](https://github.com/devannshi/alpha-research-lab/actions/workflows/tests.yml/badge.svg)](https://github.com/devannshi/alpha-research-lab/actions/workflows/tests.yml)

**Do industry momentum and reversal signals survive selection and trading costs?**

A chronological study of 12 fixed long–short candidates and an annual selector
using Kenneth French's 49 Industry Portfolios. It combines delayed execution,
exact self-financing cost accounting, frozen validation selection, HAC uncertainty,
and a stationary-bootstrap family test.

The validation winner's 2015–2025 net annualized arithmetic mean was **−0.18%** at
10 bps one-way cost; the declared family test did not reject its no-edge null
(**p = 0.792**). In a separate known-null selection experiment, naive best-of-50
selection falsely rejected in **65.0%** of 1,000 replications. That experiment uses
its own known-null cutoff and does not validate the empirical bootstrap's size.

A separate **2,000-dataset audit** then tests the inference procedure itself.
At 500 observations, within-bootstrap HAC studentization reduces the measured
false-positive rate from **9.3% to 6.0%**, with a paired reduction interval of
**2.16–4.44 percentage points**. At the actual 2,766-observation holdout length,
rates are **5.3% and 5.1%**. The secondary empirical family p-value is **0.786**;
the original negative conclusion is preserved. This establishes a useful
short-sample improvement in the declared Gaussian audit, not uniform error
control for all market data.

**Demonstrates:** disciplined hypothesis testing, an auditable portfolio ledger,
and a result that remains negative after all candidates are disclosed.
Industry research portfolios are not directly tradable securities; costs are
scenarios, and the historical data are a revised provider vintage.

[Executed report](https://github.com/devannshi/alpha-research-lab/blob/main/results/published/report.md) ·
[Candidate ledger](https://github.com/devannshi/alpha-research-lab/blob/main/results/published/research_ledger.csv) ·
[Inference calibration audit](https://github.com/devannshi/alpha-research-lab/blob/main/results/bootstrap_audit/report.md) ·
[Protocol](https://github.com/devannshi/alpha-research-lab/blob/main/research_protocol.json)

### 2. [When Does Market Making Pay After Costs and Inventory Risk?](https://github.com/devannshi/microstructure-market-making) [![Tests](https://github.com/devannshi/microstructure-market-making/actions/workflows/ci.yml/badge.svg)](https://github.com/devannshi/microstructure-market-making/actions/workflows/ci.yml)

**What does inventory control cost once execution assumptions become explicit?**

An Avellaneda–Stoikov framework with causal calibration, delayed cancel/replace,
queue proxies, partial fills, fees, inventory limits, and terminal liquidation.
The controlled study contains **5,632 policy evaluations**, including 256 independent
primary paths and a 36-scenario execution stress grid. Recorded ETHUSDT/BTCUSDT
replay covers **12.16 million events** across six asset-date samples and 1,728
policy/block/scenario evaluations.

Adaptive quoting reduced mean inventory RMS by **74.9%** versus passive BBO in the
reference synthetic experiment, while earning less raw profit. Passive BBO had
the highest mean P&L in all 36 declared stress scenarios. At the historical
reference settings (back queue, 50 ms latency, 1 bp maker
cost, 4 bps terminal taker cost), **none of 24 asset-date-policy totals was positive**.
Aggregate quotes and trades do not identify an actual queue.
The many replay evaluations are not independent historical observations.

**Demonstrates:** market microstructure, event ordering, execution engineering,
and the distinction between a risk improvement and a profit improvement.

[Executed report](https://github.com/devannshi/microstructure-market-making/blob/main/results/RESULTS.md) ·
[Historical blocks](https://github.com/devannshi/microstructure-market-making/blob/main/results/historical_blocks.csv) ·
[Execution protocol](https://github.com/devannshi/microstructure-market-making/blob/main/docs/EXPERIMENT_PROTOCOL.md)

### 3. [Does Modeling Competing Traders Improve Optimal Execution?](https://github.com/devannshi/mean-field-execution) [![Tests](https://github.com/devannshi/mean-field-execution/actions/workflows/tests.yml/badge.svg)](https://github.com/devannshi/mean-field-execution/actions/workflows/tests.yml)

**Does a computed equilibrium remain useful under partial information and finite populations?**

Heterogeneous execution games combine exact quadratic best responses, a direct
mean-field reference, residual-audited iteration, impact-corrected regime filtering,
and finite-player unilateral-deviation tests. A separate KKT-constrained study
requires every policy to liquidate fully.

Across **512 common-noise paths** in that hard-completion study, filtered mean-field
execution minus TWAP had mean penalized-objective difference **−0.001241** with
paired 95% interval **[−0.003270, 0.000788]**. It did not establish an improvement.
A simpler AC-style policy had a lower mean objective than filtered MFG, but that
paired difference also included zero.

**Demonstrates:** stochastic control, optimization, equilibrium verification,
and fair comparison under the same terminal constraint. These are synthetic
certainty-equivalent policies and open-loop deviation audits, not an adaptive
Nash-equilibrium theorem or an empirical execution edge.

[Executed report](https://github.com/devannshi/mean-field-execution/blob/main/results/published/report.md) ·
[Equal-completion study](https://github.com/devannshi/mean-field-execution/blob/main/results/hard_liquidation/REPORT.md) ·
[Derivation](https://github.com/devannshi/mean-field-execution/blob/main/docs/methodology.md)

### 4. [Do Hidden Market Regimes Improve Tail-Risk Forecasts?](https://github.com/devannshi/regime-risk-lab) [![Tests](https://github.com/devannshi/regime-risk-lab/actions/workflows/ci.yml/badge.svg)](https://github.com/devannshi/regime-risk-lab/actions/workflows/ci.yml)

**Do latent regimes add forecasting value beyond heavy tails and adaptive volatility?**

Gaussian and Student-t hidden Markov models are evaluated against IID, rolling,
and EWMA baselines. The study includes **400 independent synthetic datasets** and
**5,267 chronological forecasts per model per currency** for EUR/USD, GBP/USD,
and JPY/USD, with density scores, tail diagnostics, and optimizer audits.

Student-t HMMs improved mean log scores over Gaussian HMMs on all three currencies.
An explicitly labeled Student-t EWMA follow-up scored higher than the HMM on all
three, but had worse raw 5% breach rates (**6.40%, 6.65%, 5.81%**).
Improved average density fit and improved tail calibration are separate objectives.

**Demonstrates:** latent-state inference, causal evaluation, component ablation,
and distributional risk. Forecast scores are not trading profits; average breach
frequency does not establish conditional coverage or independent violations.

[Executed report](https://github.com/devannshi/regime-risk-lab/blob/main/results/full/REPORT.md) ·
[Forecast summary](https://github.com/devannshi/regime-risk-lab/blob/main/results/full/real_summary.csv) ·
[Initial and follow-up research log](https://github.com/devannshi/regime-risk-lab/blob/main/docs/RESEARCH_LOG.md)

### 5. [How Reliably Can We Recover Hidden States from Noisy Data?](https://github.com/devannshi/latent-state-lab) [![Tests](https://github.com/devannshi/latent-state-lab/actions/workflows/ci.yml/badge.svg)](https://github.com/devannshi/latent-state-lab/actions/workflows/ci.yml)

**How do identification, parameter fitting, and particle approximation affect state inference?**

Exact Kalman likelihood/MLE, RTS smoothing, and bootstrap/optimal-proposal particle
filters are evaluated in **1,000 independent core trials**. Additional experiments
cover particle convergence, missingness, outliers, chronological holdout prediction,
and nonlinear stochastic volatility against a deterministic grid reference.

Known-parameter Kalman state intervals achieved **95.06%** coverage; full-sample
plug-in parameter estimates reduced coverage to **92.81%**. Particle approximations
approached the exact Gaussian benchmark. A rescaling experiment demonstrates why
observation loading and state-noise scale need a normalization before estimation.

**Demonstrates:** probability, likelihood optimization, identifiability, numerical
validation, and uncertainty decomposition. Smoothing uses future information;
conditional state intervals do not integrate parameter uncertainty.

[Executed report](https://github.com/devannshi/latent-state-lab/blob/main/results/full/REPORT.md) ·
[Core trial results](https://github.com/devannshi/latent-state-lab/tree/main/results/full) ·
[Mathematical methods](https://github.com/devannshi/latent-state-lab/blob/main/docs/METHODS.md)

## How to assess the work

Start with a report's primary question and strongest baseline, then trace one
reported number to its trial table and manifest. Each repository's README provides
installation, test, quick-run, and full-reproduction commands. Executed notebooks
explain the main calculations; protocol and limitation documents identify what the
experiment can establish. Historical data access and reproduction conditions vary
by repository and are documented there.

Negative results are useful when they identify why a model loses: selection and
costs, an unequal terminal constraint, a stronger volatility baseline, or an exact
conditional-mean benchmark. Complexity has to earn its place under the intended
objective. A favorable synthetic result alone does not establish a market edge.

The algorithms build on established literature. The contributions are independent
implementations, explicit assumptions, numerical audits, and executed comparative
studies—not claims to have invented Kalman filters, HMMs, mean-field games,
Avellaneda–Stoikov quoting, or bootstrap inference. Each repository cites its
methodological sources and records its own development and data provenance.

[Concise technical project descriptions](docs/PROJECT_DESCRIPTIONS.md)
