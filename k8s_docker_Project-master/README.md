# Crypto Price Tracker - Docker & Kubernetes Exam

This project is a full-stack application consisting of a Python Flask Frontend, a Python Flask Backend, and a MySQL database. It fetches cryptocurrency prices via API, displays them, and logs the data to a database.

## 🚀 Project Components
- **Frontend (Port 5002):** Python 3.12, renders the UI and communicates with the Backend.
- **Backend (Port 5001):** Python 3.12, fetches API data and handles MySQL logic.
- **Database:** MySQL 5.7, stores price history in `crypto_db`.

---

## 🛠 Deployment Instructions

### 1. Docker Compose (Local Development)
To run the entire stack locally using Docker Compose:
```bash
docker-compose up --build
```
Access the UI at: http://localhost:5002

### 2. Kubernetes (Manual Manifests)
To deploy using standard Kubernetes objects:
- Update the image tags in k8s-manifests/frontend.yaml and backend.yaml.
- Apply the manifests:
```bash
kubectl apply -f k8s-manifests/mysql.yaml
kubectl apply -f k8s-manifests/backend.yaml
kubectl apply -f k8s-manifests/frontend.yaml
```
### 3. Helm (Automated Deployment)
To deploy using the provided Helm chart:
- Ensure you are in the project root.
- Install the chart:
```bash
helm install crypto-release ./helm-charts/crypto-app
```
## 📋 Verification
After deployment, verify the status of the resources:
- Pods: kubectl get pods (Expected: 5 pods running)
- Services: kubectl get svc (Expected: frontend-service type LoadBalancer)

---

### Final Steps to Submit:

1. **Check images:** Ensure your `values.yaml` and K8s files point to your **actual** Docker Hub username.
2. **Git Push:**
   ```bash
   git add .
   git commit -m "Final submission: Added README and verified Helm/K8s manifests"
   git push origin workshop/k8s-docker-exam