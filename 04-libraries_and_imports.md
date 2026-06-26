---
title: Limitations & Creating Your Own Model
teaching: 15
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Recognize the ethical and technical boundaries of AI, specifically regarding algorithmic bias and data privacy.
- Deconstruct the high-level, end-to-end pipeline required to build and deploy a compliant medical AI model.
- Shift the mindset from "AI replacing humans" to "AI amplifying human capability."

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- "If an AI model misdiagnoses a patient, who should carry the ultimate responsibility: the doctor who used it, the hospital that bought it, or the data scientist who built it?"
- "What is one manual, repetitive task in your specific domain that you would happily hand over to an AI assistant tomorrow if you knew it was safe?"

::::::::::::::::::::::::::::::::::::::::::::::::::

## Expansion: General Limitations of AI
### Core Concept: Math Patterns vs. Clinical Context

**Expanded Speaker Script**

"When we look at an AI model making a diagnosis, it’s easy to trick ourselves into thinking the machine is 'thinking' like a doctor. It isn't. An AI model possesses zero common sense and no actual understanding of human physiology.
If you show a lung model an X-ray where the patient accidentally swallowed a coin, it doesn't understand what a stomach is, what choking means, or what a coin is. It only maps mathematical correlations across pixel grids. It relies entirely on the consistency of statistical patterns. If those patterns change even slightly in the real world, or if they were flawed from day one, the output will look incredibly confident while being completely wrong."
**Key Teaching Point: Correlation $\neq$ Causation**

Machines are pattern-matchers, not logicians. If a dataset shows that patients who receive a specific temporary baseline medication happen to survive longer due to independent clinical routing, the model may conclude the medication is a miraculous cure, completely missing the true underlying clinical reason.

### Failure Mode 1: "Garbage In, Garbage Out" (GIGO)
When bad data enters an algorithm, the AI doesn't break down with an error message—it builds a highly polished, dangerous model out of that bad data.
**Structural Breakdowns in Clinical Data**

- Upcoding & Billing Bias: Administrative billing codes (ICD-10) are optimized for financial reimbursement, not granular clinical research. If an algorithm is trained on EHR records to predict heart failure outcomes, but clinicians systematically selected generic "unspecified heart failure" codes to ensure insurance approval, the model inherits a fundamentally warped understanding of the disease progression.
- Missing Data Misinterpretation: In healthcare records, blank spaces carry heavy meaning. A missing lab value usually means a clinician looked at the patient and decided they were healthy enough not to need the test. If a model treats missing fields as an arbitrary "zero" or fills them in with naive mathematical averages, it miscalculates risk profiles.
- Sloppy Text & Copy-Paste Culture: Clinical documentation is filled with historical copy-paste errors. If historical training notes constantly carry forward outdated medication lists or conflicting symptom notes, an NLP model will mistake this text-clutter for active, high-yield clinical signals.

### Failure Mode 2: Model Brittleness & The Generalization Gap
An AI model's performance can drop sharply when moving between hospital environments. This drop is known as Dataset Shift or The Generalization Gap.

**The Illusion of Performance: "Shortcut Learning"**
When we train a deep learning network on images from a single, high-tech facility, the model often takes an unhelpful shortcut to maximize its accuracy score. It learns to recognize the specific signatures of that hospital's hardware, scan markers, or patient protocols rather than the actual medical pathology.

!["Are we dealing with supervised or unsupervised
learning?"](fig/xray_example.png){alt="Flow Diagram for determining supvervised vs unsupervised"}.

**A Real-World Diagnostic Failure Case Study**
Consider an AI model built to spot pneumonia on chest radiographs:
- The Training Site (London Academic Center): The model is trained on thousands of scans from top-tier digital imaging suites. In these suites, stable, ambulatory patients stand up for clean, crisp posterior-anterior (PA) views.
- The Shortcut: The model notices that the highest-quality scans almost always belong to stable patients, while low-quality, high-noise scans taken by portable bedside units belong to critically ill patients in the ICU. The model covertly learns to classify "portable machine noise" as an indicator of severe lung disease.
- The Deployment Site (Rural Clinic): The model is deployed to a community clinic that relies entirely on an older, portable X-ray unit for all patients due to space constraints.
- The Crash: Because every single image coming out of the rural clinic contains high noise and lower contrast, the model's performance breaks down completely. It continuously flags healthy patients as having severe pneumonia simply because it confuses the older machine's background noise with the markers of a critical ICU case.

### Core Concept: The High Stakes of Clinical Software
**Expanded Speaker Script**
"If a music streaming app has a software bug, you get a bad song recommendation. If a commercial text predictor glitched, it typoed a text message. But in healthcare, a software bug or a hidden algorithmic flaw is a direct threat to patient safety.
When we integrate machine learning into patient care, we cannot manage it like standard consumer tech. We have to wrestle with deep historical biases, navigate complex legal accountability frameworks, and protect patient privacy under the strictest data laws on earth."

## Challenge A: The Dataset Bias Trap
Algorithms do not have moral compasses; they are historical mirrors. If the data used to train an AI model reflects societal or systemic gaps in healthcare access, the model will codify and supercharge those disparities under the guise of objective mathematics.
**The Fitzpatrick Scale Disparity in Dermatology**
In medical computer vision, skin cancer screening tools rely heavily on image pattern recognition. A historical problem is that major open-source dermatology training repositories (like the ISIC archive) have historically consisted of images taken from individuals with lighter skin tones.

- The Systemic Drop: When an algorithm trained primarily on Fitzpatrick Types 1–3 (lighter skin) is asked to evaluate a lesion on Fitzpatrick Types 5–6 (darker skin), its diagnostic accuracy drops precipitously.
- The Clinical Consequence: The model fails to recognize the edge boundaries, color variations, or texture changes of a malignant melanoma against a darker background melanin index. This leads directly to higher false-negative rates and delayed, late-stage cancer diagnoses for minority patient groups.

!["Are we dealing with supervised or unsupervised
learning?"](fig/skin_example.png){alt="Flow Diagram for determining supvervised vs unsupervised"}.

## Challenge B: The Black Box & Explainability (XAI)
Deep learning models operate by routing inputs through millions of abstract mathematical connections. This yields a Black Box problem: an input goes in, an output comes out, but the exact clinical logic remains completely invisible.
**Moving Past the Black Box with SHAP & LIME**
Physicians have an ethical and legal duty of care. You cannot prescribe a aggressive treatment protocol or send a patient to emergency surgery simply because a model generated a high risk score. You need to know why.
Medicine solves this using Explainable AI (XAI) frameworks. The two industry standards are:
- SHAP (SHapley Additive exPlanations): Uses cooperative game theory to calculate the exact structural contribution of each medical feature to the final prediction.
- LIME (Local Interpretable Model-agnostic Explanations): Purposely perturbs the data around a single patient to see which variables cause the prediction to flip.
**Reading a SHAP Force Plot**
When integrated into an Electronic Health Record (EHR), an XAI tool transforms a blind risk percentage into an actionable diagnostic map.

!["Are we dealing with supervised or unsupervised
learning?"](fig/EHR_example.png){alt="Flow Diagram for determining supvervised vs unsupervised"}.

As shown in the force plot visualization above, the model reveals its internal decision-making path for individual patients:
- The Baseline Value: The system starts at a standard population risk baseline.
- The Dynamic Vectors: Clinical variables act as directional forces. Red bars push the patient's score higher toward a critical alert threshold, while blue bars pull the prediction down toward safety.
- Clinical Verification: A clinician can quickly review the chart and see that a high risk score was driven specifically by a high respiratory rate (RR = 23.0) paired with a compromised oxygenation status (PaO2 = 53.0), allowing them to clinically validate the AI's warning.

## Challenge C: Data Privacy & Sovereign Borders

Tech giants scale their businesses by collecting massive consumer data pools into centralized clouds. In medicine, strict privacy frameworks like HIPAA (Health Insurance Portability and Accountability Act) and GDPR (General Data Protection Regulation) make this central gathering approach an operational and legal impossibility.
           [ Standard Data Collection ]          [ Medical Federated Learning ]
                Hospital A  Hospital B                 Hospital A  Hospital B
                     \          /                           ▲          ▲
                      ▼        ▼                            │  Models  │
                 [ Central Cloud ]                          ▼  (No Data)▼
             (Massive Privacy Leak Risk)               [ Federated Central Server ]

**The Solution: Federated Learning**
To train powerful models without moving highly confidential patient files across institutional boundaries, medical networks utilize Federated Learning architectures.

!["Are we dealing with supervised or unsupervised
learning?"](fig/federated_learning.png){alt="Flow Diagram for determining supvervised vs unsupervised"}.

Rather than forcing healthcare networks to pool private patient data into a vulnerable central repository, federated learning flips the pipeline completely:
- Local Preservation: The raw data stays safely behind local firewall networks at individual facilities (e.g., individual hospitals, research centers, or universities).
- Model Dissemination: A blank, unconfigured neural network model is sent out from a central federated server to each individual site.
- Local On-Site Training: The model trains locally on each hospital's local data servers. No patient charts, names, or identifiers ever leave the building.
- Global Aggregation: The sites send only their mathematical model adjustments (weight updates) back to the central server. The central server blends these updates into a master algorithm that benefits from the collective knowledge of multiple hospitals while maintaining absolute data confidentiality.

## Summary Wrap-Up for the Session
Key Takeaway: Ethical healthcare AI requires moving past the simple metric of "accuracy." We must actively inspect our datasets for demographic gaps, use XAI tools like SHAP force plots to keep clinical logic transparent, and utilize decentralized frameworks like federated learning to respect sovereign data walls.

## How to Build a Model: The Bare Minimum (15 Mins)
**Core Concept**
"If you ever want to launch an AI research project or build a tool for your department, you need to understand that coding is only about 10% of the timeline. The real work is data governance, labeling, and workflow integration. Let's walk through the actual clinical blueprint."

### The Multi-Phase Clinical AI Pipeline

!["Are we dealing with supervised or unsupervised
learning?"](fig/multi-phase.png){alt="Flow Diagram for determining supvervised vs unsupervised"}.

## Wrap-Up & Next Steps (10 Mins)
**Final Closing Thoughts**
"As we close out this foundational series, remember this fundamental truth: The goal of AI in healthcare is not to replace the clinician.
The true promise of these tools is to automate the repetitive, administrative, and exhausting tasks—the endless documentation, the initial sorting of normal scans, the manual data tracking. By offloading that cognitive load to machines, we can give human clinicians their most valuable asset back: time. Time to focus on complex cases, and time to spend at the bedside doing what humans do best—caring for patients."


:::::::::::::::::::::::::::::::::::::::: keypoints

- The Bias Trap: Models trained on narrow demographics (e.g., primarily Caucasian skin types for dermatology AI) drop significantly in accuracy when applied to diverse populations.
- Brittleness & Drift: A model optimized for a high-tech metropolitan hospital will often fail in a rural clinic due to differences in equipment, patient demographics, and charting habits ("Garbage In, Garbage Out").
- The Model Lifecycle: Building a model is only 20% math. The other 80% is data governance (HIPAA/GDPR compliance), establishing an expert "ground truth" through manual labeling, and workflow integration.

::::::::::::::::::::::::::::::::::::::::::::::::::


