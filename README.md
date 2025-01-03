##Problem Statement 1: Containerization and Deployment of Wisecow Application on Kubernetes##

Step-by-Step Details for Each Phase

1. Dockerization:
-Ensure you have installed Docker on your system and it’s running.
-Test the application locally
                docker run -p 5000:5000 wisecow:latest
-Access the app at http://localhost:5000 to verify functionality.


2. Kubernetes Deployment:
   Cluster Setup:
            -Install Minikube (for local setup) or set up a cloud-managed Kubernetes cluster (e.g., GKE, EKS, or AKS).
            -Start Minikube
minikube start

  Test Deployment:
       -After applying the manifest files (kubectl apply -f deployment.yaml and kubectl apply -f service.yaml), check the status:
kubectl get pods
kubectl get svc

      -Use minikube service wisecow-service to access the application in a local Minikube environment.

3. GitHub Actions Workflow:
  Secret Management:
          -Add the following secrets in your GitHub repository settings:
          -DOCKER_USERNAME: Your DockerHub username.
          -DOCKER_PASSWORD: Your DockerHub password.
          -KUBECONFIG: Kubernetes configuration for deployment.

  Pipeline Execution:
            -On every commit to the main branch, the pipeline:
            -Builds and pushes the Docker image to DockerHub.
            -Automatically deploys the updated app to the Kubernetes cluster.

  TLS Implementation:
      -Create an Ingress resource to handle HTTP traffic
      -Update DNS settings for wisecow.example.com to point to your Kubernetes cluster.
