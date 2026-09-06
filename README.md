# Trendify – Production Application Deployment

## Project Overview

This project demonstrates the deployment of the Trendify React application into a production-ready DevOps environment using Docker, Docker Hub, Terraform, Jenkins, Kubernetes, and Amazon EKS.

## Technology Stack

- React / Vite
- Docker
- Nginx
- Docker Hub
- Git & GitHub
- Terraform
- AWS EC2
- Amazon EKS
- Kubernetes
- Jenkins
- Helm
- Prometheus
- Grafana

## Architecture

Developer
|
v
GitHub Repository
|
v
GitHub Webhook
|
v
Jenkins CI/CD
|
+---- Docker Build
|
+---- Push Image to Docker Hub
|
+---- Deploy to Amazon EKS
|
v
Kubernetes Deployment
|
v
Trendify Pods
|
v
LoadBalancer Service
|
v
Users

## Docker

The application is packaged as a Docker image using Nginx and the production-ready files from the `dist/` directory.

Docker image:

`jayaseelan7577/trendify-app:latest`

## Kubernetes

The application is deployed to Amazon EKS using:

- Deployment: `trendify-deployment`
- Service: `trendify-service`
- Service type: `LoadBalancer`
- Application container port: 80
- Service port: 3000
- Replicas: 2

## CI/CD Pipeline

Jenkins performs the following stages:

1. Checkout source code
2. Build Docker image
3. Push Docker image to Docker Hub
4. Deploy application to Amazon EKS

## Infrastructure

Terraform is used to provision the AWS infrastructure required for the DevOps environment, including networking, IAM, security groups, and the Jenkins EC2 instance.

## GitHub Webhook

A GitHub webhook is configured to trigger the Jenkins pipeline when changes are pushed to the repository.

Webhook endpoint:

`http://13.126.49.169:8080/github-webhook/`

## Monitoring

Prometheus and Grafana are installed and verified for Kubernetes cluster and application monitoring.

## Repository

GitHub:

`https://github.com/Jayaseelan7577/trendify-devops-project2`

## Docker Hub

Docker Hub:

`https://hub.docker.com/r/jayaseelan7577/trendify-app`

## Deployment Status

The CI/CD infrastructure, Docker image, Kubernetes manifests, Jenkins pipeline, and EKS environment have been configured. Final application deployment and LoadBalancer verification are dependent on AWS EC2 capacity availability.

## Author

Jayaseelan M
