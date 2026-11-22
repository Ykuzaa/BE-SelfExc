# Self-Exciting Claim Arrivals in a Cramér–Lundberg Model

BE *Poisson Processes and Applications in Actuarial Science and Reliability* — 5 ModIA, ENSEEIHT – INSA Toulouse (2025–2026).

Study of a Cramér–Lundberg model where the Poisson claim process is replaced by a self-exciting impact model built from a Poisson random measure (thinning). We compute the expected number of claims at any date, study the role of the parameters, and analyse the ruin probability with discrete and continuous claim size distributions.

Sections marked *Complément* in the notebook (and *complement* in the report) are not required by the subject: we added them only to check our results (exact variance, comparison with Hawkes, equal-mean Poisson, variance premium, sensitivity to the weight 2, long horizon).

## Files

- `BE_SelfExc.ipynb` — notebook with all simulations, figures and results
- `rapport.pdf` — project report
- `presentation.pdf` — oral presentation (Beamer)

## Running the notebook

```bash
pip install numpy matplotlib jupyter
jupyter notebook BE_SelfExc.ipynb
```

The random generator is seeded, so all results of the report can be reproduced (about 30 seconds).

## Splitting the work between three people

The project splits along the questions of the BE. Each part has some theory, some code and a result to present, and the three parts have a similar size (about 80 lines of code and 3 to 4 figures each).

| | Person A — the model | Person B — what changes compared with Poisson | Person C — ruin and premium |
|---|---|---|---|
| Notebook sections | 1, 2, 3, 7, 6.5 | 4, 5, effect of $\alpha$ on ruin (end of 6.2), 6.3 | 6.1, 6.2, 6.4, 6.6, 6.7 |
| Theory | Poisson reminders, construction by thinning, $\mathbb{E}[N_t]$ with the Mecke formula, exact $\mathrm{Var}(N_T)$, link with Hawkes, weight of the second chaos and its sensitivity | Role of $\mu$, $\alpha$, $\beta$, conditions on the parameters, claim size distributions, effect of the structure of arrivals (equivalent Poisson) | Ruin checked after jumps, Lundberg, $\mathrm{Var}(S_t)$, premium principles, long horizon |
| Code | Algorithm 1, `sauts_N`, `simule_impact`, `esperance_impact`, `variance_impact`, Monte Carlo check, Ogata for Hawkes, sensitivity to `facteur` | Table of configurations, sample paths, the five claim size distributions, ruin as a function of $\alpha$, equal-mean comparison | Ruin computation (`marge_min`, `psi`), validation on the course case, comparison of the models, variance premium, long horizon |
| Main result | How the model works, table of course properties | What each parameter does and what the model brings compared with Poisson | How much to charge and what risk is taken |
| Depends on | — | A, then C (`psi`) | A |
| Slides at the oral | 2 to 5 | 6, 7, 10 | 8, 9, 11 |

How to organise:

1. Together at the start: fix the parameters ($\mu$, $\alpha$, $\beta$, $T$, $\eta$, `facteur`) and the function names.
2. Person A delivers the simulation functions first. Person C then delivers the ruin function `psi`. Meanwhile, C can test the ruin code with the Poisson model and B can work on sections 4 and 5, which do not need it.
3. Together at the end: the summary, the conclusion and the report layout. Everyone reads the other parts to be able to answer any question at the oral.
4. At the oral, slides 1 and 12 (title and takeaways) are presented together.
