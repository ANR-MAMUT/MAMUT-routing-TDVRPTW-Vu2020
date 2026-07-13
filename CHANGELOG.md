# Changelog — Vu2020 TDVRPTW BKS

All notable changes to the curated `Vu2020` TDVRPTW best-known solutions (BKS) are recorded here. Objective: **Duration** (duration minimization — the depot departure time of each route is a decision variable). Costs are the authoritative output of the canonical checker (`mamut_routing_lib.td.check_td_solution`): exact IEEE-754 double arithmetic, no epsilon thresholds, routes in canonical order (sorted by first customer), total summed in that order — so any strict improvement is real. Reminder: this family is the VRP variant curated by Onyr (see README.md), so these BKS are not comparable with published TD-TSPTW results on the underlying raw files.

## 2026-07-13

**7 further BKS stamped proven optimal, all 7 also checker-valid strict improvements** by the long-limit continuation of the weekend re-certification (2026-07-11/12/13, Grid'5000; time limits raised to 1800 s, 7200 s at n=99). Five of these (Vu-A4-pA-d70-w100, Vu-A5-pB-d90-w60 at n=59; Vu-A2-pB-d80-w40, Vu-A4-pB-d98-w150, Vu-A5-pB-d90-w40 at n=79) had been refused as four-way disagreements by the main wave; the longer limits closed the labeling-mode gap (the set-valued-duration repair had already removed the mispricing, the modes then agreeing once both reached proof), and the two at n=99 (Vu-A1-pA-d80-w180, Vu-A4-pB-d98-w150) closed for the first time. Protocol unchanged: four independent exact solves (cold and warm starts crossed with the two labeling modes) agreeing on one checker-exact value, an audited exact-pricing phase in every run, and no checker-infeasible priced column; the exact value-jump arm is folded direction-aware where present. This family now carries 166 certified TDVRPTW BKS, 163 of them strict improvements over the previously heuristic references.

## 2026-07-11 (second entry)

9 further BKS improved and **10 further BKS stamped proven optimal** under the clean-runs refinement of the four-run protocol: on these instances one or two of the four runs skipped a checker-infeasible priced column (an ulp-scale time-window boundary artifact of the solver's internal arithmetic, e.g. a route violating a deadline by 2e-13 s) and were excluded; the certificate stands on the remaining clean runs (all Optimum at one agreeing value, at least two runs including a cold start, exact-pricing phase audited).

## 2026-07-11

**149 BKS stamped proven optimal** (`metadata.optimality`), the family's first optimality certificates. Each stamp certifies four independent exact solves (cold and warm starts x two labeling modes) agreeing on the value, an audited exact-pricing phase in every run, zero checker-infeasible priced columns, and canonical-checker re-validation at stamping time. Instances whose runs disagreed, timed out, or priced a checker-infeasible column carry NO stamp.

## 2026-07-10

147 BKS improved by exact solves recorded as ordinary best-known solutions (no optimality stamps): a full re-certification campaign ran the exact solver (kayros lera branch-price-and-cut, HiGHS backend) four times per instance (cold and warm starts, two labeling modes) on Grid'5000 and only values with four-way agreement, an audited exact-pricing phase, and canonical-checker re-validation were accepted. The previous references at these sizes were heuristic (TD-ILS seeds), so improvements are broad: all three sizes covered (n=59/79/99), largest single improvement about -3.5%. Optimality stamping is handled separately from this fold.

## 2026-07-08

162 of 168 BKS improved (mean -1.54%, largest single improvement -6.01%) by a 20,808-run anytime-strategy head-to-head campaign on Grid'5000: kayros 0.4.0.dev0 (TD-ILS, TD-ACO+LS, and an ACO-then-ILS budget split, all over the granular time-dependent local search), per-size time limits (120 s for n<=30, 300 s for n<=60, 600 s for n<=100), seeds {42, 123, 456}, single-threaded runs. Improve-only fold: for each instance the campaign-best solution was re-priced by the canonical checker before writing (checker cost authoritative); stored BKS marked proven optimal were left untouched.

## 2026-07-06 — local-search sweep

165 BKS improved by the first sweep of kayros 0.2.0.dev0 TD-ACO with time-dependent local search (tree-evaluated VND, every accepted move repriced by the checker-identical fold), 10 seeds per instance on Grid'5000.

## 2026-07-06 — initial seeding sweep

165 BKS added, reaching full 168/168 coverage, from the initial large-scale seeding sweep across all four TD families run on 2026-07-04 (kayros 0.0.1 TD-ACO, Grid'5000, 10 seeds per instance, 13 520 runs total).

## 2026-07-03

Family populated (168 curated instances + ATF sidecars) with 3 BKS re-validated and re-priced from Onyr's legacy heuristic store (2024–2026 TDVRPTW-benchmarks pipeline).
