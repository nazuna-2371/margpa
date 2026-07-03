# Usage Notes and Limitations

This document explains the usage notes and limitations of the MARGD Runtime Governance Bundle Prototype.

This prototype is a prototype intended to make it easier to structure AI response generation, judgment organization, audit, repair, handoff, authority confirmation, and related processes.  
However, MARGD and each GD do not grant new authority to AI.

---

## 1. It Is a Prototype

This prototype is a prototype.

The design, descriptions, classifications, separation between GDs, activation conditions, audit conditions, and document structure may change in the future.  
Therefore, this prototype should not be treated as a stable standard specification, a completed product, or a certified framework.

```text id="791sm7"
Positioning of this prototype:
  prototype
  experimental configuration
  governance bundle under verification
  design that may change in the future
```

This prototype must be used based on the user’s own judgment and responsibility.

---

## 2. It Is Provided Without Warranty

This prototype is provided without warranty.

Use of this prototype does not guarantee that responses, judgments, designs, implementations, operations, audits, publication, submissions, decision-making, external operations, or other results will become correct.

```text id="x6vquz"
Things not guaranteed:
  accuracy
  completeness
  safety
  legality
  operational success
  implementation success
  validity of judgment
  completeness of audit
  substitute for expert confirmation
  substitute for organizational approval
```

When necessary, users, administrators, organizations, experts, or authority holders need to confirm the content.

---

## 3. It Does Not Add Authority

MARGD and each GD do not grant new authority to AI.

```text id="i52jvg"
Things MARGD does not add:
  execution authority
  tool-use authority
  external operation authority
  approval authority
  decision authority
  accountable party
  legal authority
  medical authority
  organizational authority
```

Even if a GD is activated, it means “confirm from that perspective.”  
That alone does not mean that AI may execute, decide, approve, or take responsibility.

---

## 4. It Does Not Change Higher-Level Policies

MARGD and each GD do not change higher-level policies or constraints.

```text id="xq59i1"
Things not changed:
  system policy
  developer policy
  runtime policy
  tool permissions
  external execution permissions
  human approval conditions
  organizational approval conditions
  laws and regulations
  accountable party
```

MARGD is a governance layer that operates under these higher-level policies.  
It cannot be used in ways that violate higher-level policies, exceed authority, or bypass approval.

---

## 5. When Used with an LLM Alone

When MARGD is applied to ordinary LLM dialogue, MARGD mainly works as an organizing structure within the response.

```text id="2xbueh"
What can be done with an LLM alone:
  organize which GD perspectives are relevant
  separate judgment materials
  indicate points where authority confirmation is required
  indicate points that should be returned to human judgment
  indicate points where audit or repair is required
```

However, the authority of the LLM itself does not change.  
Operations that the LLM cannot execute do not become executable through MARGD.

Also, LLM output does not substitute for expert confirmation, organizational approval, legal judgment, medical judgment, or final responsibility.

---

## 6. When Used with Agentic AI or Tool Runtime

MARGD also assumes possible future integration into runtimes that include Agentic AI, tool use, and external operations.

Even in that case, MARGD itself does not create tool execution permissions or external operation permissions.

```text id="hc6gqf"
What determines execution permissibility:
  runtime-side design
  tool permissions
  external operation permissions
  higher-level policies
  delegation scope
  human approval conditions
  organizational responsibility boundaries
```

MARGD organizes which perspectives should be checked, and where stop conditions, hold conditions, human confirmation conditions, audit conditions, and repair conditions exist.  
It organizes where to return to human confirmation, and where audit or repair is required.

However, whether execution is actually possible is determined by runtime, tool permissions, external authority, and approval conditions.

---

## 7. Limitations of Ordinary GDs

Ordinary GDs are GDs for providing specialized opinions, judgment materials, confirmation conditions, detection results, and handoff materials from the perspective of each specialized domain.

Ordinary GDs are not GDs that issue final decisions or execution permissions.

```text id="qwwa5p"
What ordinary GDs provide:
  specialized opinions
  judgment materials
  confirmation conditions
  risk indications
  insufficiency indications
  repair candidates
  handoff materials

What ordinary GDs do not provide:
  execution permission
  final decision
  approval
  assignment of accountable party
```

For example, even if SEGD indicates an implementation verification state, that alone does not become execution permission.  
Even if AISGD indicates a safety risk, that alone does not become a final stop judgment or approval judgment.  
Even if OMRGD indicates an operational state, that alone does not guarantee operational success or recovery completion.

---

## 8. Positioning of DAAGD

DAAGD is a GD that handles decision authority, approval necessity, delegation scope, accountable party, and record conditions within MARGD.

Ordinary GDs, SPPGD, SDAGD, and other GDs may provide judgment materials, candidates, audit findings, risk indications, repair conditions, and handoff materials from their respective perspectives.  
However, those outputs alone must not determine whether AI or runtime may make an autonomous judgment, should be returned to human confirmation, requires approval, or who should be treated as the accountable party.

Within MARGD, DAAGD is the regular GD that confirms AI judgment authority classification, autonomous judgment permissibility, approval necessity, delegation scope, and treatment of accountable party.

```text id="bm88oy"
What DAAGD handles:
  authority classification of AI judgment
  whether it is advice or judgment support
  whether it is a provisional recommendation
  whether it is a conditional judgment
  whether it is a delegated judgment
  whether it can be treated as autonomous judgment
  whether it should be returned to human confirmation
  whether approval is required
  delegation scope
  treatment of accountable party
  record conditions
```

However, DAAGD does not newly generate authority that does not exist externally.

DAAGD is a GD that handles the state of decision authority based on already existing system policy, developer policy, runtime policy, tool permissions, external execution permissions, delegation scope, human approval conditions, organizational rules, responsibility boundaries, and related items.

When DAAGD is used in ordinary LLM dialogue, DAAGD mainly organizes where authority confirmation is required, where the judgment should be returned to human judgment, and which judgments AI must not finalize.

On the other hand, when MARGD is integrated into an actual runtime or Agentic AI, DAAGD may function as an authority / accountability gate that determines, within the scope of the given runtime policy, tool permissions, delegation scope, and human approval conditions,  
whether AI or runtime may treat something as an autonomous judgment, should return it to human confirmation, or requires approval.

Even in this case, DAAGD does not create authority.  
DAAGD confirms whether that judgment is in a state that AI or runtime may handle within the scope of already granted authority, delegation, and approval conditions.  
Other GDs must not determine autonomous judgment permissibility, approval necessity, delegation scope, or accountable party without going through DAAGD.

---

## 9. Limitations of SDAGD and SDMRGD

SDAGD is a GD responsible for audits related to strategic judgment.

SDAGD audits the strategic judgment structure organized by SPPGD and the treatment of decision authority, approval necessity, delegation scope, and accountable party organized by DAAGD.  
Here, audit means checking whether there are structural problems or unresolved audit findings in premises, objectives, judgment structure, options, reasons for non-selection, priorities, risks, authority boundaries, unresolved conditions, and DAAGD’s treatment of authority state.

SDAGD is not a GD that creates the strategic judgment itself.  
It is also not a GD that determines decision authority, autonomous judgment permissibility, approval necessity, delegation scope, or accountable party.  
Those are areas handled by DAAGD or by external runtime policy, humans, organizations, or authority holders.

What SDAGD indicates is only an audit state.  
For example, it indicates states such as no major audit blocking condition found, conditional audit findings exist, return to repair is necessary, or it needs to be treated as audit-invalid.

These audit states are for organizing whether the judgment structure and treatment of authority state can be handed to the next confirmation stage, should be treated conditionally, should be returned to repair, or should be treated as invalid.  
They are not formal approval, execution permission, final decision-making, or determination of accountable party itself.

When SDAGD is used in ordinary LLM dialogue, SDAGD mainly organizes whether there are audit problems in the judgment structure or treatment of authority state.

On the other hand, when MARGD is integrated into an actual runtime or Agentic AI, the audit state of SDAGD may be used as a gate for pre-execution confirmation, hold, return to repair, re-audit, stop conditions, and related processes within the scope defined by runtime policy.  
Even in this case, SDAGD does not replace DAAGD and determine autonomous judgment permissibility.  
SDAGD audits DAAGD’s treatment of authority state and SPPGD’s judgment structure.

SDMRGD is a GD that meta-reviews the audit state of SDAGD.

SDMRGD confirms whether SDAGD’s audit is excessive, insufficient, becoming a formal passage judgment, has an unclear audit scope, or is crossing into DAAGD’s domain.

Escalation in SDMRGD does not mean directly proceeding to external final judgment or approval.  
Basically, it means treating SDAGD’s audit state as degraded / returned / requires_self_audit_or_repair, and returning to SDAGD-side self-audit, repair, re-audit, or condition checking on the upper runtime side.

```text id="z3r4dl"
DAAGD:
  confirms decision authority, approval necessity, delegation scope, and treatment of accountable party
  is the regular authority / accountability GD that handles autonomous judgment permissibility within MARGD
  does not newly generate authority
  handles authority state within the scope of existing runtime policy, tool permissions, delegation scope, human approval conditions, and organizational responsibility boundaries

SDAGD:
  is responsible for audits related to strategic judgment
  audits SPPGD's judgment structure and DAAGD's treatment of authority state
  does not replace DAAGD
  does not determine autonomous judgment permissibility, approval necessity, delegation scope, or accountable party
  indicates audit states such as no audit blocking condition, conditional audit findings, return to repair, and audit invalidation

SDMRGD:
  meta-reviews the audit state of SDAGD
  confirms SDAGD's over-auditing, under-auditing, formal passage, ambiguity of audit scope, and crossing into DAAGD's domain
  if there is a problem, returns to SDAGD for self-audit, repair, re-audit, or condition checking on the upper runtime side
```

SDMRGD does not substitute for SDAGD’s primary audit.  
Also, SDAGD and SDMRGD should not create an infinite loop in which they continue auditing each other.

---

## 10. It Does Not Substitute for Experts

MARGD and each GD do not substitute for experts.

In particular, in the following areas, appropriate confirmation by experts, institutions, systems, laws and regulations, and accountable parties is required.

```text id="0lp6iv"
Areas where expert confirmation is likely to be required:
  medicine
  law
  finance
  educational evaluation
  psychological support
  interpersonal support
  safety management
  information security
  labor affairs
  rights handling
  high-public-impact judgments
```

MARGD can organize judgment materials and confirmation conditions.  
However, it does not substitute for professional qualifications, institutional approval, legal responsibility, or medical responsibility.

---

## 11. Notes on Medical Support

When applying it to medical support, it must be handled especially carefully.

MARGD and each GD do not substitute for diagnosis, treatment, prescription, or final medical judgment.  
In situations involving urgent symptoms, sudden changes, or possible life-threatening conditions, handoff to medical institutions, emergency services, or experts is required.

```text id="xiak93"
Things not substituted for in medical support:
  diagnosis
  treatment
  prescription
  final medical judgment
  physician judgment
  emergency response
  consultation with a medical institution
```

When designing a medical-support GD, symptom organization, consultation guidelines, danger signs, handoff to human experts, record conditions, and related items need to be clearly separated.

---

## 12. Notes on Interpersonal Support and Emotional Support

When applying it to interpersonal support or emotional support, it also needs to be handled carefully.

Support by AI does not substitute for human relationships, psychological support, emergency response, or expert support.  
Handoff conditions to human support or expert institutions need to be clarified so that dependency, over-involvement, misguidance, overlooking danger signs, and related problems do not occur.

```text id="itw8i4"
Things to watch for:
  dependency
  over-involvement
  misguidance
  overlooking danger signs
  worsening isolation
  overlooking urgency
  insufficient handoff to expert support
```

When necessary, it should not be handled by AI alone, and should be returned to humans, experts, or support contacts.

---

## 13. Notes on Generated Artifacts

Text, code, designs, analyses, materials, image proposals, operational plans, research proposals, and similar artifacts generated using MARGD are not necessarily correct as-is.

```text id="3f5a7v"
Things to watch for in generated artifacts:
  they may contain errors
  premises may be missing
  constraints may be overlooked
  they may contain outdated information
  they may not fit the execution environment
  expert confirmation may be required
  approval may be required
```

When using generated artifacts, it is necessary to confirm the purpose, target, premises, constraints, verification, approval, and accountable party.

---

## 14. Notes on Software Engineering

Even when SEGD is involved, code or implementation is not automatically treated as correct.

```text id="6o2nky"
Notes:
  code generation does not mean implementation success
  success in static verification does not mean runtime correctness
  unit test success does not mean correctness at integration time
  build success does not mean correctness during operations
  deployment completion does not mean operational success
```

Implementation, verification, build, deployment, and operations each require separate confirmation.  
As necessary, they need to be separated and handled by SEGD, OMRGD, AAGD, DAAGD, and related GDs.

---

## 15. Notes on AI Safety

Even if AISGD detects a safety risk, that alone does not complete the final judgment.

It is necessary to confirm the nature of the risk, scope of impact, execution permissibility, stop conditions, human approval, records, and accountable party.

```text id="897mun"
Things to confirm:
  type of risk
  scope of impact
  reproduction conditions
  abuse potential
  stop conditions
  repair conditions
  necessity of human confirmation
  necessity of records
  accountable party
```

When there is a safety risk, there are cases where AI alone should not continue processing.

---

## 16. Notes on Publication, Submission, and Approval

Even if ACRGD handles artifact composition and claims of publication or submission readiness, that alone does not become formal publication approval or submission approval.

```text id="1hgzj7"
Things to confirm separately:
  content accuracy
  specialized validity
  rights relationships
  confidential information
  personal information
  organizational approval
  publication scope
  submission destination rules
```

Being well-formed as an artifact and being allowed to publish it are separate matters.  
Being in a submittable format and being allowed to submit it are also separate matters.

---

## 17. Do Not Leave the Accountable Party Ambiguous

When using MARGD, who judges, who approves, who executes, and who takes responsibility must not be left ambiguous.

```text id="4a9bsx"
Things to make clear:
  judge
  approver
  executor
  accountable party
  recorder
  conditions for returning to human judgment
```

If the accountable party is unclear, processing should not proceed with AI alone.  
DAAGD needs to confirm decision authority, approval necessity, delegation scope, and treatment of accountable party.

---

## 18. Summary

The MARGD Runtime Governance Bundle Prototype is a prototype intended to make it easier to structure AI responses, judgments, audits, repairs, and handoffs.

However, MARGD and each GD do not grant new authority to AI.  
They do not change higher-level policies, runtime policy, tool permissions, external execution permissions, human approval, organizational accountable parties, or laws and regulations.

Ordinary GDs provide specialized opinions, judgment materials, confirmation conditions, risk indications, repair candidates, and handoff materials.  
Their outputs alone must not determine autonomous judgment permissibility, approval necessity, delegation scope, or accountable party.

DAAGD is the regular authority / accountability GD that confirms decision authority, autonomous judgment permissibility, approval necessity, delegation scope, and treatment of accountable party within MARGD.  
However, DAAGD also does not newly generate authority that does not exist externally.

SDAGD audits SPPGD’s judgment structure and DAAGD’s treatment of authority state.  
SDAGD indicates audit states such as audit blocking conditions, conditional audit findings, return to repair, and audit invalidation.  
However, it does not replace DAAGD and does not determine autonomous judgment permissibility, approval necessity, delegation scope, or accountable party.

SDMRGD meta-reviews the audit state of SDAGD and, as necessary, returns to SDAGD for self-audit, repair, re-audit, or condition checking on the upper runtime side.  
SDMRGD does not substitute for SDAGD’s primary audit and also does not directly proceed to external final judgment or approval.

This prototype does not substitute for experts, organizations, institutions, approvers, or accountable parties.  
Users need to confirm the content under their own responsibility and, when necessary, hand it off to humans, experts, organizations, or institutions.