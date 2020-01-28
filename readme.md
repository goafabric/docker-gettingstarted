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
docker image build -t gettingstarted:1.0 .

##Run
docker run gettingstarted:1.0 
docker run -p 8000:80 --name gettingstarted gettingstarted:1.0

##Compose
docker-compose -f docker-compose.yml up -d
docker-compose -p mickeymouse -f docker-compose.yml up -d
