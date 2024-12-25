## Prequisities
###  Working kubernetes cluster

## Installation of MetalLB

### 1. Create a namespace for MetalLB

```sh
kubectl create namespace metallb-system
```



### 2. Install MetalLB using the latest manifest

```sh
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/main/config/manifests/metallb-native.yaml
```


### 3. Configure IP address pool

Replace xxx.xxx.xxx.xxx-xxx.xxx.xxx.xxx with your local IP address range.

Create a file named metallb-config.yaml with the following content:

```sh
apiVersion: metallb.io/v1beta1
kind: IPAddressPool
metadata:
  name: default-address-pool
  namespace: metallb-system
spec:
  addresses:
  - xxx.xxx.xxx.xxx-xxx.xxx.xxx.xxx # Your local addresses 
---
apiVersion: metallb.io/v1beta1
kind: L2Advertisement
metadata:
  name: l2-advertisement
  namespace: metallb-system
```


### 4. Apply the MetalLB configuration

```sh
kubectl apply -f metallb-config.yaml
```



## Installation of Load Balancer Ready WordPress

### 1. Clone the repository and navigate to the folder with all YAML files

```sh
kubectl apply -k ./
```


## Accessing the WordPress Page

### 1. Get the external IP of the WordPress service

```sh
kubectl get svc -n wordpress
```


### 2. Open your browser and navigate to the external IP address shown in the output. This will direct you to the WordPress page.
```sh
NAME        TYPE           CLUSTER-IP     EXTERNAL-IP      PORT(S)        AGE
wordpress   LoadBalancer   10.xx.xxx.xxx  xxx.xxx.xxx.xxx  80:300xx/TCP   10m
```



![obraz](https://github.com/user-attachments/assets/7ebc0dd0-57ae-4c7d-89e1-202f00202cec) can you make this readme.md more accessible and let me copy it ?
