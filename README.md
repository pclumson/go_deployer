# go_deployer
 Build a CLI tool in Go that automates the deployment of a containerized app to a Kubernetes cluster, simulating the "mission-critical internal platform" 


🚀 Go-Deployer: Kubernetes CI/CD Automation Tool

A lightweight, high-performance Golang CLI tool designed to automate microservice deployments to Kubernetes clusters. Built to enhance developer productivity and ensure zero-downtime releases through automated rolling updates and health checks.

This project demonstrates proficiency in Golang, Kubernetes (K8s), Docker, and CI/CD pipeline integration, addressing the need for scalable, secure internal tooling in cloud-native environments.
✨ Features

    🛠️ CLI Interface: Intuitive command-line arguments for namespace, image, and replica management.
    🔄 Rolling Updates: Implements Kubernetes rolling update strategies to prevent service interruption.
    🏥 Health Checks: Automatically waits for pods to become Ready before marking the deployment successful.
    ⚡ Error Handling: Robust error propagation and context cancellation for reliable production execution.
    🔒 Security First: Validates image tags (rejects latest) and enforces namespace isolation.
    🤖 CI/CD Ready: Includes a pre-configured GitLab CI pipeline for automated building and testing.

🛠️ Tech Stack
Component	Technology
Language	Golang (1.21+)
Orchestration	Kubernetes (Kubectl Client-Go)
Containerization	Docker
CI/CD	GitLab CI / GitHub Actions
Testing	Go testing package, mock
Cloud	AWS EKS / Google GKE (Compatible)
📦 Installation
Prerequisites

    Go 1.21+ installed
    kubectl configured with access to a cluster
    Docker installed (for building images)

Build from Source

# Clone the repository
git clone https://github.com/your-username/go-deployer.git
cd go-deployer

# Build the binary
go build -o go-deployer .

# Run the help command
./go-deployer --help

🚀 Usage

Deploy an application with a specific image and replica count:

./go-deployer deploy \
  --namespace production \
  --image my-app:v1.2.0 \
  --replicas 3 \
  --timeout 300s

Flags:

    --namespace: Target Kubernetes namespace (default: default)
    --image: Container image to deploy (e.g., nginx:1.21)
    --replicas: Number of desired replicas (default: 1)
    --timeout: Max wait time for rollout completion (default: 60s)

🔄 CI/CD Integration

This project includes a .gitlab-ci.yml configuration that automates the build, test, and deployment lifecycle.
Pipeline Stages

    Build: Compiles the Go binary and runs unit tests.
    Lint: Runs golangci-lint for code quality.
    Deploy: Executes the tool against a staging cluster (simulated).

Sample .gitlab-ci.yml snippet:

stages:
  - build
  - test
  - deploy

build_job:
  stage: build
  script:
    - go build -o go-deployer .
  artifacts:
    paths:
      - go-deployer

test_job:
  stage: test
  script:
    - go test -v ./...

deploy_job:
  stage: deploy
  script:
    - ./go-deployer deploy --namespace staging --image $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA --replicas 2
  only:
    - main

🧪 Testing

Run the comprehensive test suite:

go test -v -cover ./...

Coverage Report:

    Unit tests cover CLI argument parsing, error handling, and K8s client mocking.
    Integration tests simulate deployment scenarios in a local Minikube environment.

📂 Project Structure

go-deployer/
├── cmd/
│   └── main.go          # Entry point and CLI flag parsing
├── pkg/
│   ├── k8s/             # Kubernetes client logic
│   │   ├── deploy.go    # Rolling update logic
│   │   └── health.go    # Pod readiness checks
│   └── cli/             # Command definitions
├── internal/
│   └── config/          # Configuration management
├── .gitlab-ci.yml       # CI/CD Pipeline definition
├── go.mod               # Go module dependencies
└── README.md            # Documentation

🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

    Fork the project
    Create your feature branch (git checkout -b feature/AmazingFeature)
    Commit your changes (git commit -m 'Add some AmazingFeature')
    Push to the branch (git push origin feature/AmazingFeature)
    Open a Pull Request

📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

👨‍💻 Author :Prince Clumson-Eklu

    Role: Senior Full Stack Software Engineer
    Expertise: Cloud-Native Architecture, Golang, Python, Java CI/CD Automation
    GitHub: github.com/pclumson
    
