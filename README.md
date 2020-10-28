#Installing Helm 

wget https://get.helm.sh/helm-v3.3.1-linux-amd64.tar.gz
tar -zxvf helm-v3.3.1-linux-amd64.tar.gz
sudo mv linux-amd64/helm /usr/local/bin/helm
helm version 


#Deploying Postgresql cluster on K8s

cd k8s-postgresql/charts
helm install postgres-operator postgres-operator -f postgres-operator/values.yaml
helm ls 

cd k8s-postgresql/

k create -f manifests/minimal-postgres-manifest.yaml

# check the deployed cluster
kubectl get postgresql

# check created database pods
kubectl get pods -l application=spilo -L spilo-role

# check created service resources
kubectl get svc -l application=spilo -L spilo-role
