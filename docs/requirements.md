# Functional and Non-Functional Requirements

## Functional Requirements

### Epic 1: Employment opportunity and questionnaire

* Create Employment Questionnaire (US1)

    - The system shall provide a questionnaire (job type, duration, sector, preferences) when a student enrols in an employment opportunity
    - The system shall store questionnaire responses in JSON format in the backend
    - The system shall allow students to review responses before submission
    - The system shall allow custom questionnaires to be created by the coordinator

* Update Questionnaire and Opportunity-Specific Information (US2)

    - The system shall allow students or industry partners to update previously submitted questionnaire responses from their profile and store these updated responses 

### Epic 2: Open-enrollment into opportunity

* Public Enrollment (US3)

    - The system shall allow students and industry partners to enrol into public opportunities
    - The system shall show enrolment status once a user has joined an opportunity

* Partner University Student Enrollment (US4, US5)

    - The system shall validate email domains to differentiate partner vs non-partner universities
    - The system shall allow only partner university students to enrol in public domain-restricted opportunities
    - The system shall reject a non-partner univerisity student to enrol in a partner-specific opportunities
    - The system shall show a clear message to non-partner university students explaining access restrictions

* Opportunity Visibility (US6)

    - The system shall allow admins to mark opportunities as public or invite-only
    - The system shall ensure public opportunities appear in the discover page
    - The system shall ensure private opportunities can be seen by invited users only

* Viewing Enrolled Opportunities (US7)

    - The system shall allow students and industry partners to view all opportunities they have enrolled in
    - The system shall allow students and industry partners to view all opportunities they have cancelled enrolment in
    - The system shall show details of each opportunity and allow user to view questionnaire responses


* Opportunity Description Page (US9)

    - The system shall display a description page for an opportunity before a user enrols
    - The system shall not display any opportunity participant information before the user enrols

* Cancel Enrollment (US10)

    - The system shall allow users to un-enrol from opportunities
    - The system shall provide a confirmation modal before un-enrolment
    - The system shall move un-enrolled opportunities to the "Cancelled" section and remove participants from match lists immediately
    - The system shall allow users to re-enrol if still eligible

* Distance-Based Display and Sorting (US11, US12)

    - The system shall able to automatic calculate distance based on the two locations
    - The system shall able to sort opportunity for student by distance (nearest first)
    - The system shall able to sort student for organisation to match by distance (nearest first)
    - The system shall allow users to update their location in their profile
    - The system shall display the calculated distance (in kilometres) for each match

### Epic 3: Opportunity Subscription

* Subscribe with Monthly vs Yearly Tiers (US13)

    - The system shall allow users to subscribe to an opportunity with both monthly and yearly subscription tiers
    - The system shall integrate with Stripe payment gateway to handle subscription checkout and payment
    - The system shall store the subscription plan type (monthly vs yearly) in the backend
    - The system shall automatically charge the user according to their selected billing cycle
    - The system shall display the current subscription plan in the user’s profile page

* Role Subscription Levels (US14)

    - The system shall provide different subscription levels for different user types (e.g., student, organisation)
    - The system shall restrict users to only see subscription levels applicable to their role
    - The system shall assign the correct subscription entitlements once the user subscribes
    - The system shall have a frontend page for users to select their subscription

* Free Access for Certain User Type (US15)
    - The system shall allow certain user types to access opportunities for free
    - The system shall validate user eligibility for free access based on their role

* Subscription Level Specific to Role (US16)

    - The system shall define subscription levels specific to each user role
    - The system shall ensure that users are automatically assigned to the correct role-specific subscription level
    - The system shall restrict access to only the features included in the user’s subscription level
    - The system shall display the details of each subscription level (price, features, benefits) before checkout or in the detail page.
    - The system shall provide a free trial period for new subscriptions, showing the trial end date in the subscription details


## Non-functional requirements

* **Performance**: 
    - The system should be able to handle 1000 concurrent users without significant performance degradation.
    - The system frontend page load time should not exceed 2000 ms.
* **Security**: 
    - User data must be protected according to industry standards, including encryption and secure access controls.
    - The system should ensure the correct access control by different user roles (student, partent, coordinator)
    - The subscription payment must be secure and no data leakage happen.
* **Usability**: 
    - The platform should be intuitive and easy to use, with a focus on user experience.
    - The system shall display clear and easy-understanding message alert.
* **Scalability**: 
    - The architecture should support future growth in user numbers and functionality.
    - The system should support new opportunity types instead of just MTSI. 
* **Reliability**：
    - The system should have proper error handling ability, no data lost such as questionnaire response if system recover from failure.
* **Availability**:
    - The system shall maintain high availability. It should not be down due to user input errors, bugs or system maintenance.