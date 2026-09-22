# Demo Pitch Script — Edge Server Placement Solution Brief
*5 minutes. Written for a client-facing / interview presales walkthrough.*

---

## Opening (30 sec)

"I want to show you something that starts as a data problem, not an algorithm problem — because that distinction is the whole story here.

The scenario: a telecom operator has 125 edge server sites and wants to know which ones to activate to keep 5G latency under 20 milliseconds, without switching on more servers than they need to. That's the Edge User Assignment problem — and it's NP-hard, so there's no algorithm that guarantees a perfect answer at real-world scale. The best you can do is a good approximation."

---

## The twist (60 sec)

"Here's what I found before I even got to the algorithm: I ran the existing simulation data through a bias audit, and it turned out 87% of a realistic metro-scale user base was outside the reach of every single server in the dataset. Not because the servers were badly placed — because the servers were all clustered in a 3-square-kilometer patch of Melbourne CBD, while the user data spanned over 16,000 square kilometers.

That's a structural ceiling. No algorithm — however clever — can cover users that are geographically unreachable in the data. So the real first move wasn't 'build a better algorithm.' It was 'fix the evaluation environment, or every result downstream is meaningless.'"

*[Show the live diagnostic panel — bias analysis chart]*

---

## The fix (60 sec)

"I built a four-stage correction pipeline — kernel density sampling, Gaussian mixture modelling for suburban users, deduplicating clustered server sites, and expanding the server network to match. That took reachability from 13.2% to 99.2%.

That's a 629% improvement — and it came entirely from the data, before I introduced any new algorithm. That's an important finding on its own: it means a lot of published edge-placement research claiming algorithm improvements might actually be measuring data artifacts."

*[Show the augmentation validation map — the real spatial scatter]*

---

## The algorithm (60 sec)

"Once the environment was trustworthy, I designed BAAP — Bias-Aware Adaptive Placement. It's a variant of the standard greedy approach, but it weights users by how under-represented their area is in the data, not just by raw visible demand. Same computational complexity as the baseline, so there's no deployment cost penalty.

At 1,000 simulated users, BAAP places served users 10.8% closer to their server on average than the greedy baseline — roughly 0.6 milliseconds less propagation delay."

*[Toggle the live load selector to 1,000 — let the chart move]*

---

## The honest trade-off (45 sec)

"Here's the part I want to be upfront about, because a real solutions conversation should include this: BAAP isn't a strict win. At that same 1,000-user load, it served 93.7% of users versus greedy's 96.3% — 2.6% fewer people, in exchange for the ones it does serve being closer. And at 2,000 users, greedy actually comes out ahead on distance.

No single algorithm wins at every traffic level. That's not a weakness in the analysis — that's what a properly tested result looks like, and it's the kind of trade-off I'd actually walk a client through rather than oversell."

---

## Close (30 sec)

"So the takeaway: the biggest lever here wasn't a smarter algorithm — it was validating the data before trusting any comparison built on it. That's a pattern I'd bring into any solutions conversation: diagnose before you optimize, and be honest about what the numbers do and don't support.

Full methodology, all 25-seed results, and the complete dissertation are linked below if you want to go deeper."

---

## Delivery notes
- Total run time: ~4.5–5 minutes at a natural pace
- The "honest trade-off" section is the most important part of this script for a Solutions Engineer interview — it's the moment that signals judgment, not just technical output
- If asked to shorten to 2 minutes: keep Opening, Twist, and Honest trade-off; cut Fix and Algorithm detail down to one sentence each
