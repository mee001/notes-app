# PROJECT 1-4 FINAL REPORT
### Docker Notes App - Persistent Volume

**Student:** mlinx | **Repo:** github.com/mee001/notes-app | **Date:** 21-09-2026

### 1. Project 3 vs Project 4
**Project 3:** `docker run -p 8080:80 notes-app` - No volume, data inside container, lost on `docker rm`.
**Project 4:** `docker-compose.yml` with named volume `notes-data:/usr/share/nginx/html/data` - Data persists, survives down/up.

### 2. Fixed compose file
```yaml
services:
  notes-app:
    image: dockmee001/notes-app
    ports: ['8080:80']
    volumes: [notes-data:/usr/share/nginx/html/data]
volumes:
  notes-data:
