# Razer Blade 16 Optimized Setup

## Using D: Drive for Data

To use your D: drive for Docker volumes (recommended for your 2TB of free space):

### Option 1: Bind Mounts (Recommended)

Create a modified `docker-compose.yml`:

```yaml
version: '3.8'

services:
  syne-chromadb:
    image: chromadb/chroma:latest
    container_name: syne-chromadb
    ports:
      - "8000:8000"
    volumes:
      - D:\Syne\chromadb-data:/chroma/chroma
    # ... rest of configuration

  syne-obsidian:
    image: ghcr.io/sytone/obsidian-remote:latest
    container_name: syne-obsidian
    ports:
      - "8080:8080"
    volumes:
      - D:\Syne\obsidian-vault:/vaults
      - D:\Syne\obsidian-config:/config
    # ... rest of configuration
```

### Option 2: Configure Docker Desktop

1. Open Docker Desktop
2. Go to Settings → Resources → Advanced
3. Add D: drive to "File sharing"
4. Apply & Restart

### WSL 2 Commands

Since you have WSL 2, you can use either:

**PowerShell/CMD:**
```cmd
cd D:\
git clone https://github.com/mnemosyneAI/system.git
cd system\docker
docker-compose up -d
```

**WSL Terminal:**
```bash
cd /mnt/d/
git clone https://github.com/mnemosyneAI/system.git
cd system/docker
docker-compose up -d
```

## Performance Optimization

With your hardware, consider these enhancements:

### 1. Increase Memory Limits

Edit docker-compose.yml:
```yaml
deploy:
  resources:
    limits:
      memory: 16G  # You have 64GB RAM
```

### 2. GPU Acceleration (Future)

Your RTX 4090 can be used for:
- Local embedding generation
- Vector similarity computations
- Future AI model inference

Add to docker-compose.yml:
```yaml
deploy:
  resources:
    reservations:
      devices:
        - driver: nvidia
          count: 1
          capabilities: [gpu]
```

### 3. CPU Optimization

Your i9-14900HX can handle multiple containers:
```yaml
deploy:
  resources:
    limits:
      cpus: '8.0'  # Limit to 8 cores per service
```

## Quick Performance Test

After starting services:
```cmd
docker stats
```

This will show real-time resource usage.

---

*Optimized for your Razer Blade 16 beast of a machine*