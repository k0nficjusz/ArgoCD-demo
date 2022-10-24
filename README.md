# ArgoCD-demo
Demo for setup local ArgoCD

# Install argo
helm repo add argo https://argoproj.github.io/argo-helm
helm install argo-cd argo/argo-cd

# ArgoCD port forward for UI
kubectl port-forward service/argo-cd-argocd-server -n default 8080:443
# ArgoCD password for admin
kubectl -n default get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

# to create application 
kubectl apply -f application.yaml
