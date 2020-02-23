#Docker
install docker
[inside terminal]

docker ps 
docker volume create portainer_data
docker run -d -p 8000:8000 -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer

[inside browser]
localhost:9000 => choose local when asked, user: admin, pw: administrator

#Checkout
https://github.com/goafabric/docker-gettingstarted
https://github.com/goafabric/spring-boot-example-service
https://github.com/goafabric/skillz                   

