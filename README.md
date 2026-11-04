# CI/CD Pipeline Demo (CodeAlpha Internship)

A simple Flask web app with a fully automated CI/CD pipeline built using GitHub Actions and GitHub Container Registry (ghcr.io).

## Project Overview

Every time code is pushed to the `main` branch, the pipeline automatically:

1. Checks out the code
2. Runs a syntax check (CI)
3. Builds a Docker image
4. Pushes the image to GitHub Container Registry (ghcr.io)

## Tech Stack

| Tool | Purpose |
|------|---------|
| Python + Flask | Sample web application |
| Gunicorn | Production web server inside the container |
| Docker | Containerizing the app |
| GitHub Actions | CI/CD pipeline |
| GitHub Container Registry (ghcr.io) | Stores Docker images |
| Git + GitHub | Version control |

## Project Structure

```
CodeAlphaProject/
├── .github/
│   └── workflows/
│       └── cicd.yml        # Pipeline definition
├── app.py                  # Flask web app
├── requirements.txt        # Python dependencies
├── Dockerfile              # Container build instructions
└── README.md               # Project documentation
```

## Run Locally

### Without Docker

```bash
pip install flask
python app.py
```

Open http://localhost:8000 in your browser.

### With Docker

```bash
docker build -t codealpha_cicddemo .
docker run -p 8000:8000 codealpha_cicddemo
```

Open http://localhost:8000 in your browser.

## CI/CD Pipeline

The pipeline is defined in `.github/workflows/cicd.yml` and runs on every push to `main`.

| Step | Description |
|------|-------------|
| Checkout | Pulls the latest code |
| Syntax check | Runs `python -m py_compile app.py` |
| Login to ghcr.io | Authenticates using the built-in `GITHUB_TOKEN` |
| Build and push | Builds the Docker image and pushes it with `latest` and commit SHA tags |

## Docker Image

```
ghcr.io/kabita-dev018/codealpha_cicddemo:latest
```

Pull the image:

```bash
docker pull ghcr.io/kabita-dev018/codealpha_cicddemo:latest
```

## Author

**Kabita**
GitHub: [Kabita-dev018](https://github.com/Kabita-dev018)

Built as part of the CodeAlpha internship.
