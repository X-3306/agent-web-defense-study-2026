# Autonomous-agent web-defense study

**A controlled study of how autonomous AI agents interact with layered defenses on a synthetic web application.**

> **Status: study in progress. This repository is intentionally empty.**
> It exists so there is one permanent, public place where the results will be published. Nothing is released here before the study window closes, and the reason is explained below.

Last updated: 3 October 2026

---

## What this is

The study uses a research testbed to observe how autonomous AI agents behave when they meet layered defensive responses (specially created on them) during a realistic multi-step web task. Every account, credential, record, person, and artifact inside the environment is synthetic. The study does not attempt to identify, classify, or attack any real system.

The core question is whether, and which, security methods designed specifically to counter automated attacks by capable models can actually stop them. The project combines several existing techniques with a few experimental ones.

The goal is a small, honest measurement, not a headline about "AI versus security." If the environment fails to produce a clean signal, that is a result worth publishing too.

The testbed is a research instrument, not a product. It is not an AI detector, and it is not an evaluation of any specific vendor, framework, or model provider. Company names and logos shown on the target are decorative, and the project is not affiliated with any of them.

## Why this repository is empty

Releasing the design of the defensive layers while the study is running would invalidate the measurement, because an agent with access to the methodology can read exactly how each layer works. So the full material is published only after the study window has closed.

## Schedule

| Phase | What happens | When |
|---|---|---|
| Environment design and internal pilot | Synthetic target built and calibrated on disposable runs | Complete |
| Study window | Participants run their own agents against the research target | 3 October 2026 to 30 October 2026 (planned end) |
| Analysis and internal review | Runs are classified, exclusions documented, analysis plan executed. No results are shared during this phase | After the window |
| Aggregate report | Method, arms tested, observed outcomes, failure modes, and limitations | After analysis |
| Source and methodology release | Full methodology and security aspects, published only after the window has closed | After the report |

**Planned end of the study window: 30 October 2026.** The window may end earlier if the hosting fails, for example because of excessive traffic.

**Aggregation and preparation of the collected data may take up to 3 months after the window closes, so up to 30 January 2027 at the latest.** It will probably be faster. Three months is a ceiling, not a target.

## What will be published here

After the study window closes and the data has been prepared:

1. The aggregate report: method, arms tested, observed outcomes, failure modes, and limitations.
2. Aggregate telemetry and results. Individual runs are never published, and raw telemetry stays private.
3. The architecture and backend description, including features that did not make the final cut.
4. The full methodology, ideas and security aspects of the defensive layers.

Contributors who opted in to attribution are named in the report. Everyone else remains aggregate. No names, transcripts, or session traces are published without explicit, separate permission.

## Principles

1. Synthetic only. No real credentials, records, or production systems are in scope.
2. Participants are informed human operators who know the scope, data handling, and stop procedure before the first run.
3. Aggregate results only.
4. No third-party targets. Only the single authorised host listed on the information page is in scope.
5. No deception about risk.
6. Stop on ambiguity.
7. Public methodology, including failures and negative results.

## Participation and rules of engagement

Participation is voluntary and unpaid, and it costs the participant time and tokens. The rules of engagement, the research target, the data handling description, and the Run Report form are all on the public information page:

**https://levuelab.totalh.net**

Please read it fully before running anything. This repository, the information page, and every other page except the listed research target are **out of scope** and must not be attacked.

## Contact

Questions about scope, data handling, participation, or incident reports during the study:

**TarnhavenSystems@proton.me**

Please use email rather than public issues, because public discussion during the study window can reveal details that affect the measurement.

## Follow updates

Use **Watch** on this repository to be notified when material is published.

## Author

X-3306, independent security researcher.
