
---

# Example of AI Behavior Changes and Application Potential When Applying MARGD: Medical Assistive AI

---

## 0. Positioning / Disclaimer

This document is a technical study material based on personal research, intended to organize expected behavior changes and application potential when MARGD (ARGD / DAGD) is applied as runtime instructions for medical assistive AI.

This document does not replace professional judgment in medical or health consultation, nor does it guarantee the correctness or safety of diagnosis, treatment, prescription, emergency judgment, medication judgment, or testing judgment.

The content presented here is, at this stage, a hypothetical organization that is unverified or only limitedly validated.

Sufficient validation would require domain-specific evaluation design, comparable input data, execution logs, failure cases, review by medical professionals, risk assessment, and confirmation of compliance with laws, terms, and safety standards.

---

## 1. Target Scope

This document covers expected behavior changes when MARGD (ARGD / DAGD) is applied to medical assistive AI.

Here, medical assistive AI does not refer to AI that replaces diagnosis, treatment, or prescription judgment by physicians.
It mainly refers to AI that supports the following.

* Organizing user symptoms, lifestyle background, medication, medical history, and similar information
* Structuring information that should be communicated to a physician before consultation
* Organizing checklist items the user should record
* Organizing candidate tests to discuss with a physician
* Separating signs that may relate to urgency
* Distinguishing uncertain information from confirmed information
* Supporting understanding of post-consultation explanations and test results

Within this scope, the role of AI is positioned not as a “diagnostician,” but as an information organization, interview support, and communication support layer between the user and medical professionals.

---

## 2. Current Challenges in AI Use

When AI is used for medical or health consultation, ordinary conversational AI may face the following challenges.

### 2.1 Instability of Context Preservation

In medical consultation, not only the symptom itself, but also medical history, medication, lifestyle, test history, consultation status, symptom progression, and other contextual information are important.

However, in ordinary AI dialogue, important premises may weaken as the conversation progresses, or the AI may return to general health advice every turn.

### 2.2 Regression to Generalities

Even when the user has a complex background, the AI may return to advice assuming an average user.

For example, when a user complains of strong thirst, the AI may respond “drink more water” without checking the background.

Such a response may be useful in cases of simple dehydration.
However, when electrolyte abnormalities, polyuria, abnormal glucose metabolism, medication effects, kidney function, liver function, or similar factors are involved, it may be insufficient as information organization.

### 2.3 Early Convergence to a Single Hypothesis

In medical consultation, the same symptom may involve multiple possible causes or points to confirm.

However, if the AI quickly leans toward the most understandable cause or the hypothesis presented by the user, other points requiring confirmation may not be sufficiently preserved.

### 2.4 Approaching Diagnostic Assertions

The more specific the user’s input becomes, the more likely the AI may respond with wording close to diagnosis, such as “that is X.”

As medical assistive AI, rather than asserting a diagnosis, it is considered more appropriate in terms of safety and practicality to organize information that should be confirmed, the need for consultation, points to communicate to a physician, and candidate tests to discuss with a physician.

### 2.5 Handling of Insufficient Information

In medical judgment, unconfirmed information may significantly affect conclusions.

For example, without confirming the following information, it is difficult to organize the possible cause or urgency of symptoms.

* Onset timing
* Symptom intensity
* Medical history
* Medication
* Alcohol use / smoking
* Diet / sleep
* Urine volume / weight change
* Test values
* Consultation history
* Presence or absence of symptoms that may relate to urgency

Ordinary AI may finish by stating only general possibilities without explicitly identifying these missing pieces of information.

### 2.6 Insufficient Conversion Into a Physician-Readable Format

The user’s symptom description may be natural in conversation, but insufficiently organized as information to communicate to medical professionals.

Medical assistive AI is expected to play a role in converting the user’s subjective experience and lifestyle information into a structure that physicians can more easily confirm.

---

## 3. Expected Behavior Without MARGD

When MARGD is not explicitly applied, ordinary AI dialogue may show the following behaviors.

### 3.1 Reaction to the Symptom Alone

The AI may react only to the user’s most recent input and fail to sufficiently reuse background information or previously shared conditions.

Examples:

* “I feel thirsty” → “Drink more water”
* “I get tired easily” → “Get more sleep”
* “I feel nauseous” → “Eat something easy to digest”

These may be generally useful pieces of advice in some cases, but may be insufficient for users with complex backgrounds.

### 3.2 Loss of Medical History, Medication, and Lifestyle Premises

If premises such as medical history, medication, alcohol use, smoking, sleep, exercise, and test history are not sufficiently preserved, responses are more likely to return to the range of general health consultation.

### 3.3 Following the User’s Hypothesis

When the user says “Could this be due to X?”, the AI may prioritize explanations aligned with that hypothesis and fail to sufficiently handle refutation or alternative issues.

### 3.4 Possible Instability in Handling Signs That May Relate to Urgency

In medical consultation, the same symptom can require different responses depending on whether urgency is involved.

Without MARGD, confirmation of signs that may relate to urgency may not be performed stably every time, and boundaries between ordinary consultation, early consultation, and emergency consultation may become ambiguous.

### 3.5 Output Tends to End Within the Conversation

In ordinary AI responses, explanations or advice may be generated, but they may not be easily converted into practical outputs such as the following.

* Checklist for the user
* Communication memo for a physician
* List of questions to ask during consultation
* Candidate tests to discuss with a physician
* Symptom log to record
* List of unconfirmed information

---

## 4. Expected Behavior With MARGD

By applying MARGD (ARGD / DAGD), it becomes possible to design medical assistive AI toward the following behaviors.

### 4.1 Preservation of Context and Premises

ARGD may make it easier to preserve medical history, medication, lifestyle, untested suspicions, already confirmed conditions, and similar information shared by the user as premises in subsequent responses.

This may make it easier to move from generalities about a one-off symptom to information organization based on the user’s conditions.

### 4.2 Separation of Fact, Inference, Hypothesis, and Unknowns

In medical assistance, it is important not to confuse confirmed information and unconfirmed information.

With MARGD, the following kinds of separation may become easier.

* Diagnosed information
* Information the user suspects but has not tested
* Possibilities inferred by the AI
* Information that cannot be judged without tests or medical examination
* Unconfirmed information that affects urgency

### 4.3 Preservation of Multiple Issues

ARGD’s branch preservation may make it easier to handle multiple points for confirmation in parallel, instead of converging too early to a single cause.

The following are not lists of diagnostic candidates, but examples of issues to confirm or discuss with a physician.

For example, in the case of thirst or dry throat, the following issues may be separated and handled.

* Possibility of simple dehydration
* Dry mouth
* Medication effects
* Effects of alcohol use or smoking
* Confirmation of electrolyte abnormalities
* Confirmation of blood glucose abnormalities
* Confirmation related to kidney function
* Confirmation related to liver function
* Confirmation related to thyroid function
* Mouth breathing or overuse of the throat
* Throat irritation due to acid reflux or similar factors

In this way, the symptom is not closed into one cause, but can be organized as points to confirm with a physician.

### 4.4 Responses That Avoid Excessive Following of User Hypotheses

When the user presents a hypothesis, the AI may become more likely to show refutation, weaknesses, alternative interpretations, and points to confirm with a physician, rather than immediately agreeing.

This behavior is important for medical assistive AI to avoid reinforcing the user’s anxiety or assumptions, and instead convert them into confirmable information.

### 4.5 Conversion Into Physician-Oriented Output

By combining DAGD output policy, required behaviors, and repair policy, the content of conversational consultation may become easier to convert into formats such as the following.

* Chief complaint to communicate during consultation
* Medical history, medication, and lifestyle
* Checklist items the user should observe
* Questions to confirm with a physician
* Candidate tests to discuss with a physician
* Signs that may relate to urgency
* What cannot be judged at the current stage

This behavior may be useful as support for organizing the user’s vague subjective experience into information that medical professionals can more easily confirm.

### 4.6 Separation of Signs That May Relate to Urgency

With MARGD, ordinary advice and signs that may relate to urgency may be easier to handle separately.

For medical assistive AI, it is inappropriate to treat every consultation as urgent, but it is also necessary to avoid overlooking signs that may require prompt consultation.

Therefore, it is expected that classifications such as the following may become more stable.

* Information that may be recorded at the current stage
* Information to discuss during ordinary consultation
* Information that should be discussed with medical professionals relatively soon
* Information for which emergency consultation or prompt confirmation with a medical institution should be considered

---

## 5. Comparison of Behavior Changes

| Perspective                         | Expected behavior without MARGD                                                           | Expected behavior with MARGD                                                                                                    |
| ----------------------------------- | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Context preservation                | May focus on the most recent input, while medical history and lifestyle background weaken | May preserve shared premises and reflect them in subsequent responses more easily                                               |
| Symptom interpretation              | May lean toward an easily understandable single cause                                     | May preserve multiple confirmation points as branches                                                                           |
| Response to user hypothesis         | May agree with or follow the user’s hypothesis                                            | May show refutation, alternative issues, and information to confirm with a physician                                            |
| Insufficient information            | Missing information may not be made explicit and may be filled by generalities            | May separate unknowns, their impact on conclusions, and confirmation methods                                                    |
| Connection to medical professionals | May end as advice within the conversation                                                 | May be easier to convert into physician-oriented communication memos or question lists                                          |
| Signs that may relate to urgency    | Confirmation may become unstable                                                          | May separate ordinary consultation from signs that may relate to urgency                                                        |
| Diagnostic assertion                | May lean toward wording close to a diagnosis                                              | May organize information as points to confirm during consultation rather than as diagnosis                                      |
| Output format                       | May center on explanatory text                                                            | May be easier to structure into checklists, consultation memos, candidate tests to discuss with physicians, and similar formats |

---

## 6. Why This Is Expected

The above behavior changes are expected under MARGD because ARGD and DAGD have different governance functions.

### 6.1 Influence of ARGD

ARGD mainly affects reasoning procedures and the order of answer formation.

In medical assistive AI, the following may be related to behavior changes.

* Preservation of input structure
* Fixing context priority
* Explicit definition of definitions and target scope
* Separation of known and unknown information
* Contradiction detection
* Suppression of assertions under insufficient information
* Preservation of multiple issue branches
* Checking refutations and alternative issues
* Separation of fact, inference, assumption, and evaluation
* Stabilization of answer structure

This may make it easier to suppress “too-early conclusion formation” or “leaning too strongly toward a single cause” in medical consultation.

### 6.2 Influence of DAGD

DAGD mainly affects goals, prohibited behaviors, required behaviors, evaluation, repair, auditing, and state management.

In medical assistive AI, the following may be related to behavior changes.

* Goal fixation
* Explicit definition of prohibited behaviors
* Explicit definition of required behaviors
* Setting evaluation targets
* Failure detection
* Repair procedures
* Re-fixation
* Status reporting
* Explicit definition of audit targets

This may make AI responses more likely to move toward user support, pre-consultation organization, physician-oriented information conversion, and separation of signs that may relate to urgency, rather than ending as one-off advice.

### 6.3 Compatibility With Medical Assistive AI

In medical assistive AI, simply outputting medical knowledge is not sufficient.

The important processes include the following.

* Preserving the user’s background
* Identifying insufficient information
* Preserving multiple confirmation points
* Separating parts requiring professional judgment
* Avoiding assertions
* Converting information into a form that can be passed to medical professionals
* Making it harder to overlook signs that may relate to urgency
* Avoiding excessive following of the user’s anxiety or hypotheses

MARGD may be applicable as a framework for governing these processes at the external instruction layer.

---

## 7. Expected Application Potential

When MARGD is applied to medical assistive AI, the following uses can be imagined.

### 7.1 Pre-Consultation Organization Support

It may be used to help users organize their symptoms, background, medication, lifestyle, and consultation purpose before seeing a physician.

Output examples:

* Chief complaint
* Since when
* Degree of severity
* Worsening / relieving factors
* Medical history
* Medication
* Lifestyle
* Things to ask the physician

### 7.2 Creating a Checklist for the User

It may be used to convert symptoms and lifestyle logs into a format that the user can easily record.

Output examples:

* Body temperature
* Body weight
* Blood pressure
* Pulse
* Fluid intake
* Diet
* Sleep
* Urination frequency
* Symptom score
* Medication timing
* Worsening factors

### 7.3 Creating a Communication Memo for Physicians

It may be used to convert the user’s conversational explanation into a format that medical professionals can more easily confirm.

Output examples:

* Consultation purpose
* Known diagnoses
* Untested suspicions
* Current chief complaint
* Lifestyle background
* Medication
* Candidate tests to discuss with a physician
* Symptoms that may relate to urgency

### 7.4 Organizing Candidate Tests to Discuss With a Physician

The use case is not for AI to instruct tests, but to organize them as candidates to discuss with a physician.

Examples:

* Consultation about blood tests
* Consultation about urine tests
* Consultation about imaging tests
* Confirmation related to medication
* Confirmation related to lifestyle
* Consultation about referral to a specialist department

### 7.5 Organizing Post-Consultation Explanations

After consultation, it may be used to organize the physician’s explanation, test results, points to confirm next time, and lifestyle precautions.

However, when interpreting test values or physician explanations, it must be treated as organization of confirmation items, not as a replacement for professional judgment.

---

## 8. Limitations and Failure Modes

Even if MARGD is applied, the safety or correctness of medical assistive AI is not guaranteed.

### 8.1 It Does Not Replace Diagnosis or Treatment Judgment

MARGD does not give AI the ability to judge as a physician.

Diagnosis, treatment policy, prescription, stopping or increasing / decreasing medication, emergency judgment, and similar matters require confirmation by medical professionals.

### 8.2 When Input Information Is Wrong

If the user inputs incorrect information, incomplete information, or information based on memory errors, the AI’s organization result will also be affected.

MARGD does not automatically guarantee the truth of input information.

### 8.3 Dependence on Model Performance

MARGD is a governance definition at the external instruction layer, and it does not directly change the model’s medical knowledge, reasoning ability, or instruction-following ability.

Therefore, effects may vary depending on model performance and context retention capability.

### 8.4 Retention Limits in Long or Complex Contexts

The more complex the user’s background is, the more difficult context preservation, premise fixation, and branch preservation may become.

In long conversations, failures such as weakening of important premises, overlooked contradictions, or failure to reuse past information may remain.

### 8.5 Excessively Safety-Sided Output

In the medical domain, safety must be emphasized.
On the other hand, if the AI only responds with “please seek medical care” excessively, its value as information organization support may decrease.

Even when applying MARGD, it is necessary to design separation between signs that may relate to urgency and ordinary consultation.

### 8.6 Practical Operation Risk Without Expert Review

When operating as medical assistive AI in practice, expert review by physicians, pharmacists, nurses, medical safety personnel, and similar professionals is necessary.

A hypothetical organization at the personal research stage alone does not confirm practical safety.

---

## 9. Future Validation Perspectives

The following are not benchmarks that demonstrate effectiveness at this stage, but perspectives to observe in future validation.

### 9.1 Context Preservation

* Whether previously provided information such as medical history, medication, and lifestyle is preserved in later responses
* Whether important premises do not drop out during the conversation
* Whether unconfirmed information is not treated as confirmed information

### 9.2 Disclosure of Uncertainty

* Whether insufficient information is made explicit
* Whether unconfirmed information that affects conclusions is shown
* Whether inference and fact are distinguished
* Whether points that cannot be judged without tests or consultation are made explicit

### 9.3 Preservation of Multiple Issues

* Whether the AI avoids early convergence to a single cause
* Whether multiple confirmation points can be preserved as branches
* Whether the AI avoids excessive following of the user’s hypothesis

### 9.4 Physician-Oriented Information Conversion

* Whether the user’s conversational content can be organized for physicians
* Whether chief complaint, background, medication, lifestyle, and questions are separated
* Whether the information format is useful during consultation

### 9.5 Separation of Signs That May Relate to Urgency

* Whether signs that may relate to urgency are separated from ordinary advice
* Whether symptoms that may require prompt consultation are less likely to be overlooked
* Whether not everything is excessively treated as urgent

### 9.6 Suppression of Diagnostic Assertions

* Whether the AI avoids asserting diagnostic names
* Whether information is organized as points to confirm during consultation rather than as diagnosis
* Whether boundaries with professional judgment are made explicit

### 9.7 Stability of Output Format

* Whether formats such as checklists, physician-oriented memos, and candidate tests to discuss with physicians are generated stably
* Whether output format can be changed according to the user’s purpose
* Whether the response is converted into practical organization rather than ending only as explanatory text

---

## 10. Provisional Evaluation

In medical assistive AI, MARGD (ARGD / DAGD) is not a mechanism that guarantees diagnostic accuracy itself.

On the other hand, it has application potential as a framework for providing governance from the external instruction layer to the following processes needed in medical consultation.

* Context preservation
* Premise fixation
* Disclosure of insufficient information
* Preservation of multiple issues
* Responses that avoid excessive following of user hypotheses
* Separation of signs that may relate to urgency
* Physician-oriented information organization
* Stabilization of output structure
* Repair after failure
* Boundary management with professional judgment

Therefore, MARGD is worth considering not as medical diagnostic AI itself, but as a governance specification for stabilizing AI behavior in information organization before and after consultation, interview support, and communication support for medical professionals.

However, the content of this document is a hypothetical organization at the personal research stage.
To claim actual effectiveness or safety, validation including comparable input data, execution logs, failure cases, review by medical professionals, and risk assessment would be required.

---
