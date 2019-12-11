 Run Qoutes-appp with NodePort service

   kubectl cluster-info

   

  kubectl get po --all-namespaces=true

 
  kubectl apply -f qoutes-app-NodePort.yml

  kubectl get svc

  kubectl get svc
NAME                TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)                   AGE
quotes-service-np   NodePort    172.30.78.78   <none>        8080:31000/TCP     

  kubectl describe svc  quotes-service-np 

  Selector:               app=quotes-pod
Type:                     NodePort
IP:                       172.30.78.78
Port:                     <unset>  8080/TCP
TargetPort:               8080/TCP
NodePort:                 <unset>  31000/TCP
Endpoints:                172.17.0.6:8080,172.17.0.7:8080,172.17.0.8:8080
Session Affinity:         None
External Traffic Policy:  Cluster
Events:                   <none>



  kubectl get deploy

  kubectl get po


  To see the entire satus of services/pods etc.
   kubectl status -v

  kubectl status --suggest

  View details with 'kubectl describe <resource>/<name>' or list everything with 'kubectl get all'.

  Access the quotes app with pod ip
  172.17.0.6:8080/api/quote
  172.17.0.7:8080/api/quote
  172.17.0.8:8080/api/quote

  With clusterip of service  : 172.30.78.78:8080
  curl http://172.30.78.78:8080/api/quote
  Repeat with curl to check chnaging ip address of pod displkayed in the respoinse


  With Node IP : 192.168.137.128:31000/api/quote

  curl http://192.168.137.128:31000/api/quote

************************************************************

Run Qoutes-appp with LoadBalancer service

  kubectl apply -f qoutes-app-loadBalancer.yml

  kubectl get svc
NAME                TYPE           CLUSTER-IP      EXTERNAL-IP                   PORT(S)                   AGE
quotes-service-lb   LoadBalancer   172.30.199.82   172.29.163.63,172.29.163.63   8080:32000/TCP            6s

  kubectl describe svc quotes-service-lb 

  Name:                   quotes-service-lb
Namespace:                nodejs-echo
Labels:                   <none>
Annotations:              kubectl.kubernetes.io/last-applied-configuration={"apiVersion":"v1","kind":"Service","metadata":{"annotations":{},"name":"quotes-service-lb","namespace":"nodejs-echo"},"spec":{"ports":[{"nodePort":320...
Selector:                 app=quotes-app-lb-pod
Type:                     LoadBalancer
IP:                       172.30.199.82
External IPs:             172.29.163.63
LoadBalancer Ingress:     172.29.163.63
Port:                     <unset>  8080/TCP
TargetPort:               8080/TCP
NodePort:                 <unset>  32000/TCP
Endpoints:                172.17.0.6:8080,172.17.0.7:8080,172.17.0.8:8080 + 1 more...


   Access the quotes app with pod ip
  http://172.17.0.6:8080/api/quote
  http://172.17.0.7:8080/api/quote
  http://172.17.0.8:8080/api/quote
 http:// 172.17.0.9:8080/api/quote

  With clusterIp : http://172.30.199.82:8080/api/quote

  curl http://172.30.199.82:8080/api/quote

  With Node Ip : 192.168.137.128:32000/api/quote

  curl 192.168.137.128:32000/api/quote
   
 

 

