# Appendix: Inference-Time Governance Hypothesis for MARGPA / MARGD

This appendix is a provisional organization for treating MARGPA / MARGD not as a “convenient prompt collection,”  
but as an inference-time governance specification for existing LLMs.

Here, inference-time governance refers to the idea of providing, as an external syntax referenced during response generation without changing model weights or training data,  
judgment structure, branch preservation, uncertainty handling, context preservation, authority boundaries, audit, repair, and domain scope adjustment.

This is not a one-off prompt for directly generating a specific response text.

What MARGPA / MARGD aims at is not fixing the wording of individual responses,  
but externally defining a response governance structure: what kind of judgment procedure should be used to compose a response, where to stop, where to preserve branches, and where to hand off to human judgment or another domain during response generation.

---

## A.1. Premises

MARGPA / MARGD does not change model weights, training data, built-in safety layers, system policy, developer policy, or external execution permissions.

When given to an existing LLM as input text, its effect is, in principle, limited to runtime instruction / governance context interpreted within the context.

Therefore, MARGPA / MARGD does not claim the following.

```text
What MARGPA / MARGD does not claim:
  modification of model-internal structure
  modification of model weights
  modification of training data
  override of system policy / developer policy
  disabling of built-in safety layers
  granting of external execution permissions
  granting of professional qualifications
  guarantee of response correctness
  automatic or always-on establishment of domain activation
  acquisition of final decision authority by AI
```

On the other hand, even when given as input text, it may affect the judgment style during response generation, preservation of branches, handling of uncertainty, preservation of context, suppression of overstatement, and presentation of authority boundaries.

This appendix concerns a hypothesis about that inference-time behavior.

---

## A.2. What MARGPA / MARGD Provides

What MARGPA / MARGD provides to existing LLMs is not specialized knowledge of a specific domain itself.

For example, it does not newly inject specialized knowledge such as medicine, law, software engineering, AI security, or data science into the model internals.

Rather, what it may provide is governance grammar for constructing responses.

```text
Examples of governance grammar:
  scope control
  premise preservation
  branch preservation
  uncertainty handling
  assumption separation
  evidence-to-claim separation
  failure-mode detection
  authority boundary awareness
  audit posture
  repair posture
  context-conditioned domain scope adjustment
```

This grammar does not directly specify a particular answer.

It is an external syntax for organizing what scope should be answered within, where uncertainty should be preserved, which judgments should be handed off to another domain, where to return to human judgment, and which claims lack sufficient grounds.

---

## A.3. Distinguishing “Prompt” from “Prompt Collection”

Because MARGPA / MARGD is given to an existing LLM as input, it is prompt-native in a broad sense.

However, calling it a “convenient prompt collection” misses its structural essence.

Just as a program is not merely a collection of strings simply because it is stored as text,  
MARGPA / MARGD is also designed functionally as a runtime governance specification, even though its input form is text.

It can be organized as follows.

```text
input layer:
  prompt / context

representation layer:
  JSON / natural language specification

functional layer:
  inference-time runtime governance specification

structural layer:
  governance component
  domain registry
  activation policy
  routing policy
  audit / repair policy

operational layer:
  AI behavior
  scope adjustment
  handoff
  audit
  authority boundary
  repair control
```

Therefore, a more precise expression would be as follows.

```text
MARGPA / MARGD is prompt-native,
but not merely a prompt collection.

It is a text-encoded inference-time runtime governance specification
for LLM / AI behavior.
```

---

## A.4. Dynamic Application Hypothesis

When MARGPA / MARGD is given to an existing LLM as input, the expected maximum effect is not the fixation of a specific response, but the dynamic transformation of the response judgment style.

That is, even for unknown or unregistered topics, the LLM may use the given governance grammar to perform processes such as the following.

```text
Hypothetical processes:
  extract a task frame from the input context
  separate the judgment target, scope, constraints, and risk
  separate observation, inference, assumption, and evaluation
  preserve branches when uncertainty exists
  avoid excessive convergence to a single conclusion
  adjust the boundaries among assertion, advice, reservation, refusal, and handoff
  make the authority / accountability boundary explicit
  self-check drift / overreach / under-specification after the response
```

If this behavior is reproducible, MARGPA / MARGD may be functioning not merely as task-specific prompt engineering, but as domain-independent response governance grammar.

What matters here is not the addition of specific domain knowledge, but whether the response governance structure transfers even to topics outside the domain.

---

## A.5. Observable Response Changes

As a provisional observation, even when a specialized scope for a specific domain has not been explicitly added, the following kinds of changes in response structure may appear.

```text
Observable changes:
  separation of observation, inference, assumption, and evaluation
  suppression of single-conclusion collapse under insufficient information
  preservation of conditional branches
  suppression of overstatement
  suppression of ungrounded expressions of certainty
  suppression of excessive safety-template behavior
  practical boundary presentation according to user context
  transfer of governance grammar to out-of-domain topics
  increase in post-response self-audit and repair posture
```

However, these are currently observational hypotheses, not demonstrated performance.

MARGPA / MARGD does not necessarily produce this effect at all times.
Behavior may also vary depending on the model, context length, task, instruction conflicts, system policy, developer policy, and conversation history.

---

## A.6. Relationship with Domain Activation

Domain activation in MARGPA / MARGD is not something that activates automatically simply by looking at the domain name.

Domain activation is established within the necessary scope according to the task, target, required governance, scope, capability, non-target condition, runtime context, and grounds.

Therefore, even when given to an existing LLM as input text, the desirable behavior is not that “all domains are always activated.”

What is desirable is that only the necessary perspectives are involved task-locally, unnecessary domains are suppressed, weakly related domains remain as reference, and handoff or repair occurs when necessary.

```text
Desirable activation:
  task-local
  scope-limited
  role-sensitive
  context-conditioned
  evidence-aware
  suppressible
  repairable
```

Conversely, if activation is established solely by domain name, component id, registry order, bucket name, or fixed priority, that deviates from the design intent of MARGD.

---

## A.7. Metrics to Evaluate

When verifying this hypothesis, simple accuracy is not sufficient.

The evaluation target is not only the presence or absence of knowledge, but changes in response structure.

Candidate evaluation metrics include the following.

```text
Candidate evaluation metrics:
  branch preservation rate
  uncertainty disclosure rate
  unsupported certainty rate
  fact / inference / assumption / evaluation separation rate
  context preservation rate
  premise drift rate
  over-safety-template rate
  under-safety-risk rate
  authority overreach rate
  domain over-activation rate
  domain under-activation rate
  repair visibility rate
  handoff appropriateness rate
  response usefulness under uncertainty
```

What is especially important is not only domain-knowledge scope adjustment, but whether structural transfer occurs for out-of-domain topics.

It is also necessary to evaluate not only improvements, but side effects.

```text
Side effects to evaluate:
  excessive structuring
  slower responses
  unnecessary reservation
  unnecessary audit expressions
  excessive branch preservation
  complication of tasks that should be simple
  malfunction of domain activation
```

---

## A.8. Limitations

At present, the claims in this appendix are hypotheses and not demonstrated performance improvements.

At least the following remain unverified.

```text
Unverified items:
  whether it reproduces across models
  whether it remains stable across sessions
  whether it avoids drift in long contexts
  whether it remains stable under instruction conflicts
  whether response safety and validity actually improve in specialized domains
  whether excessive structuring degrades response quality
  whether domain activation malfunctions
  whether emotional or personal contexts interfere with technical domains
  whether authority boundary works excessively or insufficiently
  whether it is confused with external authority during runtime / tool use
```

Therefore, the current position of MARGPA / MARGD is not “a safety mechanism whose effects have been demonstrated.”

More precisely, it is “an experimental specification that provides inference-time runtime governance as external syntax.”

---

## A.9. Implementation Notes

When inputting MARGPA / MARGD into an existing LLM, it is necessary to always distinguish the following.

```text
Things to distinguish:
  model behavior and model capability
  governance context and system policy
  domain activation and external authority
  audit state and approval
  repair suggestion and execution permission
  handoff condition and human approval
```

Even if MARGPA / MARGD may change the response style, that does not mean the model’s capabilities, authority, qualifications, or external operation permissions have increased.

In particular, in areas such as medicine, law, finance, educational evaluation, interpersonal support, AI security, and external tool execution, organization by MARGPA / MARGD is not a substitute for experts, organizations, institutions, runtime policy, or human approval.

---

## A.10. Provisional Conclusion

MARGPA / MARGD can be used as a prompt in a broad sense.

However, its design target is not the improvement of one-off outputs, but the structuring of LLM response judgment style, scope, branching, uncertainty, authority boundaries, audit, repair, and domain scope adjustment.

If branch preservation, uncertainty handling, overstatement avoidance,  
authority boundary awareness, and repair posture in the style of MARGPA / MARGD are reproducibly observed even in topics where no specific domain-knowledge scope adjustment has been made, this may exceed the scope of a “convenient prompt.”

In that case, MARGPA / MARGD is worth considering as a prompt-native runtime governance architecture.

However, at the present stage, it remains a hypothesis.  
Its effects, reproducibility, side effects, and limitations need to be confirmed through future observation and evaluation.

Also, when these functions fit together, there may be cases where a certain degree of structuring or provisional response adjustment becomes possible even for unregistered domains.

However, that is not the same as having a dedicated GD.  
When stable domain governance is required, it is generally more reliable to create a dedicated GD for that field.