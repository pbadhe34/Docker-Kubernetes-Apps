   
 
  Build the image from current dir  
  
  docker build -t user-service-app:v1 .

  Run mysql container
docker run --name app-mysql -v /mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=MyRootPass123 -e MYSQL_DATABASE=userservice -e MYSQL_USER=app-user -e MYSQL_PASSWORD=MyRootPass123 -d mysql:5.6

 To test the image
  To Run the user-service-app image in detacheed mode withn mysql linked
 
docker run -d -p 9090:8090 --name user-app --link app-mysql:localhost user-service-app:v1  




get = http://localhost:8090/users
get = http://localhost:8090/user/Swadeshi
      http://localhost:8090/user/<userName>


post = http://localhost:8090/user
put = http://localhost:8090/user

delete = http://localhost:8090/user/{id}

 
  docker image ls

       
 Log in to the Docker public registry on your local machine.

 

 docker tag user-service-app:v1 pbadhe34/my-apps:user-app-pod 
 
  docker images
  docker image ls

  To Publish the image to docker hub

  docker login

  Publish the image on docker hub in the format
   
  Upload your tagged image to the repository:

  
  docker push pbadhe34/my-apps:user-app-pod

  docker rmi pbadhe34/my-apps:user-app-pod

Pull and run the image from the remote repository
From now on, you can use docker run and run your app on any machine with this command in the format
 

  docker run -d -p 9090:8090 --name user-app --link app-mysql:localhost pbadhe34/my-apps:user-app-pod  


 
b 
 

 
