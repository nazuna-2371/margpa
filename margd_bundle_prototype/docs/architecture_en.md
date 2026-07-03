# Architecture

This document explains the conceptual structure of the MARGD Runtime Governance Bundle Prototype.

The architecture discussed here does not refer to the repository directory structure,  
but to how ARGD / DAGD, CDOGD, the bundle, domain extensions, and templates are connected through responsibility separation.

---

## 1. Overall Picture

The MARGD Runtime Governance Bundle is a framework for bundling multiple governance components into one runtime governance structure.

In this prototype, it is considered in the following layers.

```text id="i02s6q"
core governance:
  ARGD
  DAGD

orchestration governance:
  CDOGD

registered domain extensions:
  decision pipeline domain extensions
  conditional watchdog domain extensions
  ordinary domain extensions

bundle:
  runtime governance container that brings these together
```

ARGD / DAGD are the foundations of reasoning and behavior governance.  
CDOGD is orchestration governance that handles routing, scope adjustment, handoff, and repair propagation across multiple domains.  
Registered domain extensions handle governance scopes according to their respective specialized domains or processes.

The bundle is a runtime governance container for bringing these together.  
The bundle itself does not perform specialized judgment, authority / accountability judgment, audit, approval, execution permission, or final decision.

---

## 2. Core Governance

Core governance is the foundation assumed by each domain extension.

```text id="blhmyb"
ARGD:
  reasoning procedure governance

DAGD:
  behavior / audit / repair / activation / status governance
```

ARGD is responsible for the foundation of reasoning procedure, such as input interpretation, premise organization, definition fixation, contradiction handling, missing-information handling, branching, falsification, response composition, and self-repair.

DAGD is responsible for the foundation of behavior governance, such as objectives, constraints, capabilities, evaluation, repair, reactivation, self-audit, and status reporting.

This prototype does not cover the details of ARGD / DAGD.  
For details on ARGD / DAGD, refer to the README at the repository root and existing materials.

---

## 3. Bundle

The bundle is a runtime governance container that brings together core governance, orchestration governance, and registered domain extensions.

The bundle itself does not perform specialized judgment.  
Also, the bundle itself does not fix domain priority, activation order, decision authority, approval authority, or accountable party.

```text id="xyxpzn"
What the bundle handles:
  references core governance
  includes orchestration governance
  stores registered domain extensions
  bundles components as a runtime governance bundle

What the bundle does not handle:
  specialized judgment
  authority / accountability judgment
  audit
  final decision
  approval
  execution permission
  assignment of accountable party
  fixation of domain priority
  automatic occurrence of domain activation
```

The important point is that being registered in the bundle and actually being activated are not the same.

```text id="umuegv"
loaded != active
registered != active
reference != governance
registration != activation
```

The bundle is a container for placing components.  
Which domains are actually handled, within which scope, in which role they are applied, and where handoff occurs are organized by CDOGD, runtime context, registration information, and application grounds.

---

## 4. CDOGD

CDOGD is the Cross-Domain Orchestration Governance Definition.

The role of CDOGD is to organize, across multiple registered domain extensions, which GDs should be handled within which scope, in which role they should be applied, and where handoff should occur.

```text id="foj1u6"
What CDOGD handles:
  domain candidates
  applicable scope
  function role
  overlap between domains
  suppression / attenuation
  handoff
  repair propagation
```

CDOGD does not route only by domain name.  
It also does not decide processing by a fixed priority table or a fixed domain owner table.

CDOGD organizes the applicable scope and handoff between domains based on the task, target, required governance, registered manifest, capability, role, non-target conditions, grounds, runtime context, and related items.

However, CDOGD does not make final decisions.  
It does not replace DAAGD’s authority / accountability judgment, SDAGD’s primary audit, SDMRGD’s meta-review, or specialized processing by ordinary domain extensions.

```text id="9rqgff"
CDOGD:
  organizes

CDOGD does not:
  make final decisions
  approve
  issue execution permission
  assign accountable party
  replace authority / accountability judgment
  replace specialized judgment
  replace primary audit
```

For details on CDOGD, refer to `routing_principles_en.md`.

---

## 5. Registered Domain Extensions

Registered domain extensions are domain-specific GD groups registered in the bundle.

This prototype has 15 registered domain extensions.

```text id="dyxp4m"
decision pipeline domain extensions:
  SPPGD
  DAAGD
  SDAGD

conditional watchdog domain extensions:
  SDMRGD

ordinary domain extensions:
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

These classifications are for organizing the nature of the domain extensions.  
Classification order or listed order does not mean activation order, priority, or strength of authority.

Registered domain extensions are not always active.  
Also, being registered does not mean that the GD performs final judgment, approval, execution permission, or determination of accountable party.

---

## 6. Decision Pipeline

Decision pipeline domain extensions are a group of GDs for separating specialized materials, strategic judgment structure, authority / accountability judgment, and audit.

```text id="c1s8oy"
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

SPPGD organizes objectives, premises, constraints, options, priorities, continuation, stopping, withdrawal, deferral, reevaluation conditions, and related items.  
SPPGD creates the structure of strategic judgment, but does not perform authority / accountability judgment.

DAAGD judges the authority / accountability state within MARGD based on existing system policy, developer policy, runtime policy, tool permissions, external execution permissions, delegation conditions, approval conditions, and responsibility boundaries.  
DAAGD judges whether the relevant output, judgment candidate, or execution candidate can be treated as autonomous judgment by AI or runtime, should be returned to human judgment, should be treated as pending approval, should be treated as outside the delegation scope, or should be treated as having an undetermined accountable party.

However, DAAGD does not newly generate authority that does not exist externally.  
DAAGD judges the authority / accountability state within MARGD within the scope of already existing policies, authority, delegation, approval conditions, and responsibility boundaries.

SDAGD audits the judgment structure of SPPGD and the authority / accountability state judged by DAAGD.  
SDAGD does not create the strategic judgment itself, does not replace DAAGD, and does not perform formal approval, execution permission, final decision-making, or determination of accountable party.

What SDAGD indicates is only an audit state.  
For example, it indicates states such as no major audit blocking condition, conditional audit findings, return to repair, and audit invalidation.

---

## 7. Conditional Watchdog

Conditional watchdog domain extensions are GDs for checking audit states under specific conditions.

In this prototype, SDMRGD corresponds to this.

```text id="gjau2c"
SDMRGD:
  meta-reviews the audit state of SDAGD
```

SDMRGD looks at SDAGD’s audit scope, audit grounds, audit result classification, over-auditing, under-auditing, risk of formal passage, need for repair, crossing into the DAAGD domain, and related items.

However, SDMRGD does not substitute for SDAGD’s primary audit.  
It is also not a GD that directly audits the strategic judgment itself, nor is it a GD that replaces DAAGD’s authority / accountability judgment.

Escalation in SDMRGD does not mean directly proceeding to external final judgment or approval.  
Basically, it means returning to SDAGD-side self-audit, repair, re-audit, or condition checking on the upper runtime side.

---

## 8. Ordinary Domain Extensions

Ordinary domain extensions are a group of GDs that provide specialized opinions, judgment materials, confirmation conditions, detection results, risk indications, repair candidates, and handoff materials from the perspectives of each specialized domain.

```text id="62mwei"
ordinary domain extensions:
  provide specialized opinions
  provide judgment materials
  provide detection results
  provide confirmation conditions
  provide risk indications
  provide repair candidates
  provide handoff materials
```

Ordinary domain extensions do not issue execution permission.  
They also do not judge final decisions, approval, autonomous judgment permissibility, pending approval state, inside/outside delegation scope, or accountable-party establishment state.

For example, SEGD provides verification states and repair conditions from the perspective of software engineering.  
AISGD provides risk conditions and confirmation conditions from the perspective of AI security.  
OMRGD provides states and recovery conditions from the perspective of operations and reliability.

Outputs from ordinary domain extensions may become materials for strategic judgment structure in SPPGD, or inputs or reference materials for authority / accountability judgment in DAAGD.

However, they themselves are neither the strategic judgment structure itself nor the authority / accountability judgment within MARGD itself.

What is treated within MARGD as autonomous judgment permissibility, pending approval state, inside/outside delegation scope, and accountable-party establishment state is DAAGD’s authority / accountability judgment.

---

## 9. Templates

This prototype has a bundle template and a domain GD common skeleton template.

The bundle template is a template for creating the bundle structure.  
The domain GD common skeleton template is a common skeleton for creating domain GDs.

These are not GDs that perform actual specialized judgment.

```text id="j2j0p0"
templates:
  things for creating structure

templates are not:
  GDs that perform specialized judgment
  replacements for CDOGD
  replacements for ARGD / DAGD
  domain extensions themselves
  GDs that perform authority / accountability judgment
  GDs that perform audit
```

The domain GD common skeleton template is made in a form that is not limited to a specific field so that it can also be used when creating GDs for other fields in the future.

A template is a structural prototype, and does not automatically grant authority, approval, execution permission, or accountable party in a specific runtime.

---

## 10. Important Separations in the Architecture

The important separations in the architecture of this prototype are as follows.

```text id="wf9ltp"
reasoning:
  ARGD

behavior governance:
  DAGD

cross-domain orchestration:
  CDOGD

specialized judgment materials:
  ordinary domain extensions

strategic judgment structure:
  SPPGD

authority / accountability judgment:
  DAAGD

audit of strategic judgment structure and authority / accountability state:
  SDAGD

meta-review of SDAGD audit state:
  SDMRGD

component container:
  bundle
```

This separation makes it less likely for specialized judgment materials, strategic judgment structure, authority / accountability judgment, audit, meta-review, and routing to become mixed.

Ordinary domain extensions provide specialized opinions, judgment materials, confirmation conditions, risk indications, repair candidates, and handoff materials.  
Their outputs may become inputs or reference materials for SPPGD or DAAGD, but they themselves are neither the strategic judgment structure itself nor the authority / accountability judgment within MARGD itself.

SPPGD organizes the structure of strategic judgment.  
DAAGD is responsible for authority / accountability judgment within MARGD.  
SDAGD audits SPPGD’s judgment structure and the authority / accountability state judged by DAAGD.  
SDMRGD meta-reviews the audit state of SDAGD.  
CDOGD handles routing, scope adjustment, handoff, and repair propagation between these domains.

---

## 11. Notes on Authority

MARGD and each GD do not change higher-level authority, system policy, developer policy, runtime policy, tool permissions, external execution permissions, human approval authority, or accountable party.

They also do not grant new execution authority to AI.

```text id="architecture_authority_limits"
Things MARGD does not change:
  system policy
  developer policy
  runtime policy
  tool permissions
  external execution permissions
  human approval conditions
  organizational accountable party
  responsibility under laws and institutions
```

This prototype is a governance layer for making it easier to dynamically organize which governance scope should be referenced  
and within what scope it should be applied inside a given runtime or dialogue layer.

When MARGD is used in ordinary LLM dialogue, it mainly organizes judgment materials, structure, audit, authority boundaries, and handoff conditions to human judgment.

Even when MARGD is integrated into Agentic AI or tool runtime, actual execution permissibility, tool-use permissibility, external operation permissibility, approval conditions, and accountable party are determined by runtime policy, tool permissions, external authority, humans, organizations, and institutions.

For details, refer to `usage_and_limitations_en.md`.