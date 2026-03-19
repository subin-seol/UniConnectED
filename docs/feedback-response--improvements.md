# Feedback Response & Improvements

This document explains how our team has addressed feedback from mentors.  

- [Feedback Response & Improvements](#feedback-response--improvements)
  - [Sprint 1](#sprint-1)
    - [Project Overview & Scope](#project-overview--scope)
    - [Requirements & User Stories](#requirements--user-stories)
    - [Development Environment & Tool Setup](#development-environment--tool-setup)
    - [User Story Mapping & Sprint 2 Planning](#user-story-mapping--sprint-2-planning)
    - [User Story & Prototype Validation with Industry Partners](#user-story--prototype-validation-with-industry-partners)
  - [Sprint 2](#sprint-2)
    
# Sprint 1

## Project Overview & Scope

### Feedback
- The client’s underlying motivation for pursuing this project is not explained.  
- The high-level scope would benefit from explicitly identifying what is out of scope and providing justifications.  
- There is no need to reference the other team; the background should remain focused on our assigned scope.  
- Some project constraints were mentioned, but not sufficiently detailed or documented.  
- The overview was missing a timeline.

### Actions Taken
- **Client Motivation:** We updated the project overview to include the client’s motivation, explanin why the project is important.  
- **Scope Clarification:** We revised the scope section and it has been updated. Now it explicitly list both in-scope and out-of-scope items, with justifications for exclusions.  
- **Team Focus:** Removed references to the other team to make focus on ourself in the project background.  
- **Constraints:** Added project constraints section to clearly document our (protential) challenge in this project.
- **Timeline:** Added a high-level chart and milestone table in the overview section.


## Requirements & User Stories

### Feedback
- Functional Requirements and Non-Functional Requirements have not been explicitly defined and should be clearly documented (e.g., “The system should …”). While requirements are mentioned in the background, they remain at a high level rather than being explicitly detailed.
- User stories remain at draft status, suggesting incomplete validation and refinement. Consider changing the status.
- Equating story points to fixed units of work confuses them with time estimates; they should capture relative effort and complexity. Consider using standard sizing methods.
- Justifications for the chosen story points and priorities should be included in the user story details. This helps show the reasoning behind your estimates and makes the backlog more transparent.
- Consider splitting the table into two—one for each epic—for improved clarity and readability.

### Actions Taken
- **Functional Requirements and Non-Functional Requirements:** Adding a new page for `Functional Requirements and Non-Functional Requirements`, explain the functional requirements for each user story in detail, and non-functional requirements for the whole system.
- **User Stories Status:** Updated the user stories status. All the user story should be validated. 
- **Story Point:** Now we used fibonacci number for user story point to better estimate the size of a story to avoid confusion.
- **Justifications For User Story:** Now each user story has justification for the estimation and priority.
- **Splitting The Table:** The user story overview table has been splited into two epics based on the discussion with our client.


## Development Environment & Tool Setup

### Feedback
- The README needs improvement, as it currently appears barebones rather than serving as a professional introduction to the repository.
- Workflow and branching strategies should be expanded further. For example, when creating a branch off develop, what naming convention should be followed? Is there a commit guideline? How does a task flow from Backlog → Done?
- Include details about the tech stack used in the client’s repository under a “Developer Environment” section
- Review process: Document PR requirements further (reviewers, checks, Definition of Ready (DoR) and Definition of Done (DoD) ). Show evidence of reviews on issues/PRs (e.g., reviewer comments like “LGTM,” requested changes, approvals).

### Actions Taken
- **README file:** Update the README file, having more information to the repository.
- **Workflow and branching strategies:** The workflow and branching strategies are explaned further in the development process document.
- **Tech Stack:** Update "Technologies used" section and rename it to "Developer Environment" section under project overview.
- **Review process:** Document the detial review process in the development process document.



## User Story Mapping & Sprint 2 Planning


### Feedback
- Task breakdowns should not include story points, estimation is better applied at the user story level.
- Mention if internal dependencies between the user stories exist.
- User stories remain at draft status, suggesting incomplete validation and refinement. Consider changing the status.
- Capacity planning has not been clearly addressed—how was the number of user stories for the sprint determined?
- Adding a clear sprint goal would help give the team better direction and alignment.
- There’s no need to add product handover in the user story map

### Actions Taken
- **Task breakdowns:** Instead of using story point, the estimation now is the estimation time of finishing the task.
- **Internal Dependencies:** Modify the dependency section in the task breakdown.
- **User Stories Status:** Update User story status, align with our current progress.
- **Capacity Planning:** Add a capacity planning section under the Sprint 2 planning.
- **Spring Goal:** Update the spring 2 goal. Now it should be clear to give a better understanding to the reader what is our direction in the sprint. 
- **User Story Map:** Update the user story map: Remove the handover section.



## User Story & Prototype Validation with Industry Partners

### Feedback
- The video feels a little abrupt with its cuts, making it somewhat choppy. A clearer structure would improve the flow—start by presenting a user scenario to set the context, then guide the client to work through that scenario. At the moment, it jumps straight into the client using the system.

### Actions Taken
- **Video:** Apply feedback to the next video.




# Sprint 2

## Project Documentation & Organisation

### Feedback
- Not all documentation has been exported to the repository (ie product deployment) ZIP, so make sure all relevant files are included.
- The changelog has not been updated for Sprint 2 and should reflect the latest progress.
- There is duplicated content for “Sprint 2 Retrospective” under both Ceremonies and Team Meetings, so consider consolidating it.
- Move reusable templates to a separate TEMPLATES.md file to keep main documentation pages clean and focused.
- There's a lack of testing documentation (e.g., test cases, unit tests, or plans). Including these would improve visibility into quality assurance.

### Actions Taken
- **Documentation:** Include all relevant files into repository ZIP
- **Changelog:** Update Changelog
- **Duplicated content:** Remove the content from the Team meeting.
- **Templates:** Remove the template from the documentation pages to keep them clean.
- **lack of testing documentation:** Add [test-case file](test-cases)

## Agile Task & Progress Management

### Feedback
- The burn-up chart suggests that most issues were moved to “Done” very close to the deadline. The team should improve workflow by completing and reviewing tasks more consistently throughout the sprint, avoiding last-minute rushes, and maintaining a more balanced and incremental delivery pace.

### Actions Taken
- **Improve workflow:** try to move tasks more consistently, but in sprint 3, everyone is quite busy, so the tasks might still finish late.


## Code Review & Quality Assurance

### Feedback
- While engagement with the AI and client teams is strong, there should be more peer-to-peer code reviews within the team to encourage cross-learning and shared ownership.

### Actions Taken
- **More peer-to-peer:** Add more peer-to-peer evidence in [code-review](code-reviews)

## Product Demonstration & Deployment

### Feedback 
- Ensure the product demo video is easily accessible and properly linked.
- The video felt a bit fast-paced, making it difficult to follow, consider slowing down the narration or pacing to make the demonstration clearer and easier to understand.

### Actions Taken
- **Access of demo video:** ensure the video link is properly placed on the git wiki [product-demo](product-demo) by `git pull`ing most recent changes
- **Video fast-paced:** Try do slow down the pace in the video



