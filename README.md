# kubernetes-install

This repo contains Kubernetes configs for a multiarch cluster for flannel

Make sure you use the following option for kubeadm as the flannel configs  
uses 10.245.0.0/16

```
--pod-network-cidr 10.245.0.0/16
```

Run them in the following order on the master node

For 1.6.0 run the following

```
$ cd 1.6.0
$ kubectl create -f kube-flannel-rbac.yml
$ kubectl create clusterrolebinding flannel --clusterrole=flannel --serviceaccount=kube-system:flannel
$ kubectl create --namespace kube-system -f flannel-config.yml
$ kubectl create --namespace kube-system -f kube-flannel.yml
$ kubectl create --namespace kube-system -f kube-flannel-arm.yml
```

For 1.5.2 run the following

```
$ cd 1.5.2
$ kubectl create --namespace kube-system -f flannel-config.yml
$ kubectl create --namespace kube-system -f kube-flannel.yml
$ kubectl create --namespace kube-system -f kube-flannel-arm.yml
```
