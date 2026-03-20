# Kubernetes Operator POC (Nginx)

## 📌 Overview
This project demonstrates a Kubernetes Operator built using Operator SDK (Go).

The operator manages a custom resource called **NginxApp** and automatically creates a Deployment with specified replicas.

---

## ⚙️ Tech Stack
- Go (Operator SDK)
- Kubernetes
- Kind (local cluster)
- Docker

---

## 🧠 How it works

1. User creates a custom resource:
```yaml
apiVersion: apps.demo.com/v1
kind: NginxApp
metadata:
  name: my-nginx
spec:
  replicas: 2
```

2. Operator watches this resource

3. Operator creates a Deployment

4. Kubernetes creates Pods

---

## 🚀 Setup Instructions

### 1. Start cluster
```bash
kind create cluster
```

### 2. Install CRD
```bash
make install
```

### 3. Run operator
```bash
make run
```

### 4. Apply resource
```bash
kubectl apply -f nginxapp.yaml
```

### 5. Check pods
```bash
kubectl get pods
```

---

## 🎯 Output

Pods are created automatically based on replicas:

```
my-nginx-xxxxx   Running
my-nginx-yyyyy   Running
```

---

## 📌 Features

- Custom Resource Definition (CRD)
- Controller logic using Operator SDK
- Automatic Deployment creation
- Reconciliation loop

---

## 🔮 Future Improvements

- Handle updates (replica scaling)
- Add Service creation
- Add status updates
- Error handling & retries
