#### del images
docker rmi $(docker images | grep '' | tr -s ' ' | cut -d ' ' -f 3)
docker run --add-host [Hostname]:[IPAddress]
