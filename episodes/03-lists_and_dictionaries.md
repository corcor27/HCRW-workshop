---
title: ML/AI in Healthcare Applications
teaching: 45
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Analyze real-world case studies of AI proving clinical utility across imaging, risk scoring, and genomics.
- Understand how data inputs translate directly into predictive outputs in a clinical setting.
- Identify the real-world operational bottlenecks that keep validated models out of the clinic.


::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- "What do you think is currently holding back these highly accurate models from being deployed in every single hospital tomorrow?"
- "When an AI model is used as a 'second reader' in radiology and disagrees with the human doctor, how should the clinical team resolve the conflict?"

::::::::::::::::::::::::::::::::::::::::::::::::::

## Deep Dive: 4 Clinical Use Cases (55 Mins)
### Case 1: Breast Cancer Imaging & Computer Vision (15 mins)
**Core Concept**

"Mammography is notoriously difficult. A radiologist might review over a hundred scans a day, looking for microcalcifications of tiny specks of calcium that can be the earliest sign of breast cancer. They are easy to miss on a busy shift, but computer vision models don't get tired."
**The Features & Mechanics**

- Pixel-Level Texture Gradients: The model calculates sudden shifts in contrast between adjacent pixels that can highlight subtle masses before they form distinct borders.
- Edge Sharpening: It traces micro-margins of structural changes, evaluating whether an asymmetry matches benign tissue variations or malignant architectures.
- Density Variations: It isolates localised dense regions that might hide behind or within dense breast tissue, acting as an automated second set of eyes to catch what human eyes could miss during fatigue periods.


!["Are we dealing with supervised or unsupervised
learning?"](fig/mammogram_example.png){alt="Flow Diagram for determining supvervised vs unsupervised"}.


### Case 2: Patient Risk Analysis & Tabular Prediction (15 mins)
**Core Concept**
"In an intensive care setting, sepsis doesn't just hit a patient out of nowhere—it drops clues hours in advance. Predictive tabular models pull disparate data points straight from the electronic health record to flag a crashing patient before clinical decompensation becomes obvious."

**The Features & Mechanics**
- Vital Sign Trend Cross-Matching: Rather than setting off an alarm for a single isolated parameter, the model looks for complex multi-system trends over time. For instance, it flags when a subtle heart rate elevation occurs simultaneously with a downward drift in blood pressure.
- Lab Value Concurrency: It ingests real-time lab updates, tracking indicators like steady white blood cell (WBC) count climbs or unexpected lactate level increases.
- Demographic Context Filters: It weights these real-time signals against static risk factors, including age, chronic comorbidities, and recent surgical history, to output an updated risk score.

!["Are we dealing with supervised or unsupervised
learning?"](fig/ECG_example.png){alt="Flow Diagram for determining supvervised vs unsupervised"}.

### Case 3: Microbiology & Automated Screening (10 mins)
**Core Concept**
"Think about the sheer volume of negative agar plates a microbiology lab processes daily. Automated screening lets models take over the routine triage of plates, freeing path-lab scientists to focus their energy entirely on complex, atypical growth patterns."

**The Features & Mechanics**
- Colour Segmentation: The model isolates hue ranges to distinguish bacterial types or hemolytic reactions against agar backgrounds.
- Colony Architecture Mapping: It evaluates geometric attributes such as circularity, elevation, and border characteristics to classify sample morphology.
- Kinetic Growth Metrics: By analysing time-lapse imagery, the system tracks growth velocity over specific hourly intervals, recognising specific bacterial strains by how quickly they colonise the plate.

### Case 4: Sequence & Genomic Data via Transformers (15 mins)
**Core Concept**
"We've all heard how Large Language Models analyze sentences to guess the next word. In genomics, we apply that exact same logic. We treat human DNA bases—A, T, C, and G—as letters, and long gene sequences as paragraphs to catch mutations that cause rare diseases."

**The Features & Mechanics**
- Long-Range Dependency Tracking: Traditional tools can only look at small genetic sections at a time. Transformer architectures use self-attention to link a base mutation at one end of a chromosome directly to structural changes at the far end.
- Protein Folding Alterations: The model analyzes how these far-apart sequence shifts interact to change final 3D protein structures, predicting whether a variant will disrupt normal cell function.


## Group Discussion Builder: The Translation Gap (20 Mins)

**The Core Question to Present**
"What do you think is currently holding back these incredibly powerful models from being used in every single hospital tomorrow?"

**Facilitator Framework & Navigation Prompts**
If the audience hesitates or focuses solely on a single aspect, use the structured guidance categories below to steer the conversation:

!["Are we dealing with supervised or unsupervised
learning?"](fig/the_translation_gap.png){alt="Flow Diagram for determining supvervised vs unsupervised"}.

### Technical Barriers (Data Silos & Interoperability)
- The Problem: Hospital systems rarely talk to each other seamlessly. A model trained to perfection on an Epic EHR platform at a major academic center often fails completely when deployed on a Cerner platform at a rural community hospital.
- Prompt to use: "If a model relies on structured lab inputs, what happens when it encounters a hospital where those specific labs are written as free-text notes?"
### Cultural Barriers (Clinician Distrust & Alarm Fatigue)
- The Problem: Clinicians face constant alert fatigue. If an AI model flags a sepsis risk with a high false-positive rate, doctors will quickly turn off or ignore the system entirely. Additionally, a lack of explainability leads to a "black box" issue where physicians don't trust a recommendation they can't verify.
- Prompt to use: "Would you feel comfortable altering a patient's care plan based on an AI alert if the model couldn't show you the data reasoning behind its decision?"
### Legal & Regulatory Barriers (Liability & Accountability)
- The Problem: The legal landscape remains undefined. If an algorithm misses a tumor on a mammogram, liability lines blur between the radiologist who signed off, the hospital that bought the tool, and the software company that engineered the model.
- Prompt to use: "If a tool is labeled as a 'clinical decision support aid,' who is ultimately accountable when a missed finding causes patient harm?"

## Summary wrap-up
Key Takeaway: Moving ML/AI out of a research lab and into a live clinical workflow isn't just a coding challenge. Success requires matching data types to the right model architectures, ensuring our technical systems can actually share data, and building clear interfaces that earn the trust of clinical teams.


:::::::::::::::::::::::::::::::::::::::: keypoints

- Computer Vision (Breast Cancer): Models analyze pixel-level gradients and density variations to flag early-stage microcalcifications that human eyes might miss during a long shift.
- Predictive Analytics (Sepsis/Risk): Tabular models monitor continuous streams of patient vitals over time, spotting early systemic trends (like dropping blood pressure paired with rising heart rate) hours before full clinical onset.
- Genomics (Sequence Data): Algorithms treat DNA sequences ($A, T, C, G$) like languages, utilizing transformer models to find long-range genetic mutations linked to rare diseases.
::::::::::::::::::::::::::::::::::::::::::::::::::


