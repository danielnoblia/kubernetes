# Skapa secrets för certifikaten
kubectl -n ittlabb create secret tls kuberadius-cert-tls --key=key.pem --cert=cert.pem
kubectl -n ittlabb create secret generic kuberadius-ca-cert-tls --from-file=ca.crt=./ca.pem

# Skapa configMap
kubectl -n ittlabb create configmap freeradius-eap --from-file=eap
kubectl -n ittlabb create configmap freeradius-users --from-file=users
kubectl -n ittlabb create configmap freeradius-clients.conf --from-file=clients.conf


# Replikera Secrets mellan namespace kubed
helm install kubed appscode/kubed --version v0.12.0 --namespace kube-system
kubectl get deployment --namespace kube-system -l "app.kubernetes.io/name=kubed,app.kubernetes.io/instance=kubed
git clone https://github.com/appscode/kubed.git
kubectl create secret generic kubed-config -n kube-system --from-file=./docs/examples/config-syncer/config.yaml
kubectl annotate secret freeradius-noblia-se-tls kubed.appscode.com/sync=""
