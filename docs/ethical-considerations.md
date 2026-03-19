# Ethical Considerations

## Introduction

As a student–industry collaboration platform, **UniConnected** manages sensitive personal data such as student identities, email domains, and opportunity enrollment information.  

This document outlines the **ethical risks**, **mitigation strategies**, and **responsible practices** applied during Sprint 3 to ensure the system is fair, transparent, and privacy-conscious.

---

## Ethical Risk Identification and Management

| Ethical Issue | Primary Risk Type (Team / Tech / Other) | Likelihood (1–5) | Severity (1–5) | Ethical Management Approaches |
|----------------|------------------------------------------|------------------|----------------|--------------------------------|
| “Rush job” – Delivering low quality due to time constraints | Team | 5 | 3 | Discuss sprint scope with client and mentor; prioritise one high-value deliverable; renegotiate timeline if necessary |
| Transmission of student data without encryption | Tech | 1 | 5 | Enforce HTTPS/TLS across all endpoints; store credentials and secrets securely using `.env` |
| Unauthorised access to restricted opportunities | Tech | 3 | 4 | Validate student email domains client- and server-side; restrict APIs using token authentication |
| Potential bias in opportunity visibility or eligibility | Team / Tech | 3 | 4 | Review logic for fairness; ensure all institutions have equal visibility; avoid hard-coded filtering |
| Sustainability trade-offs (e.g., overengineering or wasted computation) | Other | 2 | 2 | Avoid unnecessary features; optimise API calls and component reuse; deploy only essential services |
| Lack of clear consent for data usage | Team / Tech | 2 | 5 | Add explicit consent checkboxes in forms; document data usage in Wiki and user interface |

### Comments and Rationale

- Ethical risks reviewed regularly during sprint retrospectives and client meetings.  
- Four main ethical pillars guided development: **Privacy**, **Transparency**, **Inclusivity**, and **Sustainability**.  
- Prioritisation emphasised privacy and fairness due to the project’s handling of personal and institutional data.  
- Sustainability concerns were considered lower risk but important for long-term efficiency and ethical software use.

---

## Ethical Integration in Design and Development

### Privacy

- **Data Protection:** Personal data encrypted in transit (HTTPS) and stored securely.  
- **Domain Verification:** Prevents exposure of non-partner users’ information.  
- **Frontend Handling:** Questionnaire data stored temporarily in `sessionStorage` and cleared upon refresh.  
- **Consent:** Users explicitly opt in before enrolling.  

**Recommendations:**
- Define a data retention policy.  
- Anonymise analytics data when used for reporting.  
- Implement detailed access logging for sensitive endpoints.

### Transparency

- **Opportunity Visibility:** All opportunities clearly marked as *public* or *restricted*.  
- **User Feedback:** Unauthorised users receive clear, non-discriminatory messages (toast notifications).  
- **Workflow Clarity:** Users preview and review answers before submission.  

**Recommendations:**
- Publish partner university list in UI.  
- Use tooltips/icons for restricted opportunities.  
- Maintain documentation of eligibility logic in the Wiki.

### Inclusivity

- **Equal Access:** Restrictions based on institution only, never personal or demographic factors.  
- **Accessibility:** UI designed for clarity, mobile-friendliness, and WCAG accessibility compliance.  
- **User Support:** Uses plain English and intuitive navigation.  

**Recommendations:**
- Add accessibility preferences (e.g., pronouns, assistive features).  
- Consider translations for international users.  
- Periodically review system logic for fairness and bias.

### Sustainability

- **Optimised Components:** Shared modules (e.g., `FieldRenderer`, `QuestionnaireForm`) reduce redundancy.  
- **Resource Efficiency:** Cached API responses and lightweight React components reduce load.  
- **Deployment:** Uses efficient, scalable hosting environments.  

**Recommendations:**
- Monitor backend load to minimise energy use.  
- Prefer green hosting solutions.  
- Regularly review feature scope to prevent unnecessary builds.

---

## Lessons Learned and Client Impact

- Ethics integrated from **Sprint Planning** through to **Implementation** and **Review**.  
- Scope management prevented rushed or low-quality delivery.  
- Privacy-by-design improved stakeholder trust and compliance with university data policies.  
- The system demonstrates fairness, accessibility, and sustainable operation.

**Client Impact:**
- Increased confidence in ethical handling of student data and enrollment eligibility.  
- Documentation supports transparency and accountability.  
- Provides a foundation for ongoing ethical and privacy compliance in future sprints.


