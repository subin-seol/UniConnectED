# Requirements elicitation

- [Requirements elicitation](#requirements-elicitation)
  - [Purpose](#purpose)
  - [1. Questions prepared before the meeting](#1-questions-prepared-before-the-meeting)
  - [2. Key questions answered during client meetings](#2-key-questions-answered-during-client-meetings)
  - [3. Key insights to refine project artefacts](#3-key-insights-to-refine-project-artefacts)

## Purpose

This document summarises the requirements elicitation strategy used by the team to clarify and refine project specifications with UniConnected’s industry partners, across multiple stakeholder interactions.


## 1. Questions prepared before the meeting

Before our meetings, we identified several key questions and assumptions that needed clarification:
### Sprint 2
- Is the **Employment Opportunity Module** equivalent to a pool of opportunities (e.g., part-time, graduate), or does it refer to a single opportunity?
- Is the **Employment Questionnaire** triggered during the opportunity enrollment process or part of onboarding?
- What is meant by **open enrollment** — enrolling into the platform or into a specific opportunity?
- Will organisations be asked to complete a questionnaire like students?
- What is a **University Model**? Is it just a list of recognised institutions with email domains?
- Is the filtering logic for opportunities tightly coupled with the student questionnaire responses?
- Does the onboarding flow occur before or after students enroll in Employment Opportunities?
- Are Employment Opportunities configured as “public” or “invite-only”? How is this technically defined?
### Sprint 3
- What subscription tiers should the platform offer (e.g., free, basic, premium)?
- Is there a free trial period? If so, what's the duration?
- Do users subscribe to the platform or to opportunities? 
- If there is a free trial period, is this full access or are there still some restrictions? 
- What features are locked behind each subscription tier? 

## 2. Key questions answered during client meetings
### Sprint 2
From our 3 client meetings and asynchronous follow-ups, the following points were clarified:

- The **Employment Opportunity** is a single opportunity, not a pool.
- The **questionnaire** is prompted after enrollment and specific to each opportunity.
- **Students self-enroll** into public Employment Opportunities, not into the platform.
- **Email domain restrictions** apply depending on partner university participation.
- **University Model** consists of a name and email domain to validate access.
- **Filtering and questionnaire** are tightly linked; filters work based on questionnaire answers.
- There is **no organisation questionnaire**.
- The **onboarding** flow happens first, followed by opportunity enrollment.
- Employment Opportunities can be **flagged as public or invite-only** at the backend level.
- **Messaging**, **payments**, and **tiered access** are future features under consideration.

### Sprint 3
- Subscriptions follow a monthly versus yearly tier model with pricing flexibility 
- Subscriptions are scoped to the specific opportunity, rather than the platform  
- Role-based subscription levels apply, where students and organisations may different feature access in the future. For the public opportunity, this will simply be paid access for organisations to access the current features whilst students can access for free
- There is a free trial period for new paid users to evaluate the platform, but there should be restrictions based on role (e.g., if organisation, don't reveal any contact information)
- Certain user types can have free access to specific opportunities based on institutional partnerships 
- The free trial period will be 7 days

## 3. Key insights to refine project artefacts
### Sprint 2
- **Enrollment Flow**: The enrollment experience begins after onboarding, triggered via UI tiles; students complete a tailored questionnaire per opportunity.
- **Backend Schema Exists**: Questionnaire data is stored in a JSON schema within the backend; team must integrate this with appropriate API endpoints.
- **Admin Controls**: Admins can define the structure of Employment Opportunities and whether they are public or invite-only.
- **University Access Control**: A University model should be created to validate student access based on domain.
- **API Needs**:
  - Get all public Employment Opportunities.
  - Submit enrollment and questionnaire data.
  - Check enrollment and matching status.
- **UI/UX Ownership**: Team is responsible for designing a clean, accessible enrollment and questionnaire experience, guided by existing Figma prototypes.
- **No Org Questionnaire**: Not required for current scope; org filtering will use static metadata.
- **Extensibility**: System architecture should support future opportunities like research or mentoring.
