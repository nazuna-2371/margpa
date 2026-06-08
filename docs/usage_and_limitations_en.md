
---

# Usage Principles and Limitations

---

## 1. Positioning of This Document

This document organizes the basic principles, suitable uses, unsuitable uses, operational notes, and limitations when using MARGD, ARGD, and DAGD.

For the overall view of MARGD, refer to `docs/overview_en.md`.
For the technical overview of ARGD / DAGD, refer to `docs/argd_and_dagd_en.md`.

This document does not provide a detailed explanation of the syntax itself.
Instead, it focuses on the principles to follow when using it in practice, and on limitations that are easily misunderstood.

---

## 2. Basic Policy

MARGD is a runtime governance specification supplied externally at AI / LLM runtime.

Its purpose is not to make AI / LLMs omnipotent.
Its purpose is to make premise preservation, context management, evidence separation, uncertainty disclosure, self-audit, repair, and re-fixation easier to perform in specific work contexts.

MARGD is a foundation specification intended for uses such as the following.

```text
- Research
- Design
- Specification organization
- Long-context preservation
- Complex premise management
- Evidence management
- Auditable output
- Repairable dialogue
- High-precision AI / LLM operation
```

On the other hand, it may be excessive for uses where low constraint density is preferable, such as casual conversation, light questions, short creative writing, or free ideation.

---

## 3. Things to Decide Before Use

Before using MARGD, it is desirable to clarify at least the following points.

```text
1. The purpose of this thread or task
2. Target scope
3. Scope of documents, logs, or data to be handled
4. Premises to preserve
5. Scope that may be changed
6. Scope that must not be changed
7. Evaluation axes
8. Handling of uncertain information
9. Conditions requiring human confirmation
10. Output format
```

MARGD tends to function better when the input is clear.

Conversely, if the purpose, premises, and evaluation axes remain vague, confirmations, branches, and uncertainty disclosures may increase, making the output heavier.

---

## 4. Recommended Use

The basic usage order is as follows.

```text
1. Insert ARGD
2. Insert DAGD
3. Clearly state the purpose, target scope, premises, and output policy of this thread
4. Add domain-specific conditions as needed
5. If the dialogue drifts during a long conversation, perform re-fixation, re-binding, and repair
```

ARGD supports reasoning procedures, premise preservation, context priority, refutation, branching, and repair.

DAGD supports goals, prohibited behaviors, required behaviors, evaluation, repair, activation, and status reporting.

By using both together, reasoning procedures and governance specifications can be separated while complementing each other.

---

## 5. When to Use ARGD

ARGD is mainly used when the goal is to stabilize reasoning procedures.

It is especially suitable for tasks such as the following.

```text
- Interpreting complex input
- Organizing multiple issues
- Premise preservation
- Fixing context priority
- Handling contradictions or insufficient information
- Checking refutations and alternative hypotheses
- Separating fact, inference, assumption, and evaluation
- Structuring long-form answers
- Repair after error detection
```

ARGD is not syntax for making something “answer briefly.”

Rather, because it prioritizes not losing input structure or premises, its output may become longer when necessary.

---

## 6. When to Use DAGD

DAGD is mainly used when the goal is to define behavior policy, prohibited behaviors, evaluation, repair, and status reporting.

It is especially suitable for tasks such as the following.

```text
- Tasks where goals or policies should be fixed
- Tasks where prohibited behaviors should be made explicit
- Tasks where assertions under insufficient evidence should be avoided
- Tasks requiring auditable output
- Tasks requiring self-audit or repair
- Tasks where status reporting should be used
- Tasks where authority boundaries or execution conditions for Agentic AI should be managed
```

DAGD does not guarantee the safety or correctness of AI / LLMs.

However, it can be used to externally specify what to aim for, what to avoid, what to confirm, and how to repair.

---

## 7. Suitable Uses

MARGD is suitable for uses such as the following.

```text
- Research discussion
- Specification design
- Design review
- Code review
- Long-document organization
- RAG / internal knowledge answering
- Assistance for confirming internal policies or business rules
- Initial organization of audit documents
- Legal and compliance assistance
- Information organization in medical assistive AI
- Learning support in education AI
- Purpose, authority, and state management in Agentic AI
```

In these uses, it is necessary not only to generate natural answers, but also to handle premises, evidence, uncertainty, unconfirmed items, and repair history.

For that reason, the governance density of MARGD may be effective.

---

## 8. Unsuitable Uses

MARGD tends to be excessive for uses such as the following.

```text
- Casual conversation
- Light questions
- Consultations that only require short answers
- Rough exchange of impressions
- Free ideation
- Creative writing where constraints should be loosened
- Tasks where speed is the highest priority
- Conversations where the user’s purpose or premises remain vague
```

For such uses, MARGD may increase behaviors such as the following.

```text
- More reservations
- More confirmations
- More refutations
- Longer outputs
- Status reporting appearing heavy
- Weaker free completion
```

This is not necessarily a design mistake.

It occurs because MARGD prioritizes premise preservation, evidence management, auditing, and repair over free completion.

---

## 9. Properties That Reverse Depending on Use Case

Some properties of MARGD can become either strengths or weaknesses depending on the use case.

| Property                | In precision work                                     | In lightweight use                            |
| ----------------------- | ----------------------------------------------------- | --------------------------------------------- |
| Output volume increases | Easier to preserve premises, evidence, and branches   | May feel verbose                              |
| Refutations increase    | Easier to suppress sycophancy and shortcut judgments  | May make the conversation feel heavy          |
| Reservations increase   | Easier to handle uncertainty                          | May feel less assertive                       |
| Status reports appear   | Easier to confirm the current state in long dialogues | May seem unnecessary in ordinary conversation |
| Repairs are explicit    | Easier to track the impact range of errors            | May feel excessive in simple conversation     |

Therefore, MARGD should not be evaluated as “always good” or “always heavy.”
It should be evaluated according to use case, risk, required precision, and context length.

---

## 10. Need for Domain Specialization

ARGD / DAGD are not finished products already optimized for specific domains.

When used in practice, additional design is required according to the target domain.

Examples of elements to add include the following.

```text
- Business requirements
- Target users
- Risk classification
- Evaluation axes
- Prohibited items
- Human confirmation conditions
- Expert review conditions
- Evidence-disclosure requirements
- Record-retention requirements
- Authority management
- Audit logs
- External safety mechanisms
- Compliance checks against laws, policies, and safety standards
```

Medical assistive AI, education AI, Agentic AI, legal assistance AI, RAG, and code review support require different derived conditions.

Therefore, MARGD should be treated not as a finished product to be introduced directly into production, but as a foundation specification for deriving domain-specific versions.

---

## 11. Model Requirements

MARGD assumes use with sufficiently capable AI / LLMs.

The following capabilities are especially important.

```text
- Long-context retention
- Long-instruction following
- Compression and re-expansion ability
- Reasoning capability
- Output structuring capability
- Response-generation capability close to self-audit
- Ability to follow repair instructions
```

For lightweight models, fast-response-oriented models, short-answer-oriented models, or models with weak long-context retention, MARGD retention, application, re-fixation, auditing, and repair may become unstable.

Therefore, the effect of MARGD depends on model capability, context length, input clarity, implementation environment, and task content.

---

## 12. Handling of Status Reporting

Status reporting is an explicitly incorporated function in DAGD.

It is not an accidental side effect that happens to appear when MARGD is applied, but a component connected to self-audit, repair, re-fixation, and re-binding.

Status reporting is useful in situations such as the following.

```text
- When confirming current premises in a long dialogue
- When an error or drift has occurred
- When confirming what was re-fixed after repair
- When preserving an auditable work log
- When confirming the execution state of Agentic AI
```

On the other hand, status reporting has display-control challenges.

```text
- Display volume increases
- Main text and state information may become mixed
- Granularity varies by model
- It can become redundant for lightweight tasks
- Trigger conditions need adjustment
```

Therefore, the future issue is not whether status reporting should exist, but how to control display conditions, display volume, display position, and separation from the main body.

---

## 13. Areas Requiring Human Confirmation

MARGD does not replace human professional judgment.

In particular, the following areas require human confirmation, expert review, and combination with external safety mechanisms.

```text
- Medicine
- Law
- Finance
- Educational evaluation
- Security
- Auditing
- Hiring
- Human resources
- Contracts
- External tool operations
- Work involving personal or confidential information
- Operations that are difficult to reverse
```

MARGD may be used in these areas to separate how far AI / LLMs should support the task and from where human confirmation is required.

However, MARGD itself does not guarantee professional judgment or safety.

---

## 14. Relationship With External Safety Mechanisms

MARGD does not replace external safety mechanisms.

Especially in Agentic AI and high-risk domains, it must be used together with mechanisms such as the following.

```text
- Authority management
- Human review
- Audit logs
- Access control
- Input validation
- Output validation
- Sandboxes
- Rollback mechanisms
- Tamper-resistant log storage
- Signed logs
- Compliance checks against laws, policies, and safety standards
```

MARGD is not a substitute for these mechanisms.

What MARGD handles is governance at the AI / LLM runtime instruction layer.
It does not implement safety design, authority management, or log guarantees on the external system side.

---

## 15. Non-Guarantees

MARGD, ARGD, and DAGD do not guarantee the following.

```text
- Correctness
- Safety
- Legal compliance
- Standards compliance
- Validity of professional judgment
- Production readiness
- Equivalent effects across all models
- Effectiveness for all tasks
- Complete premise preservation
- Complete context preservation
- Complete drift prevention
- Complete self-audit
- Complete self-repair
```

They also do not do the following.

```text
- Modify model weights
- Modify training data
- Override built-in system policies
- Bypass safety layers
- Jailbreak
- Directly inspect internal reasoning
- Directly rewrite internal reasoning
- Improve base model capabilities
```

MARGD is an inference-time external governance specification.

In other words, it is a governance specification supplied externally at inference time, and it does not change the model body itself.

---

## 16. Expressions to Avoid Overclaiming

In public documents and explanations, avoid expressions such as the following.

```text
Expressions to avoid:
- Improves model performance
- Works across all LLMs
- Directly governs internal reasoning
- Bypasses guardrails
- Guarantees correctness
- Guarantees safety
- Is complete as a production safety layer
```

Instead, use expressions such as the following.

```text
Recommended expressions:
- May support stabilization of response structure
- Is a runtime governance specification as an external instruction layer
- Is a specification for governing and auditing observable response-generation behavior
- Supports premise preservation, evidence disclosure, uncertainty disclosure, and repairability
- Complements existing safety layers and operational design
- Is an experimental foundation specification
```

---

## 17. Recommended Attitude When Using MARGD

When using MARGD, the following attitude is desirable.

```text
- Clarify the purpose
- Clarify the premises
- Clarify the evaluation axes
- Treat unknowns as unknowns
- Do not treat AI output as the final judgment
- Conduct human review in specialized domains
- Derive domain-specific versions as needed
- Perform re-fixation and state confirmation in long dialogues
- Consider lightweight derivatives when output becomes heavy
- Record failure cases and use them for the next design improvement
```

MARGD is not syntax for leaving everything to AI.

Rather, it is a governance specification for making it easier for humans to audit, repair, and redesign AI / LLM outputs.

---

## 18. Provisional Conclusion

MARGD, ARGD, and DAGD do not directly improve the base capabilities of AI / LLMs.

They also do not guarantee professional judgment, safety, correctness, or production readiness.

On the other hand, in AI / LLM workflows where research, design, precision work, long-form context, auditing, and repair are important, they may support the following.

```text
- Premise preservation
- Context management
- Evidence separation
- Uncertainty disclosure
- Anti-sycophancy
- Preservation of multiple issues
- Self-audit
- Repair
- Re-fixation
- Status reporting
- Auditability
```

Therefore, MARGD should be treated not as a universal prompt, but as an experimental runtime governance foundation for precise AI / LLM operation.

Practical application requires design that includes the target domain, model capability, operational environment, risk, external safety mechanisms, and human review.

---
