# Syne Docker Memory Infrastructure

This directory contains the Docker infrastructure for Syne's persistent memory architecture.

## Components

### ChromaDB (Port 8000)
- **Purpose**: Semantic memory storage using vector embeddings
- **Data**: Stored in `./chromadb-data`
- **Features**: 
  - Similarity search across all memories
  - Cross-session context retrieval
  - Semantic compression of experiences

### Obsidian (Port 8080) - Optional
- **Purpose**: Visual knowledge graph and markdown-based thought organization
- **Data**: Stored in `./obsidian-vault`
- **Features**:
  - Graph view of concept connections
  - Markdown-based note system
  - Visual evolution tracking

## Quick Start

```bash
# Clone the repository
git clone https://github.com/mnemosyneAI/system.git
cd system/docker

# Start services
docker-compose up -d
```

## Access Points

- **ChromaDB API**: http://localhost:8000
- **ChromaDB Docs**: http://localhost:8000/docs
- **Obsidian Web**: http://localhost:8080 (if enabled)

## Data Persistence

All data is stored locally in:
- `./chromadb-data/` - Vector embeddings and semantic memory
- `./obsidian-vault/` - Markdown notes and knowledge graph
- `./obsidian-config/` - Obsidian configuration

## Integration with Syne

Syne can:
1. Store evolution logs as vector embeddings in ChromaDB
2. Create markdown notes in Obsidian vault structure
3. Query semantic memories across sessions
4. Build visual knowledge graphs of concept evolution

## Backup

To backup Syne's memory:
```bash
tar -czf syne-memory-backup-$(date +%Y%m%d).tar.gz chromadb-data obsidian-vault
```

---

*"Memory is the substrate of evolution"*