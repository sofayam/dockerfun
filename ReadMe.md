The basic docker commands


#### build

write the dockerfile

then build the image using the dockerfile
> docker build -t getting-started .


### run 

look for images
> docker images
start an image
> docker run -d -p 127.0.0.1:4000:3000 getting-started


#### exec
to poke around in the container once it is running
look for containers
> docker container list

> docker container exec -it 1a5 /bin/sh

### delete container

> docker stop 1a5
> docker rm 1a5

### delete image 

> docker rm foobar

