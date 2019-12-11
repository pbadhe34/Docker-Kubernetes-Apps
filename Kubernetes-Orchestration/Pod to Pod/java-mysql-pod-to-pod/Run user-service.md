Run mysql container by specifying env values


docker run --name app-mysql -e MYSQL_ROOT_PASSWORD=MyRootPass123 -e MYSQL_DATABASE=userservice -e MYSQL_USER=app-user -e MYSQL_PASSWORD=MyRootPass123 -d mysql:5.6


Check the log to make sure the mysql server is running OK:
 
docker logs app-mysql


Run mysql with existing volume





To create some initial records and tables in mysql container
 
 
Copy the files from host system into the Docker container context
The cp command can be used to copy files from host to docker container and reverse.
One specific file can be copied like:

Copy the file from host machine to the container


docker cp table.sql app-mysql:/table.sql
docker cp records.sql app-mysql:/records.sql

 
 

docker exec -it app-mysql bash

 
To import and execute sql  script in container

Run these from bash terminal to import sql script file into DB

mysql -uroot -p userservice < table.sql

mysql -uroot -p userservice < records.sql

 

 
File copied to container from Host machine and ready to execute
mysql  -u root  -p userservice < table.sql

mysql  -u root  -p userservice < records.sql


mysql -uroot -p userservice -e "describe users"  

mysql -uroot -p userservice -e "describe hibernate_sequence"  

mysql -uroot -p userservice -e "select * from users"  

mysql -uroot -p userservice -e "select * from hibernate_sequence"  



mysql -uroot -p userservice -e "commit"  


Run sleect query  from outside the mysql container

docker exec app-mysql sh -c 'exec mysql SELECT * from userservice.users AS Id FROM userservice.Users -uroot -p"MyRootPass123"'




#The env variables needEd to pass are
#DB_HOST
#DB_PORT
#DB_DATABASE   //userservice
#DB_USER
#DB_PASS

Find the ip address of mysql container

  docker inspect app-mysql
  172.17.0.2



  Build userservice image
   docker build -t userapp .

#To run as docker image  with mysql container ip aaddress

 docker run --name my-app -e DB_HOST=172.17.0.2 -e DB_PORT=3306  -e DB_DATABASE=userservice  -e DB_USER=root -e DB_PASS=MyRootPass123 -d userapp




