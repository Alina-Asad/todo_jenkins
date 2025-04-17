# Getting started
#part 3 \n
Docker Volume - A storage palce for files where even after the container is delete, the files are not lost.\n

1- creating the volume. command - docker volume create my-volume\n 

2- create an container using nginex image and mount the volumn to it. command - docker run -d --name my_nginx_container -v my_volume:/usr/share/nginx/html nginx\n
nginex is the web server which serves websites.

3- verify - output - welcome is showing in localhost 8082\n
just go to localhost 8082 

4-create a file name in host machine. command - echo "Hello from index.html" > index.html\n

5- copy the index file to the volumn command - docker cp index.html nginx_container:/usr/share/nginx/html/index.html\n
output - Successfully copied 2.05kB to nginx_container:/usr/share/nginx/html/index.html\n

6- verify that the file is showing in browser - command - curl http://localhost:8082 - \n 
output - 
StatusCode        : 200\n
StatusDescription : OK\n
Content           : ÿþHello from index.html\n

7- stop container - docker stop nginx_container\n

8- remove container - docker rm nginx_container\n

9- create a new container using httpd and mount - command same as before just get httpd from library\n

10- verify - same steps \n

11- create a file named about \n

12- copy the file into the volume - output - Successfully copied 2.05kB to apache_container:/usr/local/apache2/htdocs/about.html\n
13- verify using curl- curl is a client URL used to view server responses \n

14- stop and remove the container\n

15- verify that the volume still exit. To do that create container - command - docker run --rm -v my_volume:/usr/share/nginx/html nginx ls /usr/share/nginx/html

 this command create another container, mounts the volumn and then lists the content it have.\n

16- remove the volume - command - docker volume rm my_volume\n
