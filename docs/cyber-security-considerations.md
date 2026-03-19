# Cyber Security Considerations

## Introduction

This document outlines **threat modeling for Sprint 3** of the **UniConnected** project using the **STRIDE framework** (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege).

As UniConnected connects students to verified university opportunities, the system manages sensitive personal and financial data through **Stripe** integration and authenticated enrollments. We proactively analysed potential vulnerabilities, implemented mitigation measures, and formulated **architecture-level recommendations** to ensure ongoing security and scalability.

---

## 1. Identified and Documented Potential Security Threats

### Threat Analysis Conducted
We identified several risks relevant to our Django + React stack:

- Unauthenticated or unauthorised users accessing restricted opportunities  
- Exposure of **Stripe webhook endpoints** to forgery or replay attacks  
- Abuse of **admin privileges** through misconfigured role or token policies  
- Data manipulation via unvalidated questionnaire or enrollment payloads  

### Mitigation Approaches

- **Stripe Webhook Security:** Validated webhook signatures using `STRIPE_WEBHOOK_SECRET` and event timestamp checks.  
- **Authentication Enforcement:** Only authenticated users can initiate payment sessions and enrollments.  
- **Domain Restrictions:** Enforced university-specific access (`@unimelb.edu.au`) both client- and server-side.  
- **Rate Limiting:** Implemented DRF throttling to prevent repeated enrollment or webhook spam.  

## 2. Secure Coding Practices

### Input Validation
- All API requests validated using **Django REST Framework serializers**.  
- Defensive coding patterns used across forms and endpoints (e.g., checking for nulls, malformed payloads, invalid domains).  
- Sanitised all user inputs to prevent SQL/XSS injection.

### Secrets and Environment Variables
- Sensitive credentials stored securely in `.env`.  
- `.env` excluded from version control via `.gitignore`.  

### API Security
- Stripe integration uses **server-side session creation** with verified price IDs.  
- Webhooks validated through Stripe signature headers.  
- HTTPS enforced for all backend routes; HTTP automatically redirected.

## 3. Authentication and Access Control

### Frontend Access
- Unauthorised domains receive **toast feedback** (“This opportunity is not available for your university”).  
- Enrollment and profile features gated behind authentication.  
- Form data cached only in `sessionStorage` for UX continuity but not persisted permanently.  

### Backend Access Control
- **Token-based Authentication:** Sensitive endpoints (e.g., enrollment, Stripe session creation) protected via DRF `TokenAuthentication`.  
- **Role-Based Permissions:** Admin actions restricted to verified users.  
- Tokens invalidated on logout; secure cookie flags (`HttpOnly`, `Secure`) enforced.

## 4. Third-Party Libraries and Integrations

### Stripe Integration
- Used the **official Stripe SDK** for session handling and webhook processing.  
- Webhook listens only to relevant events: `checkout.session.completed`, `customer.subscription.updated`.  
- Sensitive payloads omitted from logs to prevent accidental data exposure.  

### Dependency Safety
- Ran `pip list --outdated` and `npm audit` to identify outdated and vulnerable packages.  
- Reviewed open-source licenses and any CVEs when deciding what version of dependencies to introduce to codebase.  

---

## Threat Identification with STRIDE

| ID     | STRIDE Category        | Affected Component                 | Threat Description                                                                                                 | Potential Impact                                    | Attack Vector                               | Likelihood (1–5) |
|--------|------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------|---------------------------------------------|------------------|
| **T1** | Spoofing               | Authentication / Enrollment        | Weak or missing email-domain validation could allow non-partner users (e.g., RMIT) to impersonate UniMelb students | High – Unauthorised access                          | Forged or manipulated email domains         | 4                |
| **T2** | Tampering              | Enrollment / Questionnaire APIs    | Insufficient backend validation could allow modified payloads or injection                                         | Medium – Data corruption / unauthorised enrollments | Malicious API requests                      | 3                |
| **T3** | Repudiation            | Enrollment Logs                    | Lack of audit logging prevents activity traceability                                                               | Low – Limited accountability                        | N/A                                         | 2                |
| **T4** | Information Disclosure | Stripe Integration and API Endpoints | Sensitive credentials or PII could leak via logs or HTTP                                                           | High – Data / financial leak                        | Misconfigured `.env` or unencrypted traffic | 5                |
| **T5** | Denial of Service      | Enrollment / Webhook Endpoints     | High-volume requests may overload backend                                                                          | Medium – Temporary downtime                         | Repeated POST / webhook replay              | 3                |
| **T6** | Elevation of Privilege | Admin Routes / Token Management    | Weak role checks may allow admin access                                                                            | High – System control                               | Tampered JWT or role exploit                | 3                |

---

## Mitigations and Validation

| ID     | Planned Mitigations                           | Integration with Sprint 3                                 | Status        | Validation Results                                        |
|--------|-----------------------------------------------|-----------------------------------------------------------|---------------|-----------------------------------------------------------|
| **T1** | Enforce domain validation client and server     | Implemented via `domainEligibility.ts` and backend checks | Implemented   | Verified: unimelb.edu.au (allowed), rmit.edu.au (blocked) |
| **T2** | Validate input via serialisers and sanitisation | Applied to all POST endpoints                             | Implemented   | Invalid payloads rejected safely                          |
| **T3** | Add audit logging for enrollments             | Not planned or prioritised yet                            | Not Scheduled | Acknowledged as a future improvement                      |
| **T4** | Secure Stripe keys, verify webhooks, and HTTPS  | Integrated and tested with Stripe CLI                     | Implemented   | No data leaks detected                                    |
| **T5** | Add rate-limiting middleware                  | DRF throttling enabled                                    | Partial       | Needs integration with key endpoints                      |
| **T6** | Strengthen role checks and token auth         | Applied to admin / enrolment routes                      | Implemented   | Unauthorised access blocked                               |

---

## Comments and Rationale

- **Repudiation (T3)** deferred due to lower risk and limited time.  
- All STRIDE categories considered relevant to the web application scope.  
- Highest priority threats (T1 and T4) directly mitigated during Sprint 3.  
- Attack vectors tested included webhook replay, payload tampering, and domain spoofing.
- In production, Stripe webhooks will be securely received via a public HTTPS endpoint behind a reverse proxy or cloud gateway (e.g., AWS, Heroku). CLI forwarding is only used for local testing.


---

## Lessons Learned and Client Impact

- **Prevented unauthorised enrolments** through dual domain validation and token auth.  
- **Secured financial flows** via verified Stripe webhooks and environmental secret handling.  
- **Improved system stability** with throttling and safe error responses.  
- **Reinforced data privacy** alignment with Australian standards and university policies.  

**Client Impact**
- Builds trust by demonstrating robust security for student data and payments.  
- Ensures production-readiness for future deployment.  
- Provides a repeatable threat-modeling framework for Sprint 4 handover.

---
