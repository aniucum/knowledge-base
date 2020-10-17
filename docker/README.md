#### del images
docker rmi $(docker images | grep '' | tr -s ' ' | cut -d ' ' -f 3)
