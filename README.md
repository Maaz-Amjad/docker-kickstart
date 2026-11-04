# docker-kickstart

A tiny "greeter" web page written in Python (built-in `http.server`, no framework). Open it in a browser and it greets you by name and shows today's date. It exists to practise Git branching, pull requests, merge conflicts, and shipping a container image to Docker Hub.

## Project structure

| File | Purpose |
| --- | --- |
| `app.py` | The greeter web server (listens on port 8080) |
| `Dockerfile` | Builds the image from the official `python:3.12-slim` image |
| `.dockerignore` | Keeps `.git`, caches and secrets out of the image |
| `.gitignore` | Keeps temp files out of Git |

## Prerequisites

- [Docker](https://www.docker.com/products/docker-desktop/) (nothing else is needed to run the app)

## Build and run with Docker

```bash
docker build -t docker-kickstart:1.0 .
docker run -d --name greeter -p 8080:8080 docker-kickstart:1.0
```

Then open <http://localhost:8080>. Stop and remove it with `docker rm -f greeter`.

## Run straight from Docker Hub (no source code needed)

Image: [maazamjad110/docker-kickstart](https://hub.docker.com/r/maazamjad110/docker-kickstart)

```bash
docker run -d -p 8080:8080 maazamjad110/docker-kickstart:1.1
```

## Image versions

| Tag | Greeting |
| --- | --- |
| `1.0` | Hey, Maaz! |
| `1.1` | Welcome, Maaz! |

Both can run at once on different host ports, e.g. `-p 8080:8080` and `-p 8082:8080`.
