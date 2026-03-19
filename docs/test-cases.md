# Test cases

This file will contain the test cases we used to test our implemented functionalities. These tables was generated with the assistance of generative AI. 

### [PR#88](https://github.com/uniconnected/uniconnected-django/pull/88)
| Name | Description | Expected Output |
|------|--------------|-----------------|
| `test_opportunity_default_visibility_is_public` | Verify that newly created opportunities default to public visibility. | `visibility=PUBLIC`; `get_visibility_display()="Public"` |
| `test_opportunity_can_be_created_as_private` | Verify that opportunities can be explicitly created with private visibility. | `visibility=PRIVATE`; `get_visibility_display()="Private"` |
| `test_visibility_choices_values` | Verify that the `VisibilityChoices` enum values are correct. | `PUBLIC=1`; `PRIVATE=2` |
| `test_visibility_choices_labels` | Verify that the `VisibilityChoices` enum labels are correct. | Choice labels: `1 → "Public"`, `2 → "Private"` |
| `test_filter_opportunities_by_visibility` | Verify that filtering by visibility correctly separates public and private opportunities. | Public query returns only public items; private query returns only private items. |
| `test_serializer_includes_visibility_fields` | Verify that the serializer includes both `visibility` and `visibility_display` fields. | Serialized data contains `visibility` and `visibility_display`; matches expected values. |
| `test_serializer_handles_private_visibility` | Verify serializer correctly represents private visibility opportunities. | `visibility=PRIVATE`; `visibility_display="Private"` in serialized output. |
| `test_serializer_can_create_with_visibility` | Verify serializer can create opportunities when visibility is provided. | Created instance has `visibility=PRIVATE`. |
| `test_serializer_defaults_to_public_when_not_specified` | Verify serializer defaults to public when visibility not included in input. | Created instance has `visibility=PUBLIC`. |
| `test_migration_adds_visibility_field` | Verify that the migration adds a visibility field with correct defaults and choices. | Field `visibility` exists; default=`PUBLIC`; choices=`[(1,"Public"),(2,"Private")]`. |
| `test_existing_data_preserved_after_migration` | Verify that existing data remains valid and visibility values are backfilled correctly. | Existing opportunities retain valid `visibility` values; queries by visibility succeed. |
| `test_admin_can_filter_by_visibility` | Verify that opportunities can be filtered by visibility through admin or queries. | Public and private counts > 0; total count equals sum of both. |
| `test_visibility_field_in_database` | Verify that the visibility field is stored and retrievable from the database. | Query returns valid integer values `[1,2]` for visibility. |
| `test_no_data_loss_during_migration` | Verify that no data was lost or invalidated after the visibility migration. | Total = public + private; no invalid or null visibility records. |


### [PR#92](https://github.com/uniconnected/uniconnected-django/pull/92)
| Name | Description | Expected Output |
|------|--------------|-----------------|
| `test_opportunity_detail_includes_allowed_domains_field` | Verify that the opportunity detail API (`/api/v1/opportunities/<id>/`) includes the `allowed_student_email_domains` field for opportunities with restricted domains. | Status `200 OK`; response includes `allowed_student_email_domains=['student.unimelb.edu.au']`. |
| `test_opportunity_detail_with_empty_allowed_domains` | Verify that the opportunity detail API returns an empty list for `allowed_student_email_domains` when none are specified. | Status `200 OK`; response includes `allowed_student_email_domains=[]`. |
| `test_all_opportunities_includes_allowed_domains` | Verify that the list API (`/api/v1/opportunities/`) includes the `allowed_student_email_domains` field for all opportunities. | Status `200 OK`; restricted opportunities have domains `['student.unimelb.edu.au']`; open opportunities have `[]`. |
| `test_student_can_access_individual_opportunity_with_domains` | Verify that a student user can access opportunity details and view `allowed_student_email_domains` for restricted opportunities. | Status `200 OK`; response includes `allowed_student_email_domains=['student.unimelb.edu.au']`. |
| `test_student_can_access_individual_opportunity_without_domains` | Verify that a student user can access opportunity details for open opportunities and see an empty `allowed_student_email_domains` list. | Status `200 OK`; response includes `allowed_student_email_domains=[]`. |


### [PR#90](https://github.com/uniconnected/uniconnected-django/pull/90)
| Name | Description | Expected Output |
|------|--------------|-----------------|
| `test_create_participant_in_public_opportunity` | Verify that a participant can be created in a public opportunity. | Status `201 CREATED`; response includes participant data (`email`, `user_type_key='student'`, `accepted=True`); participant record exists in DB. |
| `test_create_duplicate_participant_returns_409` | Verify that creating a duplicate participant returns a conflict error. | Status `409 CONFLICT`. |
| `test_create_participant_without_invitation_returns_403` | Verify that creating a participant in a private opportunity without an invitation is forbidden. | Status `403 FORBIDDEN`; response includes `"Invitation required"`. |
| `test_create_participant_with_valid_invitation` | Verify that a participant with a valid pending invitation can complete enrollment in a private opportunity. | Status `200 OK`; response includes `email`, `accepted=True`; database invitation updated with `user` and `questionnaire_answers`. |
| `test_complete_organization_invitation` | Verify that an organisation invitation in a private opportunity can be completed successfully. | Status `200 OK`; response includes `accepted=True`; database invitation linked to `organisation` and marked accepted. |
| `test_get_participant_as_user` | Verify that a student participant can retrieve their own participant details. | Status `200 OK`; response includes correct `participant_id`, `email`, `user_type_key='student'`, `accepted=True`. |
| `test_get_participant_as_organization` | Verify that an organisation participant can retrieve their own participant details. | Status `200 OK`; response includes correct `participant_id` and `data.name` matching organisation name. |
| `test_get_participant_not_participant_returns_404` | Verify that a user who is not a participant receives a 404 response when retrieving participant details. | Status `404 NOT FOUND`. |
| `test_update_questionnaire_answers` | Verify that a participant can update their questionnaire answers. | Status `200 OK`; database `questionnaire_answers` updated with new values. |
| `test_delete_own_participation` | Verify that a participant can delete their own participation record. | Status `204 NO CONTENT`; participant record removed from DB. |
| `test_delete_non_participant_returns_404` | Verify that deleting participation when the user is not a participant returns 404. | Status `404 NOT FOUND`. |


### [PR#94](https://github.com/uniconnected/uniconnected-django/pull/94)
| Name | Description | Expected Output |
|------|-------------|-----------------|
| `test_coordinator_gets_own_opportunities_only` | Coordinator should only see opportunities they created. | `200 OK`; exactly 2 items; includes titles for coordinator1; excludes other coordinator’s items. |
| `test_coordinator_gets_both_public_and_private_opportunities` | Coordinator should see both their public and private opportunities. | `200 OK`; 2 items; `visibility` contains `PUBLIC` and `PRIVATE`. |
| `test_non_coordinator_receives_403` | Non-coordinator user is forbidden from accessing coordinator list. | `403 FORBIDDEN`. |
| `test_unauthenticated_receives_401` | Unauthenticated request to coordinator list is unauthorized. | `401 UNAUTHORIZED`. |
| `test_response_contains_expected_fields` | Coordinator list returns required fields on each item. | `200 OK`; each item contains: `id,title,description,start_date,end_date,created_by,is_active,visibility,visibility_display,questionnaire,created_at,updated_at`. |
| `test_inactive_opportunities_included` | Inactive opportunities created by coordinator are included. | `200 OK`; count increases (2 → 3); includes “Inactive Opportunity”. |
| `test_student_sees_public_and_directly_invited_private` | Student sees public opps and private opps where they’re directly invited. | `200 OK`; 2 items: “Public Opportunity” and “Private Opportunity - User Invited”; excludes others. |
| `test_org_member_sees_public_and_org_invited_private` | Org member sees public opps and private opps where their org is invited. | `200 OK`; 2 items: “Public Opportunity” and “Private Opportunity - Org Invited”. |
| `test_coordinator_sees_public_opportunities` | Coordinator (not invited) still sees public opportunities. | `200 OK`; includes “Public Opportunity”; excludes unrelated private ones. |
| `test_unauthenticated_receives_401` | Unauthenticated request to accessible list is unauthorized. | `401 UNAUTHORIZED`. |
| `test_inactive_opportunities_excluded` | Inactive public opportunities are excluded from accessible list. | `200 OK`; excludes “Inactive Public Opportunity”. |
| `test_response_contains_expected_fields` | Accessible list returns required fields on each item. | `200 OK`; each item contains: `id,title,description,start_date,end_date,created_by,is_active,visibility,visibility_display,questionnaire,created_at,updated_at`. |
| `test_user_without_org_membership` | User without org membership sees only public opportunities. | `200 OK`; exactly 1 item: “Public Opportunity”. |
| `test_pending_invitations_included` | Pending invitations should include the private opportunity in accessible list. | `200 OK`; includes “Private Opportunity - Not Invited”. |
| `test_pending_invitations_excluded` | Without a pending invitation, the private “Not Invited” opp is excluded. | `200 OK`; excludes “Private Opportunity - Not Invited”. |
| `test_access_field_present_on_each_item` | Each returned item includes an `access` object with expected keys. | `200 OK`; every item has `access` dict with keys: `has_access,status,current_period_end,cancel_at_period_end,trial_end,active_override,access_source`. |
| `test_access_shows_override_when_active` | Access section reflects an active override for an invited private opp. | `200 OK`; item for “Private Opportunity - User Invited” has `access.has_access=True`, `access_source="override"`, `active_override.end` includes `+00:00`. |
| `test_access_shows_subscription_when_active` | Access section reflects an active subscription for an invited private opp. | `200 OK`; item shows `access.has_access=True`, `access_source="subscription"`, `status="active"`, `current_period_end` includes `+00:00`. |
| `test_access_shows_implicit_when_accepted_and_no_sub_or_override` | Accepted participant with no sub/override shows implicit access. | `200 OK`; item shows `access.has_access=True`, `access_source="implicit_grandfathered"`, `status="no_subscription"`. |
| `test_access_present_for_public_opportunity_without_participation` | Public opp without participant row still includes an `access` object. | `200 OK`; item “Public Opportunity” contains `access` with at least `has_access,status,access_source`. |


### [PR#97](https://github.com/uniconnected/uniconnected-django/pull/97)
| Name | Description | Expected Output |
|------|-------------|-----------------|
| `test_unrestricted_opportunity_allows_all_students` | Students with any email domain can enroll in an unrestricted opportunity. | `201 CREATED`; response reflects `email` of the student and `user_type_key='student'`. |
| `test_domain_restricted_opportunity_allows_matching_domain` | Students with a matching domain can enroll in a domain-restricted opportunity. | `201 CREATED`; response shows student’s `email` and `user_type_key='student'`. |
| `test_domain_restricted_opportunity_rejects_non_matching_domain` | Students with non-matching domains are rejected from a domain-restricted opportunity. | `400 BAD REQUEST`. |
| `test_multi_domain_opportunity_allows_any_matching_domain` | Students with any domain in the allowed list can enroll. | `201 CREATED`; response shows student’s `email`. |
| `test_multi_domain_opportunity_rejects_non_matching_domain` | Students with domains not in the allowed list are rejected. | `400 BAD REQUEST`. |
| `test_non_student_users_bypass_validation` | Non-student users (e.g., organisation) bypass domain validation. | `201 CREATED`; response shows org user’s `email`; `user_type_key='organisation'`. |
| `test_case_insensitive_domain_matching` | Domain matching is case-insensitive. | `201 CREATED`. |
| `test_subdomain_matching` | Subdomains are correctly treated as matching the parent domain. | `201 CREATED`. |
| `test_domains_with_whitespace_handled_correctly` | Whitespace around configured domains is ignored during validation. | `201 CREATED`. |


### [PR#100](https://github.com/uniconnected/uniconnected-django/pull/100)
| Name | Description | Expected Output |
|------|-------------|-----------------|
| `test_migration_adds_public_id_field` | Verify that the `public_id` field exists and has correct properties after migration 0009. | Model contains `public_id`; field is `editable=False`. |
| `test_migration_adds_slug_field` | Verify that the `slug` field exists and has correct properties after migration 0009. | Model contains `slug`; `max_length=140`. |
| `test_auto_generation_of_public_id_and_slug` | Verify that `public_id` and `slug` are auto-generated on save. | `public_id` is a non-null `uuid.UUID`; `slug='mtsi-career-connect-demo'`. |
| `test_slug_uniqueness_with_duplicates` | Verify unique slug generation for duplicate titles. | Three unique slugs: `duplicate-title-test`, `duplicate-title-test-2`, `duplicate-title-test-3`. |
| `test_slug_generation_with_special_characters` | Verify slugify handles special characters properly. | `slug='special-characters-symbols'`. |
| `test_slug_generation_with_empty_title` | Verify slug generation when `title` is empty. | Non-empty fallback slug starting with `opportunity-`. |
| `test_public_id_uniqueness` | Verify all created opportunities have unique `public_id` values. | All `public_id` values are unique (no duplicates). |

### [PR#110](https://github.com/uniconnected/uniconnected-django/pull/110)
| Name | Description | Expected Output |
|----------------|-------------|-----------------|
| Create checkout with new Stripe customer | Creating checkout session for user without existing Stripe customer | 200 OK, new Stripe customer created, checkout session returned with session_id and url |
| Create checkout reusing existing customer | Creating checkout session for user with existing Stripe customer ID | 200 OK, reuses existing stripe_customer_id, checkout session returned |
| Force sync updates Stripe customer | Local customer data changed, `force_sync_if_exists` syncs updates to Stripe | 200 OK, Stripe customer updated with latest local data (name, email, etc.) |
| Create checkout with invalid role type | Attempting checkout with invalid/unsupported role type | 400 Bad Request, error message indicating invalid role type |
| Create checkout with invalid price ID | Attempting checkout with non-existent Stripe price ID | 400 Bad Request, error message indicating invalid price_id |
| Create checkout without organisation membership | Organisation user without `OrganisationMemberProfile` tries to checkout | 403 Forbidden or 400 Bad Request, error message indicating missing organisation membership |
| Create checkout for different organisation | User attempts checkout for participant belonging to different organisation | 403 Forbidden, error message indicating user cannot create checkout for different organisation |

### [PR#108](https://github.com/uniconnected/uniconnected-django/pull/108)
| Name | Description | Expected Output |
|----------------|-------------|-----------------|
| Get product pricing with valid parameters | GET `/api/v1/product-pricing/?opportunity_id=7&user_type=organisation` | 200 OK, returns product pricing details |
| Get product pricing with invalid user type | GET `/api/v1/product-pricing/?opportunity_id=7&user_type=invalid_type` | 400 Bad Request, error indicating invalid user_type |
| Get product pricing with missing required parameter | GET `/api/v1/product-pricing/?user_type=organisation` | 400 Bad Request, error indicating missing opportunity_id parameter |
| Get product pricing for non-existent opportunity | GET `/api/v1/product-pricing/?opportunity_id=99999&user_type=organisation` | 404 Not Found, detail: "No opportunity matching query" |
| Get product pricing when no product exists | GET `/api/v1/product-pricing/?opportunity_id=6&user_type=organisation` | 404 Not Found, detail: "No product or matching prices found" |
| Get product pricing with no matching user type | GET `/api/v1/product-pricing/?opportunity_id=7&user_type=student` | 404 Not Found, detail: "No product or matching prices found" |