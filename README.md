# OpenSearch Template

### How to Run:
Run `docker-compose up -d`
This will bring up 2 nodes and a dashboard and create a proxy network named: `opensearch-net`

Other apps can join the same network via:

_Some other app docker-compose.yml_
```
version: '3'
services:
  app:
    container_name: my-app
    build:
      context: "."
    ports:
      - "8080:80"
    networks:
      - my-app-net

networks:
  my-app-net:
    external:
      name: opensearch-net <-- matches the OS network
```