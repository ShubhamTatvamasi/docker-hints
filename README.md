# docker-hints

delete docker interface
```bash
sudo ip link delete docker0
sudo systemctl restart docker.socket
```

filter images:
```bash
docker images -f reference='shubhamtatvamasi/*:*'

# delete all images
docker rmi $(docker images -f reference='shubhamtatvamasi/*:*' -q) --force
```

Remove all tags on a docker image:
```bash
docker images shubhamtatvamasi/nginx --quiet | while read line ; do
  docker rmi $line --force
done
```

remove all exited containers
```bash
docker container prune -f
docker rm $(docker ps -a -f status=exited -q)
```

remove all dangling images
```bash
docker image prune -f
docker rmi $(docker images -q -f dangling=true)
```

remove image with all tags
```bash
docker images | grep busybox | tr -s ' ' | cut -d ' ' -f 2 | xargs -I {} docker rmi busybox:{}
```
