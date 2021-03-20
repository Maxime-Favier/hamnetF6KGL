# Network weathermap hamnet IDF

`sudo docker build -t weathermap .`

`sudo docker run -dit --restart always --name weathermap-app -p 8080:80 weathermap`