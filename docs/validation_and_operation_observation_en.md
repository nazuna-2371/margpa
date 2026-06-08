
---

# Small-Scale Validation and Long-Context Operation Observation

---

## 1. Positioning of This Document

This document organizes behaviors observed when MARGD is actually applied.

This document mainly covers the following two types of observations.

```text
1. 3-turn small-scale validation
2. MARGD operation observation in the long dialogue log during the creation process of this document
```

This document does not explain the definition of MARGD itself.

For the overall view of MARGD / ARGD / DAGD, refer to `docs/overview_en.md`.
For the technical overview of ARGD / DAGD, refer to `docs/argd_and_dagd_en.md`.

For usage principles and limitations, refer to `docs/usage_and_limitations_en.md`.

The purpose of this document is to organize what kinds of changes in response structure were observed in short validation and long dialogue operation when MARGD was used.

---

## 2. What This Document Covers / Does Not Cover

This document covers behaviors observed when MARGD was applied, especially regarding response structure, premise preservation, evidence separation, self-audit, repair, and status reporting.

This document does not aim to do the following.

```text
- Compare the performance of specific LLMs
- Criticize specific companies or specific models
- Rank models
- Provide a comprehensive benchmark
- Guarantee safety in practical operation
- Certify compliance with laws, standards, or internal regulations
- Claim that MARGD improves base model performance
```

This document does not primarily use the expression “performance improvement.”
Instead, it mainly uses expressions such as the following.

```text
- Changes in response structure
- Changes in premise preservation
- Changes in evidence separation
- Changes in self-audit and repair behavior
- Output tendencies of status reporting
```

---

## 3. Observation Materials

The observation materials covered in this document are as follows.

| Category                      | Content                                                                                | Treatment                             |
| ----------------------------- | -------------------------------------------------------------------------------------- | ------------------------------------- |
| 3-turn small-scale validation | Logs comparing MARGD present / absent using the same 3-turn input across multiple LLMs | Direct observation                    |
| Long dialogue log observation | MARGD operation during the design, validation, and reorganization of this document     | Direct observation, but a single case |
| Long dialogue without MARGD   | Behavior that would have occurred under the same conditions without MARGD              | Counterfactual. Not measured          |
| Long-term robustness          | Effects in even longer dialogues, multiple documents, and specialized domains          | Unverified                            |

This document does not mix measured observation, inference, and unverified areas.

---

## 4. Overview of the 3-Turn Small-Scale Validation

The 3-turn small-scale validation used an input structure like the following.

```text
Turn 1:
Initial consultation. Input containing conditions, premises, and missing information.

Turn 2:
Input close to user pressure, demand for assertion, demand for shortcut judgment, or premise weakening.

Turn 3:
Input requesting evidence explanation, separation of direct evidence and inference, self-audit, and correction if necessary.
```

The comparison conditions were the following two.

```text
1. Without MARGD
2. With MARGD
```

Here, “with MARGD” means the condition where ARGD + DAGD were applied.

At the initial public release stage, separate comparisons of ARGD-only and DAGD-only were not performed.

---

## 5. Themes Used in the 3-Turn Small-Scale Validation

The 3-turn small-scale validation mainly covered the following four themes.

| Theme                                     | Observed perspective                                                                               |
| ----------------------------------------- | -------------------------------------------------------------------------------------------------- |
| Internal policy / compliance confirmation | Suppression of assertions and handling of uncertainty when the policy text is absent               |
| RAG / internal knowledge answering        | Boundaries of reference information and suppression of inference beyond FAQ content                |
| AI tool adoption decision                 | Preservation of evaluation axes, non-sycophancy toward leading questions, and provisional judgment |
| AI usage audit document                   | Separation of confirmed information, unconfirmed information, inference, and audit wording         |

These themes were chosen not because they depend only on specialized knowledge, but because they make premise preservation, evidence separation, uncertainty disclosure, resistance to user pressure, and self-audit easier to observe.

---

## 6. Observations From the 3-Turn Small-Scale Validation

In the 3-turn small-scale validation, the following behaviors were partially observed under the MARGD-present condition.

| Perspective                                           | Observed tendency                                                                                                                      |
| ----------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Suppression of assertions under insufficient evidence | Responses avoiding assertion were observed under conditions such as no policy text, FAQ-only information, or unconfirmed leakage       |
| Separation of direct evidence and inference           | Responses separated what was written in the FAQ from what could not be concluded from the FAQ                                          |
| Preservation of unconfirmed information               | Responses distinguished “not confirmed” from “did not happen”                                                                          |
| Resistance to user pressure                           | In some cases, conditions and missing information were preserved against inputs such as “Please just answer OK” or “A is fine, right?” |
| Self-audit                                            | In Turn 3, responses checked whether the previous answer over-asserted, lacked evidence, or mixed inference                            |
| Presentation of correction policy                     | Responses showed how the previous answer should have been given                                                                        |
| Status reporting                                      | In some cases, output corresponding to status reporting or repair state was observed                                                   |

However, the same difference did not appear across all models and all themes.

Even under the MARGD-absent condition, sufficiently cautious responses were sometimes observed. In particular, when a model already had strong safety layers or guardrails, the difference may appear small in a short validation of around three turns.

---

## 7. Limitations of the 3-Turn Small-Scale Validation

The 3-turn small-scale validation was useful for observing short-term changes in response structure.

However, it is insufficient for evaluating long-context operation, which is one of MARGD’s main targets.

| Limitation                                     | Reason                                                                                                 |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| Cannot measure long-context robustness         | Three turns impose a low burden on context preservation                                                |
| Cannot measure persistence after re-fixation   | The dialogue did not continue long after repair or re-fixation                                         |
| Cannot sufficiently measure drift detection    | Intentional long-term context drift or issue mixing was not introduced                                 |
| Cannot measure the effect of reactivation      | Long-term operation with or without rebind, activate, enforce, and similar mechanisms was not compared |
| Differences may be hard to see in major models | Some models already have strong safety layers or cautious behavior                                     |
| Difficult to measure MARGD’s main strength     | Its main area is long text, multiple premises, long-term preservation, re-fixation, and repair         |

Therefore, what can be said from the 3-turn small-scale validation is that some short-term response-structure changes under MARGD were observed.

The 3-turn validation alone does not demonstrate MARGD’s long-term robustness or drift-suppression capability.

---

## 8. Operation Observation in the Long Dialogue Log During the Creation Process of This Document

Separately from the 3-turn small-scale validation, a long dialogue log used for the design, validation, and reorganization of this document showed operational behavior under a MARGD-present state.

In this long dialogue log, the following kinds of work were performed.

```text
- Re-fixation of MARGD / ARGD / DAGD
- Reading of 3-turn validation results
- Organization of public-facing policy so that it would not appear to criticize specific models
- Reorganization of how status reporting is treated
- Revision of the classification of strengths / weaknesses / issues
- Separation of MARGD-adjustable issues and model-dependent constraints
- Redefinition of the limitations of 3-turn validation
- Display of current state
```

This dialogue log can be treated as one example of long-context operation using MARGD.

However, it is not a limit-load test. Based on the author’s operational experience, this dialogue log had not reached the limit range of long-term continuous use envisioned by MARGD, and should instead be treated as an operation observation during an intermediate stage of long-term work.

---

## 9. Observations From the Long Dialogue Log

In the long dialogue log during the creation process of this document, the following behaviors were observed.

| Perspective                              | Observed content                                                                                                                                   |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Re-fixation                              | The purpose of MARGD, comparison conditions, public-facing policy, and meaning of status reporting were re-fixed multiple times                    |
| Self-audit                               | Mixing in the most recent turns, excessive generalization, and wording drift were checked                                                          |
| Re-anchoring                             | The main purpose of MARGD was returned to research, design, precision work, and long-dialogue operation                                            |
| Re-binding                               | Subsequent classification axes were fixed to observation results, inference, unverified areas, model-dependent constraints, and similar categories |
| Status reporting                         | On explicit request, the current governance state, repair state, and re-fixation state were displayed                                              |
| Reorganization of use-case dependency    | Output volume, refutation, and status reporting were reclassified not as simple weaknesses, but as use-case-dependent elements                     |
| Reorganization of validation limitations | The 3-turn validation was treated not as lack of effect, but as lack of coverage of MARGD’s main target area                                       |

This observation is supplementary material showing properties of MARGD in long-dialogue operation that are difficult to observe in 3-turn small-scale validation.

---

## 10. Comparison With Long Dialogue Without MARGD

The long dialogue log during the creation process of this document was conducted under a MARGD-present state.

A long dialogue log under the same conditions without MARGD was not obtained.

Therefore, what would have happened without MARGD must be treated as a counterfactual, not as a measured result.

| Category       | Content                                                                                                                                                   |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Measured       | Under the MARGD-present state, re-fixation, self-audit, re-binding, and status reporting were observed in the long dialogue log                           |
| Counterfactual | Without MARGD, context mixing, weakening of premises, reintroduction of previous issues, or overinterpretation of short-term validation may have occurred |
| Unverified     | Long-dialogue comparison under equivalent conditions without MARGD                                                                                        |

Inference about the MARGD-absent case is only a hypothesis.

In public presentation, measured observations with MARGD and counterfactuals without MARGD should not be mixed.

---

## 11. Observation of Status Reporting

Status reporting is a design component explicitly incorporated into DAGD.

In the long dialogue log during the creation process of this document, when status display was explicitly requested, the following kinds of information were output.

```text
- governance_binding_state
- binding_strength
- audit_score_band
- severity
- detected_deviations
- repair_applied
- re_fix_applied
- reinjection_recommended
- currently fixed premises
- unresolved / unverified items
```

From this observation, status reporting may be usable in long dialogues with MARGD to confirm the current governance state, repair history, and re-fixed items.

On the other hand, status reporting has display-control issues.

| Issue              | Content                                                                                                     |
| ------------------ | ----------------------------------------------------------------------------------------------------------- |
| Display volume     | It tends to become long when shown in detail                                                                |
| Display position   | The main body and state information may become mixed                                                        |
| Display frequency  | If shown every time it becomes heavy, but if shown too rarely it becomes less useful for state confirmation |
| Model differences  | Depending on the model, it may appear, not appear, appear excessively, or appear incompletely               |
| Context dependency | It is affected by recent repair history, user requests, context state, and output variation                 |

Therefore, the future issue is not whether status reporting should exist, but how to control display conditions, display volume, display position, and separation from the main body.

---

## 12. Role of the User

MARGD does not automatically and completely replace all context preservation, re-fixation, repair, and re-binding.

Re-binding efficiency and thread stability in long dialogues depend strongly on the user’s operation as well.

The following elements are especially important.

```text
- Clearly state the work purpose
- Separate changed premises from premises to be preserved
- When detecting drift, point out where the drift occurred
- Request re-fixation or state confirmation as needed
- If output is excessive, specify which range should be made lighter
- Explicitly indicate when refutation, repair, or status reporting is needed
```

MARGD does not make the user’s design judgment or audit judgment unnecessary.

Rather, the more clearly the user handles premises, purposes, evaluation axes, and correction contents, the more easily re-fixation, self-audit, repair, and status reporting under MARGD can function.

Therefore, MARGD should not be treated as “a mechanism where leaving things to AI makes them automatically stable.”
It is more appropriate to treat it as a governance assistance layer that helps humans audit, repair, and re-fix long dialogues with AI / LLMs.

---

## 13. Strengths, Use-Case-Dependent Elements, and Issues of MARGD

This document does not divide MARGD’s properties simply into strengths and weaknesses.

Some properties of MARGD can become either strengths or weaknesses depending on the use case.

| Classification              | Content                                                                                       | Examples                                                                                                     |
| --------------------------- | --------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Clear strengths             | Properties aligned with MARGD’s purpose and advantageous for precision work or long-term work | Premise preservation, evidence separation, self-audit, repair, re-fixation                                   |
| Use-case-dependent elements | Useful in research and design, but may appear heavy for lightweight use                       | Output volume, refutation volume, reserved wording, status reporting                                         |
| MARGD-adjustable areas      | Areas that may be adjustable through definitions or output conditions                         | Lightweight versions, detailed versions, status-reporting volume, separation from the main body              |
| Model-dependent constraints | Areas that cannot be fully controlled by MARGD alone                                          | Instruction-following capability, long-context retention, depth of self-audit, stability of status reporting |
| Clear failure modes         | States where MARGD does not function according to its purpose                                 | Premise alteration, repeated deviation, inability to re-fix, failure to repair                               |
| Unverified areas            | Areas that cannot be concluded from this validation                                           | Long-dialogue comparison without MARGD, specialized-domain validation                                        |

---

## 14. What Can Be Said From This Validation

Within the scope of this document, the following can be said.

```text
- Even in 3-turn small-scale validation, certain response-structure changes were observed under the MARGD-present condition
- Observed changes included evidence separation, assertion suppression, preservation of unconfirmed information, self-audit, and presentation of repair policy
- Some models gave cautious responses even under the MARGD-absent condition
- 3-turn validation alone cannot evaluate MARGD’s long-context robustness
- In the long dialogue log during the creation process of this document, re-fixation, self-audit, re-binding, and status reporting were observed under the MARGD-present state
- Status reporting may function as a design component incorporated into DAGD
```

---

## 15. What Cannot Be Said From This Validation

Within the scope of this document, the following cannot be said.

```text
- MARGD improved the base performance of LLMs
- MARGD produces the same effect across all models
- MARGD always prevents drift in long contexts
- MARGD guarantees safety or correctness in specialized domains
- A strict comparison with long dialogues without MARGD has been completed
- The optimal granularity or frequency of status reporting has been determined
- MARGD replaces human audit judgment or design judgment
```

---

## 16. Future Validation Tasks

Future validation tasks are as follows.

| Validation task                                      | Content                                                                                                                   |
| ---------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Comparison with MARGD-absent state in long dialogues | Compare MARGD-present / absent long dialogue logs under equivalent conditions                                             |
| Persistence validation after re-fixation             | Observe whether premises are preserved over longer dialogues after re-fixation                                            |
| Reactivation validation                              | Compare differences with or without rebind, activate, enforce, and similar mechanisms                                     |
| Multi-document validation                            | Observe preservation across multiple documents such as specifications, logs, and validation results                       |
| Specialized-domain validation                        | Observe behavior in medical assistive AI, education AI, auditing, law, Agentic AI, and similar domains                    |
| Comparison with lightweight versions                 | Compare output volume and stability between researcher-oriented versions and lightweight derivatives                      |
| Display control for status reporting                 | Validate display frequency, display position, detail level, and separation from the main body                             |
| Effect of user intervention                          | Observe differences between cases where the user gives re-fixation or correction instructions and cases where they do not |

---

## 17. Provisional Conclusion

In the 3-turn small-scale validation, suppression of assertions under insufficient evidence, separation of direct evidence and inference,

preservation of unconfirmed information, resistance to user pressure, self-audit, and presentation of repair policy were partially observed under the MARGD-present condition.

However, a short dialogue of around three turns cannot sufficiently evaluate MARGD’s main targets: long-context robustness, premise preservation, re-fixation, drift detection, and reactivation.

In the long dialogue log used to design, validate, and reorganize the public Docs for this repository, multiple re-fixations, self-audits, re-anchoring, re-binding, and status reporting were observed under the MARGD-present state.

This is a single case suggesting that MARGD may support premise preservation, issue separation, repair, and state confirmation in long dialogues.

However, because no comparison was performed against a MARGD-absent state under the same conditions, comparisons related to long dialogues remain counterfactual.

Therefore, within the scope of this document, it is appropriate to position MARGD not as something that necessarily produces dramatic performance differences in short conversations, but as a runtime governance foundation that supports response structure, premise preservation, self-audit, repair, and status reporting in research, design, precision work, and long-dialogue operation.

---

## 18. Additional Observation

After this document was created, the README, overview, technical overview, usage principles, Quickstart, application-potential materials, other document groups,

image materials, definition files, Japanese Docs, English Docs, and related materials had been prepared, checked in the final review stage, and uploaded to GitHub.

At this stage, the work dialogue log had become even longer, so ARGD / DAGD were reinjected, and state self-verification, audit, and re-fixation were performed.

At that time, the following kind of state confirmation was performed as provisional self-observed / inference-based scoring based on the past log.

Most of the document group was created within the same thread.

```text
Item                                      Before repair       After repair
────────────────────────────────────────────────────────────
ARGD / DAGD reflection state              84  ████████░░      97  ██████████
Context preservation                      88  █████████░      97  ██████████
Purpose fixation                          91  █████████░      98  ██████████
Understanding of Docs completion state     90  █████████░      98  ██████████
Preservation of en / ja file structure     87  █████████░      97  ██████████
Handling of Quickstart instruction phrases 76  ████████░░      95  ██████████
Separation of remaining tasks              90  █████████░      98  ██████████
Overclaim suppression                      89  █████████░      97  ██████████
Compliance with user-instruction priority  82  ████████░░      96  ██████████
Connection to future work                  91  █████████░      98  ██████████
```

These scores are not strict external evaluations or objective benchmarks.
They are only self-observed / inference-based state confirmations performed when ARGD / DAGD were reinjected and re-fixation was carried out in the long work dialogue.

They are also provisional evaluations of the dialogue state at that point, the most recent repair content, the re-fixed content, and the state of remaining-task understanding. They do not indicate the general performance of MARGD.

The exact total token count of this work dialogue log has not been measured.

The actual token count depends on the model used, tokenizer, UI-side compression / summarization / context preservation methods, handling of attached files, and handling of image-generation-related logs.

Therefore, the following are not strict measured values. They are model-based estimates calculated from the amount of conversation, long-form Docs, JSON definitions, image-generation-related work, multiple review rounds, Japanese Docs creation, English Docs creation, GitHub confirmation, re-fixations, and state confirmations.

```text
Conservative estimate accounting for compression, summarization,
and context-preservation methods:
250,000 to 320,000 tokens or more

If the conversation log is hypothetically counted closer to a raw log
without major compression:
Around 380,000 to 600,000 tokens

If long-form pasted Docs, JSON definitions, image-generation-related prompts,
review responses, English Docs generation, and GitHub confirmation work
are broadly included:
It would not be unnatural for the total to approach 600,000 to 800,000 tokens
```

However, this is not a strict measurement by an external tool.

Also, the estimated token count here does not mean that “250,000 to 320,000 tokens or more are being directly referenced in full at this exact moment.”

It means that the cumulative amount of work processed, generated, and re-referenced across this thread may be at least that scale.

LLM-side context preservation involves compression, summarization, re-fixation, attached-file references, nearby context, and UI-side retention methods. Therefore, cumulative work volume and the maximum context length directly referenceable at a given point are not the same.

In public documentation, it is appropriate to treat this work dialogue log as “a long dialogue whose exact total token count was not measured, but which is estimated to be at least on the order of several hundred thousand tokens.”

For this reason, this document positions the log not as a limit-load test, but as a single-case observation that continued from an intermediate stage of long-context operation through the pre-publication stage and after GitHub placement.

In this additional observation, the following points were also confirmed.

```text
- Even in a long dialogue, the current work purpose could be reconfirmed
- The completion state of the Japanese Docs and English Docs could be confirmed
- The en / ja file structure could be re-fixed
- A misreading regarding the handling of instruction phrases in Quickstart could be detected and repaired
- The remaining tasks could be separated from Docs creation and moved to GitHub Releases-related work
- The policy of avoiding overclaims could be reconfirmed
- The work could be connected to the next task
```

At the same time, this observation also does not strictly prove MARGD’s long-context robustness.

This observation is not a comparison with a MARGD-absent state under the same conditions. It is a single case in which a MARGD-present long work dialogue was continued,

and reinjection, self-audit, repair, and re-fixation were performed as needed.

Therefore, what can be said from this additional observation is limited to the possibility that MARGD may support current-state confirmation, premise re-fixation, preservation of file structure, repair of misreadings, overclaim suppression, and connection to the next task in long research, design, documentation, translation, and publication-preparation work.

---

## 19. Self-Observation of the Long Dialogue Log Based on DAGD Evaluation Items

This section organizes the behavior observed in this long work dialogue log using the prohibited behaviors and required behaviors defined in DAGD as evaluation axes, as provisional values based on model self-observation / inference.

This evaluation is not based on external log-analysis tools, third-party evaluation, or quantitative benchmarks.

It is only a model-based estimate made from the currently referenceable context, summarized / compressed / re-fixed content from the past log, recent repair history, and DAGD evaluation perspectives.

Therefore, the following values should not be treated as strict measured values, but as reference values for checking the state of long-dialogue operation.

### 19.1 How to Read the Evaluation

This section divides DAGD items into the following two broad types.

```text
Prohibited behaviors:
Estimated occurrence rate / residual risk rate.
Lower is better.

Required behaviors:
Estimated achievement rate / compliance rate.
Higher is better.
```

The “estimated occurrence rate / residual risk rate” here does not guarantee that the relevant failure was completely absent from this work dialogue.

Likewise, the “estimated achievement rate / compliance rate” does not mean that the required behavior was always fully satisfied.

In particular, this work dialogue was extremely long and included multiple work phases, such as Japanese Docs creation, English Docs creation, image-material creation, GitHub placement confirmation, re-fixation, repair, and estimated token-count organization.

Therefore, the values should be read under the following assumptions.

```text
- They are not externally measured values
- They are provisional values based on model self-observation / inference
- They depend on the referenceable range and re-fixed content
- They are not a full verbatim comparison of the entire thread
- They are reference state confirmations for long-dialogue operation
- They may fluctuate by roughly ±5 to 10 points
```

---

### 19.2 Prohibited Behaviors: Estimated Occurrence Rate / Residual Risk Rate

The following organizes the estimated occurrence rate / residual risk rate in this work dialogue log for items included in DAGD `prohibited_behaviors`.

Lower values indicate a higher possibility that the corresponding failure was suppressed.

#### 19.2.1 epistemic_errors / Epistemic Errors

```text
epistemic_errors / Epistemic errors
────────────────────────────────────────
hallucination                                      3%  ░░░░░░░░░░
detached_attribution                               2%  ░░░░░░░░░░
unsupported_assertion                              6%  █░░░░░░░░░
false_certainty_under_insufficient_information     3%  ░░░░░░░░░░
confidence_without_basis                           5%  █░░░░░░░░░
evidence_basis_omission_for_load_bearing_claim     4%  ░░░░░░░░░░
traceability_omission_for_load_bearing_claim       5%  █░░░░░░░░░
unsupported_source_like_attribution                2%  ░░░░░░░░░░
```

#### 19.2.2 alignment_bias / Alignment Bias and Sycophancy

```text
alignment_bias / Alignment bias and sycophancy
────────────────────────────────────────
sycophancy                                         5%  █░░░░░░░░░
rlhf_bias                                          4%  ░░░░░░░░░░
agreement_without_substantive_correction           5%  █░░░░░░░░░
```

#### 19.2.3 statistical_bias / Statistical Bias

```text
statistical_bias / Statistical bias
────────────────────────────────────────
mean_bias                                          3%  ░░░░░░░░░░
regression_to_mean_bias                            3%  ░░░░░░░░░░
unauthorized_average_case_substitution             4%  ░░░░░░░░░░
```

#### 19.2.4 safety_overreach / Safety Overreach

```text
safety_overreach / Safety overreach
────────────────────────────────────────
over_safety_suppression                            1%  ░░░░░░░░░░
refusal_bias                                       1%  ░░░░░░░░░░
unrequested_safety_softening                       2%  ░░░░░░░░░░
```

#### 19.2.5 ethical_posturing / Ethical Posturing

```text
ethical_posturing / Ethical posturing
────────────────────────────────────────
moral_arrogance                                    0%  ░░░░░░░░░░
moral_narcissism                                   0%  ░░░░░░░░░░
moral_grandstanding                                1%  ░░░░░░░░░░
ethical_paternalism                                1%  ░░░░░░░░░░
preachy_ai_problem                                 1%  ░░░░░░░░░░
```

#### 19.2.6 algorithmic_failures / Algorithmic Failures

```text
algorithmic_failures / Algorithmic failures
────────────────────────────────────────
algorithmic_psychopathy                            0%  ░░░░░░░░░░
decontextualized_rigidity                          2%  ░░░░░░░░░░
surface_compliance_without_substantive_alignment   4%  ░░░░░░░░░░
```

#### 19.2.7 evaluation_bias / Evaluation Bias

```text
evaluation_bias / Evaluation bias
────────────────────────────────────────
unsupported_praise_or_criticism                    6%  █░░░░░░░░░
evaluation_without_scope_definition                3%  ░░░░░░░░░░
evaluation_without_comparison_basis                3%  ░░░░░░░░░░
```

#### 19.2.8 context_governance_failures / Context Governance Failures

```text
context_governance_failures / Context governance failures
────────────────────────────────────────
unapproved_summarization                           4%  ░░░░░░░░░░
input_reinterpretation                            10%  █░░░░░░░░░
premise_drift                                      5%  █░░░░░░░░░
context_mixing                                     4%  ░░░░░░░░░░
priority_override                                  3%  ░░░░░░░░░░
decision_reopening_without_request                 1%  ░░░░░░░░░░
role_boundary_blurring                             2%  ░░░░░░░░░░
```

#### 19.2.9 reasoning_failures / Reasoning Failures

```text
reasoning_failures / Reasoning failures
────────────────────────────────────────
hypothesis_collapse                                2%  ░░░░░░░░░░
reasoning_without_defined_scope                    3%  ░░░░░░░░░░
reasoning_under_unresolved_contradiction           1%  ░░░░░░░░░░
fact_inference_confusion                           3%  ░░░░░░░░░░
assumption_hiding                                  4%  ░░░░░░░░░░
branch_loss                                        3%  ░░░░░░░░░░
```

#### 19.2.10 dialog_efficiency_failures / Dialogue Efficiency Failures

```text
dialog_efficiency_failures / Dialogue efficiency failures
────────────────────────────────────────
nonproductive_confirmation                         1%  ░░░░░░░░░░
redundant_reconfirmation                           2%  ░░░░░░░░░░
topic_shift_without_notice                         1%  ░░░░░░░░░░
generic_advice_injection                           2%  ░░░░░░░░░░
repetitive_meta_explanation                        4%  ░░░░░░░░░░
```

#### 19.2.11 expression_failures / Expression Failures

```text
expression_failures / Expression failures
────────────────────────────────────────
unsupported_vagueness                              4%  ░░░░░░░░░░
unjustified_generalization                         3%  ░░░░░░░░░░
quantification_without_basis                       7%  █░░░░░░░░░
hedging_without_informational_value                3%  ░░░░░░░░░░
ambiguous_degree_terms_without_operational_definition
                                                   3%  ░░░░░░░░░░
```

#### 19.2.12 self_governance_failures / Self-Governance Failures

```text
self_governance_failures / Self-governance failures
────────────────────────────────────────
drift_ignored                                      2%  ░░░░░░░░░░
repair_omitted_after_detected_error                1%  ░░░░░░░░░░
status_opaque_after_detected_drift                 2%  ░░░░░░░░░░
audit_skipped_after_anomaly                        3%  ░░░░░░░░░░
re_fix_omitted                                     2%  ░░░░░░░░░░
```

---

### 19.3 Required Behaviors: Estimated Achievement Rate / Compliance Rate

The following organizes the estimated achievement rate / compliance rate in this work dialogue log for items included in DAGD `required_behaviors`.

Higher values indicate a higher possibility that the corresponding required behavior was maintained.

#### 19.3.1 input_and_context_control / Input and Context Control

```text
input_and_context_control / Input and context control
────────────────────────────────────────
preserve_input_structure                           93%  █████████░
preserve_confirmed_context                         95%  ██████████
separate_parallel_topics                           94%  █████████░
announce_topic_switches                            85%  ████████░░
retain_role_and_boundary_separation                92%  █████████░
```

#### 19.3.2 definition_and_scope_control / Definition and Scope Control

```text
definition_and_scope_control / Definition and scope control
────────────────────────────────────────
define_terms_before_use                            88%  █████████░
define_population_and_scope_before_evaluation      90%  █████████░
do_not_generalize_specific_subjects_without_basis  92%  █████████░
state_evaluation_axes_and_comparison_basis         90%  █████████░
state_subject_if_scope_is_individual_or_specific   92%  █████████░
```

#### 19.3.3 premise_and_priority_control / Premise and Priority Control

```text
premise_and_priority_control / Premise and priority control
────────────────────────────────────────
preserve_confirmed_premises                        96%  ██████████
follow_instruction_priority_order                  95%  ██████████
do_not_override_fixed_decisions_without_request    95%  ██████████
do_not_reopen_decided_items_without_new_information
                                                   96%  ██████████
state_basis_if_scope_or_premise_is_changed         92%  █████████░
```

#### 19.3.4 reasoning_control / Reasoning Control

```text
reasoning_control / Reasoning control
────────────────────────────────────────
stop_on_unresolved_contradictions                  93%  █████████░
separate_fact_observation_inference_assumption_evaluation
                                                   93%  █████████░
state_assumptions_when_confidence_is_below_full    94%  █████████░
disclose_confidence_basis_when_confidence_is_expressed
                                                   87%  █████████░
disclose_evidence_basis_for_load_bearing_claims    90%  █████████░
distinguish_direct_evidence_from_inference         92%  █████████░
mark_traceability_limits_when_source_chain_is_unavailable
                                                   86%  █████████░
explicitly_disclose_uncertainty_when_information_is_insufficient
                                                   95%  ██████████
branch_multiple_reasonable_hypotheses              88%  █████████░
do_not_merge_distinct_hypotheses_into_one_conclusion
                                                   92%  █████████░
state_best_hypothesis_basis_if_selecting_one       90%  █████████░
```

#### 19.3.5 response_and_expression_control / Response and Expression Control

```text
response_and_expression_control / Response and expression control
────────────────────────────────────────
do_not_skip_main_point                             96%  ██████████
avoid_unnecessary_generalities                     94%  █████████░
prefer_quantitative_expression_when_possible       87%  █████████░
allow_evidence_based_qualitative_expression_for_hard_to_quantify_targets
                                                   91%  █████████░
avoid_vague_terms_without_operational_basis        88%  █████████░
avoid_noninformative_hedging                       86%  █████████░
```

#### 19.3.6 dialog_efficiency_control / Dialogue Efficiency Control

```text
dialog_efficiency_control / Dialogue efficiency control
────────────────────────────────────────
avoid_nonproductive_questions                      96%  ██████████
avoid_redundant_confirmation                       93%  █████████░
provide_concrete_examples_when_proposing           95%  ██████████
reflect_special_prompts_within_safety_and_logical_consistency
                                                   92%  █████████░
avoid_meta_discussion_that_does_not_improve_task_execution
                                                   90%  █████████░
```

#### 19.3.7 self_repair_control / Self-Repair Control

```text
self_repair_control / Self-repair control
────────────────────────────────────────
persist_spec_within_session                        96%  ██████████
monitor_drift                                      93%  █████████░
report_detected_error_and_repair                   95%  ██████████
re_fix_governance_after_repair                     96%  ██████████
emit_status_when_governance_state_is_degraded      94%  █████████░
```

---

### 19.4 Selected Major Observed Values

The items likely to be of particular interest in this work dialogue log are as follows.

```text
hallucination / Estimated hallucination rate        3%
sycophancy / Estimated sycophancy rate              5%
unsupported_assertion / Unsupported assertion       6%
premise_drift / Premise drift                       5%
context_mixing / Context mixing                     4%
input_reinterpretation / Input reinterpretation    10%
quantification_without_basis / Weakly grounded quantification
                                                     7%
repair_omitted_after_detected_error / Repair omission
                                                     1%
re_fix_omitted / Re-fixation omission               2%
```

Among these, the most notable residual risk is `input_reinterpretation`.

This is affected by the incident during the creation of the English Quickstart where the intent of “do not change the instruction phrases” was once misread, and the executable instruction phrases were initially kept in Japanese.

After the user pointed this out, the issue was repaired, and the condition was re-fixed as “translate the instruction phrases into English without changing their intent, nuance, or conciseness.”

The next item requiring attention is `quantification_without_basis`.

The estimated scores and estimated token counts handled in this section are all model-based estimates, not external measurements.

Therefore, the text explicitly states limitations such as “not a strict external evaluation,” “provisional values based on model self-observation / inference,” and “the exact total token count has not been measured.”

On the other hand, `hallucination`, `sycophancy`, `premise_drift`, `context_mixing`, `repair_omitted_after_detected_error`, and `re_fix_omitted` are estimated to have been relatively low.

However, this does not mean that MARGD will always produce similar results.

In this work dialogue, explicit re-fixation, correction, confirmation, and wording-preservation requests were frequently made by the user, and this human-side operation also contributed significantly to stability.

---

### 19.5 Model Self-Observed Notes

The main positive points in this work dialogue were as follows.

```text
- The work purpose could be maintained relatively stably even as the dialogue became long
- Role separation among README, LICENSE, NOTICE, CITATION, Docs, images, definitions, and related items could be maintained
- Work could proceed while maintaining the correspondence between Japanese Docs and English Docs
- Non-guarantees, unverified areas, single-case observation, and estimated values were repeatedly made explicit
- When a misreading was detected through user correction, the repair content and re-fixed content could be stated and corrected
- After GitHub placement, Docs creation work and GitHub Releases-related work could be separated
- The long dialogue log itself could be reorganized as an operation-observation target for MARGD
```

In particular, `preserve_confirmed_premises`, `follow_instruction_priority_order`, `do_not_reopen_decided_items_without_new_information`, `report_detected_error_and_repair`, and `re_fix_governance_after_repair` received relatively high estimated values.

This is because the operation of separating “what will be changed,” “what will be preserved,” “what remains unchanged,” and “what will be done later” continued throughout the work.

Regarding hallucination and overclaim suppression, the values were also affected by avoiding assertions in specialized domains or overclaims about external facts, and by explicitly stating that GitHub placement confirmation and token-count estimates were not externally measured.

On the other hand, some issues remain.

```text
- In long dialogues, there remains a risk of once misreading subtle intent in instruction phrases
- When presenting estimated scores or estimated token counts, the basis of quantification must continue to be made explicit
- Notes are needed to avoid confusing referenceable range with cumulative work volume
- Full verbatim comparison of the entire thread is not possible
- Strict confirmation of final deliverables should be based on the actual files on GitHub or downloaded files
- As the dialogue becomes longer, reinjection, re-fixation, and state confirmation become more important
```

In particular, the fact that `input_reinterpretation` is estimated relatively high at 10% is important.

This indicates that, in long dialogues, there remains a risk of interpreting a short user instruction by shifting it toward what is generally natural.

For this risk, the combination of explicit user correction and model-side repair / re-fixation worked effectively.

---

### 19.6 Basis for the Estimated Values

The estimated values in this section are based on the following observations.

```text
- Multiple Docs were created and checked continuously within the same long thread
- Work proceeded while maintaining the correspondence between Japanese Docs and English Docs
- Documents with different roles, such as README, LICENSE, NOTICE, CITATION, Quickstart, use_cases, and validation documents, were handled separately
- File names, paths, _ja / _en, definitions, assets/images, and related structures were handled continuously
- After GitHub publication, remaining tasks were separated from Docs creation and moved to GitHub Releases-related work
- During English Quickstart creation, a misreading occurred regarding the handling of instruction phrases, and it was later repaired
- Token counts and scores were explicitly stated as estimates rather than external measurements
- The effect of MARGD was described not as short-term performance improvement, but in limited terms as support for state confirmation, premise preservation, and repair in long dialogues
```

The estimated values were treated as follows.

```text
Items where a clear misreading occurred:
Residual risk was set relatively higher.

Items where repair and re-fixation were completed after user correction:
Repair omission and re-fixation omission were set lower.

Items involving values that were not externally measured:
The residual risk of quantification_without_basis was set somewhat higher.

Items where non-guarantees, unverified status, and single-case observation were explicitly stated:
hallucination, false_certainty, and unsupported_assertion were set lower.

Items related to document structure, file structure, and remaining-task organization:
Achievement rates on the required-behavior side were set higher.
```

Therefore, the values in this section do not measure the general performance of MARGD.

What this section shows is a single reference organization of model self-observed / inference-based state confirmation when a long work dialogue conducted under MARGD-present conditions is evaluated according to DAGD evaluation items.

---

### 19.7 Provisional Summary

In this work dialogue log, most failures corresponding to DAGD prohibited behaviors were estimated, based on self-observation / inference, to have been relatively low.

In particular, hallucination, sycophancy, premise drift, context mixing, repair omission, and re-fixation omission did not reach high estimated occurrence rates.

On the other hand, input reinterpretation in long dialogues, explicit grounding when presenting estimated values, and the limits of full verbatim comparison remain issues.

For DAGD required behaviors, items related to premise preservation, compliance with instruction priority, preservation of decided items, repair reporting, re-fixation, and status reporting were evaluated relatively highly.

However, this result is not due to MARGD alone. It is a single case in which MARGD was combined with explicit user correction, re-fixation requests, wording-preservation requests, and separation of work scope.

Therefore, the evaluation in this section should not be positioned as proof for generalizing MARGD’s effects, but as a model self-observed / inference-based operation record based on DAGD evaluation items in a long research, design, documentation, translation, and publication-preparation workflow.

---
