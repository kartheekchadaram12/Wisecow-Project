# Wisecow-Project
<img width="1920" height="1080" alt="Screenshot (529)" src="https://github.com/user-attachments/assets/5127eb1e-d98c-42bf-9bca-d7193382b933" />

<img width="1920" height="1080" alt="Screenshot (531)" src="https://github.com/user-attachments/assets/f3e73ca7-16ca-4f03-8ae3-d8bf1db7f6df" />

<img width="1920" height="1080" alt="Screenshot (534)" src="https://github.com/user-attachments/assets/68f86a59-c480-49dd-9250-2d74498e30c3" />

Wisecow Application:
Overview

Wisecow is a web application deployed using a modern DevOps workflow. The deployment pipeline automates build, Docker image creation, artifact storage, and Kubernetes deployment using Minikube.

CI/CD Pipeline Steps:

* Checkout Code

Jenkins pulls the latest code from the GitHub repository:
git clone https://github.com/kartheekchadaram12/Wisecow-Project.git


* Build Application

The application is built and any necessary dependencies are installed.

Example: Custom scripts or build commands are executed.

* Archive Artifacts

Key project files (Dockerfile, wisecow.sh) are stored in Jenkins as build artifacts for traceability.

* Docker Build & Push

A Docker image of the Wisecow application is built using the Dockerfile:

docker build -t rateshivakumar/wisecow:<BUILD_NUMBER> /root/Wisecow-Project


The image is pushed to Docker Hub:

docker push rateshivakumar/wisecow:<BUILD_NUMBER>
docker push rateshivakumar/wisecow:latest


* Deploy Locally (Optional)

Run the Docker container locally for testing:

docker rm -f wisecow || true
docker run -d --name wisecow -p 4499:4499 rateshivakumar/wisecow:<BUILD_NUMBER>


* Deploy on Kubernetes (Minikube)

Use the provided Kubernetes manifest wisecow-deploy.yaml to deploy Wisecow:

kubectl apply -f wisecow-deploy.yaml


Verify pods and service:

kubectl get pods
kubectl get svc

Access the Application

After deployment, access the application using the Minikube service URL:

minikube service wisecow

*Technologies Used:

CI/CD: Jenkins

Containerization: Docker, Docker Hub

Orchestration: Kubernetes, Minikube

Scripting: Shell scripts (wisecow.sh, deployment scripts)

Repository: GitHub


