# Deploy application

Create application code
Create Dockerfile
Login to DockerHub

Build and push image to DockerHub

```bash
docker build -t docker_hub_user/fastapi:latest .

docker push docker_hub_user/fastapi:latest
```

Deploy application to Kubernetes

```bash
cd k8s

k create ns skillab
helm install -name fastapi --namespace skillab .

kubectl port-forward svc/fastapi 8080:80

# connect to the browser: localhost:8080
```
