# Workshop with 
* Frontend
  * Angular
  * Vue
* Backend
  * .NET C#

## 1. Build backend
```
docker compose build api
docker compose up -d api
```
Access to url=http://localhost:8080/weatherforecast

Push image to Docker Registry
```
docker push somkiat/demo-dotnet:1.0
```

## 2. Build frontend with Angular
```
docker compose build angular
docker compose up -d angular
```

Access to url
* http://localhost:8888
* http://localhost:8888/api/weatherforecast

Push image to Docker Registry
```
docker push somkiat/demo-angular:1.0
```

## 3. Deploy with Kubernetes

Install [Ingress Nginx Controller](https://kubernetes.github.io/ingress-nginx/)
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.8.2/deploy/static/provider/cloud/deploy.yaml
```

Deploy .NET C#
```
cd k8s/
kubectl apply -f api.yml
kubectl apply -f ingress.yml

kubectl get all
kubectl get ingress
kubectl get svc -A
```