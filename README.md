# Node.js CI/CD Pipeline using GitHub Actions, Docker & AWS EC2 🚀

A complete CI/CD pipeline project using GitHub Actions, Docker, DockerHub, and AWS EC2.

---

## 📌 Project Overview

This project demonstrates how to automate the build process of a Node.js application using GitHub Actions.

Whenever code is pushed to the `master` branch:
- GitHub Actions workflow is triggered
- Dependencies are installed
- Docker image is built
- Docker image is pushed to DockerHub automatically

---

## 🛠️ Technologies Used

- Node.js
- Express.js
- Docker
- DockerHub
- GitHub Actions
- AWS EC2
- Ubuntu Linux

---

## 📂 Project Structure

```text
nodejs-demo-app/
│
├── .github/
│   └── workflows/
│       └── main.yml
│
├── Dockerfile
├── package.json
├── package-lock.json
├── index.js
└── README.md
```

---

## 🚀 Run Application Locally

### Install Dependencies

```bash
npm install
```

### Start Application

```bash
npm start
```

Application runs on:

```text
http://localhost:3000
```

---

## 🐳 Docker Commands

### Build Docker Image

```bash
docker build -t nodejs-demo-app .
```

### Run Docker Container

```bash
docker run -d -p 3000:3000 nodejs-demo-app
```

---

## ⚙️ GitHub Actions Workflow

Workflow file location:

```text
.github/workflows/main.yml
```

Workflow automatically triggers on:

```yaml
push to master branch
```

---

## 🔐 GitHub Secrets

Add the following secrets in:

```text
GitHub Repository → Settings → Secrets and variables → Actions
```

| Secret Name | Description |
|---|---|
| DOCKER_USERNAME | DockerHub Username |
| DOCKER_PASSWORD | DockerHub Access Token |

---

## 📄 CI/CD Workflow File

```yaml
name: CI/CD Pipeline

on:
  push:
    branches:
      - master

jobs:

  build-and-push:
    runs-on: ubuntu-latest

    steps:

      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 18

      - name: Install Dependencies
        run: npm install

      - name: Run Tests
        run: echo "No tests yet"

      - name: Login to DockerHub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKER_USERNAME }}
          password: ${{ secrets.DOCKER_PASSWORD }}

      - name: Build Docker Image
        run: docker build -t ${{ secrets.DOCKER_USERNAME }}/nodejs-demo-app .

      - name: Push Docker Image
        run: docker push ${{ secrets.DOCKER_USERNAME }}/nodejs-demo-app
```

---

## 🎯 Learning Outcomes

- Understanding CI/CD concepts
- Automating workflows using GitHub Actions
- Building Docker images
- Pushing images to DockerHub
- Node.js application containerization
- DevOps automation fundamentals

---

## 👨‍💻 Author

### Siddhesh Sarnobat

---

## 📜 License

This project is licensed under the MIT License.
