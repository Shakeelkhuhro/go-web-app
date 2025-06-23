# go-web-app

A simple Go web application, containerized and production-ready with Kubernetes manifests, CI/CD automation, and GitOps deployment via Argo CD.

> **Note:** The Golang application code for `go-web-app` is sourced from [https://github.com/iam-veeramalla](https://github.com/iam-veeramalla). All Kubernetes manifests, CI/CD workflows, Argo CD integration, and deployment automation are created and maintained by myself, as I do not have expertise with Go.

---

## Features

- **Go Web Application**: Lightweight HTTP server written in Go.
- **Dockerized**: Easily build and run the app in any containerized environment.
- **Kubernetes Manifests**: Includes Deployment, Service, and Ingress YAMLs for easy deployment.
- **Helm Chart**: (If present) For templated, reusable Kubernetes deployments.
- **GitHub Actions CI/CD**: Automated build, test, lint, Docker image push, and Helm chart update workflows.
- **Argo CD GitOps**: Declarative, automated deployment to Kubernetes using Argo CD.

---

## Project Structure

```
.
├── Dockerfile
├── main.go
├── k8s/
│   └── manifest/
│       ├── deployment.yaml
│       ├── service.yaml
│       └── ingress.yaml
├── helm/
│   └── go-web-app-chart/
│       └── values.yaml
├── .github/
│   └── workflows/
│       └── ci.yaml
└── README.md
```

---

## Getting Started

### 1. Clone the Repository

```sh
git clone https://github.com/shakeelkhuhro/go-web-app.git
cd go-web-app
```

### 2. Build and Run Locally

```sh
go build -o go-web-app
./go-web-app
```

Or with Docker:

```sh
docker build -t go-web-app .
docker run -p 8081:8081 go-web-app
```

### 3. Kubernetes Deployment

Apply the manifests:

```sh
kubectl apply -f k8s/manifest/
```

- The app runs on port **8081** (see `service.yaml` and `main.go`).
- Ingress is configured for the host `go-web-app.local`.

### 4. CI/CD

- **GitHub Actions**: Automated workflows for build, test, lint, Docker image push, and Helm chart tag update.
- See `.github/workflows/ci.yaml` for details.

### 5. GitOps with Argo CD

- Point your Argo CD application to this repository and the desired path (e.g., `k8s/manifest/` or your Helm chart).
- Argo CD will automatically sync and deploy changes from Git to your Kubernetes cluster.

---

## Customization

- **Application Port**: Default is `8081`. Change in `main.go`, `Dockerfile`, and Kubernetes manifests if needed.
- **DockerHub Credentials**: Set `DOCKERHUB_USERNAME` and `DOCKERHUB_TOKEN` as GitHub repository secrets for Docker image push.
- **Helm Chart**: Update `helm/go-web-app-chart/values.yaml` as needed.
- **Argo CD**: Update your Argo CD application manifest to point to the correct repo path and revision.

---

## Credits

- **Go Application Code**: [https://github.com/iam-veeramalla](https://github.com/iam-veeramalla)
- **Kubernetes, CI/CD, Argo CD, and Automation**: Created and maintained by myself.

---

## License

This project is for educational and demonstration purposes.  
Please refer to the original Go application repository for its license.
