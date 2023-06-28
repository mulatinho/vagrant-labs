## Lab01: Kubernetes Cluster 

A Vagrant Kubernetes cluster with one master node and two workers.

### Running
````
$ vagrant up
$ ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory kubernetes-clients.yml
$ ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory kubernetes-master.yml
```

### Status

```
$ vagrant status
Current machine states:

kubemaster1               running (libvirt)
kubenode1                 running (libvirt)
kubenode2                 running (libvirt)
```

Running with versions 1.24.14-00 on kubelet, kubeadm and kubectl. Calico Networking.
 
```
Every 8.0s: kubectl get all -A                                                                                                                            kubemaster1: Mon Jun 26 03:00:00 2023

NAMESPACE     NAME                                           READY   STATUS    RESTARTS   AGE
kube-system   pod/calico-kube-controllers-79dcc699f8-vcdnn   1/1     Running   0          18m
kube-system   pod/calico-node-mpjfx                          1/1     Running   0          18m
kube-system   pod/coredns-57575c5f89-t7vrd                   1/1     Running   0          18m
kube-system   pod/coredns-57575c5f89-v8gtv                   1/1     Running   0          18m
kube-system   pod/etcd-kubemaster1                           1/1     Running   0          18m
kube-system   pod/kube-apiserver-kubemaster1                 1/1     Running   0          18m
kube-system   pod/kube-controller-manager-kubemaster1        1/1     Running   0          19m
kube-system   pod/kube-proxy-qcqq4                           1/1     Running   0          18m
kube-system   pod/kube-scheduler-kubemaster1                 1/1     Running   0          18m

NAMESPACE     NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)                  AGE
default       service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP                  19m
kube-system   service/kube-dns     ClusterIP   10.96.0.10   <none>        53/UDP,53/TCP,9153/TCP   18m

NAMESPACE     NAME                         DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR            AGE
kube-system   daemonset.apps/calico-node   1         1         1       1            1           kubernetes.io/os=linux   18m
kube-system   daemonset.apps/kube-proxy    1         1         1       1            1           kubernetes.io/os=linux   18m

NAMESPACE     NAME                                      READY   UP-TO-DATE   AVAILABLE   AGE
kube-system   deployment.apps/calico-kube-controllers   1/1     1            1           18m
kube-system   deployment.apps/coredns                   2/2     2            2           18m

NAMESPACE     NAME                                                 DESIRED   CURRENT   READY   AGE
kube-system   replicaset.apps/calico-kube-controllers-79dcc699f8   1         1         1       18m
kube-system   replicaset.apps/coredns-57575c5f89                   2         2         2       18m
```


