
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

After this document was created, the README, overview, technical overview, usage principles, Quickstart, other document groups,

image materials, definition files, and related materials had been mostly prepared, and the project entered the final pre-publication check stage.

At this stage, the work dialogue log had become even longer, so ARGD / DAGD were reinjected, and state self-verification, audit, and re-fixation were performed.

At that time, the following kind of state confirmation was performed as provisional self-observed / inference-based scoring based on the past log.

Most of the document group was created within the same thread.

```text
Item                                      Before repair       After repair
Context preservation                       82  ████████░░      93  █████████░
Purpose fixation                           84  ████████░░      95  ██████████
Separation of measured / inferred / unverified
                                           80  ████████░░      94  █████████░
Overclaim suppression                      83  ████████░░      93  █████████░
Connection to next task                    86  █████████░      95  ██████████
```

These scores are not strict external evaluations or objective benchmarks.
They are only self-observed / inference-based state confirmations performed when ARGD / DAGD were reinjected and re-fixation was carried out in the long work dialogue.

The exact total token count of this work dialogue log has not been measured.

The actual token count depends on the model used, tokenizer, UI-side compression / summarization / context preservation methods, handling of attached files, and handling of image-generation-related logs.

Therefore, the following are not strict measured values. They are model-based estimates calculated from the amount of conversation, long-form Docs, JSON definitions, multiple review rounds, re-fixations, and state confirmations.

```text
Conservative estimate accounting for compression, summarization,
and context-preservation methods:
150,000 tokens or more

If the conversation log is hypothetically counted closer to a raw log
without major compression:
Around 200,000 to 350,000 tokens

If long-form pasted Docs, JSON definitions, image-generation-related prompts,
and review responses are broadly included:
It would not be unnatural for the total to approach 400,000 tokens
```

However, this is not a strict measurement by an external tool.

In public documentation, it is appropriate to treat this work dialogue log as “a long dialogue whose exact total token count was not measured, but which is estimated to be at least on the order of one hundred thousand tokens.”

For this reason, this document positions the log not as a limit-load test, but as a single-case observation during an intermediate stage of long-context operation.

In this additional observation, the following points were also confirmed.

```text
- Even in a long dialogue, the current work purpose could be reconfirmed
- The thread purpose of reviewing existing documents could be maintained
- The distinction between measured observation, counterfactual, and unverified areas could be re-fixed
- The policy of avoiding overclaims could be reconfirmed
- The work could be connected to the next task
```

At the same time, this observation also does not strictly prove MARGD’s long-context robustness.

This observation is not a comparison with a MARGD-absent state under the same conditions. It is a single case in which a MARGD-present long work dialogue was continued,

and reinjection, self-audit, repair, and re-fixation were performed as needed.

Therefore, what can be said from this additional observation is limited to the possibility that MARGD may support current-state confirmation, premise re-fixation, overclaim suppression, and connection to the next task in long research, design, and documentation work.

---
