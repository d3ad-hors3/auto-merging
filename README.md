# Auto Merging

This repository demonstrates a method for keeping dependencies up to date using automations to ensure a 'more' secure supply chain.

## Getting Started

The repository contains some dependencies that are outdated/vulnerable and should be updated:

| Package Name | Version | Description                                                                         |
| ------------ | ------- | ----------------------------------------------------------------------------------- |
| next         | 15.0.4  | vulnerable - [rce vulnerability](https://github.com/advisories/GHSA-9qr9-h5gf-34mp) |
| expressjs    | 5.2.0   | outdated - 5.2.1 exists                                                             |

> [!NOTE]
> There are also github actions in the [.github/workflows](.github/workflows/) that will eventually become outdated.
