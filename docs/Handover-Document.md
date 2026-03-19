# Final Product Completion and Deployment
## Completed Work

All user stories have been mapped to detailed development tasks and tracked across sprints, with documentation for each sprint available at:
- [Sprint 1](https://github.com/COMP90082-2025-sem2/UC-Koala/wiki/ceremonies#sprint-1-planning)
- [Sprint 2](https://github.com/COMP90082-2025-sem2/UC-Koala/wiki/ceremonies#sprint-2-planning)
- [Sprint 3](https://github.com/COMP90082-2025-sem2/UC-Koala/wiki/ceremonies#sprint-3-planning)
- [Sprint 4](https://github.com/COMP90082-2025-sem2/UC-Koala/wiki/ceremonies#sprint-4-planning)

### Justification of Open PRs 
Most implementation work has been completed, tested, and handed over to the client (i.e., merged directly to client repository). The two remaining open PRs are awaiting the client’s review and merge approval:
- UC-350: Implemented a daily sweep task and automated email notifications. The feature functions as expected but failed one integration test due to a Stripe external-platform dependency. After discussion, the client confirmed that the current implementation is acceptable and will take ownership of the final integration when available.
- UC-347: Added structured logging for key Stripe-related endpoints, including session creation and webhook handlers. This PR remains open pending dependency resolution and finalisation of the Stripe flow by the client.

These open PRs are primarily due to:
- Inter-ticket and cross-team dependencies
- Extended integration testing with third-party systems (Stripe)
- Additional validation required for privacy and PII-handling compliance

A detailed discussion of the technical challenges and resolutions can be found [here](https://github.com/COMP90082-2025-sem2/UC-Koala/wiki/ceremonies#mid-sprint-technical-challenges-and-resolution).

## Deployment Process
We followed the client’s established CI/CD deployment workflow:
1. Rebase the `dev` branch and create a `feature` branch for development
2. Develop and test features locally and via CI pipelines
3. Submit a pull request summarising implemented functions/features and any tests
4. Conduct peer review within the team
6. Await client review and approval before merge and deployment

## Handover and Final Release
No separate handover package (e.g., ZIP file) is required because all deliverables (i.e., source code, test cases, and associated seed data) reside directly within the client’s GitHub repository. The repository already integrates with the client’s CI/CD system, and the product is fully functional and deployed within their environment. The two remaining open PRs represent completed features pending final review, not incomplete work.

