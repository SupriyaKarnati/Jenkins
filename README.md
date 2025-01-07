# CI/CD Pipeline with Jenkins, Argo CD, Maven, SonarQube, Docker, and Kubernetes

https://github.com/SupriyaKarnati/Jenkins/blob/a9e8b5205cd7674674ec17b6b1625fac41b721bf/Screenshot%202025-01-07%20at%2015-41-21%20228301952-abc02ca2-9942-4a67-8293-f76647b6f9d8.png%20(PNG%20Image%201321%20%C3%97%20659%20pixels).png

This repository demonstrates my implementation of a **CI/CD pipeline** using industry-standard tools for **continuous integration** and **continuous delivery**. The pipeline integrates **Jenkins** for building and testing, **Argo CD** for deployment automation, and **Kubernetes** for container orchestration. **Maven** is used for building Java applications, **SonarQube** for static code analysis, and **Docker** for containerizing the application.

## Table of Contents

- [Overview](#overview)
- [Skills & Technologies](#skills--technologies)
- [CI/CD Workflow](#cicd-workflow)
- [Setup Instructions](#setup-instructions)
  - [Prerequisites](#prerequisites)
  - [Step-by-Step Setup](#step-by-step-setup)
- [Argo CD Configuration](#argo-cd-configuration)
- [Conclusion](#conclusion)

## Overview

This project showcases my ability to design, implement, and manage a full **CI/CD pipeline** for **Java-based applications**. The pipeline includes:

### CI Process:
- **GitHub Repository**: Source code and versioning.
- **Jenkins**: Automates build, testing, and Docker image creation.
- **SonarQube**: Static code analysis for quality assurance.
- **Docker**: Containerizes the Java application for consistency.
- **Container Registry**: Stores Docker images (e.g., DockerHub, ECR).

### CD Process:
- **Argo Image Updater**: Monitors the container registry for image updates.
- **Argo CD**: Automates deployments to the Kubernetes cluster upon detecting new image versions.

The workflow ensures automated, reliable, and scalable application deployment using **GitOps** and **Kubernetes**.

## Skills & Technologies

- **Jenkins**: Automates the CI process (builds, tests, Docker images).
- **Argo CD**: GitOps tool for Kubernetes continuous delivery.
- **Maven**: Build automation for Java applications.
- **SonarQube**: Static code analysis for maintaining code quality.
- **Docker**: Containerizes the application for deployment consistency.
- **Kubernetes**: Manages deployment and scaling of containers.
- **GitHub**: Repository management and integration with Jenkins/Argo CD.

## CI/CD Workflow

1. **Code Commit**: Developer pushes code to GitHub.
2. **Trigger Jenkins Pipeline**: Jenkins automatically triggers when code is pushed to GitHub (via webhooks).
3. **Build and Test**:
   - Jenkins pulls the code.
   - **Maven** builds the Java app and runs unit tests.
   - **SonarQube** performs static code analysis for quality assurance.
4. **Docker Image Creation**: If the build passes, Jenkins creates a Docker image and pushes it to a container registry (e.g., DockerHub, AWS ECR).
5. **Argo Image Updater**: Monitors the container registry for image changes and updates the version in the GitHub repository.
6. **Argo CD Deployment**: Argo CD deploys the updated Docker image to the Kubernetes cluster.

## Setup Instructions

### Prerequisites

Before you start, ensure you have the following installed:

- **Jenkins**: For automating builds, tests, and deployments.
- **Argo CD**: For deploying applications in Kubernetes.
- **Docker**: For containerizing your application.
- **Kubernetes**: A Kubernetes cluster for hosting the application.
- **GitHub**: To store your source code and deployment manifests.

### Step-by-Step Setup

#### 1. Jenkins Setup

- Install the necessary Jenkins plugins:
  - Maven Integration Plugin
  - Docker Pipeline Plugin
  - SonarQube Scanner Plugin
- Create a `Jenkinsfile` to define the pipeline steps:
  - Pulls code from GitHub.
  - Builds the application using Maven.
  - Runs unit tests.
  - Performs static code analysis with SonarQube.
  - Builds a Docker image and pushes it to a registry.

#### 2. Argo CD Setup

- Install **Argo CD** on your Kubernetes cluster.
- Set up Argo CD to monitor the **GitHub repository** for Kubernetes manifests (Helm charts or YAML files).
- Configure Argo CD to deploy changes to the Kubernetes cluster.

#### 3. Argo Image Updater Setup

- Install **Argo Image Updater** in your Kubernetes cluster.
- Configure it to monitor the container registry (e.g., DockerHub, ECR) for new images.
- It will automatically update Kubernetes deployment manifests in GitHub when a new Docker image version is detected.

#### 4. Container Registry

- Set up a container registry (DockerHub or AWS ECR).
- Configure Jenkins to push Docker images to the registry after successful builds.

## Argo CD Configuration

- **Argo CD** monitors the repository containing Kubernetes manifests.
- **Argo Image Updater** ensures that any new Docker image versions are reflected in the manifests and automatically deploys changes.

## Conclusion

This project highlights the power of modern **CI/CD pipelines**, showcasing automation and integration across popular DevOps tools. By utilizing **Jenkins**, **Argo CD**, **Docker**, and **Kubernetes**, the pipeline ensures continuous integration and deployment in a scalable, efficient manner. The use of **GitOps** practices with Argo CD brings enhanced visibility and control over deployments, while tools like **SonarQube** and **Maven** improve code quality and streamline the build process.

Feel free to explore and leverage this pipeline for your own Java-based applications, or use it as a reference for building a similar automated deployment workflow.

