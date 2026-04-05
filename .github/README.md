# GitHub Workflows Overview

This repository includes several automated workflows located in `.github/workflows`. These workflows provide consistent linting, security scanning, and Terraform validation across all projects created from this template.

## 1. Lint Workflow `lint.yml`
Runs on all branches. This workflow performs general repository linting: YAML linting, markdown linting, and basic formatting checks. Its purpose is to ensure consistent structure and formatting across all repos created from this template.

## 2. Security Workflow `security.yml`
Runs on all branches. This workflow performs static analysis using GitHub CodeQL. It helps identify potential security issues early in development.

## 3. Terraform Workflow `terraform.yml`
Runs where Terraform is used. This workflow runs terraform fmt, terraform init -backend=false, and terraform validate to ensure the Terraform code is syntax error-free and properly formatted before merging.

## 4. Dependabot `dependabot.yml`
Dependabot is configured to check for GitHub Actions updates once per month. It will open PRs only when updates exist using a consistent commit message prefix: ci:. However, it still requires configuration for the project‑specific dependencies.

[Configuration documentation](https://docs.github.com/en/code-security/how-tos/secure-your-supply-chain/secure-your-dependencies/configuring-dependabot-version-updates)

Dependabot must be enabled in:
**Settings → Code security & analysis → Dependabot**

## 5. Pull Request Template
Located at `.github/PULL_REQUEST_TEMPLATE.md`. This template provides a consistent structure for all pull requests created from this repository template.

## Branch Protection
To ensure workflows enforce quality gates, enable branch protection rules for:
- `staging`
- `main`

## Recommended settings
- Require pull requests before merging.
- Require status checks to pass.
- Require branches to be up to date.
- Restrict who can push to the branch.

These settings ensure all workflows pass before code can be merged, even by the code owner.

## Additional Testing (not included)
This template repository includes only generic workflows. Projects created from this template may require additional testing workflows depending on the languages or frameworks used. For example:

- **JavaScript / TypeScript**  
  Unit tests, integration tests, linting (e.g., Jest, Vitest, ESLint)
- **Python**  
  Unit tests, type checking, linting (e.g., pytest, mypy, flake8)
- **Go**  
  Unit tests, vetting, module verification
- **Java / Kotlin**  
  Build and test pipelines (e.g., Maven, Gradle)
- **Terraform (real infrastructure)**  
  Terraform plan, policy checks, OPA/Conftest, backend‑enabled validation
- **Docker / Containerised apps**  
  Build, scan, and optionally push images
- **Frontend frameworks**  
  Build pipelines, static analysis, UI tests (e.g., React, Angular, Vue)