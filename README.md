# 🔐 Mobile & Payment App Security Assessment  
**Threat Modeling | SAST | DAST | Risk Analysis**  

---

## 📌 Background

In this project, I assumed the role of **Lead Cybersecurity Specialist at CGL Wellness Inc.**, a fictional private healthcare organization serving **high-net-worth families**. As part of digital transformation:

- A **digital payment app** is being proposed by management to replace semi-manual billing.
- Management is evaluating two **third-party wellness apps** for care delivery:
  - **WeCare App (v2.6.1)**
  - **Wellness Corner App (v6.9)**

### ✨ **Objective**
To assess the security risks of all applications and recommend whether they should be adopted (Go/No-Go decision), while defining required baseline controls.

| Application Type | Methodology | Objective |
|------------------|-------------|-----------|
| In-house Payment App | **Threat Modeling (DFD + STRIDE)** | Identify design-level security risks |
| WeCare App | **SAST + DAST** | Assess mobile app code and runtime risks |
| Wellness Corner App | **SAST + DAST** | Assess mobile app security posture |

---

## 🛠️ Tools & Technologies

| Category | Tools |
|----------|-------|
| Threat Modeling | Microsoft Threat Modeling Tool |
| Static Analysis (SAST) | MobSF |
| Dynamic Analysis (DAST) | OWASP ZAP *(not completed due to technical issues)* |
| Visualization | Draw.io, MS PowerPoint |
| Reporting | MS Word, Excel, PowerPoint |
| Supporting Controls | OWASP MASVS, STRIDE, ISO 27001, OWASP MASTG |

---

## 📍 Threat Modeling – Payment App

### 🧩 Architecture Components
- **Mobile Client (iOS/Android)** → **API Gateway** → **Payment Service**
- **Payment Processor (3rd party)**
- **Identity Provider (OIDC/OAuth2)**
- **Data Stores:** Transaction DB, PII DB, Token Vault
- **Observability:** SIEM, Telemetry, Fraud Engine
- **Admin Portal (separate trust zone)**

### 🔐 Trust Boundaries
- Device ↔ Internet  
- DMZ ↔ Internal Zone  
- Internal ↔ High-Sensitivity Enclave (Vault)

---

### 📊 STRIDE Threat Summary

| Category | Threats | Treatment |
|----------|---------|-----------|
| Spoofing | 2 | Mitigate |
| Tampering | 2 | Mitigate |
| Repudiation | 3 | Mitigate / Accept |
| Information Disclosure | 5 | Mitigate / Transfer |
| Denial of Service | 3 | Mitigate / Accept / Transfer |
| Elevation of Privilege | 2 | Mitigate |
| **Total** | **19** | **Mitigate (12), Transfer (3), Accept (2), Avoid (1)** |

💡 **Conclusion:** *Conditional Go* – Implement priority mitigations before deployment.

---

## 📱 Mobile App Security Assessment (SAST/DAST)

### WeCare App (v2.6.1) – Results

| Severity | Count | Key Issues |
|----------|-------|------------|
| **High** | 22 | Weak crypto, SQL injection, hardcoded secrets |
| **Medium** | 33 | Excessive permissions, sensitive data logs |
| **Low/Info** | 12 | Firebase tracker |

📌 **Risk Score:** 48/100 (Grade B)  
🚨 **Conclusion:** **No-Go** – Requires remediation.

---

### Wellness Corner App (v6.9) – Results

| Severity | Count | Key Issues |
|----------|-------|------------|
| **High** | 88 | Insecure WebView, missing AppLink verification, weak crypto |
| **Medium** | 35 | Insecure storage, RNG issues |
| **Low/Info** | 77 | 11 third-party trackers |

📌 **Risk Score:** 45/100 (Grade B)  
🚨 **Conclusion:** **No-Go** – Severe privacy/compliance concerns.

---

## 📊 Comparative Risk Summary

| Metric | Payment App | WeCare | Wellness Corner |
|----------|-------|------------|------------|
| **Method** | STRIDE | SAST/DAST | SAST/DAST |
| **Total Threats/Vulnerabilities** | 19 | 55 | 123 |
| **Risk Level** | High (Mitigation required) | Medium | High |
| **Recommendation** | Conditional Go | No-Go | No-Go |

---

## 🏁 Final Conclusion

The Payment App may be adopted only after priority mitigations are implemented (authentication, encryption, access control). Both Wellness Apps (WeCare & Wellness Corner) are not suitable for adoption due to significant security risks exposing sensitive health data. Deployment of any app must follow cybersecurity gating aligned with HIPAA, PCI DSS & ISO 27001 controls. Re-testing is required post-remediation before integration.

## 📌 Lessons Learned

Technical risks must be translated into business impact for management.
Time management during executive presentations is crucial.
Completing both SAST and DAST provides a stronger mobile security posture.
Improved significantly in executive communication compared to Task 1.

## 👤 Author

🔹 Francis Uramah

📍 Nigeria

💼 Risk, Threat Intelligence, Application Security

🔗 LinkedIn

 ```md
