# [DEPRECATED] MinIO Docker Compose Setup

This repository provides a simple **Docker Compose** configuration to run a **MinIO** object storage server locally.  
MinIO is a high-performance, S3-compatible object storage solution that can be used for development, testing, or production environments.

---

## 🧩 Overview

The setup includes a single MinIO container exposing both:

- **S3 API endpoint** — for programmatic access (`http://127.0.0.1:9000`)
- **Web Console** — for managing storage visually (`http://127.0.0.1:9001`)

The container is configured to persist data locally and will automatically restart unless manually stopped.

---

## ⚙️ Configuration

### Environment Variables

| Variable              | Default Value | Description                         |
| --------------------- | ------------- | ----------------------------------- |
| `TZ`                  | `UTC`         | Sets container timezone             |
| `MINIO_ROOT_USER`     | `root`        | Root username for the MinIO console |
| `MINIO_ROOT_PASSWORD` | `password`    | Root password for the MinIO console |

> ⚠️ **Important:** Change the default `MINIO_ROOT_USER` and `MINIO_ROOT_PASSWORD` for security.

---

## 🗂️ Volume

| Host Path | Container Path | Description                              |
| --------- | -------------- | ---------------------------------------- |
| `./data`  | `/data`        | Directory used by MinIO to store objects |

Data persists on your host machine, so containers can be rebuilt without losing stored data.

---

## 🚀 Usage

### 1. Start the service

```bash
docker compose up -d
```

### 2. Access the services

- Web Console: http://127.0.0.1:9001
  Log in with MINIO_ROOT_USER and MINIO_ROOT_PASSWORD

- S3 API Endpoint: http://127.0.0.1:9000

### 3. Stop the service

```bash
docker compose down
```

## 🛠️ Troubleshooting

- If ports 9000 or 9001 are already in use, modify them in docker-compose.yaml.

- Ensure docker and docker compose are installed and up-to-date.

- Check container logs with:

```bash
docker logs minio
```

## 📚 References

- [MinIO Documentation](https://docs.min.io/)
- [Docker Hub: minio/minio](https://hub.docker.com/r/minio/minio)
