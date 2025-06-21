# Test First Docker: <mark>hello-docker-hush</mark>
<mark>test with vs code, wsl2, docker desktop, Ubuntu24.04.1</mark>
## Create a new folder: HELLODOCKER
## create index.js:  
`console.log('Hello, World! Test test Hush');`
## create Dockerfile:
```
FROM node:14-alpine
COPY index.js /index.js
CMD ["node", "index.js"]
```
![](https://s3.bmp.ovh/imgs/2025/06/21/1d9d458846127647.png)
# build image:
`docker build -t hello-docker-hush .`  
![](https://s3.bmp.ovh/imgs/2025/06/21/edee01b6ce791c2a.png)   
meet error:
```
 failed to create shim task: OCI runtime create failed: runc create failed: systemd not running on this host, cannot use systemd cgroups manager: unknown
```
go to docker desktop setting, Docker Engine, and set `systemd` to `cgroupfs`, then docker run success
```
 "exec-opts": [
    "native.cgroupdriver=cgroupfs"
  ]
  ```
![](https://s3.bmp.ovh/imgs/2025/06/22/f4e2e155b64967c3.png)  
# check image:
`docker images` or `docker image ls`    
if not set tag when we build it, then will use the default tag: latest  
![](https://s3.bmp.ovh/imgs/2025/06/21/7275469e9f31c9f8.png)  

# run:
`docker run hello-docker-hush`    
![](https://s3.bmp.ovh/imgs/2025/06/21/255d85096b3ee472.png)  

# push to Docker Hub
<mark>TODO, no access at this moment</mark>  

# free online tool: Play with Docker
pull image from Docker Hub and run  
```
docker pull geekhour/hello-docker
docker images
docker run geekhour/hello-docker
```
![](https://s3.bmp.ovh/imgs/2025/06/21/1e16fe28000a9ffe.png)  
![](https://s3.bmp.ovh/imgs/2025/06/21/071e367a323789b5.png)  
