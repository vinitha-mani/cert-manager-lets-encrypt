# cert-manager-lets-encrypt
Cert-manager using lets encrypt in eks cluster

Step 1:- curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash

Step 2:- helm version

Step 3:- helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx

Step 4:- helm repo update

Step 5:- helm upgrade --install ingress-nginx ingress-nginx/ingress-nginx --namespace ingress-nginx --create-namespace --set-string       controller.service.annotations."service\.beta\.kubernetes\.io/aws-load-balancer-type"="nlb"

Step 6:- vi deployment-svc.yaml && k apply -f deployment-svc.yaml

Step 7:- k get svc && k get pods && k get deployment

Step 8:- Need to create hosted zone in route53 and created A records for domain and sub-domain

Step 9:- helm repo add jetstack https://charts.jetstack.io

Step 10:- helm repo update

Step 11:- helm install cert-manager jetstack/cert-manager \
--namespace cert-manager --create-namespace \
--version v1.12.0 \
--set installCRDs=true

Step 12:- kubectl get pods -n cert-manager

Step 13:- vi clusterissuer.yaml && k apply -f clusterissuer.yaml

Step 14:- K get clusterissuer 

Step 15:- vi tls-ingress.yaml

Step 16:- kubectl apply -f tls-ingress.yaml

Step 17:- kubectl describe certificate example-tls

Step 18:- kubectl get cert -> true

Verify https://app.harinanda.shop in web-browser
