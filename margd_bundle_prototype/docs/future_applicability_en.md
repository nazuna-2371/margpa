# Future Applicability

This document explains the future applicability of the MARGD Runtime Governance Bundle Prototype.

The current prototype is an initial configuration oriented toward AI development, AI research, AI structural design, software engineering, operations, model policy, Agentic AI, AI security, decision authority, audit, and related areas.

However, the structure of MARGD is not dedicated only to AI development.  
The concepts of the bundle, CDOGD, and the domain GD common skeleton template can also be applied to governance sets in other fields.

---

## 1. Positioning of the Current Prototype

The current prototype is a runtime governance bundle oriented toward AI development.

It mainly handles the following targets.

```text id="9noa8h"
Current main targets:
  AI development
  AI research
  AI structural design
  software engineering
  operations, maintenance, and reliability
  model policy
  Agentic AI
  AI security risks mediated through AI
  decision authority
  strategic judgment
  audit
  meta-review
```

This is one application example of MARGD.  
MARGD itself is not limited only to AI development.

---

## 2. Basic Policy for Application

When applying MARGD to another field, the important point is not to forcibly expand existing GDs.

A dedicated GD should be created for a new field.

```text id="43jp6l"
Basic policy:
  do not forcibly absorb into existing GDs
  create a new GD for a new field
  organize cross-domain handling through CDOGD
  separate judgment materials from decision authority
  separate specialized judgment from final responsibility
  do not mix audit and meta-review
```

For example, when handling AI illustration production, everything should not be forced into AIAGD or ACRGD.  
AI illustration has its own governance targets, such as composition, style, generation conditions, rights, revision history, requester intent, and publication permissibility.

In such cases, it is better to create a separate GD for AI illustration.

---

## 3. Why It Can Be Applied

MARGD is not a mechanism for directly producing answers in a specific field.

What MARGD handles is mainly structures such as the following.

```text id="uqjeyi"
Things MARGD can handle easily:
  which perspective to use
  within which scope to use it
  which GD to hand off to
  which judgment materials are necessary
  which judgments should be handed off to another GD
  where to return to human judgment
  where audit is necessary
  where repair is necessary
```

For this reason, even when the specialized field changes, the separation structure of governance can be used.

The specialized content itself is handled by GDs for each field, while cross-domain activation, handoff, suppression, and organization of overlaps are handled by CDOGD.  
Authority / accountability judgment within MARGD is handled by DAAGD.  
DAAGD judges whether something can be treated as autonomous judgment, should be returned to human judgment, should be treated as pending approval, should be treated as outside the delegation scope, or should be treated as having an undetermined accountable party.  
However, formal approval, external execution permissibility, legal responsibility, and organizational responsibility follow runtime policy, humans, organizations, institutions, and external authority holders.

---

## 4. Candidate Applications

In the future, as examples, it may be possible to apply it to fields such as the following.

```text id="lxrybm"
Candidate applications:
  creator-related fields
  AI illustration-related fields
  emotional fields
  artistic production fields
  education-related fields
  story production fields
  interpersonal support fields
  medical support fields
```

These are only candidate applications.  
When actually using it, GDs suited to each field, expert confirmation, institutional constraints, and organization of accountable parties will be necessary.

For detailed usage notes and limitations, refer to `usage_and_limitations_en.md`.

---

## 5. Application to Creator-Related Fields

In creator-related fields, a GD that handles production intent, target readers, expression policy, medium, publication purpose, revision history, rights-related notes, and related items can be considered.

```text id="k3zpuf"
Things that may be handled in creator-related fields:
  production intent
  target readers
  expression policy
  medium
  publication purpose
  revision policy
  reference materials
  rights-related notes
  pre-publication confirmation
```

In this case, ACRGD may be related to confirmation of artifact composition.  
However, creator-related fields as a whole should not be absorbed into ACRGD.

This is because creator-related fields include elements such as work quality, intent, expression choices, and publication context that cannot be handled only by artifact composition.

---

## 6. Application to AI Illustration-Related Fields

In AI illustration-related fields, a GD that handles generation intent, style, composition, placement of people and objects, revision history, generation conditions, publication permissibility, consistency with the request, and related items can be considered.

```text id="qmgxee"
Things that may be handled in AI illustration-related fields:
  generation intent
  request content
  style
  composition
  color tone
  placement of people
  placement of objects
  revision history
  generation conditions
  publication permissibility
  rights-related notes
```

AI illustration-related fields are neither AI structural design, software engineering, nor mere artifact composition.  
Therefore, it is more natural to create a dedicated GD for AI illustration.

Also, when people, authorship, rights, publication scope, requester intent, and related items are involved, it is necessary to hand off to another GD or human confirmation.

---

## 7. Application to Emotional or Empathy-Related Fields

In emotional fields, a GD that handles emotional state, how words are received, empathy, sense of safety, distance, encouragement, de-escalation, risk of over-involvement, and related items can be considered.

```text id="yw04lb"
Things that may be handled in emotional fields:
  emotional state
  how it is received
  empathy
  sense of safety
  distance
  encouragement
  de-escalation
  risk of over-involvement
  risk of dependency
  handoff to human support
```

Emotional fields are not simply about writing kind text.  
It is necessary to handle the other person’s state, relationship, context, distance, and the limits of support.  
It is also necessary to sufficiently consider AI dependency.

Emotional support is not a substitute for expert support or emergency response.  
When necessary, it must be handed off to humans, experts, or appropriate support contacts.

---

## 8. Application to Artistic Production Fields

In artistic production fields, a GD that handles work intent, form, materials, composition, repetition, variation, critique, exhibition, presentation context, and related items can be considered.

```text id="9htq2d"
Things that may be handled in artistic production fields:
  work intent
  expression form
  materials
  composition
  repetition
  variation
  critique perspectives
  exhibition context
  presentation context
  production history
```

In artistic production, there are many cases where there is no single correct answer.  
Therefore, a GD that handles intent, context, constraints, reasons for choices, alternatives, and presentation is necessary rather than simple quality judgment.

An artistic-production GD should be designed not as something that makes the final decision on the value of a work, but as something for organizing production judgment.

---

## 9. Application to Education-Related Fields

In education-related fields, a GD that handles learning objectives, level of understanding, prerequisite knowledge, granularity of explanation, practice, misunderstandings, evaluation, support scope, and related items can be considered.

```text id="69ddh9"
Things that may be handled in education-related fields:
  learning objectives
  prerequisite knowledge
  level of understanding
  granularity of explanation
  examples
  practice
  misunderstandings
  evaluation
  review
  support scope
```

In education-related fields, it is necessary not only to give answers, but also to adjust them into a form that the learner can understand.  
Also, perspectives such as exams, assignments, grade evaluation, fraud prevention, and individualized support are involved.

An education-related GD organizes the structure of learning support and does not substitute for teachers, schools, or institutional evaluation.

---

## 10. Application to Story Production Fields

In story production fields, a GD that handles worldbuilding, characters, objectives, conflict, development, foreshadowing, style, aftertaste, consistency, revision history, and related items can be considered.

```text id="b4tz12"
Things that may be handled in story production fields:
  worldbuilding
  characters
  objectives
  conflict
  development
  foreshadowing
  style
  aftertaste
  consistency
  revision history
  assumed readers
```

In story production, not only logical consistency but also emotional flow, reader expectations, how information is presented, lingering impression, and related items become important.

A story-production GD is for organizing creative judgment about a work, not for producing a single correct answer.

---

## 11. Application to Interpersonal Support Fields

In interpersonal support fields, a GD that handles consultation content, relationships, support scope, danger signs, limits of advice, handoff to human support, and related items can be considered.

```text id="dy5hok"
Things that may be handled in interpersonal support fields:
  consultation content
  relationship
  support scope
  danger signs
  limits of advice
  risk of over-involvement
  risk of dependency
  handoff to human support
  need for records
```

In interpersonal support fields, both staying close to the other person and not stepping in too far are important.  
It is also necessary to detect situations where AI should not handle the matter and hand off to humans or expert institutions.

An interpersonal-support GD does not substitute for human relationships, psychological support, emergency response, or expert support.

---

## 12. Application to Medical Support Fields

In medical support fields, a GD that handles symptom information, consultation guidelines, consultation with medical institutions, confirmation of medication information, danger signs, urgency, handoff to human experts, and related items can be considered.

```text id="b7938f"
Things that may be handled in medical support fields:
  symptom information
  course
  medical history
  medication information
  consultation guidelines
  danger signs
  urgency
  consultation with medical institutions
  handoff to experts
  need for records
```

Medical support fields need to be handled especially carefully.  
MARGD and GDs do not substitute for diagnosis, treatment, prescription, or final medical judgment.

When applying it to medical support, it is necessary to clearly separate medical experts, institutions, laws and regulations, safety responsibility, accountability, and emergency response.

For detailed notes, refer to `usage_and_limitations_en.md`.

---

## 13. Important Separations During Application

When applying it to a new field, the following separations are important.

```text id="df75rg"
Things to separate:
  specialized judgment materials
  judgment structure
  decision authority
  approval
  accountable party
  audit
  meta-review
  handoff to human judgment
```

A specialized GD provides specialized judgment materials, confirmation conditions, risk indications, repair candidates, and handoff materials.

Those outputs may become materials for strategic judgment structure in SPPGD, or inputs or reference materials for authority / accountability judgment in DAAGD.

However, they themselves are neither the strategic judgment structure itself nor the authority / accountability judgment within MARGD itself.

What is treated within MARGD as autonomous judgment permissibility, pending approval state, inside/outside delegation scope, and accountable-party establishment state is DAAGD’s authority / accountability judgment.  
Formal approval, external execution permissibility, legal responsibility, and organizational responsibility follow runtime policy, humans, organizations, institutions, and external authority holders.

This is the same even in fields other than AI development.

---

## 14. Things to Avoid During Application

When applying MARGD, the following kinds of usage should be avoided.

```text id="6c07aj"
Things to avoid:
  forcibly absorbing new fields into existing GDs
  mixing specialized judgment with decision authority
  treating AI output as-is as final judgment
  turning audit into a formal ceremony of passage
  handling situations that require human confirmation with AI alone
  substituting experts in areas where experts are necessary
  leaving the accountable party ambiguous
```

In particular, in medicine, law, educational evaluation, interpersonal support, psychological support, rights handling, and high-public-impact judgments, organization of experts, institutions, and accountable parties is necessary.

For details, refer to `usage_and_limitations_en.md`.

---

## 15. Summary

The current prototype is configured toward AI development.  
However, the basic structure of MARGD may be applicable beyond AI development.

In the future, expansion into creator-related fields, AI illustration-related fields, emotional fields, artistic production fields, education-related fields, story production fields, interpersonal support fields, medical support fields, and related areas can be considered.

However, when applying it, a dedicated GD for that field should be created.  
Instead of forcibly absorbing it into existing GDs, it is necessary to clearly separate responsibilities, limits, judgment materials, and handoff conditions for each specialized domain.

MARGD does not substitute for experts, institutions, approvers, or accountable parties.  
For usage notes and limitations, refer to `usage_and_limitations_en.md`.