# Tumble Toys

A small toy shop website (React + Vite) used for a DevOps CI/CD lab.

Pipeline: Git → GitHub → branch → npm → lint → tests → SonarQube → Trivy → GitHub Actions → Amazon ECR → EC2 → Docker → browser.

## Run locally

```bash
npm ci
npm run lint
npm test
npm run build
npm run dev
```

## Docker

```bash
docker build -t toy-shop .
docker run -d --name toy-shop -p 8080:80 toy-shop
```

Open http://localhost:8080

## GitHub secrets for CI

- `SONAR_HOST_URL`, e.g. `http://<EC2-IP>:9000`
- `SONAR_TOKEN`
- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`

CI runs lint, tests, build, SonarQube and Trivy on every pull request.
On merge to `main` it builds the Docker image and pushes it to Amazon ECR (`toy-shop` repository, `us-east-1`).

Project by Marta Dzekevich
Made by Marta
Toy Shop CI Project
