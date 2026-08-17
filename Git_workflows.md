# Git Workflows

## GitFlow

GitFlow is a branching strategy that uses multiple long-lived branches, where each branch has a specific purpose.

### Branches

- **main** – Production-ready code.
- **develop** – Integration branch for ongoing development.
- **feature/*** – Used to develop individual features.
- **release/*** – Used to prepare a release before deployment.
- **hotfix/*** – Used to fix critical production issues.

### When does GitFlow make sense?

GitFlow is a good choice when:

1. Your software is released in versions.
2. You need to maintain multiple versions of the application at the same time.
3. Your team is large and requires a well-defined branching strategy.
4. You work in regulated industries such as banking, healthcare, or government projects.

### Drawbacks of GitFlow

1. Slows down the development cycle because branch management becomes complex.
2. Does not work well with Continuous Delivery due to frequent merge conflicts.
3. Not suitable for web applications that are deployed continuously.
4. Best suited for applications with versioned releases and slower deployment cycles.

---

# GitHub Flow

GitHub Flow is a simple branching strategy where the **main** branch is always deployable.

### Workflow

1. Create a branch from `main`.
2. Develop your feature.
3. Create a Pull Request.
4. Review and merge into `main`.
5. Deploy from `main`.

### When does GitHub Flow make sense?

GitHub Flow is a good choice when:

1. Your application is deployed frequently.
2. You build SaaS applications, APIs, or web applications where only one version is running in production.
3. Your team is small or medium-sized.
4. You have strong automated testing and CI/CD pipelines.
5. You prefer shipping features quickly instead of managing multiple long-lived branches.

### Drawbacks of GitHub Flow

1. Difficult to maintain multiple production versions.
2. Requires strong team discipline.
3. A bad merge into `main` can break production if testing is weak.
4. Coordination becomes difficult when many teams work on the same codebase.

---

# Trunk-Based Development (TBD)

In Trunk-Based Development, developers commit small changes directly to the **main** (trunk) branch frequently.

Incomplete features are hidden from users using **Feature Flags** (also called **Feature Toggles**).

- If the feature flag is **OFF**, users cannot see the feature.
- Once development is complete and tested, the feature flag is turned **ON**, making the feature available to users.

### Why use Trunk-Based Development?

1. Supports Continuous Integration and Continuous Delivery (CI/CD).
2. Developers integrate code frequently, reducing merge conflicts.
3. Automated tests run after every commit.
4. Faster integration and deployment.
5. Easier to recover from failures because changes are small.
6. Only one version of the application is maintained in production.

### Requirements

Trunk-Based Development works best when:

- Developers commit small, frequent changes.
- Strong automated testing is in place.
- CI/CD pipelines are reliable.
- Developers follow coding standards.
- Teams collaborate closely.

### Drawbacks of Trunk-Based Development

1. Not ideal for inexperienced teams without strong development practices.
2. Weak test coverage can allow bugs into production.
3. Requires a cultural shift towards frequent integration.
4. Developers must learn to make small, incremental commits.
5. Teams must understand and use Feature Flags effectively.
6. Continuous Integration must be well established.

---

# Real-World Observation

Many modern engineering teams combine **GitHub Flow** with **Trunk-Based Development**.

Typical workflow:

- Short-lived feature branches
- Frequent merges into `main`
- Feature Flags for incomplete work
- Automated CI/CD pipelines
- Continuous deployment

This provides the simplicity of GitHub Flow while following the rapid integration principles of Trunk-Based Development.

---

# Practical Tips

## 1. Automate Everything Possible

Automate as many tasks as possible, including:

- Automated testing
- CI/CD pipelines
- Code linting
- Code formatting
- Security scanning
- Vulnerability testing

---

## 2. Maintain Good Documentation

Document your development workflow clearly.

Include:

- Branching strategy
- Commit message conventions
- Code review expectations
- Pull Request workflow
- Release process

---

## 3. Use Tools That Support Your Workflow

Example:

- **tbdflow** – A lightweight CLI tool that simplifies Git workflows for teams using Trunk-Based Development by automating common Git operations.

---

## 4. Measure Engineering Performance

### Deployment Frequency (DF)

How often the team successfully deploys code to production.

### Lead Time for Changes (LTC)

The time taken from committing code until it is running in production.

### Mean Time to Recovery (MTTR)

The average time required to restore service after a production failure.

### Change Failure Rate (CFR)

The percentage of deployments that result in a production failure.

---

## 5. Continuously Improve Your Workflow

Your workflow should evolve as your project grows.

Regularly review and improve:

- Branching strategy
- CI/CD pipelines
- Testing practices
- Deployment process
- Code review process
- Development standards
