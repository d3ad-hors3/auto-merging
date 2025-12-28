# Template

This repository is a template designed to get you started with a secure Continous Integration and Development (CI/CD) pipeline. The template includes:

- **[Continuous Integration](./.github/workflows/ci.yaml) (CI):**
  - Validates commit messages using `commitlint` to ensure they follow a conventional format.
  - Checks PR titles and commits for adherence to predefined rules.

- **[Continuous Deployment](./.github/workflows/cd.yaml) (CD):**
  - Automatically creates releases when changes are pushed to the `main` branch.

- [Issue Templates](./.github/ISSUE_TEMPLATE/) to standardize feature and bug reports.
- [Commitlint configuration](./.commitlintrc) for standardized and readable commit messages.

This repository contains a set of GitHub Actions workflows designed to automate continuous integration (CI) and continuous deployment (CD) processes. The workflows are tailored to ensure that code changes adhere to specific standards and guidelines, enhancing the reliability and maintainability of the project.

## Getting Started

This repository is designed with some expectations and guidelines to ensure that code changes adhere. Read the [`CONTRIBUTION.md` file](./CONTRIBUTION.md) to understand how to use this repository effectively.
