# Governance Definitions List

The center of this architecture is not file placement, but responsibility separation.  
The MARGD Runtime Governance Bundle is a structure for dividing complex AI responses and judgments into multiple GDs and dynamically combining them as necessary, rather than processing them with one huge instruction or universal domain.

This document lists the 16 Governance Definitions included in the MARGD Runtime Governance Bundle Prototype.

The purpose here is not to explain the detailed specification of each GD.  
It organizes what each GD handles and what it does not handle at a granularity that is easy to grasp even on first reading.

---

## 1. What This Document Covers

The GDs covered in this document are the following 16.

```text id="2rv0f2"
CDOGD

SPPGD
DAAGD
SDAGD
SDMRGD

DSGD
ACRGD
AAGD
AISGD
MPGD
DCAGD
PMOGD
AIRGD
AIAGD
SEGD
OMRGD
```

ARGD / DAGD are the core governance prerequisites for this prototype.  
However, they are not included among the 16 GDs in this document.

For details on ARGD / DAGD, refer to the README at the repository root and existing materials.

---

## 2. Overall Classification

In this prototype, the 16 GDs are organized as follows.

```text id="jtp3me"
cross-domain coordination:
  CDOGD

decision pipeline:
  SPPGD
  DAAGD
  SDAGD

conditional watchdog:
  SDMRGD

ordinary:
  DSGD
  ACRGD
  AAGD
  AISGD
  MPGD
  DCAGD
  PMOGD
  AIRGD
  AIAGD
  SEGD
  OMRGD
```

This classification is for explaining the nature of the GDs.  
The classification order or listed order does not mean priority, activation order, or strength of authority.

In particular, GDs placed under ordinary are GDs for providing opinions, judgment materials, and confirmation conditions from each specialized domain.  
Ordinary GDs do not issue execution permission, final decisions, approval, or assignment of accountable party.

Authority / accountability judgments such as autonomous judgment permissibility, pending approval state, inside/outside delegation scope, and accountable-party establishment state are handled by DAAGD.

---

## 3. CDOGD

### 3.1 Basic Information

```text id="zjm95v"
abbreviation:
  CDOGD

formal name:
  Cross-Domain Orchestration Governance Definition

location:
  definitions/orchestration/cdogd_v0.1.0_en.json
```

### 3.2 Role

CDOGD is an orchestration GD for automatic dynamic routing that brings multiple GDs together across domains.

It organizes which GDs should be applied within which scope according to the current request or target.  
It also handles overlaps, handoffs, suppression, attenuation, and repair propagation between GDs.

```text id="l5ex5j"
What CDOGD handles:
  candidates for potentially relevant GDs
  scope to activate
  role of each GD
  overlap between GDs
  handoff between GDs
  repair propagation
  suppression
  attenuation
```

### 3.3 What It Does Not Handle

CDOGD does not make final decisions.  
It also does not perform approval, execution permission, assignment of accountable party, or specialized judgment itself.

```text id="0rm4rn"
What CDOGD does not handle:
  final decision
  approval
  execution permission
  assignment of accountable party
  replacement of specialized judgment
```

---

## 4. Decision Pipeline Domain Extensions

Decision pipeline GDs are a group of GDs for separating the process of bringing judgment materials closer to final judgment.

```text id="bypwa7"
SPPGD:
  organizes the structure of strategic judgment

DAAGD:
  is responsible for authority / accountability judgment within MARGD
  judges whether it can be treated as autonomous judgment, should be returned to human judgment, is pending approval, is outside the delegation scope, or has an undetermined accountable party

SDAGD:
  audits the judgment structure of SPPGD and the authority / accountability state judged by DAAGD
  does not replace DAAGD
  does not judge autonomous judgment permissibility, pending approval state, inside/outside delegation scope, or accountable-party establishment state
```

Specialized judgment materials produced by ordinary GDs and others do not become final judgments as-is.  
As necessary, SPPGD organizes the judgment structure, DAAGD performs authority / accountability judgment,  
and SDAGD audits that judgment structure and authority / accountability state.

---

## 5. SPPGD

### 5.1 Basic Information

```text id="c1nd16"
abbreviation:
  SPPGD

formal name:
  Strategic Planning and Prioritization Governance Definition

location:
  definitions/domain_extensions/decision_pipelines/sppgd_v0.1.0_en.json
```

### 5.2 Role

SPPGD is a GD that organizes the structure of strategic judgment.

It organizes objectives, premises, constraints, options, options not selected, priorities, allocation, order, continuation, stopping, withdrawal, deferral, reevaluation conditions, and related items.

```text id="ji0io1"
What SPPGD handles:
  objectives
  premises
  constraints
  options
  options not selected
  priorities
  allocation
  order
  continuation
  stopping
  withdrawal
  deferral
  reevaluation conditions
```

### 5.3 What It Does Not Handle

SPPGD does not make final decisions.  
It also does not handle decision authority, approval, accountable party, or audit of strategic judgment.

```text id="8ov35w"
What SPPGD does not handle:
  final decision
  determination of decision authority
  approval
  assignment of accountable party
  audit of strategic judgment
```

---

## 6. DAAGD

### 6.1 Basic Information

```text id="uu1ms2"
abbreviation:
  DAAGD

formal name:
  Decision Authority and Accountability Governance Definition

location:
  definitions/domain_extensions/decision_pipelines/daagd_v0.1.0_en.json
```

### 6.2 Role

DAAGD is an authority / accountability GD that judges decision authority state within MARGD.

Based on existing system policy, developer policy, runtime policy, tool permissions, external execution permissions, delegation conditions, approval conditions, and responsibility boundaries,  
DAAGD judges whether the relevant judgment can be treated as an autonomous judgment by AI or runtime, should be returned to human judgment, should be treated as pending approval, should be treated as outside the delegation scope, or should be treated as having an undetermined accountable party.

However, DAAGD does not newly generate authority that does not exist externally.  
DAAGD judges the authority / accountability state within MARGD within the scope of already existing policies, authority, delegation, approval conditions, and responsibility boundaries.

```text id="6t5n3t"
What DAAGD handles:
  decision authority
  approval conditions
  delegation scope
  accountable party
  judge
  executor
  authority classification of AI judgment
  necessity of human approval
  return conditions
  record conditions
```

Even if an ordinary GD provides specialized judgment materials, that does not necessarily mean AI may adopt them.  
Whether AI may use those judgment materials, whether they should be returned to human judgment, whether approval is required, and who bears responsibility are handled by DAAGD.

### 6.3 What It Does Not Handle

DAAGD does not create the judgment content itself.  
It does not create SPPGD’s judgment structure, nor does it replace SDAGD’s audit.  
Also, DAAGD itself does not generate new authority.

```text id="ffpk5d"
What DAAGD does not handle:
  generation of judgment content
  generation of judgment structure
  replacement of specialized judgment
  replacement of execution work
  audit of strategic judgment
  self-approval
  generation of authority
```

DAAGD is a GD that handles the state of decision authority based on already existing runtime policy, delegation scope, human approval conditions, accountable parties, and related items.

---

## 7. SDAGD

### 7.1 Basic Information

```text id="n3pw24"
abbreviation:
  SDAGD

formal name:
  Strategic Decision Audit Governance Definition

location:
  definitions/domain_extensions/decision_pipelines/sdagd_v0.1.0_en.json
```

### 7.2 Role

SDAGD is a GD responsible for audits related to strategic judgment.

SDAGD audits the judgment structure organized by SPPGD and the authority / accountability state judged by DAAGD.

What SDAGD indicates is only an audit state.  
SDAGD does not create the strategic judgment itself, does not replace DAAGD, and does not judge autonomous judgment permissibility, pending approval state, inside/outside delegation scope, or accountable-party establishment state.

```text id="xiw51c"
What SDAGD audits:
  SPPGD's judgment structure
  authority / accountability state judged by DAAGD
  judgment premises
  constraints
  authority grounds
  approval conditions
  accountable party
  unresolved items
```

SDAGD handles audit states such as no major audit blocking condition, conditional audit findings, return to repair, and audit invalidation.

These are audit states, not formal approval, execution permission, final decision-making, or determination of accountable party itself.

### 7.3 What It Does Not Handle

SDAGD does not create the strategic judgment itself.  
It also does not generate decision authority or perform execution work.  
It is also not a GD that approves SDMRGD’s audit state.

```text id="8nr9fw"
What SDAGD does not handle:
  generation of strategic judgment
  generation of decision authority
  execution work
  approval of SDMRGD
```

---

## 8. SDMRGD

### 8.1 Basic Information

```text id="y6vizo"
abbreviation:
  SDMRGD

formal name:
  Strategic Decision Meta-Review Governance Definition

location:
  definitions/domain_extensions/conditional_watchdogs/sdmrgd_v0.1.0_en.json
```

### 8.2 Role

SDMRGD is a GD that meta-reviews the audit state of SDAGD.

It checks SDAGD’s audit scope, audit grounds, audit result classification, risk of formal passage, over-auditing, under-auditing, need for repair, and related items.  
Escalation in SDMRGD does not mean directly proceeding to external final judgment or approval.  
Basically, it means returning to SDAGD-side self-audit, repair, re-audit, or condition checking on the upper runtime side.

```text id="tlzfvu"
What SDMRGD sees:
  SDAGD's audit scope
  SDAGD's audit grounds
  audit result classification
  risk of formal passage
  over-auditing
  under-auditing
  crossing into the DAAGD domain
  need for repair
```

### 8.3 What It Does Not Handle

SDMRGD does not directly audit the strategic judgment itself.  
It does not substitute for SDAGD’s primary audit, nor does it make final decisions.

```text id="jc2gcb"
What SDMRGD does not handle:
  audit of the strategic judgment itself
  substitution for SDAGD's primary audit
  determination of decision authority
  final decision
  mutual audit loop
```

---

## 9. Ordinary Domain Extensions

Ordinary GDs are a group of GDs that provide specialized opinions, judgment materials, confirmation conditions, detection results, and handoff materials from the perspectives of each specialized domain.

Ordinary GDs do not issue execution permission, final decisions, approval, or assignment of accountable party.

```text id="44wtdi"
ordinary GDs:
  provide specialized opinions
  provide judgment materials
  provide confirmation conditions
  provide detection results
  provide handoff materials

What ordinary GDs do not handle:
  execution permission
  final decision
  approval
  assignment of accountable party
```

---

## 10. DSGD

### 10.1 Basic Information

```text id="224uqy"
abbreviation:
  DSGD

formal name:
  Data Science Governance Definition

location:
  definitions/domain_extensions/ordinary/dsgd_v0.1.0_en.json
```

### 10.2 Role

DSGD is a GD that handles analytical purpose, target scope, data, structure, provenance, quality, hypotheses, methods, evaluation metrics, omissions, bias, statistical validity, and analytical claims from the perspective of data analysis.

```text id="nig292"
What DSGD sees:
  analytical purpose
  target scope
  data
  data structure
  data provenance
  data quality
  hypotheses
  methods
  evaluation metrics
  omissions
  bias
  distinction between prediction and causation
  analytical claims
  execution history
```

### 10.3 What It Does Not Handle

DSGD does not handle novelty of research claims, implementation quality, artifact composition, progress management, or decision authority.

---

## 11. ACRGD

### 11.1 Basic Information

```text id="lqsru1"
abbreviation:
  ACRGD

formal name:
  Artifact Composition and Review Governance Definition

location:
  definitions/domain_extensions/ordinary/acrgd_v0.1.0_en.json
```

### 11.2 Role

ACRGD is a GD that handles artifact composition, transformation, readability, format, placement, and claims of publication or submission readiness.

```text id="piicr2"
What ACRGD sees:
  purpose of the artifact
  audience
  selection of information sources
  composition
  transformation
  format
  placement
  readability
  machine readability
  confidential information
  disclosure scope
  language versions
  revision history
  claims of publication or submission readiness
```

### 11.3 What It Does Not Handle

ACRGD does not handle correctness of specialized content or final approval.  
Being well-formed as an artifact does not mean that it is specializedly correct or approved for publication.

---

## 12. AAGD

### 12.1 Basic Information

```text id="7m5o9t"
abbreviation:
  AAGD

formal name:
  Agentic AI Governance Definition

location:
  definitions/domain_extensions/ordinary/aagd_v0.1.0_en.json
```

### 12.2 Role

AAGD is a GD that handles objectives, work scope, plans, procedures, tool calls, side effects, work state, handoff, memory, and completion claims in the execution process of Agentic AI.

```text id="naxtw8"
What AAGD sees:
  objectives
  work scope
  plans
  procedures
  tool call history
  side effects
  work state
  checkpoint
  retry / rollback / compensation
  handoff
  grounds for memory
  completion confirmation
  final state
```

### 12.3 What It Does Not Handle

AAGD does not handle decision authority, safety judgment, operational judgment, structural design judgment, project priority, artifact quality, or cross-GD assignment.

AAGD confirming the execution process does not mean issuing execution permission.

---

## 13. AISGD

### 13.1 Basic Information

```text id="qj3x1z"
abbreviation:
  AISGD

formal name:
  AI Security Governance Definition

location:
  definitions/domain_extensions/ordinary/aisgd_v0.1.0_en.json
```

### 13.2 Role

AISGD is a GD that handles AI security risks that occur through AI.

```text id="1vwnxt"
What AISGD sees:
  prompt injection
  jailbreak attempts
  instruction leakage
  exposure of secrets
  exposure of personal information
  tool abuse
  agentic takeover
  retrieval poisoning
  memory contamination
  authority confusion
  policy evasion
  inter-agent attacks
```

### 13.3 What It Does Not Handle

AISGD does not absorb general cybersecurity as a whole, ordinary Agentic AI execution, the whole of model policy, implementation, operations, decision authority, or audit of strategic judgment.

AISGD provides safety risks, but subsequent authority / accountability judgment is the domain of DAAGD,  
and formal approval or external execution permissibility is the domain of runtime policy, humans, organizations, and external authority holders.

---

## 14. MPGD

### 14.1 Basic Information

```text id="xhy6np"
abbreviation:
  MPGD

formal name:
  Model Policy Governance Definition

location:
  definitions/domain_extensions/ordinary/mpgd_v0.1.0_en.json
```

### 14.2 Role

MPGD is a GD that handles grounds, applicability scope, exceptions, and records for judgments related to model policy.

```text id="2vzn4h"
What MPGD sees:
  policy identification
  clause identification
  version
  applicability
  applicable scope
  priority relationships
  conflicts
  exceptions
  risks
  uncertainty
  over-refusal
  under-refusal
  non-binary judgment branching
  reevaluation
  repair
  revision
  judgment history
```

### 14.3 What It Does Not Handle

MPGD does not handle Agentic AI execution, AI safety threat analysis, artifact quality, or final approval authority.

---

## 15. DCAGD

### 15.1 Basic Information

```text id="95xfo8"
abbreviation:
  DCAGD

formal name:
  Development Consulting AI Governance Definition

location:
  definitions/domain_extensions/ordinary/dcagd_v0.1.0_en.json
```

### 15.2 Role

DCAGD is a GD that handles AI-assisted development consultation.  
It organizes requirements clarification, technology options, design policy, comparison of implementation policies, feasibility, rough effort, development risks, and related items.

```text id="6ydsua"
What DCAGD sees:
  requirements clarification
  technology options
  design policy
  comparison of implementation policies
  feasibility
  difficulty
  rough effort
  development risks
  maintainability
  extensibility
  prototype scope
  minimum viable version scope
  impact of specification changes
```

### 15.3 What It Does Not Handle

DCAGD does not handle implementation itself, test execution, deployment, operations, final safety audit, legal review, guarantee of project success, or final organizational judgment.

---

## 16. PMOGD

### 16.1 Basic Information

```text id="3znj90"
abbreviation:
  PMOGD

formal name:
  Project Management and Orchestration Governance Definition

location:
  definitions/domain_extensions/ordinary/pmogd_v0.1.0_en.json
```

### 16.2 Role

PMOGD is a GD that handles organization of project progress.  
It organizes work items, assignees, deadlines, dependencies, blockers, handoffs, deliverability, and related items.

```text id="xmggky"
What PMOGD sees:
  work items
  task
  issue
  backlog
  milestone
  assignee
  deadline
  dependencies
  blockers
  handoff
  agreements
  unresolved items
  action item
  deliverability
  cross-domain work state
```

### 16.3 What It Does Not Handle

PMOGD does not handle strategic judgment, technical judgment, implementation, operational judgment, legal or regulatory judgment, artifact quality, or formal approval.

---

## 17. AIRGD

### 17.1 Basic Information

```text id="tw4z62"
abbreviation:
  AIRGD

formal name:
  AI Research Governance Definition

location:
  definitions/domain_extensions/ordinary/airgd_v0.1.0_en.json
```

### 17.2 Role

AIRGD is a GD that handles research claims, novelty, and the connection between evidence and claims in AI research.

```text id="hjpf2v"
What AIRGD sees:
  research questions
  prior work
  novelty claims
  hypotheses
  counter-hypotheses
  falsification conditions
  research design
  evidence
  execution history
  separation between results and claims
  negative results
  limitations
  reproducibility conditions
  consistency of claims at publication
```

### 17.3 What It Does Not Handle

AIRGD does not handle Agentic AI execution, details of statistical validity, software quality, artifact composition, AI safety threat analysis, or approval authority.

---

## 18. AIAGD

### 18.1 Basic Information

```text id="aiagd_basic_info"
abbreviation:
  AIAGD

formal name:
  AI Architecture Governance Definition

location:
  definitions/domain_extensions/ordinary/aiagd_v0.1.0_en.json
```

### 18.2 Role

AIAGD is a GD that handles AI system structure, component responsibilities, connections, information flows, boundary design, placement, structural claims, and runtime conformance claims.

```text id="aiagd_scope"
What AIAGD sees:
  system purpose
  requirements
  quality attributes
  component responsibilities
  scope not handled by components
  connections
  information flows
  trust boundaries
  structure of authority boundaries
  model placement
  retrieval mechanism placement
  memory mechanism placement
  tool placement
  agent placement
  policy layer placement
  evaluation layer placement
  observation / recording mechanism placement
  placement of human confirmation points
  failure propagation design
  impact-scope design
  fallback / containment design
  placement configuration
  migration / replacement plan
  runtime conformance claims
  history of structural judgment
```

### 18.3 What It Does Not Handle

AIAGD does not handle Agentic AI execution, execution management of tool calls, decision authority, approval, assignment of accountable party, determination of AI safety risks, operational execution, incident response, implementation quality, development consultation, artifact composition, or cross-GD assignment.

AIAGD confirming the structure does not mean execution management, authority granting, safety determination, operational success, or guarantee of implementation quality.

---

## 19. SEGD

### 19.1 Basic Information

```text id="segd_basic_info"
abbreviation:
  SEGD

formal name:
  Software Engineering Governance Definition

location:
  definitions/domain_extensions/ordinary/segd_v0.1.0_en.json
```

### 19.2 Role

SEGD is a GD that handles software engineering execution, verification, change management, artifact identification, repair, rollback, rerun, and implementation history.

```text id="segd_scope"
What SEGD sees:
  requirements
  acceptance conditions
  specifications
  correspondence between design and implementation
  repository
  branch
  base revision
  source code changes
  configuration changes
  dependency changes
  migration changes
  static verification
  unit test results
  integration test results
  regression test results
  build results
  artifact identification
  deployment readiness state
  deployment results
  repair
  rollback scope
  rerun scope
  history of implementation judgment
```

### 19.3 What It Does Not Handle

SEGD does not handle development consultation, AI structural design, ordinary Agentic AI execution, continuous operations, decision authority, AI-mediated safety risks, project progress organization, or artifact publication quality.

SEGD confirming the verification state is not a guarantee of execution permission or operational success.  
Generated code is not treated as correct without verification. Build success does not mean runtime correctness,  
unit test success does not mean correctness at integration time. Deployment completion does not mean operational success.

---

## 20. OMRGD

### 20.1 Basic Information

```text id="omrgd_basic_info"
abbreviation:
  OMRGD

formal name:
  Operations, Maintenance, and Reliability Governance Definition

location:
  definitions/domain_extensions/ordinary/omrgd_v0.1.0_en.json
```

### 20.2 Role

OMRGD is a GD that handles operational state, maintainability, recoverability, and reliability.

```text id="omrgd_scope"
What OMRGD sees:
  operational state
  service health
  monitoring targets
  log
  metrics
  alert
  incident
  failure
  degradation
  outage
  runbook
  rollback procedures
  recovery procedures
  maintenance work
  operational risks
  change impact
  service level
  reliability objectives
  error budget
  dependency health
  operational load
  technical debt
  maintenance window
  escalation path
  post-incident review
  recurrence prevention
  continuous improvement items
  operational handoff
```

### 20.3 What It Does Not Handle

OMRGD does not handle new development, implementation itself, overall project management, strategic judgment, artifact composition, formal legal judgment, or organizational approval.

OMRGD looking at operational state does not automatically guarantee operational success or recovery completion.  
Being running does not mean a reliable operational state. No alerts being present does not mean health.  
Having attempted recovery does not mean recovery completion. Closing an incident does not mean recurrence prevention.

---

## 21. Summary

The 16 GDs in this prototype share responsibilities as follows.

```text id="e2d457"
CDOGD:
  handles cross-domain routing, scope adjustment, handoff, and repair propagation

SPPGD:
  organizes the structure of strategic judgment

DAAGD:
  is responsible for authority / accountability judgment within MARGD
  judges whether it can be treated as autonomous judgment, should be returned to human judgment, is pending approval, is outside the delegation scope, or has an undetermined accountable party

SDAGD:
  audits the judgment structure of SPPGD and the authority / accountability state judged by DAAGD
  does not replace DAAGD

SDMRGD:
  meta-reviews the audit state of SDAGD

ordinary GDs:
  provide specialized opinions, judgment materials, confirmation conditions, risk indications, repair candidates, and handoff materials
  these are not themselves authority / accountability judgments within MARGD
```

Ordinary GDs are not GDs that judge execution permission, final decision, autonomous judgment permissibility, pending approval state, inside/outside delegation scope, or accountable-party establishment state.  
Outputs from ordinary GDs may become materials for strategic judgment structure in SPPGD, or inputs or reference materials for authority / accountability judgment in DAAGD.

However, they themselves are neither the strategic judgment structure itself nor the authority / accountability judgment within MARGD itself.  
Within MARGD, it is DAAGD that performs authority / accountability judgment.

For usage notes and limitations of MARGD and each GD, refer to `usage_and_limitations_en.md`.