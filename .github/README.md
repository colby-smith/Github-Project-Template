# GitHub Workflows Overview

This repository includes several automated workflows located in `.github/workflows`. These workflows provide consistent linting, security scanning, and Terraform validation across all projects created from this template.

## Initial setup

Before using this template, complete the following one‑time steps in the GitHub UI.

### 1. Enable the following Dependabot features:
*Settings -> Advanced Security -> Dependabot*
- `Dependabot alerts`
- `Dependabot security updates`
- `Grouped security updates`
- `Dependabot version updates`



### 2. Enable the following Code scanning features:
*Settings -> Advanced Security -> Code scanning -> Tools*
- `CodeQL analysis (default)`
- `Copilot Autofix`

### 3. Create the required workflow labels
*Issues -> Rules -> New label -> Create label*
- `dependencies` - `#1f883d` - *Used for automated or manual updates to project dependencies.*
- `github-actions` - `#000000` - *Used for changes related to GitHub Actions workflows.*

### 4. Create the additional standard repository branches
*Code -> Branch dropdown -> view all branches -> New branch*
- `development`
- `staging`

### 5. Import each JSON file into GitHub Rulesets:
*Settings -> Rules -> New ruleset*
- `dev‑branch.json`
- `stage‑branch.json`
- `main‑branch.json`

### 6. Configure Dependabot
*.github\dependabot.yml*
- [Configuration documentation](https://docs.github.com/en/code-security/how-tos/secure-your-supply-chain/secure-your-dependencies/configuring-dependabot-version-updates)

## Workflows

### 1. `lint.yml`
Runs on all branches. This workflow performs general repository linting: YAML linting, markdown linting, and basic formatting checks. Its purpose is to ensure consistent structure and formatting across all repos created from this template.

### 2. `security.yml`
Runs on all branches. This workflow performs static analysis using GitHub CodeQL. It helps identify potential security issues early in development.

### 3. `terraform.yml`
Runs where Terraform is used. This workflow runs terraform fmt, terraform init -backend=false, and terraform validate to ensure the Terraform code is syntax error-free and properly formatted before merging.

### 4. `dependabot.yml`
Dependabot is configured to check for GitHub Actions updates once per month. It will open PRs only when updates exist using a consistent commit message prefix: ci:. However, it still requires configuration for the project‑specific dependencies.

## Pull Request Template
Located at `.github/PULL_REQUEST_TEMPLATE.md`. This template provides a consistent structure for all pull requests created from this repository template.

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