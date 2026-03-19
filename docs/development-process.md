# Development Process

- [Development Process](#development-process)
  - [Developer Environment](#developer-environment)
      - [Setup](#setup)
  - [Development Guide](#development-guide)
  - [Task Flow](#task-flow)
  - [Review Process](#review-process)
    - [Review Workflow](#review-workflow)   
    - [Evidence of Review](#evidence-of-review)
    - [PR Reviewer](#pr-reviewer)
    - [AI Check](#ai-check)
    - [Definition of Ready (DoR)](#definition-of-ready-dor)
    - [Definition of Done (DoD)](#definition-of-done-dod)
  - [Best practices](#best-practices)
    - [Naming conventions](#naming-conventions)
    - [Branches](#branches)
    - [Commit](#commits)


## Developer Environment

The UniConnected platform is developed across two repositories:

### 1. Frontend Repository – `uniconnected2-frontend`
- **Framework:** Next.js  
- **Language:** TypeScript  
- **UI Library:** React + Chakra UI  
- **Hosting / Deployment:** AWS Amplify  

### 2. Backend Repository – `uniconnected-django`
- **Framework:** Django
- **Language:** Python 
- **Database:** PostgreSQL  
- **Containerization:** Docker + docker-compose 

### Setup

For the enviroment setup, please follow the instruction under the client repositories: [uniconnected2-frontend](https://github.com/uniconnected/uniconnected2-frontend#readme) and [uniconnected-django](https://github.com/uniconnected/uniconnected-django#readme).


## Development Guide

The general development workflow can be found from the uniconnected-django repository's `README.md` file under the "Contributing" heading [[link](https://github.com/uniconnected/uniconnected-django?tab=readme-ov-file#-contributing)].

At a high level the flow looks like the below:

1. Create a new branch off `develop` branch.
2. Make changes to the codebase.
3. Write tests to cover the new changes.
4. Create a pull request for review with at least one approval.
5. Merge the pull request into the `develop` branch.

## Task Work Flow

The task implementation follow a structured work flow to ensure transparency. The task status will be recorded in the [Team Kanban board](https://github.com/orgs/COMP90082-2025-sem2/projects/43), other team member can view the status of the task.

The task work flow:

1. All the identify user story will be placed on the backlog section. With the start of the each sprint, move the items that will be implemented during the sprint into `todo` section.
2. The tasks breakdown from the user stories will be identified during the sprint planning session. Then the task will be created on the kanban board and placed on the `todo` section.
3. Once the assignees has started the task, move the task from `todo` to `In Progress` in the task borad.
4. Once the assignees think the task has meet the criteria of **Definition of Ready**, move the task from `In Progress` to `In Review` section in the task borad, and assign other team member as reviewers to review the task.
5. Once the assigned reviewers believe that the task has meet the criteria of **Definition of Done**, move the task from `In Review` to `Done` section in the task board.
6. If the assignees think the task is currently blocked, then move the task to `Blocked` section, and report that issue to the team.


## Review Process

### Review Workflow
1. Author opens PR with a descriptive summary, links to issues.  
2. Author assigns reviewers run (linting, tests, build).  
3. Reviewers provide evidence of review
4. Author addresses feedback in following commits ,or clarifying in comments, and left comment/conversation to state that issues are addressed.  
5. Approval is given by reviewers if they believe there is no issue in the PR.  
6. The Merge optionto `develop` branch is performed by our client Bassam.  

### Evidence of Review
- **Reviewer comments:**  
   - *“LGTM”* (look good to me) to mention no issue is found.  
   - Requested changes for issues in functionality, bugs, or and issue.  
   - or comments suggesting improvements. 
- **Reviewer approval:**  
  - Reviewers approval this pr to merge into the `develop` branch

Additionaly, Reviewers can check the commit history in the PR to see how the author addresses identified issues.

### PR Reviewer
 - Each PR must request at least **two reviewers** (one reviewer must be the team member, and another reviewer will be our client Bassam).  
 - Reviewers are assigned via GitHub’s *Reviewers* section before the PR can be marked as ready for merge.

### AI Check
- Each PR can assign AI "Copliot" as a reviewer to check your commits.

### Definition of Ready (DoR)  
  A PR is only considered *ready for review* if it meets all of the following:  
  - Linked to a corresponding task or user story.  
  - The implement functionalitiy has covered the user story or task.
  - Code changes are scoped and do not include unrelated modifications.  
  - Tests and documentation are updated.  

### Definition of Done (DoD)  
  A PR can be merged once:  
  - At least 2 reviewers have approved the changes.  
  - All functionalities can pass the test.
  - Required documentation (or changelog) are updated.  
  - No unresolved comments remain. 

## Best practices

### Naming conventions

- For markdown files for the wiki, use kebab-case (e.g., `user-guide.md`, `development-process.md`).
- For documentation titles, use sentence case (e.g. User guide, Development process).
- For code files and branching pattern, follow the conventions from the code repositories [uniconnected2-frontend](https://github.com/uniconnected/uniconnected2-frontend) and [uniconnected-django](https://github.com/uniconnected/uniconnected-django).
- Pull Requests must be reviewed by at least one member of the team before merging.

### Branches

In this project, we create branch on the client's repository, which follows Client branch rules: Gitflow branching strategy. There are two branches which will always exist and maintain by the client:

- main: This is a long-lived, stable branch that contains the final, production-ready code, representing the official release history. 
- develop: A long-lived integration branch where all features are merged after being developed in feature branches.

When creating new branching, we need to follow the below statements:

**Allowed Branch Names**
- feature/* – for new features (branch off develop)
- bugfix/* – for bug fixes (branch off develop)
- hotfix/* – for urgent fixes discovered in production (branch off master)
- release/* – for preparing production releases (branch off master)

**Rules**
- Never push directly to master or develop.
- Always open a Pull Request (PR).
- The client (Bassam) must approve and merge the PR.


### Commits

In client repository, [Conventional Commits](https://www.conventionalcommits.org/) is enforced to use:

The commit message should be structured as follows:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

In the commit message, `type` and `description` are necessary. 

For the common `type` usage:

- **feat**: a commit that introduces a new feature.
- **fix**: a commit that patches a bug.
- **docs**: documentation-only changes (e.g., README, Wiki, comments).
- **style**: code style changes (formatting, missing semicolons, whitespace) without affecting code meaning.
- **refactor**: code changes that neither fix a bug nor add a feature (e.g., code restructuring).
- **perf**: a commit that improves performance.
- **test**: adding or correcting tests.
- **chore**: changes to the build process, tools, or other auxiliary code (e.g., dependency updates).
- **build**: changes that affect the build system or external dependencies.
- **ci**: changes to CI/CD configuration files and scripts.

The client highly recommend using [**Commitizen**](https://commitizen-tools.github.io/commitizen/) to simplify the process.


