# Projet Clusterisation de Conteneurs

## 📦 Objectif

Mettre en place une application conteneurisée et orchestrée avec :
- Backend : NestJS (TypeScript)
- Frontend : React (JavaScript)
- Base de données : PostgreSQL

Déployée sur un cluster Kubernetes pour démontrer :
✅ Haute disponibilité  
✅ Persistance des données  
✅ Sécurité (Secrets)  
✅ Exposition via Ingress

---

## 📁 Structure du projet

```

/backend/backend-app        → NestJS backend
/frontend/frontend-app      → React frontend
/k8s                       → Manifests Kubernetes (YAML)

````

---

## 🚀 Étapes d’installation

### 1️⃣ Démarrer Kubernetes avec Docker Desktop
- Active Kubernetes dans Docker Desktop
- Vérifie :
  ```bash
  kubectl cluster-info
  kubectl get nodes
````

---

### 2️⃣ Construire et pousser les images Docker

Backend :

```bash
cd backend/backend-app
docker build -t iouahabi/backend:latest .
docker push iouahabi/backend:latest
```

Frontend :

```bash
cd frontend/frontend-app
docker build -t iouahabi/frontend:latest .
docker push iouahabi/frontend:latest
```

---

### 3️⃣ Configurer le fichier hosts

Ajoute à la fin de `C:\Windows\System32\drivers\etc\hosts` :

```
127.0.0.1 app.local
```

---

### 4️⃣ Déployer Kubernetes

```bash
kubectl apply -f k8s/secrets.yaml
kubectl apply -f k8s/postgres.yaml
kubectl apply -f k8s/backend.yaml
kubectl apply -f k8s/frontend.yaml
kubectl apply -f k8s/ingress.yaml
```

---

### 5️⃣ Vérifier les déploiements

```bash
kubectl get pods
kubectl get services
kubectl get ingress
```

---

### 6️⃣ Accéder à l’application

* Frontend → [http://app.local/frontend](http://app.local/frontend)
* Backend → [http://app.local/backend](http://app.local/backend)

---

## 🔐 Sécurité

* Secrets stockés dans `k8s/secrets.yaml`
* Variables d’environnement injectées dans les pods

---

## 📊 Monitoring (bonus possible)

```bash
kubectl get pods -w
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```

---

## 📷 Captures attendues pour le rendu

✅ Cluster nodes (`kubectl get nodes`)
✅ Pods running (`kubectl get pods`)
✅ Services (`kubectl get services`)
✅ Ingress (`kubectl get ingress`)
✅ Tests de scalabilité : scale up/down, kill pod

---

## ✅ Bonus recommandés (jusqu’à +5 points)

* Autoscaling horizontal (HPA)
* Rolling updates
* NetworkPolicy
* Helm charts
* CI/CD pipeline

---

## ✏ Rapport final

* Schéma d’architecture
* Étapes d’installation
* Captures de preuve
* Liste des bonus réalisés

---

## 💬 Auteur

* Docker Hub : iouahabi
* GitHub : \[Narutino10]

