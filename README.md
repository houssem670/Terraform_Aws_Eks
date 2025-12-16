# Terraform AWS EKS Project

## Description
Ce projet met en place une **infrastructure Kubernetes complète sur AWS** en utilisant **Terraform**.  
Il comprend la création du réseau, d’un cluster **Amazon EKS** et le déploiement d’une application **Nginx** sur Kubernetes.

---

## Architecture globale

- VPC AWS avec un **CIDR configurable via Terraform**
- Subnets **publics et privés** répartis sur plusieurs Availability Zones
- **Internet Gateway** pour l’accès Internet des subnets publics
- **NAT Gateway** pour l’accès sortant des subnets privés
- **Cluster Amazon EKS** (control plane managé par AWS)
- **Worker nodes EC2** exécutant les workloads Kubernetes
- Application **Nginx** exposée via un **Service Kubernetes de type LoadBalancer**

---

## Structure du projet

TERRAFORM_AWS_EKS/
├── vpc.tf                 # Création de la VPC, subnets, IGW, NAT et route tables

├── eks-cluster.tf         # Cluster EKS et worker nodes

├── terraform.tfvars       # Valeurs des variables Terraform

├── nginx-config.yaml      # Deployment et Service Kubernetes (Nginx)

├── README.md              # Documentation du projet

├── .gitignore

└── .terraform.lock.hcl

## Commande Utiliser

# Terraform:

terraform init

terraform plan

terraform apply

# Configuration de kubectl:

aws eks --region eu-west-3 update-kubeconfig --name myapp-eks-cluster


# Kubernetes:

kubectl apply -f nginx-config.yaml

kubectl get pods

kubectl get svc

# Accéder à l’application Nginx

Après avoir déployé Nginx, récupère l’adresse publique avec :

kubectl get svc 

Ensuite, ouvre cette adresse dans le navigateur ou utilise curl :

curl http://EXTERNAL-IP


# Objectifs du projet:

- Déployer une infrastructure AWS avec Terraform
- Comprendre l’architecture EKS (control plane vs worker nodes)
- Déployer une application conteneurisée sur Kubernetes
- Appliquer les bonnes pratiques DevOps & Cloud

