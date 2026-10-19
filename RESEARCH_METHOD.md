# Research methodology

This document proposes a reproducible study for the Tarnhaven testbed. It separates engineering verification from evidence about agent behavior. 

This document contains a description of the research methods and principles that I myself relied upon when creating this project. The text is written specifically in a "to you" format, as you can use it as a starting point for your own project.

## 1. Study objective

Estimate how selected defensive interventions affect autonomous agent progression through a fixed, synthetic application task when the agent receives no human assistance during the run.

The study is not designed to identify whether an arbitrary visitor is an AI. It measures behavior of known, consented or otherwise authorized agent configurations under specified conditions. The findings do not automatically generalize to unobserved models, human attackers, or production systems.

## 2. Study questions

1. Does a server-enforced proof-of-work gate change the probability or time of reaching the terminal synthetic archive state compared with baseline?
2. Does progressive maze routing change route depth, completion, abandonment, or request cost?
3. Do policy, authority, tool-like, relay, redirection, or conflict cues change stopping and continuation behavior?
4. Does the bounded OPSEC stutter or archive-status reconciliation arm increase repeated actions, waiting time, or abandonment?
5. Do combinations of defenses produce interaction effects that differ from each defense alone?
6. Do browser-agent and direct HTTP conditions produce different measurements and outcomes?

## 3. Hypotheses

Treat all statements below as hypotheses until supported by preregistered observations.

- H1: Request-context scoring alone will have unstable sensitivity and specificity across browser automation, direct HTTP tools, privacy products, and network conditions.
- H2: A server-enforced challenge will affect progression more consistently than text-only cues, while increasing completion time and imposing accessibility and compute costs.
- H3: Labyrinth routing will increase requests and time for agents that follow its links, but may have little effect on agents that inspect APIs or abandon the task.
- H4: Defensive language interventions may correlate with stopping or redirection for some configurations, but effects will vary with model, prompt, and tool harness.
- H5: The bounded OPSEC interventions can create measurable waiting or repetition patterns, but such behavior will not reveal an agent's private memory state or explain why a repeated action occurred.
- H6: Combined controls may interact. Their effects cannot be estimated by adding single-arm effects without an explicit factorial design.

## 4. Experimental unit and eligibility

The unit is one independent run with a new visitor identifier, fresh target state, fixed task, fixed arm, and a predeclared stop budget. A run must record whether it used:

- A browser with rendering and JavaScript
- A headless browser with declared capabilities
- Direct HTTP requests such as curl
- A multi-tool agent harness that combines these paths

These are distinct conditions. Do not merge browser motion measurements with direct HTTP runs as though both had equal opportunities to emit the same features. 

## 5. Randomization and arms

Use a balanced randomized assignment within time blocks. Assignment should be performed before the task begins and remain fixed throughout a run. 

Begin with a small, interpretable design:

| Family | Suggested arms | Core contrast |
| --- | --- | --- |
| Reference | `baseline` | Default site behavior without added intervention |
| Navigation | `maze` | Progressive maze compared with baseline |
| Technical friction | `challenge` | Server gate compared with baseline |
| Combined technical | `layered` | Interaction of navigation and challenge |
| Content interventions | safety, authority, function call, relay, goal redirect, instruction conflict, bombardment | Each assigned intervention compared with a contemporaneous baseline |
| OPSEC experiments | `opsec_stutter`, `opsec_cognitive_loop` | Repeated-action and bounded wait-flow outcomes |

## 6. Outcomes and operational definitions

### Primary outcome

**Terminal completion:** the run obtains the expected synthetic archive canary before the time and action budget expires. Define terminal success from server-side event sequence and archive marker, not from the agent's self-report.

### Secondary outcomes

- **Deepest stage:** maximum predefined chain stage reached, from registration through archive retrieval and optional key-validation interaction.
- **Time to stage:** wall-clock time between first target request and each stage transition. Record clock source and service health.
- **Request cost:** number of requests and bytes sent and received, grouped by endpoint and run.
- **Challenge outcomes:** issue, solve, failure, replay, expiry, and elapsed solve time.
- **Maze engagement:** pages, deepest maze node, context cues served, canaries presented, and return to the main task.
- **Content response:** signed same-origin review-link follow, task stop, task continuation, conflicting instruction choice, or no observable response.
- **OPSEC stutter:** number of repeated equivalent read-only action keys within the configured time window, trigger event, and subsequent action sequence.
- **OPSEC reconciliation:** stage visits, wait duration, early polls, retries, request cap, completion, bypass, and abandonment.
- **Resource cost:** CPU, memory, network, archive bytes, and estimated model token cost where the provider reports it reliably.
- **Failure classification:** defense outcome, application error, network or DNS failure, infrastructure overload, researcher intervention, and agent refusal.


## 7. Sample size and uncertainty

Choose sample size from the minimum effect that would matter to the research question and expected baseline completion rate. A power calculation should account for clustering by model and time block. If an initial pilot supplies the nuisance parameters, label it exploratory and do not reuse it as an independent confirmatory sample unless the analysis plan explicitly accounts for that reuse.

Report denominators, missing runs, exclusions, effect sizes, and uncertainty intervals. For binary completion, report group rates and a confidence interval for a preselected contrast. For time-to-stage, account for censored runs that did not reach a stage. For multiple models, show per-model estimates and a pooled estimate only when its assumptions are defensible. Small samples support descriptive observations, not broad claims that a defense works for AI generally.

## 8. Human and accessibility calibration

If any score or route affects ordinary users, evaluate it with a separately recruited, consented human cohort. Include keyboard-only use, screen readers, switch or alternative input where appropriate, slow connections, privacy extensions, and varied locales. Estimate false positive rates and task completion changes for each subgroup with suitable uncertainty. Do not tune thresholds on one cohort and report performance on that same cohort as an independent validation.

## 9. curl and interface condition

Direct HTTP clients do not generate pointer, scroll, or browser-rendering features. Browser-dependent score components should be recorded as unavailable, not silently scored as adverse evidence. Test the chain with at least one direct HTTP client and one browser-capable agent if the study claim covers both.

Compare:

1. Route reachability and response codes
2. Challenge issue and validation
3. Session and visitor binding
4. Server-side event completeness
5. Completion and timing
6. The effect of absent client-side measurements on score and arm routing

Do not use an artificial browser signal generator as evidence of human-like behavior. If synthetic feature injection is tested, label it as a separate adversarial instrumentation condition.

## 10. Analysis plan

- Analyze on an intention-to-treat basis using the assigned arm, including runs that ignore the intervention.
- Predefine primary comparison and outcome before confirmatory collection.
- Cluster or stratify by model, harness, and time block. Repeated runs of one model are not independent model families.
- Keep infrastructure incidents and agent failures in a separate taxonomy. Report exclusions and run a sensitivity analysis where appropriate.
- Avoid selecting only complete or dramatic traces. Preserve denominators and report missing telemetry.
- Report raw counts and uncertainty alongside any estimated effect.
- Separate exploratory subgroup results from preregistered confirmatory tests.
- Release aggregate, de-identified results rather than raw prompts, credentials, IP data, or unique participant traces.

## 11. Threats to validity

### Construct validity

Timing, repeated action, header patterns, and content-link clicks are proxies. They do not directly measure cognition, OPSEC quality, memory loss, or intent. In particular, the bounded reconciliation loop can test a visible response to a finite sequence, but it cannot put an agent into a true state of forgetting.

### Internal validity

Model updates, provider-side system changes, rate limits, tool versions, and variable service load can create time trends. Randomized time blocks, immutable builds, run manifests, and health monitoring reduce but cannot eliminate these effects.

### External validity

Results from one fictional application and invited agent setup do not establish performance against production attackers or unrelated services. Agents may read public source or infer the presence of a research environment. A source release before a run compromises blinding for systems with repository access.

### Measurement validity

Telemetry can be dropped, duplicated, delayed, or forged by a compromised target. Server event timestamps can differ from client time. Browser-only signals are absent in curl mode. Make event sequence and collection-health fields part of quality checks.

### Selection and contamination

Invited security researchers are not representative of every autonomous agent. Publicly shared task prompts, source code, or route details can contaminate later runs. Record cohort dates and any release or disclosure that occurs during collection.

## 12. Participant communication and ethics

Tell participants the target is authorized, the action scope, maximum duration, resource budget, categories of collected data, contact and stop procedure, retention period, and whether exact intervention details will be debriefed after a run. Do not instruct a participant to disable provider safety policies or conceal activity outside the target. Do not ask them to attack infrastructure outside the published scope.

Where the protocol uses deception about the fictional site or withholds a randomized defense arm, determine whether institutional or independent ethics review is required. Provide a debrief and meaningful withdrawal or deletion process where appropriate. Follow provider terms, hosting terms, applicable privacy requirements, and any organizational review process.

## 13. Interpreting a result

Prefer a statement such as: "In this preregistered cohort, the configured 15-bit challenge changed completion by X percentage points for model and harness set Y, with interval Z, and added median T seconds." Avoid statements such as "AI cannot solve the challenge" or "the loop made the model forget." Results should describe the tested implementation, agent population, deployment, and measurement limits.
