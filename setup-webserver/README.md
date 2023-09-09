# setup webserver


## Create Container from Image and Access it:
docker pull httpd -> This is pull latest httpd image from docker hub to local.
docker image ls -> To list all images.
docker run -d --name webserver -p 9090:80 httpd -> This is run webserver named container in detached mode (background) from httpd image in localhost from 9090 port by http://localhost:9090
docker exec -it webserver bash -> This is used to go to httpd path by interactive terminal.

-> In that Terinal type following 
cd htdocs
cat > mypage.html
-> Create any content on that file.
-> Once saved, then go to following link.
http://localhost:9090/mypage.html


## Create and Share image to others:
sudo docker diff webserver -> shows diff from source image
docker commit webserver -> return id of newly created image
docker image ls 
docker stop webserver
docker run -d --name my-own-webserver -p 9091:80 4bf8141cc186 -> new image id
docker ps
-> http://localhost:9091/mypage.html

docker tag 4bf8141cc186 myhttpd:v1
docker image ls
docker save myhttpd:v1 > myhttpd-v1.tar  (or) docker save -o myhttpd-v1.tar
docker load < myhttpd-v1.tar (or) docker load -i myhttpd-v1.tar
-> -o => output
-> -i => input
-> > => redirect input operator
-> < => redirect output operator


## Push image to docker hub:
register account
create repo with same image name in local
docker login
docker push ganesh/myhttpd:v1 -> note: not working becoz repo name and image name is different
docker tag myhttpd ganesh/myhttpd:v1
docker push ganesh/myhttpd:v1 -> now will work
