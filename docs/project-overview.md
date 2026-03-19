# Project overview

- [Project overview](#project-overview)
  - [Project background](#project-background)
  - [Project goal](#project-goal)
  - [Client motivation](#client-motivation)
  - [Project scope](#project-scope)
    - [In scope](#in-scope)
    - [Out of scope](#Out-of-scope)
  - [Project Constraints](#project-constraints)
  - [Technologies used](#technologies-used)
  - [Our client](#our-client)

## Project background

UniConnected is a platform aimed at bringing together students, alumni, academics, and organisations to explore and discover opportunities that enrich careers and lives. In the first pilot conducted in early 2025, the UniConnected team created an opportunity for the Masters of Teaching Student Internship (MTSI) program which allowed students to connect with schools and educational institutions for internship placements. However, this pilot was limited to only the MTSI program and can only join by invitation.

The next stage of UniConnected is to extend from signle curriculum-based opportunity into real employement opportunites, allowing different students and organisations to make matches for casual, part-time, full-time or graduate roles. This evolution reflects the platform’s broader vision of supporting multiple types of opportunities across diverse domains, eventually creating a comprehensive platform for student and organisation connections.

## Project goal

The main goal of this project is to extend the UniConnected platform with a new opportunity module called the "Employment Opportunity" which allows students from a select number of universities to connect with potential employers and explore job opportunities. The goal is to not be like a job board, but rather a platform that **facilitates meaningful connections** and interactions between students and employers. We hope to make a measurable impact with at least 10 successful student-employer connections by the end of the year.


## Client Motivation

The client aims to expand UniConnected's value from a curriculum-based pilot into an open-enrolment, scalable opportunity matching platform. Key motivations include:
* To **scale platform impact** beyond the MTSI pilot program to support real employment opportunities, enabling students from both partner and non-partner universities to seek matches
* To **reverse traditional employment processes** and distinguish themselves from commercial job boards, by offering students a trusted platform through user onboarding and verification processes that validate institutional affiliations 
* **Build the foundation for further expansion** to support further opportunity types, including employment, curriculum-linked opportunities, mentorship, and research and entrepreneurship

## Project scope

### In-Scope
* A new **employment opportunity** that allows open-enrolment for student and organisations, with optional domain restrictions and a customisable questionnaire workflow
* **Subscription management** including monthly and yearly subscription tiers, role-based subscription levels, and free trial implementation without access limitations
* **Supporting existing infrastructure** including API documentation, Swagger specifications, and comprehensive unit tests for all added functionality. Additionally, bug fixes as needed to support core functionality are also in-scope

Additionally, the client has expressed interest in location-based matching to enhance matching criteria through proximity, but prefers this as a stretch goal (i.e., the focus will be on public opportunities and subscription features).

### Out-of-Scope
* **Job advertising functionality** as this platform focuses on curated opportunities and matching rather than broad advertising, and should be distinct from other job boards
* Platform **message communication** system, which although mentioned in the initial briefing, has been deferred by the client due to project timeline constraints
* **Platform deployment**, which will be handled by our client

## Project Constraints

1. **Technical unfamiliarity**, given our team has limited prior experience with Django framework (i.e., as identified by our skill matrix), this may require additional learning time and could slow backend development velocity
2. **Parallel implementation and task dependencies** as both teams (UC-Koala and UC-Wombat) are working on the same epic across sprints, therefore any work division requires consistent communication and alignment to avoid integration issues and maintain code quality. Additionally, despite workload division to minimise dependencies, features like matching algorithm integration and user visibility controls may create inter-team dependencies that require careful coordination and task prioritisation to prevent blockers from arising
3. Team **access to the client repository** was granted only at Sprint 2 start, which meant additional time was required for codebase familiarisation, potentially impacting planned timeline alignment


## Our client

| Name          | Role         | Description                                                  | Email                        | Links                                         |
|---------------|--------------|--------------------------------------------------------------|------------------------------|-----------------------------------------------|
| Bassam Jalgha | Tech Lead    | First point of contact for technical details of UniConnected | bassam@uniconnected.com      | [LinkedIn](https://www.linkedin.com/in/bassamjalgha)      |
| Amanda Samson | Project Lead | Responsible for the project vision                           | amanda.samson@unimelb.edu.au | [LinkedIn](https://www.linkedin.com/in/dr-amanda-samson/) |

<!-- ## Timeline

- **Phase 1:** Research & Planning (dd/mm/yyyy - dd/mm/yyyy)
- **Phase 2:** Development (dd/mm/yyyy - dd/mm/yyyy)
- **Phase 3:** Testing & Deployment (dd/mm/yyyy - dd/mm/yyyy) -->
