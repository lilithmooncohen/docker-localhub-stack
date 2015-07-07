#run redis
docker run -d --name redis redis

#run registry
cd docker-registry
sudo docker build -t localhub.stratospire.com:5000/docker-registry .
sudo docker run -d --name registry --link redis:redis -v /path/to/store:/data localhub.stratospire.com:5000/docker-registry

#frontend
sudo docker run -d --name registry-frontend --link registry:registry -e ENV_DOCKER_REGISTRY_HOST=registry -e ENV_DOCKER_REGISTRY_PORT=5000 konradkleine/docker-registry-frontend

#nginx
cd docker-nginx-registry-proxy
sudo docker build -t localhub.stratospire.com:5000/docker-registry .
sudo docker run -d -p 443:443 -p 5000:5000 --name registry-proxy --link registry:registry --link registry-frontend:registry-frontend localhub.stratospire.com:5000/docker-nginx-registry-proxy







htpasswd -c hub.stratospire.htpasswd ryanckoch
htpasswd hub.stratospire.htpasswd othernewuser

openssl req -x509 -newkey rsa:4086 -keyout key.pem -out cert.pem -days 3650 -nodes




sudo docker start redis
sudo docker registry
sudo docker registry-frontend
sudo docker registry-proxy
