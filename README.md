# Dynamic Edge Server Placement — Solutions Engineering Case Study

**[→ Open the interactive briefing](https://sanehaa.github.io/edge-placement-demo/)** — a live diagnostic panel built on real evaluation data. Select a traffic load and watch coverage and distance respond; every number is pulled from the actual 25-seed simulation results.

**MSc dissertation, graded 86%.** *"Dynamic Edge Server Placement for Scalable IoT Networks: A Data-Driven Approach using Real-World Workloads"* — built on real Optus Melbourne CBD infrastructure data (125 server sites), with a novel placement algorithm (BAAP) designed and evaluated against the standard greedy baseline.

Reframed here as a solutions-engineering case study: the same rigor, presented as a client-facing technical briefing rather than an academic write-up.

## The headline findings

| Finding | Number |
|---|---|
| Structural coverage ceiling in the original data | 13.2% — regardless of algorithm |
| Coverage after data correction alone | 96.3% (a 629% relative improvement) |
| BAAP's distance improvement over greedy, at load 1,000 | 10.8% closer (1.05km vs 1.17km) |
| Honest trade-off | BAAP serves 2.6% fewer users at that same load |

The biggest lever wasn't a smarter algorithm — it was validating the data before trusting any comparison built on it.

## What's in this repo

| Folder | Contents |
|---|---|
| [`index.html`](index.html) | **Interactive briefing** — live load-level diagnostic, real research charts, honest trade-off callouts |
| [`/docs`](docs/) | Full dissertation PDF, 5-min demo pitch script, objection-handling FAQ |
| [`/notebook`](notebook/) | Full Python implementation — bias analysis, augmentation pipeline, BAAP algorithm, 25-seed evaluation |
| [`/assets`](assets/) | Real charts extracted directly from the research notebook's output |

## Approach

1. **Audited the data before touching the algorithm.** Seven checks surfaced nine distinct biases in the source datasets, the most severe capping coverage at 13.2% regardless of placement method.
2. **Built a four-stage correction pipeline** — KDE sampling, Gaussian Mixture Model-generated suburban users, server deduplication, and network expansion — lifting reachability to 99.2%.
3. **Designed BAAP** (Bias-Aware Adaptive Placement), weighting user importance by data under-representation, not just raw visible demand.
4. **Evaluated both algorithms across 4 scenarios × 5 traffic loads × 25 repeated seeds**, specifically to isolate whether performance gains came from the data or the algorithm.
5. **Reported the trade-off honestly** — BAAP wins on distance at moderate load, loses slightly on coverage, and loses to greedy entirely at high load. No algorithm wins everywhere.

## Tools used

Python (pandas, scikit-learn, scipy) · Kernel Density Estimation · Gaussian Mixture Models · Jupyter/Colab · Matplotlib/Seaborn · Harvard-cited academic methodology

---

*Supervised by Dr Amin Karami. Full methodology, literature review, and complete results tables in the dissertation PDF.*
