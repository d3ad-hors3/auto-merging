# Auto Merging

This repository demonstrates a method for keeping dependencies up to date using automations to ensure a 'more' secure supply chain.

## Getting Started

The repository contains some dependencies that are outdated/vulnerable and should be updated:

| Package Name | Version | Description                                                                          |
| ------------ | ------- | ------------------------------------------------------------------------------------ |
| next         | 15.0.4  | < 15.0.5 is [vulnerable with rce](https://github.com/advisories/GHSA-9qr9-h5gf-34mp) |
| expressjs    | 5.2.0   | outdated - 5.2.1 exists                                                              |

> [!NOTE]
> There are also github actions in the [.github/workflows](.github/workflows/) that will eventually become outdated.

## Good to know

### Dependabot Labels

If you use labels in your dependabot configuration then **you have to create the labels** before running a dependency update. Otherwise, it won't be able to find them and will fail assign the label which can affect automations that depend on said labels.
