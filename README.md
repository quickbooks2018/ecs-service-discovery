## cloudgeeks.ca

- docker custom network

```network
docker network create cloudgeeks
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