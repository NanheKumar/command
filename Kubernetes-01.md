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
git clone https://github.com/KamranAzeem/kubernetes-katas.git
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
