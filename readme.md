# 🗒️ Notes App on Kubernetes

This project deploys a containerized Flask-based Notes App to a Kubernetes cluster with a focus on scalability, resiliency, and resource efficiency. It uses MySQL (not included here, assumed to be separately configured), and includes auto-scaling with **HPA**, **KEDA**, and **VPA**.

---

##  Components

- **Flask Notes App** deployed via Kubernetes Deployment
- **Service** to expose the app within the cluster
- **Namespace** isolation (`notes-app`)
- **Liveness, Readiness, and Startup Probes** for health checking
- **VerticalPodAutoscaler (VPA)** for automatic resource recommendations
- **HorizontalPodAutoscaler (HPA)** for scaling based on CPU utilization
- **KEDA ScaledObject** for custom scaling logic

---

## Kubernetes Resources

###  Namespace

Creates a dedicated namespace for the app:

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: notes-app
```

### To create all those object run commands 

1. Build the app
```
docker build -t devendracode1910/notes-app-k8s:v1 .
```

2. Build the app
```
docker run -d -p 8000:8000 notes-app:latest
```

3. Create Namespace
```
kubectl apply -f namespace.yaml
```

4. Create deployment
```
kubectl apply -f deployment.yaml
```

5. Create Service
```
kubectl apply -f service.yaml
```

6. Create Horizontal Pod Autoscaling
```
kubectl apply -f hpa.yaml
```

7. Create Vertical Pod Autoscaling
```
kubectl apply -f vpa.yaml
```

8. Create Kubernetes Event Driven Autoscaling
```
kubectl apply -f keda.yaml
```

