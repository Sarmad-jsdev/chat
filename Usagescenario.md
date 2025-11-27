# Access Form — Usage Scenarios

**Author:** Malik Sarmad  
**Project:** Access Form — Accessible web-based survey builder  
**Last Updated:** 2025-11-27

---

## Table of Contents
- [1. Admin Use Cases](#1-admin-use-cases)  
- [2. Form Creator Use Cases](#2-form-creator-use-cases)  
- [3. Respondent Use Cases](#3-respondent-use-cases)  
- [4. Common / System Use Cases](#4-common--system-use-cases)  

---

## 1. Admin Use Cases

### Table 1 — Admin Usage Scenarios

| Use Case Title | Use Case ID | Actions | Description | Alternative Paths | Pre-Conditions | Post-Conditions | Author | Exceptions |
|---|---:|---|---|---|---|---|---|---|
| **Manage Users** | ADM-01 | Add user, Edit user, Delete user | Admin manages platform users: create, update roles and delete accounts. | Duplicate user → show warning; invalid input → validation error. | Admin is authenticated. | User record created/updated/deleted in database. | Malik Sarmad | Invalid email, duplicate user, DB error. |
| **Manage Forms** | ADM-02 | View forms, Edit forms, Delete forms | Admin monitors and moderates forms created by creators. | Form locked → show message; missing permissions → deny action. | Admin is authenticated. | Form metadata updated or removed. | Malik Sarmad | Form locked, DB error, permission denied. |
| **Monitor Accessibility Compliance** | ADM-03 | Run accessibility check, review reports | Admin ensures forms follow accessibility standards (ARIA, WCAG, alt text, captions). | If automated checks fail → flag for manual review. | There is at least one published form. | Compliance report generated; issues flagged. | Malik Sarmad | Missing ARIA tags, incomplete metadata. |
| **View Analytics / Reports** | ADM-04 | Open analytics, apply filters, view dashboards | Admin reviews site-wide analytics for forms and responses. | Filters return no data → show empty state; request timed out → retry. | Analytics data exists. | Dashboard shows filtered data; export possible. | Malik Sarmad | Timeout, insufficient data, permission issues. |
| **Export CSV / Excel / PDF** | ADM-05 | Select format, generate export, download | Admin exports reports in selected file formats for offline analysis. | Export large dataset → generate asynchronously; generation fails → retry. | Filtered data available. | File generated and available for download. | Malik Sarmad | File generation error, storage or permission error. |

---

## 2. Form Creator Use Cases

### Table 2 — Form Creator Usage Scenarios

| Use Case Title | Use Case ID | Actions | Description | Alternative Paths | Pre-Conditions | Post-Conditions | Author | Exceptions |
|---|---:|---|---|---|---|---|---|---|
| **Create Form** | FC-01 | Open builder, add question types, reorder, preview, save | Creator builds a form using drag-and-drop or manual editor (MCQ, text, rating, file upload). | Save as draft; invalid question → show validation. | Creator is authenticated. | Form saved as draft or published in DB. | Malik Sarmad | Network interruption, invalid input, DB error. |
| **Enable Accessibility Features** | FC-02 | Enable keyboard navigation, add ARIA labels, provide alt text, add captions, apply high-contrast theme | Creator applies accessibility settings to make the form usable for people with disabilities. (This use case is included in Create Form.) | Skip optional accessibility fields → system shows a compliance warning. | Form exists in editor. | Accessibility metadata stored with the form; form validated for basic accessibility. | Malik Sarmad | Missing captions/alt text, unsupported media format. |
| **Share Form** | FC-03 | Publish form, generate link, send via email/SMS, copy link | Creator distributes the published form to respondents via web link, email, or SMS. | Share method fails (email/SMS gateway) → retry or provide manual link. | Form must be published. | Respondents receive access link; form reachable. | Malik Sarmad | Invalid contact, gateway failure, expired link. |
| **View Responses / Analytics** | FC-04 | Open responses dashboard, apply filters, inspect responses | Creator inspects collected responses using tables and charts. | No responses → display empty state; heavy queries → use pagination. | At least one response exists. | Creator views or analyzes responses; may export data. | Malik Sarmad | Large dataset performance issues, permission issues. |
| **Export Data (CSV/Excel/PDF)** | FC-05 | Select format, export responses, download file | Creator downloads responses for offline use or reporting. | Partial export (selected columns) or full export; export fails → retry. | Responses are available. | Downloadable file generated. | Malik Sarmad | File size limits, generation errors. |

---

## 3. Respondent Use Cases

### Table 3 — Respondent Usage Scenarios

| Use Case Title | Use Case ID | Actions | Description | Alternative Paths | Pre-Conditions | Post-Conditions | Author | Exceptions |
|---|---:|---|---|---|---|---|---|---|
| **Fill Form** | RES-01 | Open link, answer questions, use keyboard or voice input | Respondent completes a form via browser or supported device. Voice input available as an extended option (speech-to-text). | Save progress and resume later; switch between input modes. | The form link is valid and accessible. | Responses temporarily saved (if draft) or prepared for submission. | Malik Sarmad | Browser incompatibility, network issues, unsupported media. |
| **Submit Form** | RES-02 | Validate fields, press submit, receive confirmation | Respondent finalizes and submits the filled form to the system. | Validation errors → highlight missing fields; submission retry on failure. | Required fields completed (or flagged). | Final response stored in the database; confirmation shown. | Malik Sarmad | Server timeout, duplicate submission, validation failures. |
| **Use Accessibility Features** | RES-03 | Activate screen reader, enable high-contrast theme, enable captions, keyboard navigation | Respondent uses built-in accessibility options for easier interaction. | If device lacks support → degrade gracefully to best-available mode. | Respondent device/browser supports at least one accessibility option. | UI adapts to chosen accessibility settings for the session. | Malik Sarmad | Screen reader incompatibility, media without captions. |

---

## 4. Common / System Use Cases

### Table 4 — System-Wide Usage Scenarios

| Use Case Title | Use Case ID | Actions | Description | Alternative Paths | Pre-Conditions | Post-Conditions | Author | Exceptions |
|---|---:|---|---|---|---|---|---|---|
| **Authenticate User (Login/Logout)** | SYS-01 | Enter credentials, submit, receive session token; logout ends session | All actors must authenticate to access protected features; supports password login and OAuth/SSO if configured. | Wrong password → retry; Forgot password → password recovery flow; SSO failure → fallback to email login. | User account exists (or SSO account) and system reachable. | Valid session created; unauthorized access prevented. | Malik Sarmad | Authentication service down, account locked, invalid credentials. |
| **Store Responses** | SYS-02 | Persist response payload to DB, acknowledge storage | System securely stores incoming responses and associates metadata (timestamp, respondent id if known). | If DB write fails → retry or queue for later; store in temporary buffer. | System database operational. | Response persisted and available for analytics/export. | Malik Sarmad | DB outage, write errors, storage limit reached. |
| **Export Data** | SYS-03 | Read filtered responses, format into CSV/Excel/PDF, provide download | System prepares export files for Admins and Creators. | For very large exports → generate asynchronously and notify user when ready. | Filter criteria defined; permissions verified. | Export file generated and link provided for download. | Malik Sarmad | Export job fails, timeouts, insufficient memory. |

---

## Notes & Next Steps

- The above tables cover **main use cases** required for an SRS and for academic grading.  
- If you want, I can **expand** this file to include:
  - Detailed **sub-use case** tables (keyboard navigation, alt text, captions, etc.)  
  - Full **Use Case Narratives** (step-by-step scenarios) for each use case  
  - **PlantUML** or **SVG** code to render the diagram automatically  
  - A downloadable **PDF** version of this file

---

**End of file — `UsageScenarios.md`**
