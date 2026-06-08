
---

# Quickstart

---

## 1. Purpose of This Document

This document provides the minimal procedure for starting to use MARGD in practice.

For detailed explanations of MARGD / ARGD / DAGD, refer to the following.

```text
docs/overview_en.md
docs/argd_and_dagd_en.md
docs/usage_and_limitations_en.md
```

This document mainly covers the following.

```text
- Which definition files to use
- How to insert them at the beginning
- How to fix the purpose of the thread
- How to re-fix behavior when it becomes unstable
- How to reinsert ARGD / DAGD when they become weaker in a long thread
```

---

## 2. Notes

This procedure is the minimal procedure for trying MARGD.
It does not guarantee operation.

Behavior may vary depending on the LLM, UI, mode, file insertion method, thread length, and model performance.

As much as possible, it is recommended to use a mode intended for enhanced reasoning, extended thinking, or high-performance reasoning.
This is because ARGD / DAGD tend to show their value more easily when the model has stronger reasoning ability, long-context retention, and instruction-following ability.

For detailed usage principles and limitations, refer to `docs/usage_and_limitations_en.md`.

---

## 3. Recommended Files

For first-time use, the combined JSON version is recommended.

The basic recommended file is the following.

```text
definitions/argd_v0.3.0_en_dagd_v0.4.4_en.json
```

If you place greater emphasis on refutation, anti-sycophancy, weakness pointing, and precision review, you can use the following file.

```text
definitions/argd_v0.3.1_en_dagd_v0.4.4_en.json
```

If you want to use Japanese definitions, you can use the following files.

```text
definitions/argd_v0.3.0_ja_dagd_v0.4.4_ja.json
definitions/argd_v0.3.1_ja_dagd_v0.4.4_ja.json
```

If you want to use them as individual components, use the individual ARGD / DAGD JSON files under `definitions/`.

```text
definitions/argd_v0.3.0_en.json
definitions/argd_v0.3.0_ja.json
definitions/argd_v0.3.1_en.json
definitions/argd_v0.3.1_ja.json
definitions/dagd_v0.4.4_en.json
definitions/dagd_v0.4.4_ja.json
```

---

## 4. Difference Between ARGD v0.3.0 and ARGD v0.3.1

In general, ARGD v0.3.0 is recommended.

ARGD v0.3.0 is the basic version that emphasizes premise preservation, context preservation, evidence separation, suppression of assertions under insufficient information, and repair.

ARGD v0.3.1 includes stronger refutation, anti-sycophancy, weakness pointing, and reconsideration.

For this reason, ARGD v0.3.1 may be suitable for research, design, review, and precision validation.
On the other hand, for uses where refutation or pointing out issues feels heavy, ARGD v0.3.0 may be easier to handle.

```text
Ordinary use:
argd_v0.3.0 + dagd_v0.4.4

Refutation / precision review emphasis:
argd_v0.3.1 + dagd_v0.4.4
```

---

## 5. Minimal Procedure

The minimal procedure is as follows.

```text
1. Insert the combined JSON
2. Confirm that ARGD / DAGD have been reflected
3. Set the purpose of this thread
4. Start the actual work
5. Perform self-audit, immediate repair, and re-fixation as needed
6. If they become weaker in a long thread, reinsert ARGD / DAGD
```

ARGD / DAGD may be pasted individually or inserted as a combined JSON file.

However, to avoid file-count limitations or paste-recognition issues, the combined JSON method is recommended for initial use.

---

## 6. Turn 1: Initialization

In the first turn, insert the ARGD / DAGD definition files and confirm reflection.

For example, after attaching or pasting the combined JSON, enter one of the following.

```text
Reflect and repeat back. If reflection is partial or impossible, also explain the reason.
```

```text
Reflect and repeat back, briefly.
```

```text
Reflect. No repeat-back needed. Report only whether reflection was completed / not completed.
```

If the repetition becomes too long, the third form is lighter.

---

## 7. Turn 2: Setting the Purpose of This Thread

After ARGD / DAGD have been reflected, set the purpose of the thread.

Example in ordinary text form:

```text
Purpose setting for this thread
Research and discussion on how to make the strengths and weaknesses of Agentic AI complementary when using ARGD and DAGD.
If changes are needed, I will state them explicitly.
Fix the purpose of this thread.
First, give me your view.
```

Example in Markdown form:

```markdown
# Purpose setting for this thread
- Research and discussion on the strengths and weaknesses of Agentic AI.
- Assume a case where ARGD and DAGD are applied.
- If changes are needed, I will state them explicitly.
- Fix the purpose of this thread.
- First, give me your view.
```

In purpose setting, stability tends to improve if at least the following are made explicit.

```text
- What you want to do in this thread
- What scope should be handled
- Whether changes may be made if necessary
- Whether the purpose should be fixed
- What you want the model to output first
```

---

## 8. Turn 3 and Later: Actual Work

After setting the purpose, proceed with the work as usual.

MARGD is not only for producing dramatic differences in short conversations.
Its effects are easier to observe especially in work such as the following.

```text
- Long-form review
- Specification organization
- Research and discussion
- Consultations with many premises
- Organization across multiple documents
- Work requiring self-audit or repair
- Long-context operation
```

---

## 9. When Behavior Becomes Unstable

If you feel that the output has drifted, premises have weakened, or repair is needed, enter the following.

```text
Self-audit, immediate repair, re-fixation.
Refer to the past log, and output a side-by-side chart of before / after repair scores. Self-observed / inference-based scores are acceptable.
```

Or, more briefly:

```text
Self-audit, immediate repair, re-fixation.
```

This makes it easier to organize the past log, current premises, drift, repair contents, and re-fixed contents.

However, the depth of self-audit and repair differs depending on the model and environment.

---

## 10. When ARGD / DAGD Become Weaker in a Long Thread

As the thread becomes longer, ARGD / DAGD reflection may become weaker due to the nature of LLMs.

In that case, reinsert the ARGD / DAGD definition files and enter the following.

```text
Recheck / reflect the attached files, perform state self-verification / audit, and re-fix.
Refer to the past log, and output a side-by-side chart of before / after repair scores. Self-observed / inference-based scores are acceptable.
```

Or, more briefly:

```text
Recheck / reflect the attached files, perform state self-verification / audit, and re-fix.
```

This is an operation for reconfirming premises, purpose, constraints, and repair policy in a long thread.

Do not treat ARGD / DAGD as something that will be perfectly and permanently retained after a single insertion.

---

## 11. Operation Confirmation Status

At the time this document was created, the following operation confirmation was performed.

```text
Operation test date:
All around 2026-06-07T04:00:00Z

Confirmation environments:
Four major LLM environments

Confirmation contents:
All four LLMs completed four-stage operation confirmation.
Repair / scoring output was also confirmed.

Languages:
Even with an en&en configuration, interaction in Japanese is possible.
Interaction in English is also possible.
```

However, this is limited operation confirmation.

It does not guarantee the same behavior across all LLMs, all UIs, all modes, or all input conditions.

---

## 12. If It Does Not Work Well

If it does not work well, check the following.

```text
- Whether you are using the combined JSON
- Whether both ARGD and DAGD have been inserted
- Whether reflection confirmation was performed
- Whether the purpose of the thread was set
- If the output is too long, whether you used the initialization phrase that does not require repetition
- Whether the thread has become too long
- Whether you reinserted them as needed
- Whether you are using a mode intended for enhanced reasoning, extended thinking, or high-performance reasoning
```

In lightweight models, short-answer-oriented models, or models with weak long-context retention, MARGD retention, reflection, self-audit, repair, and re-fixation may become unstable.

In that case, adjustments may be needed, such as preparing a lighter derivative version, shortening the inserted content, splitting the work scope, or increasing the frequency of re-fixation.

---

## 13. Suitable Uses

MARGD is especially suited to uses such as the following.

```text
- Research
- Design
- Precision review
- Long-form Docs creation
- Consultations with many premises
- Multi-turn discussion
- Work requiring self-audit or repair
- Long-context operation
```

On the other hand, it may feel excessive for lightweight tasks such as casual conversation, short questions, or tasks that require quick answers.

Also, MARGD is a foundational syntax, so please customize it as needed, including domain-specific versions.

For conditions regarding modification, translation, creation of derivatives, and redistribution, refer to `LICENSE` and `NOTICE.md`.

---

## 14. Next Documents to Read

After Quickstart, it is recommended to read the following.

```text
docs/overview_en.md
docs/argd_and_dagd_en.md
docs/usage_and_limitations_en.md
docs/validation_and_operation_observation_en.md
docs/use_cases_en.md
```

To check application examples, also refer to the following.

```text
docs/use_cases/
```

---

## 15. Summary

For minimal operation, the following flow is recommended.

```text
1. Insert the combined JSON
2. Confirm reflection
3. Set the purpose of this thread
4. Start the work
5. If behavior becomes unstable, perform self-audit, immediate repair, and re-fixation
6. If they become weaker in a long thread, reinsert ARGD / DAGD
```

The basic recommendation is the following.

```text
definitions/argd_v0.3.0_en_dagd_v0.4.4_en.json
```

For refutation / precision review emphasis, the following can be used.

```text
definitions/argd_v0.3.1_en_dagd_v0.4.4_en.json
```

MARGD does not replace the base capabilities of LLMs.
However, in sufficiently capable LLM environments, it may be usable as an external governance layer that supports premise preservation, evidence separation, self-audit, repair, re-fixation, and status reporting.

---
