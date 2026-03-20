# Kubernetes Operator POC - Nginx

## 📌 Overview
This project demonstrates a Kubernetes Operator built using Operator SDK (Go).

The operator introduces a custom resource called **NginxApp**. Based on the user-defined configuration (like replicas), the operator automatically creates and manages a Kubernetes Deployment.

---

## ⚙️ Tech Stack
- Go (Operator SDK)
- Kubernetes
- Kind (local Kubernetes cluster)
- Docker

---

## 🧠 How it works

1. User defines a custom resource:

```yaml
apiVersion: apps.demo.com/v1
kind: NginxApp
metadata:
  name: my-nginx
spec:
  replicas: 2
```

2. The operator continuously watches for `NginxApp` resources  
3. On detecting a new resource, it triggers the controller logic  
4. The controller creates a Kubernetes Deployment  
5. Kubernetes automatically creates Pods based on the desired replicas  

---

## 🚀 Setup Instructions

### 1. Create local Kubernetes cluster
```bash
kind create cluster
```

### 2. Install CRD (Custom Resource Definition)
```bash
make install
```

### 3. Run the operator
```bash
make run
```

### 4. Apply custom resource
```bash
kubectl apply -f nginxapp.yaml
```

### 5. Verify pods
```bash
kubectl get pods
```

---

## 🎯 Expected Output

Pods will be created automatically:

```
my-nginx-xxxxx   Running
my-nginx-yyyyy   Running
```

---

## 📌 Features

- Custom Resource Definition (CRD)
- Controller built using Operator SDK
- Automatic Deployment creation
- Reconciliation loop implementation
- Local Kubernetes setup using Kind

---

## 🔄 Example Flow

1. Apply resource → `kubectl apply -f nginxapp.yaml`  
2. Operator detects resource  
3. Deployment is created  
4. Pods are automatically spawned  

---

## 🔮 Future Improvements

- Handle updates (dynamic replica scaling)
- Add Service for external access
- Add status updates in CRD
- Improve error handling and retries
- Deploy operator inside cluster (production setup)

---

## 💼 Use Case

This POC demonstrates how Kubernetes Operators can automate application lifecycle management by extending Kubernetes APIs with custom logic.

---

## 📎 Repository

GitHub: https://github.com/anujmehta29/nginx-k8s-operator
