# Prototype validation

This document outlines the validation process for the **UniConnected** prototype, focusing on:

- Demonstrated user stories, prototype
- Client feedback from **Client Meeting 4 (28 Aug 2025)**
- Design and backlog updates based on that feedback
  - See figma prototype in Appendix for before and after client feedback


## 📽️ Prototype validation video

Watch the video demonstration here:  
[Click to view the validation video](https://www.canva.com/design/DAGxXxNi1Hk/CGPbfImpeRyiHiGrAkJNrw/watch?utm_content=DAGxXxNi1Hk&utm_campaign=designshare&utm_medium=link2&utm_source=uniquelinks&utlId=hfb81f571cb)

## 1. Edit enrolment in opportunities

**Original user story:**

> “As a student or an organisation, I want to view and edit my enrolment (i.e., join or leave opportunities), so I can manage my participation as circumstances change.”

### Client feedback:

- Supported both *enrollment* and *unenrollment* actions.
- Suggested visibility improvements:
  - Private/invite-only opportunities should only be shown if the user is enrolled.
  - Enrolled opportunities should not appear in the Discover tab.
  - Once unenrolled, the opportunity should reappear in Discover if still eligible.
- Recommended using visual **badges** for public/private status in dropdown filters.

### User story update based on client feedback

As a result of discussion, the above user story was **split into two distinct, clearer stories**:

#### 1.1 View enrolled opportunities  

> [US7] “As a student, I want to view a list of all opportunities I’m enrolled in from my user profile, so that I can keep track of my applications."

#### 1.2 Unenroll from opportunities  

> [US10] “As a student or industry partner, I want to un-enrol from opportunities, so that I’m no longer discoverable and my current opportunities reflect my interests.”

### Backlog updates:

- Original story split for clarity and better task distribution.
- Logic updates:
  - Enrolled opportunities hidden from Discover.
  - Unenrolled opportunities reappear in Discover (if eligible).
- 'Public opportunities' removed from profile display.
- 'Re-enroll' should lead to Questionnaire page.

## 2. Employment questionnaire

**User story:**

> [US1] “As a student, I want to complete an Employment Questionnaire (job type, duration, sector, preferences), so that I can receive relevant matches.”

### Client feedback:
- Simplify the questionnaire into a single-page form.
- Add a **status indicator** for completion.
- Upon completion, user should be redirected to the Discover page.

### Backlog updates:
- User story confirmed by client.
- Reworked into a **single-page layout**.
- Added status tracking for completion.
- Adjusted task complexity in the backlog.

## 3. Enrol in public opportunities

**Original user story:**  
> "As a student or industry partner, I want to enrol in public opportunities, so that I can participate in opportunities open to all users."

**Client feedback:**
- Encourage user-driven selection with more **personalised intent**.
- The team and the client agreed to reframe the user story to align with the client’s emphasis on purposeful engagement and program alignment.

**Updated user story:**  
> [US3] "As a student or industry partner, I want to enrol in public opportunities that interest me, so that I can connect with potential matches and participate in the program."

**Backlog update:**
- User story reworded for clarity and motivation.
- Task complexity unchanged.

## Additional notes from validation meeting

- No need for a homepage — Discover will be the default landing page.
- “Badge” system approved to clarify public vs private opportunities.
- Paywall system postponed until **after Sprint 2**.
- New feature idea: **distance calculation/matching matrix** for student–opportunity fit — to be evaluated in future backlog grooming.
- The use of **Employment Opportunity** as a core opportunity type may be appropriate for our project scope, but this requires further discussion and alignment with the other team.

## Summary of takeaways

- Most of the proposed features were accepted with minor UX suggestions.
- Client appreciated simplicity and clarity; emphasized focus on technical implementation in Sprint 2.
- Future roadmap may include distance-based matching feature and possible paywall discussions.

## Appendix

- 🔗 [Figma Prototype Link](https://www.figma.com/design/2iYdcR4AmusqHoQ3yWvwWU/Prototype?node-id=1-2&t=RmayiUy4kZxoo7vd-1)
- 🧾 Meeting Minutes: [Client meeting 4](Meetings#client-meeting-4)
