https://docs.bitnami.com/tutorials/secure-kubernetes-services-with-ingress-tls-letsencrypt/

helm repo add bitnami https://charts.bitnami.com/bitnami
helm install ingress bitnami/nginx-ingress-controller

kubectl get svc ingress-nginx-ingress-controller -o jsonpath="{.status.loadBalancer.ingress[0].ip}"

This will be give you a public ip for example : 34.93.6.184 you can point your domain here
