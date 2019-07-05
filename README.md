# docker-hints

remove all exited containers
```bash
docker rm $(docker ps -a -f status=exited -q)
```

remove all dangling images
```bash
docker rmi $(docker images -q -f dangling=true)
```

remove image with all tags
```bash
docker images | grep busybox | tr -s ' ' | cut -d ' ' -f 2 | xargs -I {} docker rmi busybox:{}
```
