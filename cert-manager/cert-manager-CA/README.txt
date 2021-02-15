kubectl create namespace cert-manager
 
helm repo add jetstack https://charts.jetstack.io
 
helm repo update
 
kubectl apply -f https://github.com/jetstack/cert-manager/releases/download/v1.1.0/cert-manager.crds.yaml
 
helm install \
  cert-manager jetstack/cert-manager \
  --namespace cert-manager \
  --version v1.1.0 \
  # --set installCRDs=true


Create CA  Issuer

kubectl -n ittlabb create secret tls ca-key-pair --key=key.pem --cert=cert.pem

