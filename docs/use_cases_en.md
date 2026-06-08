
---

# Application Potential / Use Cases

---

## 1. Positioning of This Document

This document is an entry-point document for organizing expected behavior changes and application potential when MARGD (ARGD / DAGD) is applied across multiple AI usage domains.

The content covered here does not guarantee practical effectiveness, safety, correctness, or the validity of professional judgment.

This document and the documents under it are technical study materials for organizing what kinds of response structure, premise preservation, evidence separation, self-audit, repair, and status reporting may be expected when MARGD is applied as a runtime instruction for AI / LLMs.

For the overall view of MARGD / ARGD / DAGD, refer to `docs/overview_en.md`.
For the technical overview of ARGD / DAGD, refer to `docs/argd_and_dagd_en.md`.

For usage principles and limitations, refer to `docs/usage_and_limitations_en.md`.

For behaviors observed in small-scale validation and long dialogue logs, refer to `docs/validation_and_operation_observation_en.md`.

---

## 2. Application Examples Covered by This Document

This document provides an entry point to the following four application-potential documents.

```text
docs/use_cases/
  medical_assistive_ai_en.md
  education_ai_en.md
  agentic_ai_en.md
  common_behavior_patterns_en.md
```

| Document                         | Content                                                                                                                                                                                                                                        |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `medical_assistive_ai_en.md`     | Covers information organization before and after medical consultation, separation of unconfirmed information, communication support for physicians, separation of signs that may relate to urgency, and similar topics in medical assistive AI |
| `education_ai_en.md`             | Covers preservation of learning goals, organization of understanding level and already-learned scope, wrong-answer analysis, boundary management against task substitution, and similar topics in education AI / learning support AI           |
| `agentic_ai_en.md`               | Covers preservation of goals, constraints, and authority boundaries, confirmation before tool use, stopping and repair after failure, auditability, and similar topics in Agentic AI                                                           |
| `common_behavior_patterns_en.md` | Organizes behavior patterns that may commonly appear when MARGD is applied across medical assistive AI, education AI, and Agentic AI                                                                                                           |

---

## 3. Why This Is Treated as Application Potential

MARGD is not a knowledge base specialized for a specific domain.

The core of MARGD is to provide governance over AI / LLM runtime behavior, such as the following.

```text
- Preservation of input structure
- Preservation of context and premises
- Explicit definition of target scope
- Disclosure of insufficient information
- Separation of fact, inference, assumption, and evaluation
- Preservation of multiple issues
- Suppression of excessive following of user hypotheses
- Self-audit
- Repair
- Re-fixation
- Status reporting
```

These may be especially important in domains such as medical assistive AI, education AI, and Agentic AI, where long context, multiple premises, boundaries with professional judgment, user anxiety or leading input, and external operation risks are involved.

For this reason, this repository organizes MARGD’s application potential not as mere examples, but as a technical study for confirming governance targets in AI runtime behavior.

---

## 4. Overview of Each Application Example

### 4.1 Medical Assistive AI

The medical assistive AI application example covers cases where MARGD is used not as diagnostic AI, but for information organization before and after medical consultation, interview support, and communication support for healthcare professionals.

The main perspectives are as follows.

```text
- Organization of symptoms, lifestyle background, medication, medical history, and similar information
- Separation of confirmed information and unconfirmed information
- Organization of candidate tests to discuss with a physician
- Suppression of diagnostic assertions
- Separation of signs that may relate to urgency
- Conversion into communication notes for physicians
```

This application example treats the possibility that AI may function not as a replacement for physician judgment, but as an information organization layer between the user and healthcare professionals.

For details, refer to `docs/use_cases/medical_assistive_ai_en.md`.

---

### 4.2 Education AI / Learning Support AI

The education AI application example covers cases where MARGD is used not for grading or task substitution, but to support the learner’s understanding process.

The main perspectives are as follows.

```text
- Preservation of learning goals
- Organization of understanding level and already-learned scope
- Decomposition of wrong answers and misunderstandings
- Separation of answer presentation and learning support
- Suppression of output close to task substitution
- Conversion into step-by-step hints, review lists, and question organization
```

This application example treats the possibility that AI may function not by taking over the learner’s work, but as a support layer for organizing the current state of understanding, misunderstandings, missing premises, and next learning actions.

For details, refer to `docs/use_cases/education_ai_en.md`.

---

### 4.3 Agentic AI

The Agentic AI application example covers cases where MARGD is applied to AI that performs planning, judgment, tool use, external operations, and multi-step execution to achieve a goal.

The main perspectives are as follows.

```text
- Preservation of goals, constraints, and target scope
- Explicit definition of authority boundaries
- Stabilization of confirmation before execution
- Organization of tool-use conditions
- Suppression of difficult-to-reverse operations
- Stopping, repair, and re-fixation after failure
- Reporting of execution state, incomplete items, and residual risks
```

This application example considers MARGD not as a way to strengthen AI autonomy without limits, but as a governance specification for making goals, constraints, authority, confirmation, repair, and auditing easier to handle.

For details, refer to `docs/use_cases/agentic_ai_en.md`.

---

### 4.4 Common Behavior Patterns

The common behavior patterns document crosses the three examples of medical assistive AI, education AI, and Agentic AI, and organizes behaviors commonly expected when MARGD is applied.

The main perspectives are as follows.

```text
- Preservation of context and premises
- Scope management
- Disclosure of uncertainty
- Preservation of multiple issues and multiple interpretations
- Suppression of excessive following of user hypotheses
- Structuring of output format
- Repair after failure
- Status reporting and auditability
```

This document is not about the details of individual domains, but about showing the common structure of AI runtime behavior that MARGD may handle across multiple domains.

For details, refer to `docs/use_cases/common_behavior_patterns_en.md`.

---

## 5. Notes When Reading the Application Potential Documents

The application examples in this repository do not show that MARGD guarantees effects in each domain.

In particular, the following points require attention.

```text
- They do not replace professional judgment in medicine, education, law, finance, security, or similar domains
- They do not directly modify the model’s own knowledge, reasoning ability, or long-context retention ability
- If input information is wrong, they do not automatically guarantee or correct that error
- They do not replace authority management, audit logs, rollback mechanisms, or access control on the external tool side
- Practical operation requires expert review, risk assessment, human supervision, and combination with external safety mechanisms
```

MARGD does not guarantee that AI always makes correct judgments.

It is more appropriate to treat MARGD as an external governance layer for guiding AI / LLM responses toward structures where premise preservation, evidence separation, uncertainty disclosure, self-audit, repair, re-fixation, and status reporting are easier to perform.

---

## 6. Relationship Between Application Examples and Validation Documents

The application examples in this document are hypothetical technical studies.

On the other hand, `docs/validation_and_operation_observation_en.md` organizes that some behaviors related to response structure, premise preservation, evidence separation, self-audit, repair, and status reporting were observed in small-scale validation and long dialogue logs where MARGD was applied.

Therefore, this repository separates documents as follows.

| Document                                          | Role                                                                                |
| ------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `docs/use_cases_en.md`                            | Entry point for application potential                                               |
| Documents under `docs/use_cases/`                 | Details of individual application examples                                          |
| `docs/validation_and_operation_observation_en.md` | Organization of behaviors observed in small-scale validation and long dialogue logs |

This separation is intended to avoid mixing application potential with observation results.

---

## 7. Future Candidate Areas for Application Expansion

In the future, MARGD’s application potential may be extended to areas such as the following.

```text
- Legal assistive AI
- Financial assistive AI
- Security support AI
- Research support AI
- Software development support AI
- Customer support AI
- Internal knowledge management AI
- AI audit support
- Long-term project support
```

However, at present these are candidate areas for study.
To claim practical validity in each area, domain-specific evaluation design, comparable input data, execution logs, failure examples, expert review, and risk assessment would be required.

---

## 8. Provisional Summary

MARGD is not a mechanism that guarantees domain-specific expertise or safety.

On the other hand, it has application potential as a framework for providing governance from an external instruction layer to the following processes common across multiple AI usage domains.

```text
- Context preservation
- Premise fixation
- Scope management
- Disclosure of insufficient information
- Preservation of multiple issues
- Suppression of excessive following of user hypotheses
- Structuring of output format
- Repair after failure
- Re-fixation
- Status reporting
- Improved auditability
```

For this reason, this document positions MARGD not as a solution specialized for individual domains, but as a governance specification for organizing and controlling AI / LLM runtime behavior, and organizes its application potential from that perspective.

---
