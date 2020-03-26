#Setup
##Docker Commands
docker ps
docker volume ls
docker image ls

##Portainer
docker volume create portainer_data
docker run -d -p 8000:8000 -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer

#Image Creation
##Build
cd src/deploy
docker image build .
docker image ls | grep 37f14a1b4d2f

##Build with name
##app.py add comment to avoid caching
docker image build -t gettingstarted:latest .
docker image tag gettingstarted:latest gettingstarted:1.0


##Run
##just start but no access
docker run gettingstarted:1.0
##start with access 
docker run -p 8100:80 gettingstarted:1.0
##start with name in background
docker run -p 8100:80 --name gettingstarted -d gettingstarted:1.0 

#Compose
docker-compose -f docker-compose.yml up -d
docker-compose -f docker-compose.yml down

docker-compose -p mickeymouse -f docker-compose.yml up -d

#Push
docker image tag gettingstarted:1.0 docker.io/goafabric/gettingstarted:1.0
docker login
docker push docker.io/goafabric/gettingstarted:1.0 


#Cleanup (be careful!)
docker system prune -a
docker volume prune