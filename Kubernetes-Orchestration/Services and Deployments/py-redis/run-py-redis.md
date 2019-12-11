

 Pyhton-redis-app
  

  kubectl apply -f RedisPersistenceVolume.yml

  kubectl get pv

  kubectl apply -f RedisPersistenceVolumeClaim.yml

  kubectl get pvc
  
  kubectl apply -f py-app-service-volume-LoadBalancer.yml

 To remove thee application
  kubectl delete  -f py-app-service-volume-LoadBalancer.yml

  kubectl get po

  kubectl exec  py-app-deployment-68f5899fd-5v6nk -- printenv | grep SERVICE

  REDIS_SERVICE_SERVICE_HOST=172.30.152.23

  kubectl describe svc redis-service
  ClusterIP = 172.30.152.23

  kubectl exec  azure-vote-deployment-68d87c9f5f-rj5tq -- printenv | grep AZURE

  REDIS_SERVICE_SERVICE_HOST=172.30.152.23

  kubectl exec py-app-deployment-76d49fbc4f-7rrn5  -- printenv | grep SERVICE
  REDIS_SERVICE_SERVICE_HOST=172.30.152.23


  Execute on container in the pod

  kubectl exec azure-vote-deployment-58dc5b6b8b-flb8n -c azure-vote-app-container  -- printenv | grep redis

  kubectl exec azure-vote-deployment-68d87c9f5f-jpdcn  -- printenv


   
PY_APP_SERVICE_LB_PORT_8090_TCP_PROTO=tcp
 
PY_APP_SERVICE_LB_SERVICE_HOST=172.30.220.153
PY_APP_SERVICE_LB_PORT_8090_TCP_ADDR=172.30.220.153
REDIS_SERVICE_SERVICE_PORT=6379
REDIS_SERVICE_PORT_6379_TCP_PROTO=tcp
REDIS_SERVICE_PORT_6379_TCP_PORT=6379
REDIS_SERVICE_PORT_6379_TCP_ADDR=172.30.152.23
ROUTER_SERVICE_PORT_443_TCP=443

REDIS_SERVICE_SERVICE_HOST=172.30.152.23

 
PY_APP_SERVICE_LB_PORT=tcp://172.30.220.153:8090
PY_APP_SERVICE_LB_PORT_8090_TCP=tcp://172.30.220.153:8090
 

PY_APP_SERVICE_LB_SERVICE_PORT=8090
PY_APP_SERVICE_LB_PORT_8090_TCP_PORT=8090
REDIS_SERVICE_PORT=tcp://172.30.152.23:6379
REDIS_SERVICE_PORT_6379_TCP=tcp://172.30.152.23:6379
KUBERNETES_SERVICE_HOST=172.30.0.1
ROUTER_SERVICE_PORT_80_TCP=80
ROUTER_SERVICE_PORT_1936_TCP=1936


  kubectl describe svc redis-service

 -->PClusgterIP : 172.30.152.23


  *88888********888888888**
  To see the entire satus of services/pods etc.
   kubectl status -v

  kubectl status --suggest

   ****************************************

  svc/py-app-service-lb - 172.30.220.153:8090


  kubectl describe svc py-app-service-lb
  IP:				172.30.220.153
 External IPs:              
 LoadBalancer Ingress:      
Port:                     <unset>  8090/TCP
TargetPort:               8090/TCP
NodePort:                 <unset>  30193/TCP
Endpoints:                172.17.0.6:8090,172.17.0.7:8090,172.17.0.8:8090
Session Affinity:         None
External Traffic Policy:  Cluster

  app accesible at cluster ip : http://172.30.220.153:8090
  With lkubectlalhost ip : http://192.168.137.128:31740
 as well as http://lkubectlalhost:31740
   
  with end points on lkubectlal machine

  http://172.17.0.6:8090
  http://172.17.0.7:8090
  http://172.17.0.890
  http://172.17.0.8090


  To expose the service use
  kubectl expose service py-app-service-lb


  kubectl describe route py-app-service-lb
  
  kubectl exec py-app-deployment-76d49fbc4f-7rrn5 cat /etc/resolv.conf
-->nameserver 172.30.0.2
search nodejs-echo.svc.cluster.lkubectlal svc.cluster.lkubectlal cluster.lkubectlal lkubectlaldomain
options ndots:5

  Connect to pod  
  kubectl rsh py-app-deployment-76d49fbc4f-7rrn5
# cat /etc/resolv.conf
nameserver 172.30.0.2
search nodejs-echo.svc.cluster.lkubectlal svc.cluster.lkubectlal cluster.lkubectlal lkubectlaldomain
options ndots:5


firewall-cmd --permanent --new-zone dkubectlkerc
firewall-cmd --permanent --zone dkubectlkerc --add-source $(dkubectlker network inspect -f "{{range .IPAM.Config }}{{ .Subnet }}{{end}}" bridge)
firewall-cmd --permanent --zone dkubectlkerc --add-port 8443/tcp --add-port 53/udp --add-port 8053/udp
firewall-cmd --reload
  



