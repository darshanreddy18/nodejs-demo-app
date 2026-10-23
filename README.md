Node.js CI/CD Pipeline with GitHub Actions and Docker

📌 Project Overview

This project demonstrates how to automate the testing, Docker image building, and deployment preparation of a Node.js application using GitHub Actions and Docker Hub.

Whenever code is pushed to the "main" branch, GitHub Actions automatically runs the CI/CD workflow. It checks the application, builds a Docker image, and pushes the image to Docker Hub.

🎯 Project Objectives

- Understand Continuous Integration (CI) and Continuous Deployment (CD).
- Automate application checks using GitHub Actions.
- Containerize a Node.js application using Docker.
- Build and publish Docker images automatically.
- Store Docker images in Docker Hub.
- Learn the fundamentals of DevOps automation.

🛠️ Technologies Used

- Node.js — JavaScript runtime.
- Express.js — Web application framework.
- Git and GitHub — Source code management.
- GitHub Actions — CI/CD workflow automation.
- Docker — Application containerization.
- Docker Hub — Docker image registry.
- Linux — Command-line environment.

🏗️ Project Architecture

Developer
    |
    v
GitHub Repository
    |
    | Push code to main
    v
GitHub Actions Workflow
    |
    v
Install Dependencies & Check Application
    |
    v
Build Docker Image
    |
    v
Authenticate with Docker Hub
    |
    v
Push Docker Image to Docker Hub
    |
    v
Pull and Run the Docker Container

📂 Project Structure

nodejs-demo-app/
├── .github/
│   └── workflows/
│       └── main.yml
├── app.js
├── package.json
├── package-lock.json
├── Dockerfile
├── .dockerignore
├── .gitignore
└── README.md

⚙️ Application Details

The application is built with Node.js and Express.js.

It provides two endpoints:

Endpoint| Description
"/"| Displays a welcome message confirming that the application is running.
"/health"| Returns the application's health status as JSON.

Example health-check response:

{
  "status": "healthy"
}

🐳 Docker Configuration

The Dockerfile packages the application into a container.

The image uses Node.js 22 Alpine as its base image, installs dependencies with "npm ci", copies the application files, and starts the Node.js application.

Build the Docker image locally:

docker build -t nodejs-demo-app .

Run the container:

docker run -d --name nodejs-demo -p 3000:3000 nodejs-demo-app

Open the application in your browser:

- Application: "http://localhost:3000"
- Health check: "http://localhost:3000/health"

To stop and remove the container:

docker stop nodejs-demo
docker rm nodejs-demo

🔄 CI/CD Workflow

The GitHub Actions workflow is configured in:

".github/workflows/main.yml"

The workflow performs these steps:

1. Checkout Code — Retrieves the repository source code.
2. Set Up Node.js — Configures the Node.js environment.
3. Install Dependencies — Installs dependencies using "npm ci".
4. Check JavaScript Syntax — Checks "app.js" for syntax errors.
5. Set Up Docker Buildx — Prepares Docker image building.
6. Authenticate with Docker Hub — Uses GitHub Actions secrets.
7. Build Docker Image — Builds the container image.
8. Push Docker Image — Publishes the image to Docker Hub.

The Docker image is published only when the workflow runs after a push to the "main" branch and the test job succeeds.

🔐 GitHub Secrets Configuration

For secure Docker Hub authentication, configure these repository secrets:

Secret Name| Value
"DOCKERHUB_USERNAME"| Your Docker Hub username
"DOCKERHUB_TOKEN"| Your Docker Hub access token

Add them under:

GitHub Repository → Settings → Secrets and variables → Actions → New repository secret

Security note: Never hardcode your Docker Hub token in the workflow file or commit it to GitHub.

📦 Docker Hub Image

After a successful workflow run, the Docker image is available in Docker Hub.

Expected image name:

darshanreddy18/nodejs-demo-app:latest

The workflow also publishes an image tagged with the Git commit SHA.

Replace "darshanreddy18" if your Docker Hub username is different.

🚀 Run the Published Docker Image

Pull the latest image:

docker pull darshanreddy18/nodejs-demo-app:latest

Run the container:

docker run -d --name cicd-test -p 3001:3000 darshanreddy18/nodejs-demo-app:latest

Test the application:

- Application: "http://localhost:3001"
- Health check: "http://localhost:3001/health"

Stop and remove the test container:

docker stop cicd-test
docker rm cicd-test

✅ Expected Results

After successful execution:

- The Node.js application runs inside a Docker container.
- GitHub Actions automatically checks the application.
- Docker images are built automatically after successful checks.
- Docker images are pushed to Docker Hub.
- The published image can be pulled and run on another compatible system.

📚 Key Learnings

Through this project, I learned:

- Basic CI/CD pipeline implementation.
- Git and GitHub repository management.
- GitHub Actions workflow configuration.
- Docker image creation and container management.
- Docker Hub authentication using repository secrets.
- Automated Docker image publishing.
- Basic application health checks and troubleshooting.

🔮 Future Improvements

- Add automated unit and integration tests.
- Deploy the application to AWS.
- Add a production deployment stage.
- Integrate monitoring and logging.
- Add automated rollback support.

👨‍💻 Author

Darshan

BCA Student | Aspiring DevOps Engineer

Project: Automate Code Deployment Using a CI/CD Pipeline with GitHub Actions and Docker.