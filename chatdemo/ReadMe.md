

 docker build -t chatdemo .

 docker run -d --name chatdemocont -v ~/repos/dockerfun/testdata:/mnt/shared chatdemo


docker exec -it chatdemocont sh