# Vu2020 TDVRPTW benchmark family (Arigliano-generator TD travel times, larger sizes, curated VRP variant)

Satellite benchmark repository of [MAMUT-routing](https://github.com/ANR-MAMUT/MAMUT-routing) (ANR MAMUT, ANR-22-CE22-0016), mounted there as `benchmarks/TDVRPTW/Vu2020`. Self-contained: instances, canonical arrival-time-function (ATF) sidecars and best-known solutions ship together.

## What this family is — and what it is not

The raw data extends the Arigliano et al. **TD-TSPTW** generator (same IGP model: 73 speed zones, 3 shared speed profiles) to larger sizes, as used by Vu et al. (2020): sizes 59/79/99 customers, congestion depth Delta ∈ {70, 80, 90, 98}, traffic patterns A/B, absolute TW widths ∈ {40, 60, 80, 100, 120, 150, 180}, five instances each — an 840-instance full factorial with no demands, capacities, fleet sizes or service times. Instance names keep the `Vu-` prefix; the recorded `instance_origin` is `Ari2018` (same generator).

This canonical family is the **VRP variant curated by Onyr (2024–2026)**: demands, vehicle capacities, fleet sizes and gaussian service times were generated once by the legacy TDVRPTW-benchmarks pipeline and are pinned here verbatim (recorded per instance in `metadata.legacy_attribute_source`); raw time windows kept verbatim (two raw files have customer windows ending after the depot due date; they are kept — the unusable tail is cut by ATF-domain restriction at check time). It is therefore **not** comparable with published TD-TSPTW results on the underlying raw files.

## Curated subset (deterministic)

The family ships **168 instances**, not the full 840: one per structural cell `(n, Delta, pattern, width)`, candidates holding a legacy best-known solution first, remaining ties by ascending SHA-256 of the canonical instance name. Names `Vu-A<id>-p<Pattern>-d<Delta>-w<Width>` under `n=<customers>` carry all structural parameters. The full raw trees remain available upstream.

## Format

- `<Name>.vrp.json` — MAMUT shape: depot 0, mandatory display `coordinates` (deterministic stress-layout embedding of the symmetric raw distance matrix; near-exact here, quality in `metadata.coordinates_method`), `horizon` `[0, depot due date]`, `td` block with the sidecar's storage-independent sha256.
- `<Name>.atf.json.gz` — canonical ground truth: one arrival-time NDCPWLF per arc, exact IGP consolidation (breakpoints at every speed-zone boundary crossing, exact forward Ichoua re-evaluation; last zone extended beyond the horizon). All sidecars are gzipped in this satellite.
- `<Name>.bks.Duration.json` — best known solution under the `Duration` objective; costs are always the canonical checker's output.

Population pipeline: `populate_td_ari_vu` v1 (curation tooling maintained outside this repository; links will be published with the benchmark paper).

## Provenance and licensing

Underlying raw data: the Arigliano-generator TD-TSPTW distribution at Vu et al. (2020) sizes. MAMUT-authored curation artifacts under the MIT license; this notice does not relicense the underlying third-party benchmark definitions.
