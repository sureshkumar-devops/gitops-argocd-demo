Install with Helm
# Add the Argo Helm repository
helm repo add argo https://argoproj.github.io/argo-helm
helm repo update

# Install Image Updater with custom values
image update url : kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj-labs/argocd-image-updater/stable/config/install.yaml

kubectl create namespace argocd

helm install argocd argo/argo-cd --namespace argocd
kubectl get pods -n argocd

# Accessing the Argo CD UI

# Port-forward the Argo CD server service:
kubectl port-forward svc/argocd-server -n argocd 8080:443

# Retrieve the initial admin password

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode ; echo

login admin
password xxxxxxxx
