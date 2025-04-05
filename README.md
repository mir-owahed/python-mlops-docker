# python-mlops-docker

# 🧠 Secure Python MLOps Project with Docker and GitHub Actions

This project demonstrates a basic MLOps setup for a machine learning application built with Python. It includes model training, testing, Docker containerization, and secure CI/CD automation using GitHub Actions.

---

## 📌 Features

- ✅ Model training using `scikit-learn`
- ✅ Unit testing with `pytest`
- 🛡️ Python dependency vulnerability scan with `Safety`
- 🐳 Docker image vulnerability scan using `Trivy`
- 🔐 Build and push Docker image to **GitHub Container Registry (GHCR)**
- ⚙️ CI/CD automation with **GitHub Actions**
- 👤 Non-root Docker user for enhanced security

---

## 📁 Project Structure

```
mlops-project/
├── app/
│   ├── train.py               # Model training code
│   └── model.pkl              # Trained model (generated)
├── tests/
│   └── test_train.py          # Unit tests for training code
├── requirements.txt           # Project dependencies
├── Dockerfile                 # Secure multi-stage Dockerfile
├── .gitignore
├── .dockerignore
└── .github/
    └── workflows/
        └── ci.yml             # GitHub Actions CI/CD pipeline
```

---

## 🚀 Quick Start

### 🔧 Build and Run Locally

```bash
# Build Docker image
docker build -t mlops-secure-app .

# Run container
docker run --rm mlops-secure-app
```

### ✅ Run Unit Tests Locally

```bash
pip install -r requirements.txt
pytest tests/
```

---

## 🔐 Security Features

### 📦 Python Dependency Scan

- Tool: [`safety`](https://github.com/pyupio/safety)
- Purpose: Scan `requirements.txt` for known CVEs.

### 🐳 Docker Image Scan

- Tool: [`trivy`](https://github.com/aquasecurity/trivy)
- Purpose: Scan built Docker image for OS and software vulnerabilities.

---

## ⚙️ GitHub Actions CI/CD Pipeline

The `.github/workflows/ci.yml` workflow includes:

1. ✅ Install Python dependencies
2. 🧪 Run `pytest` unit tests
3. 🛡️ Run `safety` scan on dependencies
4. 🐳 Build Docker image
5. 🔍 Run `trivy` scan
6. 📦 Push image to **GHCR**

---

## 📦 GitHub Container Registry (GHCR)

After a successful pipeline run, the Docker image is pushed to:

```
ghcr.io/<your-username>/mlops-secure-app:latest
```

### ⬇️ Pull and Run

```bash
docker pull ghcr.io/<your-username>/mlops-secure-app:latest
docker run --rm ghcr.io/<your-username>/mlops-secure-app
```

> Replace `<your-username>` with your GitHub username.

---

## 🧪 Example Unit Test (`tests/test_train.py`)

```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.datasets import load_iris
import pickle, os

def test_model_training():
    iris = load_iris()
    X, y = iris.data, iris.target

    model = RandomForestClassifier().fit(X, y)
    assert model is not None

    with open("test_model.pkl", "wb") as f:
        pickle.dump(model, f)
    assert os.path.exists("test_model.pkl")
```

---

## 📌 Next Steps

- [ ] Deploy model as REST API using FastAPI or Flask
- [ ] Add MLflow for experiment tracking
- [ ] Terraform infra deployment (e.g., AWS ECS or Azure Container Apps)
- [ ] Push images to Docker Hub

---

## 🙌 Credits

Developed with ❤️ by **Mir Owahed Ali**

GitHub: [@mir-owahed](https://github.com/mir-owahed)

---

## 🧷 License

This project is open-source and available under the [MIT License](LICENSE).
```

---

Let me know if you’d like:
- A **badge section** (CI Status, Security Scan, GHCR Push)
- Docker Hub publishing instructions
- FastAPI integration to serve the model

I can generate those as well!
