# docker-hints

remove all exited containers
```
docker rm $(docker ps -a -f status=exited -q)
```

remove all dangling images
```
docker rmi $(docker images -q -f dangling=true)
```

remove image with all tags
```
docker images | grep busybox | tr -s ' ' | cut -d ' ' -f 2 | xargs -I {} docker rmi busybox:{}
```
