# Design System
### Purva Laksana — Clean. Simple. Productive.

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=rect&color=gradient&customColorList=12,20,26&height=8&section=header&width=100%" width="100%" />
</div>

This document defines the visual design system, UI components, design tokens, and clinical user experience standards for the **Purva Laksana** multi-organ healthcare diagnostic platform. The goal is to establish an authoritative, clear, and calming clinical interface across medical imaging viewers, biometric telemetry widgets, and risk reports.

---

### 1. Design Principles

<p align="center" style="margin: 20px 0;">
  <img src="./principles.svg" alt="Purva Laksana Design Principles" width="100%" />
</p>

---

### 2. Color Palette
*Primary colors used across the clinical interface, diagnostic models, and vital tracking dashboards:*

<p align="center" style="margin: 20px 0;">
  <img src="./palette.svg" alt="Purva Laksana Design System Color Palette" width="100%" />
</p>

---

### 3. Typography
*We use Inter as the primary interface font and JetBrains Mono for diagnostic confidence scores and biometric telemetry:*

<div style="background-color: #0D1117; border: 1px solid #30363D; border-radius: 8px; padding: 18px 20px; margin: 14px 0;">
  <table width="100%" cellpadding="0" cellspacing="0" border="0">
    <tr>
      <td width="90" align="center" style="font-size: 40px; font-weight: 800; background-color: #161B22; color: #818CF8; border: 1px solid #30363D; border-radius: 8px; padding: 8px 12px;">Aa</td>
      <td style="padding-left: 20px;">
        <div style="font-size: 18px; font-weight: 700; color: #F0F6FC;">Inter &amp; JetBrains Mono</div>
        <div style="color: #818CF8; font-size: 12px; font-weight: 600; margin-top: 2px;">Primary clinical font family</div>
        <div style="color: #8B949E; font-size: 12px; margin-top: 4px;">Clean, modern, and highly legible across clinical summaries, biomarker tables, and diagnostic scans.</div>
      </td>
    </tr>
  </table>
</div>

| Role | Font Family | Size / Weight | Usage |
| :-- | :-- | :-- | :-- |
| **Clinical Title** | Inter | 24px / 700 Bold | Streamlit main page headers |
| **Section Header** | Inter | 18px / 600 Semi-Bold | Organ diagnostic module titles |
| **Body Regular** | Inter | 14px / 400 Regular | Clinical guidance, findings, and explanations |
| **Biometric Mono** | JetBrains Mono | 12px / 600 Semi-Bold | Heart rate (BPM), blood pressure (mmHg), confidence (%) |

---

### 4. UI Components & Visual Tokens

#### 4.1 Diagnostic Triage Status Badges

| Classification | Background | Text Color | Border | Meaning |
| :-- | :-- | :-- | :-- | :-- |
| **NORMAL / LOW RISK** | `#ECFDF5` | `#059669` | `1px solid #A7F3D0` | Scan exhibits no detectable pathology ($\ge 90\%$ healthy) |
| **BORDERLINE / REVIEW** | `#FFFBEB` | `#D97706` | `1px solid #FDE68A` | Ambiguous features; secondary physician review advised |
| **HIGH RISK ANOMALY** | `#FEF2F2` | `#DC2626` | `1px solid #FECACA` | High-confidence pathological lesion detected |

#### 4.2 Biometric Telemetry Card

<div style="background-color: #0D1117; border: 1px solid #30363D; border-radius: 8px; padding: 18px 20px; margin: 14px 0;">
  <div style="display: flex; justify-content: space-between; align-items: center;">
    <div>
      <span style="font-size: 11px; font-weight: 600; color: #8B949E; text-transform: uppercase; letter-spacing: 0.05em;">Live Biometrics &bull; Google Fit</span>
      <div style="font-size: 22px; font-weight: 700; color: #F0F6FC; margin-top: 4px;">Resting Heart Rate: 72 BPM</div>
    </div>
    <div style="text-align: right;">
      <span style="background-color: #064E3B; color: #34D399; border: 1px solid #059669; padding: 4px 10px; border-radius: 12px; font-size: 11px; font-weight: 600;">CARDIAC STATUS: OPTIMAL</span>
      <div style="font-size: 11px; color: #8B949E; margin-top: 6px;">BP: <code style="color: #818CF8;">120/80 mmHg</code> &bull; Synced 2m ago</div>
    </div>
  </div>
</div>

