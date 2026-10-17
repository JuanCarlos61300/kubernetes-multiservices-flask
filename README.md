#Flask multiservicios en Kubernetes
Despliegue en Kubernetes (k3s) de una aplicación Flask con frontend, backend, MySQL y nginx como proxy inverso.
#Ficheros
- `mysql-deployment.yml`: Deployment, Service y PVC (1Gi) de MySQL
- `backend-deployment.yml`: Deployment y Service del backend (`flasker/api:latest`)
- `frontend-deployment.yml`: Deployment y Service del frontend (`flasker/frontend:latest`)
- `nginx-deployment.yml`: ConfigMap `nginx-config`, Deployment y Service NodePort 30000
- `backend/` y `frontend/`: código y Dockerfile de cada imagen
#Despliegue
```bash
docker build -t flasker/api:latest backend/
docker build -t flasker/frontend:latest frontend/
kubectl apply -f mysql-deployment.yml
#configurar la base de datos dentro del pod de MySQL (usuario, test_db y tabla message)
kubectl apply -f backend-deployment.yml
kubectl apply -f frontend-deployment.yml
kubectl apply -f nginx-deployment.yml
```
Resultado: `http://localhost:30000` muestra "hola mundo".
