# Self-Exciting Claim Arrivals in a Cramér–Lundberg Model

BE *Poisson Processes and Applications in Actuarial Science and Reliability* — 5 ModIA, ENSEEIHT – INSA Toulouse (2025–2026).

Study of a Cramér–Lundberg model where the Poisson claim process is replaced by a self-exciting impact model built from a Poisson random measure (thinning). We compute the expected number of claims at any date, study the role of the parameters, and analyse the ruin probability with discrete and continuous claim size distributions.

## Files

- `BE_SelfExc.ipynb` — notebook with all simulations, figures and results
- `rapport.pdf` — project report

## Running the notebook

```bash
pip install numpy matplotlib jupyter
jupyter notebook BE_SelfExc.ipynb
```

The random generator is seeded, so all results of the report can be reproduced (about 15 seconds).

## Splitting the work between three people

The project splits naturally along the three questions of the BE. Each part has some theory, some code and something to explain to the manager.

| | Person A — the model | Person B — parameters and claim sizes | Person C — ruin and premium |
|---|---|---|---|
| Notebook sections | 1, 2, 3, 7 | 4, 5 | 6 (6.1 to 6.5) |
| Theory | Poisson reminders, construction by thinning, $\mathbb{E}[N_t]$ with the Mecke formula, link with Hawkes, weight of the second chaos | Role of $\mu$, $\alpha$, $\beta$, conditions on the parameters | Ruin checked after jumps, Lundberg, $\mathrm{Var}(S_t)$, premium principles |
| Code | Algorithm 1, `sauts_N`, `simule_impact`, `esperance_impact`, Monte Carlo check, Ogata for Hawkes | Table of configurations, sample paths, the five claim size distributions | Vectorised ruin computation, validation on the course case, equal-mean comparison, variance premium, long horizon |
| For the manager | How the model works, table of course properties | What each parameter does and its impact | How much to charge and what risk is taken |
| Provides | Simulation functions (first) | The `lois` dictionary | Uses A and B |

How to organise:

1. Together at the start: fix the parameters ($\mu$, $\alpha$, $\beta$, $T$, $\eta$, `facteur`) and the function names.
2. Person A delivers the simulation functions first, since B and C depend on them. Meanwhile C can test the ruin code with the Poisson model.
3. Together at the end: the summary for the manager and the conclusion. Everyone reads the other parts to be able to answer any question at the oral.

Person C has the most code and person A the hardest theory; person B can also take care of the report layout and the figures.
