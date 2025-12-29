# Auto Merging

Keeping up with the latest dependencies for security vulnerabilities is very time consuming. You have to stay up to date with the news or social media AND THEN you have to find the latest version for your dependency that is not vulnerable to X, Y and Z.

This repository demonstrates a method for keeping dependencies up to date using automations to ensure a 'more' secure supply chain and a better sleep at night.

## Introduction

This automation uses Dependabot to track dependencies and open pull requests when security/version updates are available. The automation then uses GitHub Actions to listen for new pull requests and merge them automatically.

### Dependabot

[Dependabot](https://docs.github.com/en/code-security/getting-started/dependabot-quickstart-guide) is a tool that helps you keep your dependencies up to date. It can be [configured](https://docs.github.com/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference) to filter updates and present them in a certain way.

Most software libraries follow semantic versioning (i.e. `<major>.<minor>.<patch>`):

- `<patch>` refers to bug fixes that do not change the behaviour of a software.
- `<minor>` refers to new features and improvements that do not break existing behaviour.
- `<major>` refers to changes that alter the fundamental behaviour of a software.

> [!WARNING]
> Not everyone follows semantic versioning and it's important to check the release notes before updating to a new version.
>
> That being said, it is safe to assume that `<patch>` updates will not break your application which is why
> we automatically merge `<patch>` updates but **we do not merge `<minor>` or `<major>` updates**.

This repository configures the dependabot in [.github/dependabot.yaml](./github/dependabot.yaml). The most important aspects to consider when configuring dependabot is that you:

- Configure for all the ecosystems that you are using (i.e. github actions, npm, pip, docker)
- Group your `<patch>` updates and give them an `id` that you can look for in your automations. This automation groups dependabot pull requests for version (`safe-version-updates`) and security updates (`safe-security-updates`) and then filters for the pattern `safe-updates` in the [.github/workflows/auto-merge.yaml](.github/workflows/auto-merge.yaml) workflow automation.
- Always use the `--auto` flag in `gh pr merge --auto <pr number>` to ensure that the pull request is only merged after all 'checks' pass. Avoid the `--force` flag which might merge a pr that doesn't pass unit tests or some other 'check' that you have in place.

## Getting Started

The repository contains some dependencies that are outdated/vulnerable and should be updated:

| Package Name | Version | Description                                                                          |
| ------------ | ------- | ------------------------------------------------------------------------------------ |
| next         | 15.0.4  | < 15.0.5 is [vulnerable with rce](https://github.com/advisories/GHSA-9qr9-h5gf-34mp) |
| expressjs    | 5.2.0   | outdated - 5.2.1 exists                                                              |

> [!NOTE]
> There are also github actions in the [.github/workflows](.github/workflows/) that will eventually become outdated.

## Good to know

There are a few things you need to configure for auto merge to work:

- You need to use a PAT for the `gh cli` commands with the `content:write` scope for general dependencies and `workflow:write` for merging dependabot prs for github actions.

- [Enable auto-merge](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-auto-merge-for-pull-requests-in-your-repository): Settings > General > Pull Requests > "Allow auto-merge Loading"

### Dependabot Labels

If you use labels in your dependabot configuration then **you have to create the labels** before running a dependency update. Otherwise, it won't be able to find them and will fail assign the label which can affect automations that depend on said labels.
