## WordPress ArgoCD Deployment
###> Note: This documentation is a work in progress. Please check back for updates and improvements.


## Configuration
![obraz](https://github.com/user-attachments/assets/732b1c61-bf2e-47d5-b723-b20b96390e35)
![obraz](https://github.com/user-attachments/assets/4dcc29fc-d2a6-4e22-b165-60b9347443ed)



## Dashboard

![obraz](https://github.com/user-attachments/assets/fdb39996-0b31-4e51-86aa-f1068e534527)


## K8s Service preview (I have loadbalancer running)
![obraz](https://github.com/user-attachments/assets/5332e5fb-1524-4e9e-9a7b-d5022e573aa5)


## Page access

![obraz](https://github.com/user-attachments/assets/a876adc8-1659-402e-8011-08c48352b2c4)


## Example argocd .yaml file


```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: wordpress-argocd
spec:
  destination:
    name: ''
    namespace: wordpress-argocd
    server: https://kubernetes.default.svc
  source:
    path: .
    repoURL: https://github.com/Shizzy-ctrl/wordpress-argocd-ready.git
    targetRevision: HEAD
  sources: []
  project: default
  syncPolicy:
    syncOptions:
      - CreateNamespace=true
```
