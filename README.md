# k8s reloader configmap
A Kubernetes controller to watch changes in ConfigMap and Secrets and do rolling upgrades on Pods Deployment
- GKE 1.22.3-gke.1500
- Helm 3

### Install [Stakater Reloader](https://github.com/stakater/Reloader) via helm in namespace production, if you have another namespace repeat install in other namespace like staging etc in your cluster
```
helm repo add stakater https://stakater.github.io/stakater-charts
helm repo update
helm install stakater/reloader --generate-name --set reloader.watchGlobally=false --namespace production

kubectl get pods -n production
NAME                                           READY   STATUS    RESTARTS   AGE
reloader-1640070947-reloader-5f55dbc46-hkqpt   1/1     Running   0          39s
```
### Test create deployment and configmap, try update configmap and deployment automated rolling upgrades on Pods Deploymen
