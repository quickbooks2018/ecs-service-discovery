## cloudgeeks.ca

- docker custom network

```network
docker network create cloudgeeks --attachable
```

- Redis
```redis
 docker run --name redis --network cloudgeeks --restart unless-stopped -id redis:latest
```


- Python
```python-app
 docker run --name python-app --network cloudgeeks --restart unless-stopped -e redis_host=redis -p 80:5000 -id quickbooks2018/python-app:latest
 ```
 - url https://hub.docker.com/r/quickbooks2018/python-app


- Docker Compose
```yaml
services:
  redis:
    image: redis:latest
    restart: unless-stopped
    networks:
      - cloudgeeks

  python-app:
    image: quickbooks2018/python-app:latest
    restart: unless-stopped
    environment:
      - redis_host=redis
    ports:
      - "80:5000"
    depends_on:
      - redis
    networks:
      - cloudgeeks

networks:
  cloudgeeks:
    name: cloudgeeks
    attachable: true
```

- docker compose version 2 command
```bash
docker compose up -d
```
