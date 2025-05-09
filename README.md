# MLOps Image Classification App 🚀

This is a complete MLOps-ready image classification application. The app classifies images (fruits/birds/vegetables) and supports:

- 📤 Upload via frontend
- 🔍 Real-time predictions via FastAPI
- 🧠 Model training using PyTorch (ResNet18)
- 📦 Dockerized deployment
- 🚀 CI/CD pipeline using GitHub Actions
- ⚙️ Kubernetes deployment
- 📊 Grafana monitoring for inference metrics

---

## 📁 Project Structure
```
mlops_image_app/
├── ml/ # Training script
│ └── train.py
├── inference/ # Inference logic
│ └── predictor.py
├── api/ # FastAPI backend
│ └── main.py
├── frontend/ # Upload UI
│ └── index.html
├── model/ # Trained model
│ └── model.pt
├── static/ # Uploaded images (optional)
├── Dockerfile # Docker build for inference API
├── requirements.txt
├── README.md
└── .github/
└── workflows/
└── ci-cd.yml # Training + Docker CI/CD
```

## 🏗️ Setup and Run Locally

### 1. Install Dependencies
```bash
pip install -r requirements.txt
```
### 2. Train the Model
```
bash
python ml/train.py
```
This saves the model to model/model.pt.

### 3. Run API Locally
bash
```
uvicorn api.main:app --reload
Access UI at: http://localhost:8000
```

### 4. Docker Deployment
```
bash
docker build -t image-classifier-app .
docker run -p 8000:8000 image-classifier-app
```

### 5. Kubernetes Deployment
```
kubectl apply -f k8s/deployment.yaml
```

### 6. Monitor Inference Metrics
Use Prometheus + Grafana to monitor FastAPI request latency and throughput.
Integrate FastAPI middleware with Prometheus exporter (e.g. prometheus_fastapi_instrumentator).

### 7.  CI/CD on GitHub Actions
The .github/workflows/ci-cd.yml file will:

-  Trigger on push
-  Run training script
-  Save model artifact
-  Build and push Docker image (if configured)
-  📊 Monitoring with Grafana
-  Use FastAPI + Prometheus + Grafana stack.
-  Add prometheus_fastapi_instrumentator to API
-  Scrape metrics at /metrics
-  Configure Grafana dashboard with latency, request counts, status codes

### 8. TODO to Productionize
 
 Kubernetes manifests to cloud
 Add Prometheus metrics
 Add logging (ELK / Loki)
 Add auth, versioning

 
### 9. Contact
For questions or enhancements, open an issue or reach out.
