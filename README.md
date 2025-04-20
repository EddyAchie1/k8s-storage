# 🗄️ Kubernetes Storage Manifests – WordPress & MySQL

This repository contains Kubernetes manifests for deploying a WordPress application with a MySQL database, both using Persistent Volume Claims (PVCs) for storage.


## 📂 What's Included

| File              | Purpose                                                   |
|-------------------|-----------------------------------------------------------|
| `configmap.yaml`  | Environment configuration for the WordPress app           |
| `secret.yaml`     | Stores sensitive data like MySQL root password            |
| `deployment.yaml` | Deploys WordPress and MySQL pods                          |
| `service.yaml`    | Exposes the WordPress and MySQL services                  |
| `mysql-pvc.yaml`  | Persistent Volume Claim for MySQL storage                 |
| `wordpress-pvc.yaml` | Persistent Volume Claim for WordPress storage         |


## 🚀 Getting Started

> Make sure your Kubernetes cluster is up and running with persistent storage support.

## Step 1: Clone the Repository


git clone https://github.com/EddyAchie1/k8s-storage.git

cd k8s-storage

## Step 2: Apply the manifests in order

kubectl apply -f mysql-pvc.yaml

kubectl apply -f wordpress-pvc.yaml

kubectl apply -f wordpress-manifest

✅ This will:

+ Create persistent volumes for MySQL and WordPress using AWS EBS

* Deploy the backend and frontend apps

- Expose them via Kubernetes services

## Step 3: Access the WordPress Site

Check the service:

kubectl get svc

Depending on your service type:

If LoadBalancer, use the EXTERNAL-IP

If NodePort, get the node’s public IP and use the allocated port


### 🧹 Cleanup
To delete all resources:

kubectl delete -f .

ℹ️ Note: AWS EBS volumes may persist even after PVCs are deleted. You may need to manually delete them via the AWS Console or CLI.


### 📌 Notes

The PVCs use the default StorageClass to dynamically provision EBS volumes.

Ensure your EKS nodes are in an Availability Zone that supports EBS.

In production, use encrypted secrets and IAM roles for service accounts (IRSA).


### 📚 References

+ Kubernetes Volumes

- Persistent Volumes & Claims

* AWS EBS 

- WordPress on Kubernetes

+ Amazon EKS Documentation


You can reach out on eddywenger3283@gmail.com
