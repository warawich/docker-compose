# docker-compose
Keep docker-compose.yml

## Registry
Start Docker
- docker-compose up -d

Generate Login and Password
- docker run --rm --entrypoint htpasswd registry -Bbn <user> "<password>" > /opt/registry/htpasswd/htpasswd
- docker login -u <user> -p <password> <url>
  Example: docker login -u truevoice images.mari.ai
- docker pull images.mari.ai:testapp
- docker logoff images.mari.ai

## Registry-UI
1. Copy config.yml to /opt/quiq/.
2. docker-compose up -d
3. Access websit: 192.168.1.130:8000
