# Deploying Airflow with Helm
This module contains a `values.yaml` and example dags to deploy and run Airflow locally with Helm.
It can also be extended to work in the cloud, given you have `kubectl`, an enabled kubernetes context and 
`helm` installed locally. 

## Commands to install and run airflow locally with minikube
```bash 
minikube start --driver=docker --network-plugin=cni

helm repo add apache-airflow https://airflow.apache.org
helm repo update

helm upgrade --install airflow apache-airflow/airflow \
  --namespace airflow \
  --create-namespace \
  -f values.yaml \
  --timeout 10m

kubectl port-forward svc/airflow-api-server 8080:8080 --namespace airflow
``` 




