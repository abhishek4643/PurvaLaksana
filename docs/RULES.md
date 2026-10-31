# Engineering Rules & Standards
### Purva Laksana — Code Conventions, Deep Learning Guardrails, and Patient Privacy

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=rect&color=gradient&customColorList=12,20,26&height=8&section=header&width=100%" width="100%" />
</div>

This document specifies the non-negotiable coding conventions, PyTorch execution rules, and patient data confidentiality guardrails governing the **Purva Laksana** healthcare platform.

---

## 1. PyTorch & Computer Vision Guardrails

### 1.1 Mandatory `torch.no_grad()` and `.eval()`
- All model inference routines MUST execute inside a `torch.no_grad()` context with the model set explicitly to evaluation mode:
  ```python
  # CORRECT
  model.eval()
  with torch.no_grad():
      output = model(input_tensor)
      probabilities = torch.softmax(output, dim=1)
  ```
- Failure to disable gradient tracking wastes GPU/CPU RAM and degrades inference latency.

### 1.2 Model Weight Caching with `@st.cache_resource`
- PyTorch model weights (`.pt`) MUST be loaded using Streamlit's `@st.cache_resource` decorator:
  ```python
  @st.cache_resource
  def load_bone_model():
      model = torch.load("bone.pt", map_location=torch.device('cpu'))
      model.eval()
      return model
  ```
- NEVER load model weights inside the raw script execution body, as this forces reload on every UI interaction.

### 1.3 Device Agnostic Tensor Execution
- All tensor transformations must dynamically adapt to GPU availability:
  ```python
  device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
  input_tensor = input_tensor.to(device)
  ```

---

## 2. Patient Privacy & Healthcare Compliance

### 2.1 Ephemeral In-Memory Image Handling
- Patient medical scans (X-rays, MRIs, fundus photos) MUST remain strictly in volatile memory.
- NEVER write uploaded patient images to local disk directories (`/tmp` or root repo) unless explicitly requested for local debug tests.

### 2.2 Mandatory Clinical Assistive Disclaimer
- Every diagnostic view and generated report MUST display the official assistive screening disclaimer:
  > **Clinical Disclaimer**: *Purva Laksana is an AI-assisted preliminary triage tool designed to support, not replace, certified clinical evaluation. All outputs must be validated by a licensed physician before clinical decision-making.*

---

## 3. Streamlit & Python Code Style

### 3.1 Type Annotations & Clean Structuring
- Functions performing tensor transformations, feature scaling, or Google Fit API parsing MUST declare type hints:
  ```python
  def preprocess_scan(image_bytes: bytes, target_size: Tuple[int, int] = (224, 224)) -> torch.Tensor:
      ...
  ```
- Separate UI rendering logic from deep learning inference subroutines. Place reusable computer vision helpers in `vision_analyzer.py`.

