kubectl get nodes
NAME                    STATUS     ROLES    AGE     VERSION
localhost.localdomain   NotReady   master   5m52s   v1.16.2



kubectl get pods --all-namespaces
NAMESPACE     NAME                                            READY   STATUS    RESTARTS   AGE
kube-system   coredns-5644d7b6d9-kdnjm                        0/1     Running   0          6m5s
kube-system   coredns-5644d7b6d9-zh6hn                        0/1     Running   0          6m5s



kubectl logs coredns-5644d7b6d9-kdnjm -n kube-syste
dial tcp 10.96.0.1:443: connect: no route to host
E1111 14:45:40.106152       1 reflector.go:126] pkg/

core-dns pod not riunning
Error : dial tcp 10.96.0.1:443: connect: no route to host

 Initial output

 kubectl get pods --all-namespaces
NAMESPACE     NAME                                            READY   STATUS    RESTARTS   AGE
kube-system   coredns-5644d7b6d9-kdnjm                        0/1     Running   0          8m23s
kube-system   coredns-5644d7b6d9-zh6hn                        0/1     Running   0          8m23s
kube-system   etcd-localhost.localdomain                      1/1     Running   0          7m24s
kube-system   kube-apiserver-localhost.localdomain            1/1     Running   0          7m51s
kube-system   kube-controller-manager-localhost.localdomain   1/1     Running   0          7m31s
kube-system   kube-proxy-vnjhp                                1/1     Running   0          8m23s
kube-system   kube-scheduler-localhost.localdomain            1/1     Running   0          7m44s
kube-system   weave-net-2qf5d                                 2/2     Running   0          3m2s



Problem solved by following commands

systemctl stop kubelet
systemctl stop docker
iptables --flush
iptables -tnat --flush
systemctl start kubelet
systemctl start docker

The route problem can be solved by flush iptables.

 Aftre this action

 kubectl get pods --all-namespaces
NAMESPACE     NAME                                            READY   STATUS    RESTARTS   AGE
kube-system   coredns-5644d7b6d9-kdnjm                        1/1     Running   1          50m
kube-system   coredns-5644d7b6d9-zh6hn                        1/1     Running   1          50m


ubectl get nodes
NAME                    STATUS   ROLES    AGE   VERSION
localhost.localdomain   Ready    master   57m   v1.16.2
[root@localhost ~]# 