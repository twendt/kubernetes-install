# kubernetes-install

This repo contains Kubernetes configs for a multiarch cluster for flannel

Run them in the following order on the master node

```
$ kubectl create -f kube-flannel-rbac.yml
$ kubectl create clusterrolebinding flannel --clusterrole=flannel --serviceaccount=kube-system:flannel
$ kubectl create --namespace kube-system -f flannel-config.yml
$ kubectl create --namespace kube-system -f kube-flannel.yml
$ kubectl create --namespace kube-system -f kube-flannel-arm.yml
```
