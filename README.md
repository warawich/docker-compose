# docker-compose
Keep docker-compose.yml

<!-- ## Registry
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
3. Access websit: 192.168.1.130:8000 -->


## Harbor (Replace Docker registry)
Link: https://github.com/goharbor/harbor/blob/master/docs/installation_guide.md

Harbor Configuration
1. cd /opt/harbor
2. vim harbor.cfg
3. change host to 192.168.1.130

Insecure configuration - Using for non ssl
1. vim /etc/docker/daemon.json
2. Add configure as below
    {
    "insecure-registries" : ["192.168.1.130:5000", "images.mari.ai"]
    }

Start Docker
1. cd /opt/harbor/
2. docker-compose up -d

Stop Docker
1. cd /opt/harbor
2. docker-compose down -v

Reconfiguration 
1. Stop Docker
2. Reconfiguration
3. Start Docker

Data Path: /data

Push Images
1. docker login images.mari.ai or docker login 192.168.1.130
2. docker build -t <image> .
3. docker tag <image>  <192.168.1.130>/<project>/<image>:<tag>
4. docker push <192.168.1.130>/<project>/<image>:<tag>


Pull Images
1. docker login images.mari.ai or docker login 192.168.1.130
2. docker pull <192.168.1.130>/<project>/<image>:<tag>
