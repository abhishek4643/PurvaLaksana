# Product Requirements Document (PRD)
### Purva Laksana — AI-Powered Multi-Organ Healthcare Companion & Clinical Diagnostic System

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=rect&color=gradient&customColorList=12,20,26&height=8&section=header&width=100%" width="100%" />
</div>

## 1. Executive Summary

In primary healthcare clinics, rural outreach facilities, and telemedicine consultations, timely detection of chronic and acute medical conditions (such as pulmonary lesions, diabetic retinopathy, fractures, and intracranial tumors) is hindered by severe radiologist shortages and diagnostic backlog. Patients often face critical delays between symptom onset and specialized clinical interpretation.

**Purva Laksana** is an AI-powered multi-modal healthcare diagnostic and vital tracking platform built with **Python 3.10+**, **Streamlit Cloud**, **PyTorch**, and **OpenCV**. It integrates 10+ deep learning computer vision models with real-time biometric telemetry (via **Google Fit API**) and automated **Telegram Bot** triage, providing preliminary clinical assessments, risk stratification scores, and actionable diagnostic reports.

---

## 2. Target Personas

| Persona | Primary Goal | Pain Points Addressed |
| :-- | :-- | :-- |
| **Rural Primary Care Clinicians** | Obtain rapid secondary opinions on X-rays and dermatological scans | Lack of immediate access to specialist radiologists and pathologists |
| **Telemedicine Doctors** | Correlate patient-uploaded scans with longitudinal Google Fit vitals | Manual parsing of separate wearable exports and medical imaging discs |
| **Remote Patients** | Receive immediate preliminary triage and structured next-step guidance | High anxiety, long wait times, and confusing technical clinical jargon |

---

## 3. Core Functional Requirements

### 3.1 Multi-Organ Deep Learning Vision Suite
- **Orthopedic & Radiographic Analysis**:
  - `bone.pt`: Detects bone fractures and dislocations from musculoskeletal X-rays.
  - `braintumorp1.pt` & `brain123.pt`: Identifies and segments intracranial tumors on MRI scans.
  - `lung_cancer.pt`: Flags pulmonary nodules and malignancy indicators on chest radiographs.
- **Dermatological & Ophthalmic Screening**:
  - `diabetic.pt` & `eye.pt`: Evaluates fundus photography for diabetic retinopathy and retinal microaneurysms.
  - `skin345.pt`: Analyzes dermoscopic lesions for melanoma and benign keratosis.
- **Physical Symptom & Tongue / Nail Inspection**:
  - `tongue(2).pt`, `nails.pt`, `ulcer.pt`: Classifies visible physiological indicators of nutritional deficiencies and ulcers.
  - `yolo11n.pt`: Real-time object and pathology bounding box detection.

### 3.2 Wearable Telemetry & Heart Disease Risk Engine
- **Google Fit API Synchronization**:
  - Seamless OAuth2 integration importing patient heart rate, daily step counts, resting blood pressure, and sleep duration.
- **Biometric Heart Disease Prediction**:
  - Machine learning classification engine evaluating patient age, cholesterol, resting ECG, blood pressure, and ST-segment depression to output quantitative cardiac risk scores.

### 3.3 Multi-Channel Ingestion & Conversational Triage
- **Streamlit Web Portal**:
  - Interactive multi-page clinical dashboard with direct drag-and-drop scan uploads and side-by-side visualization.
- **Telegram Diagnostic Bot**:
  - Automated conversational bot allowing patients to send medical scan images over Telegram and receive structured risk verdicts.

---

## 4. Non-Functional Requirements

- **Inference Speed**:
  - Deep learning model inference: $< 1.5\text{ seconds}$ per image scan on CPU/GPU.
- **Safety & Ethical Disclaimers**:
  - Explicit prominent clinical disclaimers stating Purva Laksana is an assistive screening tool and not a replacement for certified physician diagnosis.
- **Data Confidentiality & Privacy**:
  - Client scan data is processed ephemerally in session memory and never shared without patient consent.

---

## 5. Scope & Out-of-Scope (v1.0)

- **In Scope**:
  - 10+ PyTorch deep learning models deployed via Streamlit multi-page interface.
  - Google Fit API wearable telemetry synchronization.
  - Telegram conversational triage bot integration.
  - Heart disease predictive scoring and comprehensive diagnostic PDF summary exports.
- **Out of Scope (Deferred to v2.0)**:
  - Real-time video telemedicine consultation stream.
  - Direct HL7/FHIR hospital EHR server integration.

