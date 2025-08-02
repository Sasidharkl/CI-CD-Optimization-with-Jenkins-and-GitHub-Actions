# 🚀 CI/CD Optimization with Jenkins & GitHub Actions

This project demonstrates an optimized CI/CD workflow using **Jenkins** and **GitHub Actions**, with support for:

- Docker build layer **caching**
- Automated **deployment**
- **Rollback** mechanism on failure
- Integration with **DockerHub**
- Sample Flask-based web app

---

---

## 🧩 Tech Stack

| Layer            | Technology                |
|------------------|---------------------------|
| CI/CD Tools      | Jenkins, GitHub Actions   |
| Containerization | Docker                    |
| App Framework    | Python (Flask)            |
| Infrastructure   | AWS (EC2) / Terraform     |
| Scripting        | Bash / Shell              |
| Caching          | Docker Layer Caching      |

---

## 🔄 CI/CD Flow Summary

### ✅ GitHub Actions Pipeline

1. On push to `main`:
   - Checkout code
   - Enable Docker caching
   - Build Docker image
   - Push to DockerHub
   - Deploy with `deploy.sh`
   - On failure: `rollback.sh` is triggered

### 🔧 Jenkins Pipeline

- Same stages as GitHub Actions:
  - Checkout
  - Build with cache
  - Push image
  - Deploy
  - Rollback if needed

---

## 🐳 Docker Build (with caching)

```bash
docker build --cache-from=my-app:latest -t my-app:latest .


