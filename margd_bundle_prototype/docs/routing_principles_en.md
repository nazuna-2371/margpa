# Routing Principles

This document explains the concept of routing in the MARGD Runtime Governance Bundle Prototype.

Here, routing refers to the concept of organizing which GD should be made to work, within which scope, and in which role.  
This does not mean execution permission, approval, determination of accountable party, or final decision.

---

## 1. Basics of Routing

In this prototype, simply having a GD included in the bundle does not mean that the GD is always active.

```text id="3r9jaf"
loaded != active
registered != active
reference != governance
registration != activation
```

A GD being registered in the bundle and that GD becoming active for the current task are separate matters.  
Also, a GD being referenceable and that GD having decision authority are separate matters.

The purpose of routing is to organize which GDs are necessary for the current task, within which scope, in which role they are involved, and where handoff should occur.

---

## 2. Role of CDOGD

CDOGD is an orchestration GD for bringing multiple GDs together across domains.

CDOGD does not select GDs only by domain name or fixed order.  
It also does not decide processing by a fixed priority table or a fixed owner-domain table.

```text id="5dba3a"
What CDOGD sees:
  task content
  target
  required governance
  registered manifest
  capability
  role
  non-target conditions
  grounds
  runtime context
```

Based on these, CDOGD organizes which GDs should be handled within which scope, in which role they should be involved, and where suppression, attenuation, handoff, or repair propagation should occur.

However, CDOGD does not make final decisions.  
CDOGD does not replace approval, execution permission, assignment of accountable party, authority / accountability judgment, or specialized judgment itself.

---

## 3. Routing Is Not Authority Granting

Even if routing organizes that a certain GD is relevant to the current task, that does not mean authority granting.

```text id="52zprf"
routing does not mean:
  execution permission
  final decision
  approval
  assignment of accountable party
  addition of tool permissions
  addition of external execution permissions
```

Activation or reference of a GD is only the selection of governance scope.  
It is for organizing which perspectives to refer to, within which scope to confirm, and which GD to hand off to.

For authority boundaries in usage, refer to `usage_and_limitations_en.md`.

---

## 4. Not a Fixed Order

In this prototype, GD classification or listed order does not mean priority or activation order.

```text id="0k32nk"
bucket order != priority
file order != priority
registry order != priority
domain name != routing result
```

For example, a GD placed under `ordinary/` is not necessarily deferred.  
Also, a GD placed under `decision_pipelines/` does not always work first.

Routing is determined according to the current task, target, grounds, required governance, and runtime context.

---

## 5. Do Not Decide by Domain Name Alone

CDOGD does not route only by domain name or keyword.

For example, the mere presence of the word “security” in a task does not necessarily make AISGD the primary actor.  
The mere presence of the word “architecture” also does not necessarily make AIAGD the primary actor.

What matters is what the task is trying to handle.

```text id="g3ijlu"
Things to see:
  what the target is
  what is being judged
  what is being output
  which specialized perspectives are necessary
  which judgment materials are necessary
  whether authority / accountability judgment is necessary
  whether audit is necessary
  whether it needs to return to human judgment
```

A domain name can be a clue, but it alone does not determine routing.

---

## 6. Why Routing Works and the Design Emphasis

One prerequisite for this routing to work is to avoid making routing logic depend as much as possible on proper nouns or fixed values such as domain names, component ids, file names, bucket names, registry order, fixed owners, or fixed priority.

Hardcoding is avoided as much as possible, and abstraction is applied.

If proper-name branches are added every time GDs increase, names change, similar-domain GDs are added, runtime context changes, or roles change, routing logic quickly becomes unmaintainable.

For this reason, in this prototype, hardcoding that cannot be avoided for identification, reference, records, and version management is retained, while parts that can be abstracted are abstracted as much as possible.

What routing should see is not the name itself, but what the GD can handle, what it does not handle, whether it is necessary for the current task, within which scope it is involved, in which role it works, where suppression, attenuation, or handoff is necessary, and what grounds exist.

In other words, IDs and similar items are name tags, not routing judgment itself.  
In MARGD, what is seen is not the name tag, but the duty definition, applicable scope, non-target conditions, runtime context, and grounds.

---

## 7. Function Role

Even when a GD is activated, that GD does not always become the primary actor.

The same GD can have different roles depending on the task.

```text id="5ajhpd"
role examples:
  primary
  supporting
  validation
  reference
  suppressed
```

For example, SEGD may become the primary actor, or it may become a supporting actor that confirms judgment materials for AIAGD.  
AISGD may become the primary actor, or it may be only a supporting actor where AI security risk is lightly related.

Function role is determined per task.  
It is not determined only by the GD’s registered location or file order.

---

## 8. Routing of Ordinary Domain Extensions

Ordinary domain extensions are a group of GDs that provide specialized opinions, judgment materials, detection results, confirmation conditions, risk indications, repair candidates, and handoff materials from the perspectives of each specialized domain.

```text id="1hqgfq"
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

For example, DSGD confirms analytical validity from the perspective of data science.  
SEGD confirms verification states and repair conditions from the perspective of software engineering.  
OMRGD confirms states and recovery conditions from the perspective of operations and reliability.

Outputs from ordinary domain extensions may become materials for strategic judgment structure in SPPGD,  
or inputs or reference materials for authority / accountability judgment in DAAGD.

However, they themselves are neither the strategic judgment structure itself nor the authority / accountability judgment within MARGD itself.

What is treated within MARGD as autonomous judgment permissibility, pending approval state, inside/outside delegation scope, and accountable-party establishment state is DAAGD’s authority / accountability judgment.

---

## 9. Position of DAAGD

DAAGD is a GD responsible for authority / accountability judgment within MARGD.

Based on existing system policy, developer policy, runtime policy, tool permissions, external execution permissions, delegation conditions, approval conditions, and responsibility boundaries,  
DAAGD judges whether the relevant output, judgment candidate, or execution candidate can be treated as autonomous judgment by AI or runtime, should be returned to human judgment, should be treated as pending approval, should be treated as outside the delegation scope, or should be treated as having an undetermined accountable party.

```text id="mg21co"
What DAAGD sees:
  whether AI judgment remains advice
  whether it is judgment support
  whether it is a provisional recommendation
  whether it is a conditional judgment
  whether it is a delegated judgment
  whether it is an autonomous execution decision
  whether it should be returned to human judgment
  whether it should be treated as pending approval
  whether it is inside or outside the delegation scope
  whether the accountable party is established or undetermined
  whether record conditions are satisfied
```

However, DAAGD does not newly generate authority that does not exist externally.  
DAAGD judges the authority / accountability state within MARGD within the scope of already existing policies, authority, delegation, approval conditions, and responsibility boundaries.

---

## 10. Handoff to the Decision Pipeline

In routing, judgment materials may be handed off from ordinary domain extensions to the decision pipeline.

A typical flow is as follows.

```text id="d8kntj"
ordinary domain extensions:
  provide specialized judgment materials, confirmation conditions, risk indications, repair candidates, and handoff materials

SPPGD:
  treats materials handed off from ordinary GDs and others as materials for strategic judgment structure
  organizes objectives, premises, constraints, options, priorities, continuation, stopping, withdrawal, reevaluation conditions, and related items

DAAGD:
  is responsible for authority / accountability judgment within MARGD
  judges whether it can be treated as autonomous judgment, should be returned to human judgment, is pending approval, is outside the delegation scope, or has an undetermined accountable party

SDAGD:
  audits the judgment structure of SPPGD and the authority / accountability state judged by DAAGD

SDMRGD:
  meta-reviews the audit state of SDAGD
```

This flow is not a fixed pipeline.  
Depending on the task, only some GDs may be relevant.

What matters is not to mix specialized judgment materials, strategic judgment structure, authority / accountability judgment, audit, and meta-audit.

---

## 11. Scope of Activation

Even when a GD is activated, all functions of that GD do not always work.

```text id="kz4z02"
activation is scope-limited:
  only the scope necessary for the current task works
  only the necessary function role is held
  unnecessary parts do not work
  weakly related GDs remain as reference
  unrelated GDs do not activate
```

For example, even if AISGD is relevant, it is not necessarily necessary to cover all AI security perspectives.  
Even if SEGD is relevant, it is not necessarily necessary to handle the entirety of software engineering.

GD activation is task-local.

---

## 12. Reevaluation

Routing does not end once it has been decided.

If the task premises, target, constraints, risk, output requirements, or authority / accountability state change, the relevant GDs also change.

```text id="0wbp8f"
Examples where reevaluation becomes necessary:
  the target changed
  the premises changed
  the constraints changed
  the risk changed
  the output format changed
  human approval became necessary
  execution judgment became relevant
  audit became necessary
```

For this reason, domain activation is not a one-time fixed state.  
It is reevaluated within the necessary scope according to changes in the task or context, and is called again as necessary.

---

## 13. Summary

Routing in this prototype is not determined by fixed order or domain names.  
CDOGD organizes which GDs to handle within which scope and in which role to involve them, based on the task, target, required governance, registered manifest, capability, role, grounds, and runtime context.

However, routing is not authority granting.  
Even if a GD is activated, AI execution authority, tool permissions, external operation permissions, human approval, and accountable party do not change.

Ordinary domain extensions provide specialized opinions, judgment materials, confirmation conditions, risk indications, repair candidates, and handoff materials.

Outputs from ordinary domain extensions may become materials for strategic judgment structure in SPPGD,  
or inputs or reference materials for authority / accountability judgment in DAAGD.  
However, they themselves are neither the strategic judgment structure itself nor the authority / accountability judgment within MARGD itself.

What is treated within MARGD as autonomous judgment permissibility, pending approval state, inside/outside delegation scope, and accountable-party establishment state is DAAGD’s authority / accountability judgment.

For detailed usage notes and limitations, refer to `usage_and_limitations_en.md`.