# 🚀 Deploying Multi-Tier Java Web Application on Kubernetes (K8s)

## 📌 Project Overview
This project deploys a **multi-tier Java web application** on **Kubernetes**, ensuring **scalability, resilience, and security**. By leveraging **Kubernetes Deployments, Services, Secrets, and Init Containers**, we create a highly available architecture.

## 🎯 Purpose
- **Automate deployment & scaling** of multi-tier applications.
- **Ensure secure communication** between services using **K8s Secrets & Networking**.
- **Improve reliability** with **self-healing & load balancing**.
- **Streamline operations** for real-world Kubernetes deployments.

## 🔧 Kubernetes Resources & Tech Stack
| Resource | Purpose |
|----------|---------|
| **Deployments** | Manages scaling & updates of application components |
| **Services** | Connects & exposes app components securely |
| **Secrets** | Protects sensitive data (DB credentials, RabbitMQ passwords) |
| **Init Containers** | Ensures dependencies are available before app starts |
| **LoadBalancer & NodePort** | Manages external access |
| **Kubernetes Cluster** | Hosts and manages all workloads |
| **Docker** | Containerizes the application for portability |

## 🏗️ Architecture
The project consists of the following components deployed as **Kubernetes workloads**:
- **Application Deployment (Tomcat-based Java Web App)**
- **Database Deployment (MySQL)**
- **Message Queue (RabbitMQ)**
- **Cache Layer (Memcached)**
- **Load Balancer for traffic management**
- **Secrets for secure authentication**

![Project Architecture](./architecture.gif)

## 📌 Setup Instructions

### 1️⃣ Prerequisites
Ensure you have:
- **Kubernetes Cluster** (Minikube, K3s, or AWS/GCP cluster)
- **kubectl Installed** → [Install Guide](https://kubernetes.io/docs/tasks/tools/)
- **Docker Installed** → [Download Docker](https://www.docker.com/get-started)

### 2️⃣ Clone This Repository
```sh
$ git clone https://github.com/yourusername/K8s-MultiTier-App.git
$ cd K8s-MultiTier-App
```

### 3️⃣ Deploy Services & Components
#### 🚀 **Step 1: Deploy the Database**
```sh
$ kubectl apply -f k8s/database-deployment.yaml
$ kubectl apply -f k8s/database-service.yaml
$ kubectl apply -f k8s/database-secret.yaml
```
- Ensures **MySQL is running securely** with Kubernetes Secrets.

#### ⚡ **Step 2: Deploy RabbitMQ**
```sh
$ kubectl apply -f k8s/rabbitmq-deployment.yaml
$ kubectl apply -f k8s/rabbitmq-service.yaml
$ kubectl apply -f k8s/rabbitmq-secret.yaml
```
- RabbitMQ is set up with **secure credentials & internal networking**.

#### 🔥 **Step 3: Deploy Memcached (Caching Layer)**
```sh
$ kubectl apply -f k8s/memcached-deployment.yaml
$ kubectl apply -f k8s/memcached-service.yaml
```
- Memcached provides **fast in-memory caching** for better app performance.

#### 🌍 **Step 4: Deploy the Java Web Application**
```sh
$ kubectl apply -f k8s/application-deployment.yaml
```
- Uses **Init Containers** to ensure dependencies **(Database, Cache)** are ready before starting.

#### 🌐 **Step 5: Expose the Application with Load Balancer**
```sh
$ kubectl apply -f k8s/loadbalancer-service.yaml
```
- External users can access the application through **a public LoadBalancer**.

### 4️⃣ Testing & Validation
Once all components are running, verify the deployment:
```sh
$ kubectl get pods -n java
$ kubectl get services -n java
```
Expected Response:
```
NAME                     READY   STATUS    RESTARTS   AGE
app01-xxxxxxx            1/1     Running   0          5m
mc01-xxxxxxx             1/1     Running   0          5m
db01-xxxxxxx             1/1     Running   0          5m
rmq01-xxxxxxx            1/1     Running   0          5m
```

## 🔥 Security Best Practices
✅ **Each service has a dedicated Secret for credentials**
✅ **Least privilege networking (ClusterIP Services)**
✅ **Load Balancer & NodePort for controlled external access**
✅ **Self-healing deployments for reliability**


## 👨‍💻 Contributors
- **Mohamed Elweza**
- **Nader Ashour**

## 📜 License
This project is licensed under the **MIT License**.

---

📌 **Follow this repository for updates!**
✅ If you found this useful, don't forget to **star ⭐ the repo**!

💬 Feel free to open issues or contribute to improve this setup!
