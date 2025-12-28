# Contribution Guideline

This repository follows the Secure Software Development Life Cycle (SSDLC) principles with a pragmatic approach. The SSDLC is a cyclical development process - `plan -> code -> test -> deploy -> maintain`.

## Code

...

## Test

### Security

This repository scans for several security vulnerabilities that can be introduced dduring development using open source security scanning tools.

- [Trivy](https://trivy.dev/docs/latest/getting-started/) is used to scan for vulnerabl dependencies, configurations, and hard-coded credentials in the source code.

| Vulnerability                        | What is it?                               | Why is it bad?                                                                                                    | Tools             |
| ------------------------------------ | ----------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ----------------- |
| **Vulnerable Dependencies**          | Using outdated or flawed software parts.  | Allows attackers to exploit known weaknesses which can lead to system takeover, data theft, application crash.    | Trivy, Dependabot |
| **Hardcoded Credentials/Secrets**    | Storing passwords/keys directly in code.  | Makes it easy for attackers to find them which can lead to account hijacking, data breaches, unauthorized access. | Trivy             |
| **Misconfigured or Vulnerable Code** | Mistakes in how the application is built. | Creates entry points for attackers which can lead to data breaches, application crashes, remote control.          | Trivy             |

### Testing

Write some tests so that you can sleep better at night.

## Deploy

...
