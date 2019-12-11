 Java microservice app pod with MySQL pod


  
Build the java service image from docker file

  docker build -t userapp-pod .    //Default Dockerfile



 
  oc apply -f MySql-PersistentVoulme.yml
  oc get pv

  oc apply -f MySql-PersistentVoulme-Claim.yml

  oc get pvc
  
 Deploy mysql pod
  oc apply -f mysql-pod.yml

  oc get pods


  Deploy java service pod
  oc apply -f java-user-pod.yml
   oc get po

  oc describe pod java-user-pod

  oc describe pod java-user-pod | grep IP

  172.17.0.7

  oc exec -it java-user-service /bin/bash



  oc exec java-user-service -- printenv

    oc exec mysql -- printenv

   
  


  Access the application with pod ip as http://172.17.0.7:8090/users


  


