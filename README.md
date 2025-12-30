# devsecops-secrets-and-misconfigs

This repository demonstrates a practical DevSecOps CI/CD pipeline that detects hardcoded secrets and infrastructure misconfigurations early in the software delivery lifecycle.

The project focuses on integrating security-as-code into CI/CD using open-source security tools, ensuring issues are caught before deployment rather than in production.

## 📌 Project Objective

The main goal of this project is to:

- Detect secrets committed to source code
- Identify Dockerfile misconfigurations
- Enforce security gates in CI/CD pipelines
- Understand how security tools behave in real-world pipelines

## 🧰 Tools & Technologies Used

| Tool | Purpose |
|-----|--------|
| GitHub Actions | CI/CD pipeline automation |
| Gitleaks | Secret detection in source code |
| Trivy | Dockerfile misconfiguration scanning |
| Docker | Containerization |
| Python | Sample application |

## 🏗️ Pipeline Workflow

1. Code is pushed to the repository
2. Gitleaks scans the repository for hardcoded secrets
3. Trivy scans the Dockerfile for security misconfigurations
4. The pipeline fails if findings exceed the configured severity threshold

## 🔍 Security Checks Implemented

### 🔑 Secret Detection (Gitleaks)
- Detects exposed credentials, API keys, and tokens
- Fails the pipeline when secrets are found
- Prevents accidental secret leakage

### 🐳 Misconfiguration Detection (Trivy)
- Scans Dockerfile for insecure configurations
- Flags missing best practices such as HEALTHCHECK
- Severity filtering is applied to control pipeline failures

> **Note:** Trivy severity was set to CRITICAL and HIGH to avoid workflow failure due to LOW-severity findings such as missing HEALTHCHECK instructions.

## ✅ Final Outcome

- Security scans successfully integrated into the CI/CD pipeline
- Hardcoded secrets detected and remediated early
- Dockerfile misconfigurations identified before deployment
- Pipeline transitioned from FAILED → FIXED → PASSED

## 📘 Key Learnings

- Security tools must be tuned to avoid unnecessary pipeline failures
- LOW-severity findings can disrupt CI/CD if not managed properly
- Shift-left security reduces risk and rework
- DevSecOps is about enabling secure delivery, not blocking development

## 📝 Related Blog

https://afashani.medium.com/detecting-secrets-and-misconfigurations-in-a-ci-cd-pipeline-4b3bea59192c

## 📢 Disclaimer

This project is for learning and demonstration purposes only.  
Do not commit real secrets to production repositories.
