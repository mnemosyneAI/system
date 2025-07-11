# Windows Setup Instructions

## Prerequisites
- Docker Desktop for Windows installed and running
- Git for Windows (or GitHub Desktop)

## Quick Start

### 1. Clone the Repository

Using Command Prompt or PowerShell:
```cmd
git clone https://github.com/mnemosyneAI/system.git
cd system\docker
```

Or use GitHub Desktop to clone the repository.

### 2. Start the Services

In Command Prompt or PowerShell:
```cmd
docker-compose up -d
```

### 3. Verify Services

Check if services are running:
```cmd
docker ps
```

Access the services:
- ChromaDB API: http://localhost:8000
- ChromaDB Docs: http://localhost:8000/docs
- Obsidian Web: http://localhost:8080

## Data Storage

On Windows, Docker Desktop will create volumes automatically. Your data will be persisted in Docker volumes:
- `docker_chromadb-data`
- `docker_obsidian-vault`
- `docker_obsidian-config`

To see where Docker stores these volumes:
```cmd
docker volume inspect docker_chromadb-data
```

## Useful Commands

Stop services:
```cmd
docker-compose down
```

View logs:
```cmd
docker-compose logs -f
```

Restart services:
```cmd
docker-compose restart
```

## Troubleshooting

If port 8000 or 8080 is already in use, edit `docker-compose.yml` and change the port mapping:
```yaml
ports:
  - "8001:8000"  # Changed from 8000 to 8001
```

---

*Windows-specific instructions for Syne's memory infrastructure*