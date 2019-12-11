 Edit /Create new file as   ~/.docker/config.json in the home directory of the user (train)which starts containers. 

{
 "proxies":
 {
   "default":
   {
     "httpProxy": "http://10.19.16.q65:8080",
     "httpsProxy": "http://127.0.0.1:3001",
     "noProxy": "localhost,10.19.41.61,127.0.0.1"
   }
 }
}

 Save the file and close the editor

Reload the docker daemon
sudo systemctl stop docker

sudo systemctl status docker

sudo systemctl start docker

sudo systemctl status docker

 Check the docker commands as
docker info
 docker version
