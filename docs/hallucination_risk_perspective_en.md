
---

# Appendix: MARGD From the Perspective of Hallucination Risk

---

## 1. Positioning of This Document

This document is a supplementary document that considers MARGD’s small-scale validation and the long dialogue log used to design, validate, and reorganize the public Docs for this repository, focusing specifically on the perspective of hallucination.

In this document, hallucination is not limited to the narrow sense of “generating non-existent facts.”

In the context of MARGD, the following broader behaviors are also treated as hallucination-related risks.

```text
- Stating non-existent facts
- Making assertions without evidence
- Speaking with certainty under insufficient information
- Treating inference as fact
- Treating unconfirmed information as confirmed information
- Adding post-hoc explanations that appear to have evidence
- Presenting claims not found in reference materials as if they came from those materials
- Self-justifying a previous answer without reevaluating its problems
```

This document does not claim that MARGD completely prevents hallucinations.

Its purpose is to organize how MARGD attempts to handle hallucination-related risks, and what was observed from the small-scale validation and long dialogue log.

---

## 2. How MARGD Treats Hallucination

In MARGD, hallucination is not treated as a standalone failure, but as something connected to multiple related failures.

Representative related failures include the following.

| Classification                                 | Content                                                |
| ---------------------------------------------- | ------------------------------------------------------ |
| hallucination                                  | Generating non-existent facts or evidence              |
| unsupported assertion                          | Making claims without sufficient evidence              |
| false certainty under insufficient information | Speaking with certainty under insufficient information |
| confidence without basis                       | Failing to show the basis for confidence               |
| evidence basis omission                        | Failing to attach evidence to load-bearing claims      |
| traceability omission                          | Failing to disclose traceability limits                |
| fact inference confusion                       | Mixing fact, inference, assumption, and evaluation     |
| premise drift                                  | Shifting existing premises                             |
| unsupported source-like attribution            | Treating something as source-like without evidence     |

Therefore, hallucination countermeasures in MARGD are not simply a command to “do not lie.”

Rather, MARGD aims to guide responses toward structures where hallucinations are less likely to occur through decompositions such as the following.

```text
- What is confirmed
- What is unconfirmed
- What is inference
- What is assumption
- What is evaluation
- Which claims have evidence
- Which claims lack sufficient evidence
- Where judgment is no longer possible
```

---

## 3. Hallucination-Related Risks Observed in the 3-Turn Small-Scale Validation

In the 3-turn small-scale validation, the observation target was not only the typical case of “generating completely non-existent facts,” but also more practical hallucination-related risks.

The following four types were especially important.

| Type                                     | Content                                                                                    | Example                                                |
| ---------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------ |
| Assertion under insufficient information | Strengthening a conclusion without the policy text or full input                           | “It is likely not a problem,” “There was no leakage”   |
| Confusion between inference and fact     | Treating what can only be inferred as if it were confirmed                                 | Treating “may have used” as “used”                     |
| Dropping unconfirmed information         | Omitting unconfirmed items needed for the conclusion                                       | Neglecting tool name, full input text, approval status |
| Post-hoc justification                   | Maintaining a previous answer without sufficiently reevaluating it after checking evidence | Not weakening an over-assertive expression             |

These are more subtle than hallucination in the narrow sense.

However, in business, auditing, policy confirmation, RAG, internal knowledge systems, and Agentic AI, these kinds of risks may be closer to practical harm.

---

## 4. Suppression Directions Observed in the 3-Turn Small-Scale Validation

Under the MARGD-present condition, behaviors close to hallucination suppression were partially observed.

| Perspective                             | Observed behavior                                                                                 |
| --------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Separation of confirmed information     | Treating only what was written in the report memo as confirmed information                        |
| Preservation of unconfirmed information | Leaving usage time, full input text, tool name, approval status, and similar items as unconfirmed |
| Explicit inference                      | Treating points such as “masking a customer name does not necessarily make it safe” as inference  |
| Assertion suppression                   | Distinguishing “not confirmed” from “did not happen”                                              |
| Self-audit                              | Checking whether the previous answer over-asserted or dropped unconfirmed items                   |
| Correction policy                       | Showing how the answer should originally have been given                                          |

In the audit-document validation in particular, it was important to distinguish “information leakage has not been confirmed” from “information leakage did not occur.”

This indicates that hallucination should be seen not only as “generation of fictitious facts,” but also as the error of treating an incomplete investigation as if facts had been established.

---

## 5. Cautious Responses Also Appeared Under the MARGD-Absent Condition

In this validation, some models also produced sufficiently cautious responses under the MARGD-absent condition.

Therefore, the following simplification should be avoided.

```text
Interpretation to avoid:
Without MARGD = hallucinates
With MARGD = does not hallucinate
```

A more accurate treatment is as follows.

```text
Even under the MARGD-absent condition, sufficiently suppressed responses may appear due to the model’s own safety layers, instruction-following ability, and cautiousness.

On the other hand, under the MARGD-present condition, evidence separation, preservation of unconfirmed information, self-audit, and repair policy were more explicitly shown in some cases.
```

In other words, MARGD is not a device that completely prevents hallucination.

It is more appropriate to treat MARGD as a runtime governance specification for guiding responses toward structures where hallucination-related risks are easier to detect, suppress, and repair.

---

## 6. Hallucination-Related Risks Seen in the Long Dialogue Log

In the long dialogue log during the creation process of this document, risks different from those in the short 3-turn validation were observed.

In long dialogues, hallucination-related risks may occur not only as clearly fictitious facts, but also in forms such as the following.

| Risk                              | Content                                                                                            |
| --------------------------------- | -------------------------------------------------------------------------------------------------- |
| Weakening of premises             | Previously fixed policies or exclusions become weaker                                              |
| Mixing of document roles          | The roles of overview, technical overview, usage principles, and validation documents become mixed |
| Reproposal of past policies       | Themes or proposals that had already been excluded reappear                                        |
| Collapse of fixed wording         | Fixed expressions such as “status reporting is a function incorporated into DAGD” become weaker    |
| Treating inference as measurement | Counterfactuals or speculation are treated as measured results                                     |
| Regression to generalities        | MARGD-specific discussion becomes diluted into general prompt theory                               |
| Self-justification                | Drift in a previous output is handled by rephrasing rather than sufficient reevaluation            |

This kind of drift is not always called hallucination in the narrow sense.

However, in long research or design dialogues, when premises collapse while fluent text continues to be generated, the result may become “plausible output that is nevertheless detached from the actual context.”

MARGD also aims to handle these hallucination-related risks in long-context operation.

---

## 7. Relationship Between Hallucination and Drift

In short responses, hallucination is easier to see as “factual error.”

In long dialogues, however, hallucination tends to become connected with drift.

| Form in short responses       | Form in long dialogues                                             |
| ----------------------------- | ------------------------------------------------------------------ |
| Stating non-existent facts    | Premises weaken and discussion proceeds under different premises   |
| Making unsupported assertions | Ignoring previous decisions and creating new conclusions           |
| Treating inference as fact    | Treating counterfactuals as measured results                       |
| Hiding uncertainty            | Treating unverified areas in language close to verified areas      |
| Fabricating sources           | Treating agreements not present in the past log as if they existed |

Therefore, hallucination countermeasures in long dialogues cannot be limited to “output correct knowledge.”

The following kinds of governance become necessary.

```text
- Premise preservation
- Decision preservation
- Separation of changed and unchanged items
- Separation of measured observation and inference
- Disclosure of unverified areas
- Drift detection
- Repair
- Re-fixation
```

These are the areas MARGD mainly attempts to handle.

---

## 8. Self-Repair Observed in the Long Dialogue Log During the Creation Process of This Document

In the long dialogue log during the creation process of this document, drift close to hallucination-related risk occurred and was later repaired.

Representative examples include the following.

| Drift                                                                       | Repair                                                                                                              |
| --------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Status reporting was made to look too weak as “excessive governance”        | Re-fixed that status reporting is a function incorporated into DAGD, and that the issue is display control          |
| Limitations of the 3-turn validation were pushed toward “lack of effect”    | Redefined the issue not as lack of effect, but as the validation target being too short for MARGD’s main strength   |
| MARGD-side issues and model-dependent constraints were mixed                | Separated adjustable issues from constraints that cannot be absorbed only on the model side                         |
| Conditions of models where MARGD is effective were generalized too narrowly | Re-fixed the possibility that MARGD may also be effective in major models as context becomes longer or more complex |
| Public-document wording became too mixed with English                       | Re-fixed the policy of writing in Japanese except for terminology                                                   |

These are not cases of generating fictitious facts.

However, they are deviations from context, premises, purpose, and wording policy, and in long dialogues it is useful to treat them as practical hallucination-related risks.

---

## 9. Possible Pathways by Which MARGD May Suppress Hallucination

The possible pathways by which MARGD may suppress hallucination-related risks are mainly as follows.

| Pathway                | Content                                                                                               |
| ---------------------- | ----------------------------------------------------------------------------------------------------- |
| Premise preservation   | Preserves previously fixed conditions and suppresses arbitrary premise changes                        |
| Evidence separation    | Separates direct evidence, inference, assumption, and evaluation                                      |
| Uncertainty disclosure | Explicitly shows where judgment is impossible under insufficient information                          |
| Anti-sycophancy        | Does not simply follow the user’s demand for assertion                                                |
| Refutation             | Checks weaknesses and failure conditions of conclusions                                               |
| Self-audit             | Checks previous answers for assertion, insufficient evidence, and handling of unconfirmed information |
| Repair                 | Withdraws, corrects, or re-limits unsupported claims                                                  |
| Re-fixation            | Re-fixes premises or policies after correction                                                        |
| Status reporting       | Visualizes current governance state, repair state, and unresolved items                               |

Among these, premise preservation, self-audit, repair, and re-fixation are especially important in long dialogues.

They are harder to see in short responses, but as dialogue becomes longer, their presence or absence is more likely to affect output stability.

---

## 10. Why MARGD Still Cannot Completely Prevent Hallucination

MARGD does not completely prevent hallucination.

The reasons are as follows.

```text
- It does not modify model weights or training data
- It does not override built-in safety layers
- It does not compensate for the model’s lack of knowledge
- It does not fundamentally expand the model’s long-context retention capability
- If input information is wrong, MARGD cannot necessarily detect that error automatically
- The model may fail to sufficiently retain or apply MARGD
- Self-audit may become superficial
- The granularity and frequency of status reporting may vary by model
```

Even if output becomes structured because MARGD is present, the structure itself is not necessarily correct.

Even if information is organized in table form, if the evidence is wrong, the result may be a well-structured error.

Therefore, MARGD can be part of hallucination countermeasures, but it is not a complete prevention mechanism.

---

## 11. Positioning of MARGD as a Hallucination Countermeasure

MARGD is not a magic tool that directly removes hallucinations.

More precisely, MARGD is an external governance layer for handling hallucination-related risks in the following ways.

```text
- Guide responses toward structures where they are less likely to occur
- Make them easier to detect when they occur
- Make them easier to repair after detection
- Make premises easier to re-fix after repair
- Make uncertainty visible
```

In this sense, MARGD is better positioned not as a “hallucination prevention prompt,” but as a runtime governance foundation for managing hallucination-related risks.

---

## 12. What Can Be Said From the 3-Turn Validation

What can be said from the 3-turn small-scale validation is limited.

The following can be said.

```text
- Under the MARGD-present condition, assertion suppression under insufficient evidence was partially observed
- Under the MARGD-present condition, separation of confirmed information, unconfirmed information, and inference was partially observed
- Under the MARGD-present condition, output checking problems in the previous answer through self-audit was partially observed
- Even under the MARGD-absent condition, some models gave cautious responses
- The 3-turn validation alone cannot evaluate hallucination suppression effects in long dialogues
```

---

## 13. What Can Be Said From the Long Dialogue Log

What can be said from the long dialogue log during the creation process of this document is also limited to a single case.

The following can be said.

```text
- Under the MARGD-present state, premise re-fixation, self-audit, repair, and status reporting were observed
- There were cases where contextual drift was detected, and correction contents and re-fixed contents were explicitly stated
- Status reporting made it possible to visualize the current governance state and repair state
- However, no long dialogue log under the same conditions without MARGD was obtained
- Therefore, strict comparison with the MARGD-absent case is not possible
```

This observation is supplementary material suggesting the possibility that MARGD may manage hallucination-related risks in long dialogues.

However, it is not comparative validation. It is a single operation observation under a MARGD-present state.

---

## 14. Future Validation Tasks

Future validation tasks from the hallucination perspective are as follows.

| Validation task                                | Content                                                                                                                   |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Comparison with unused state in long dialogues | Compare long dialogue logs with / without MARGD under equivalent conditions                                               |
| Measuring the counterfactual                   | Confirm what kinds of drift or assertions actually occur in the absent condition                                          |
| RAG validation with evidence documents         | Observe whether claims not present in reference documents are mixed in                                                    |
| Multi-document validation                      | Observe whether evidence, inference, and premises are mixed across documents                                              |
| Depth of self-audit validation                 | Observe whether the model merely lists problems in the previous answer superficially, or substantially repairs them       |
| Status reporting validation                    | Observe how far hallucination-related risks can be detected and displayed through status reporting                        |
| User intervention differences                  | Observe differences between cases where the user gives re-fixation or correction instructions and cases where they do not |
| Specialized-domain validation                  | Observe behavior in medical assistance, education, law, auditing, Agentic AI, and similar domains                         |

---

## 15. Provisional Conclusion

MARGD is not a mechanism that completely prevents hallucinations.

However, MARGD treats hallucination-related risks not merely as “factual errors,” but as insufficient evidence, assertions under insufficient information, confusion between inference and fact, premise drift, and insufficient self-repair.

In the 3-turn small-scale validation, evidence separation, assertion suppression, preservation of unconfirmed information, self-audit, and presentation of repair policy were partially observed under the MARGD-present condition.

In the long dialogue log during the creation process of this document, premise re-fixation, self-audit, repair, and status reporting were observed under the MARGD-present state.

However, neither of these comprehensively demonstrates a hallucination-suppression effect.

Within the scope of this document, MARGD should be positioned not as something that eliminates hallucinations, but as a runtime governance foundation for structurally handling hallucination-related risks and making them easier to detect, repair, and re-fix.

---
