# Objection Handling — Edge Server Placement Solution

Anticipated questions from technical and business stakeholders, with concise, honest answers grounded in the actual dissertation results.

---

## Technical objections

**"Why not just add more servers instead of optimizing placement?"**
Idle edge servers still draw roughly 60-70% of their rated power even when not serving traffic (Guo et al., 2012) — so over-provisioning is close to as expensive as running servers at full load, without the coverage benefit. The problem isn't "not enough servers," it's "which ones should be switched on," which is why this is a placement problem, not a procurement problem.

**"Is BAAP actually better than the existing greedy approach?"**
Not universally — and that's an intentional finding, not a gap. BAAP wins on average distance at moderate load (10.8% closer at 1,000 users) but serves slightly fewer users at that same load, and greedy is actually closer at 2,000 users. The honest answer is: BAAP is a better choice when minimizing latency for served users matters more than maximizing raw coverage — it's a trade-off decision, not a strict replacement.

**"How does this scale to a full metropolitan deployment, not just Melbourne CBD?"**
The methodology — bias audit, then data correction, then algorithm evaluation — is dataset-agnostic and was explicitly built to generalize. The specific numbers (99.2% reachability, 629% improvement) are tied to the Melbourne dataset; a different city's infrastructure would need the same audit run against its own data before any placement decision.

**"What's the computational cost of BAAP versus greedy?"**
Same asymptotic complexity as the greedy baseline. The added step — computing a KDE-based importance weight per user — doesn't change the overall scaling behavior, so there's no meaningful deployment cost difference.

**"Is this tested against real-time or moving traffic?"**
No — this is a stated limitation. Users were treated as static in this evaluation. Testing against time-varying traffic patterns (peak vs off-peak load) is flagged as future work.

---

## Business / procurement objections

**"Is this production-ready, or research-only?"**
Research-stage, evaluated on real infrastructure data (Optus Melbourne CBD server sites) but with generated rather than measured user location data for the metro-scale test. The recommended next step before production deployment is validating against a real operator's actual sites and, ideally, census-based population data rather than generated distributions — both are explicitly named as future work.

**"What's the actual business impact in plain terms?"**
Two separate wins, worth quoting separately: (1) fixing data quality issues alone took usable coverage from 13% to 96% — meaning existing infrastructure, correctly evaluated, may already perform far better than flawed simulations suggested; (2) the BAAP algorithm shaves meaningful latency for served users at moderate load, which matters most for latency-sensitive applications (AR/VR, industrial IoT) rather than blanket coverage.

**"Why should we trust these numbers?"**
Every headline number is backed by 25 repeated simulation runs across 5 traffic levels and 4 experimental scenarios (original data + greedy, original data + BAAP, augmented data + greedy, augmented data + BAAP) — designed specifically to isolate whether an improvement came from the data or the algorithm, rather than conflating the two.

**"What would the next phase of this work look like?"**
In priority order: (1) validate against a real operator's actual server sites rather than generated suburban expansion, (2) replace generated population estimates with official census data, (3) benchmark against an exact optimal solution and other published methods, not just the greedy baseline, (4) test against time-varying rather than static traffic.

---

*All figures sourced from the dissertation "Dynamic Edge Server Placement for Scalable IoT Networks" (MSc Computer Science, graded 86%) — see the full write-up for complete methodology and results tables.*
