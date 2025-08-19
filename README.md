# Project Overview

This project demonstrates how to **build and automate a complete CI/CD pipeline** for the popular **2048 web game** using **Terraform** for Infrastructure as Code (IaC) and **GitHub Actions** for continuous integration and delivery.  

The pipeline provisions cloud infrastructure (networking, compute, and storage) and automates the deployment of the 2048 game. With every commit, the workflow ensures code is tested, infrastructure is validated, and the game is deployed reliably. This project is a showcase of combining **DevOps practices, automation, and cloud-native IaC** into a single, production-ready workflow.

---

# Build a CI/CD Pipeline for the 2048 Game using Terraform & GitHub Actions

[![CI](https://github.com/akupheaws/Build-a-CI-CD-Pipeline-for-the-2048-Game-using-Terraform-and-GitHub-Actions/actions/workflows/ci.yml/badge.svg)](https://github.com/akupheaws/Build-a-CI-CD-Pipeline-for-the-2048-Game-using-Terraform-and-GitHub-Actions/actions)
![Terraform](https://img.shields.io/badge/IaC-Terraform-blueviolet)
![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub%20Actions-blue)
![License](https://img.shields.io/badge/license-MIT-informational)

---

## ✨ Key Features

- **Game Deployment:** Deploys the 2048 web game to AWS infrastructure using Terraform.
- **Automated CI/CD:** GitHub Actions pipeline runs tests, validates Terraform, and applies changes on merges.
- **Infrastructure as Code:** Reproducible cloud resources (VPC, compute instances, storage, etc.).
- **Scalable Design:** Can be adapted to host other web apps with minimal code changes.
- **Fast Feedback Loop:** On each push/PR, tests and Terraform plan are executed automatically.

---

## 📁 Repository Structure

```
.
├── .github/workflows/     # GitHub Actions workflows (CI/CD pipelines)
├── terraform/             # IaC for networking, compute, storage
├── game/                  # 2048 game source code (HTML, CSS, JS)
├── scripts/               # Helper scripts (deployment, bootstrap)
├── package.json           # If additional Node-based tooling is used
└── README.md
```

> The `game/` folder holds the static files for the 2048 game (index.html, styles, JS logic). Terraform handles provisioning of infrastructure where these assets are hosted.

---

## 🚀 Getting Started

### Prerequisites

- **AWS account** with IAM role/credentials set up for Terraform or OIDC from GitHub.
- **Terraform ≥ 1.5**
- **GitHub Actions** enabled in your repo.

### Deployment Flow

1. **Clone** the repository:
   ```bash
   git clone https://github.com/akupheaws/Build-a-CI-CD-Pipeline-for-the-2048-Game-using-Terraform-and-GitHub-Actions
   cd Build-a-CI-CD-Pipeline-for-the-2048-Game-using-Terraform-and-GitHub-Actions
   ```

2. **Initialize Terraform:**
   ```bash
   cd terraform
   terraform init
   terraform plan
   terraform apply -auto-approve
   ```

3. **CI/CD via GitHub Actions:**
   - On PRs → Terraform lint & validate, run tests.
   - On merge to `main` → Terraform apply, deploy game assets to infrastructure.

4. **Access the game:** The output from Terraform will provide a public URL (e.g., S3 bucket static site or ALB DNS).

---

## 🔧 GitHub Actions Workflows

The pipeline includes:

- **Terraform Lint/Validate** – ensures IaC formatting & correctness.
- **Plan & Apply** – runs plan on PRs, apply on merge to main branch.
- **Game Deployment** – copies game files to provisioned infrastructure (S3, EC2, or equivalent).
- **Smoke Test** – curl endpoint to ensure the 2048 game is reachable.

Badge example (update with actual workflow filename if different):
```md
[![CI](https://github.com/akupheaws/Build-a-CI-CD-Pipeline-for-the-2048-Game-using-Terraform-and-GitHub-Actions/actions/workflows/ci.yml/badge.svg)](…)
```

---

## 🧪 Local Testing

You can serve the 2048 game locally for quick iteration:

```bash
cd game
python3 -m http.server 8080
# visit http://localhost:8080
```

Or package/deploy with your chosen Node/HTTP server if preferred.

---

## ⚙️ Infrastructure Components (Terraform)

- **Networking:** VPC, public subnets, internet gateway, route tables.
- **Compute/Hosting:** Can be EC2 or S3 static site depending on configuration.
- **Security:** Security groups for access, least-privilege IAM roles for GitHub Actions.
- **Outputs:** Public URL/DNS for the 2048 game.

---

## 🛣️ Roadmap

- [ ] Add monitoring & alerts (CloudWatch, health checks).
- [ ] Containerize 2048 app with Docker + ECS/Fargate deploy.
- [ ] Add multi-region failover with Route 53 health checks.
- [ ] Add automated integration testing with Playwright or Cypress.

---

## 📜 License

MIT © Akuphe
