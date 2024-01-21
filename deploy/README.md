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

## 2. Build frontend with Angular
```
docker compose build angular
docker compose up -d angular
```

Access to url
* http://localhost:8888
* http://localhost:8888/api/weatherforecast