minikube run

minikube ip

minikube dashboard

minikube ssh

minikube stop

kubectl config get-clusters

kubectl config get-contexts

kubectl config use-context minikube

kubectl cluster-info

kubectl get cs

cat .kube/config


kubectl get nodes

kubectl get nodes -o wide

kubectl run nginx --image=nginx:alpine --port=80

kubectl scale deployment nginx --replicas=2


kubectl get deployments 

kubectl get deployments -o wide

kubectl delete deployment nginx

kubectl get services

kubectl get svc

kubectl get services -o wide

kubectl describe services nginx


kubectl get pods

kubectl get pods -o wide

kubectl get pods -w

kubectl logs POD_NAME

kubectl exec -it multitool-6d598c8f8-5d5pt bash

kubectl delete pods nginx-7b676545bc-4xhnq

curl POD_IP

Service Expose

kubectl expose deployment nginx --type ClusterIP --port 80

kubectl exec -it multitool-6d598c8f8-5d5pt bash

curl nginx 

dig nginx.default.svc.cluster.local

curl nginx.default.svc.cluster.local

kubectl describe svc nginx (kubectl describe services nginx)


Public Expose

kubectl expose deployment nginx --type NodePort --port 80

minikube ip

192.168.64.2

kubectl get service -o wide

http://192.168.64.2:32187








## First Lession End







https://www.youtube.com/watch?v=kDGRqNUhNnA

Go to home directory (Open your terminal 1. pwd 2. pwd)

ls .kube

cat .kube/config 

kubectl config view

kubectl config view --minify=true

kubectl config get-contexts

kubectl config use-context minikube

kubectl cluster-info
kubectl config get-clusters
kubectl get cs
kubectl get nodes
kubectl get nodes -o wide
kubectl describe node m01 (m01 node name)

docker run --name nginx -p 80:80 -d nginx:alpine
docker ps
docker stop nginx
docker rm nginx

kubectl run nginx --image=nginx:alpine
kubectl get deployments
kubectl get pods
kubectl get all
kubectl get services
kubectl get pods -o wide

kubectl get namespaces

kubectl -n kube-system get pods

kubectl -n kube-public get pods

kubectl -n default get pods


kubectl describe deployment nginx

kubectl describe pods nginx-686449ff6b-jgkrb (pod name)


kubectl get pod nginx-686449ff6b-jgkrb -o yaml

kubectl get pod nginx-686449ff6b-jgkrb -o yaml > /tmp/test.yaml


kubectl delete pod nginx-686449ff6b-jgkrb (pod name)


kubectl delete deployment nginx

kubectl delete services kubernetes


https://github.com/KamranAzeem/kubernetes-katas

git clone https://github.com/NanheKumar/kubernetes-katas.git

cd kubernetes-katas

cd support-files

kubectl apply -f nginx-simple-deployment.yaml

kubectl get pods -w

ssh root@kubeadm-node2


if you are using minikube then 

minikube ssh

docker ps | grep "nginx"

kubectl delete -f nginx-simple-deployment.yaml

kubectl create -f nginx-simple-deployment.yaml

kubectl create -f standalone-nginx-pod.yaml

kubectl delete pod standalone-nginx-pod


kubectl run nginx --image=nginx:alpine

kubectl run multitool  --image=praqma/network-multitool

kubectl get pods -o wide

kubectl exec -it multitool-6d598c8f8-5d5pt bash (pod name)

curl 172.17.0.2 (This is IP of nginx pods)

ping 172.17.0.2



telnet 172.17.0.2 80



kubectl get pods

kubectl logs nginx-686449ff6b-cx85j (pod name)



kubectl expose deployment nginx --type ClusterIP --port 80

kubectl exec -it multitool-6d598c8f8-5d5pt bash

curl nginx 

dig nginx.default.svc.cluster.local

curl nginx.default.svc.cluster.local

kubectl describe svc nginx (kubectl describe services nginx)

kubectl delete services nginx

kubectl expose deployment nginx --type NodePort --port 80

kubectl get ingress

kubectl get ClusterIssuer

kubectl get certificate

kubectl describe certificate quickstart-ans3-ansd-in-tls

kubectl get secrets

kubectl describe secrets/kartify-chahak-tls-cert  

kubectl get secret kartify-chahak-tls-cert -o yaml

kubectl describe secret quickstart-ans3-ansd-in-tls

kubectl describe ClusterIssue letsencrypt-prod

kubectl describe certs >> to get all certificates 




kubectl get challenges >> to see where are issues


https://docs.bitnami.com/tutorials/secure-kubernetes-services-with-ingress-tls-letsencrypt/

https://cert-manager.io/docs/tutorials/acme/ingress/

https://hub.helm.sh/charts/bitnami/elasticsearch

https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale-walkthrough/

kubectl get hpa
kubectl delete hpa kartify-chahak

kubectl autoscale deployment kartify-chahak --cpu-percent=70 --min=4 --max=100

kubectl autoscale deployment majorbrands-chahak --cpu-percent=70 --min=4 --max=100

kubectl scale deployment kartify-chahak-elasticsearch-elasticsearch-coordinating-only --replicas=4

kubectl get statefulsets kartify-chahak-elasticsearch-elasticsearch-data

kubectl scale statefulsets kartify-chahak-elasticsearch-elasticsearch-data --replicas=4

kubectl get statefulsets kartify-chahak-elasticsearch-elasticsearch-master

kubectl scale statefulsets kartify-chahak-elasticsearch-elasticsearch-master --replicas=4


# Change Name space


kubectl get pods --all-namespaces

kubectl get namespace

kubectl config set-context --current --namespace=

kubectl config set-context --current --namespace=default


https://docs.bitnami.com/google-templates/infrastructure/mariadb/configuration/enable-additional-nodes/

gcloud deployment-manager deployments update bs-mariadb-cluster --config expanded-config.yaml --preview

gcloud deployment-manager deployments update bs-mariadb-cluster  


## Trouble shooting

kubectl get ClusterIssuer  

kubectl describe ClusterIssuer letsencrypt-prod-issuer1

kubectl get certificaterequest

kubectl describe certificaterequest  kartify-chahak-tls-cert-issuer1-2068363811

kubectl get order

kubectl describe order kartify-chahak-tls-cert-issuer1-2068363811-1909097558

kubectl get challenges

## Download deployment file in yaml

kubectl get deployment redis-ha-1-haproxy  -o yaml > redis-ha-1-haproxy.yaml

