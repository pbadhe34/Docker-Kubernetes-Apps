The PYthon app image pbadhe34/my-apps:app1 has been modified to 
look for the redis host on localhost machine.
This redis container deployed in the same POD is recognozed as redis runningn on localhost:6379 


kubectl create  -f hostNetwork-Py.yml

kubectl create  -f hostPort-Py1.yml

kubectl create  -f hostPort-Py2.yml

kubectl create  -f  hostPort-Linked-Py3.yml

sudo kubectl create  -f  SharedVolume-Containers.yml
 
clusterName: kubernetes



