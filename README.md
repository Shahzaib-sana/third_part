# Docker_Volumes

-docker volume create my_volume (to create the new volume named my_volume):

#output:

my_volume (created)

-docker run -d --name nginx_container -v my_volume:/usr/share/nginx/html nginx (-d detached the container, --name assign the given name, -v mount the "my_volume", nginx specify the image to use for container):

#output:

4b2e48307483222cbdfa930159d2bb9e1879a1fa27d5b8a4a8f6b130e63c37f7

-create "index.html" on vs code with text "this is new website" in the same directory where py and dockerfile located.

-docker cp index.html nginx_container:/usr/share/nginx/html/ (to copy the html file from host to "my_volume"):

#output:

Successfully copied 2.05kB to nginx_container:/usr/share/nginx/html/

-http://localhost:8080/index.html (to show the content of html file):

#output:

"this is new website" will be printed on the localhost 

-docker stop nginx_container (to stop the running container named nginx_container):

#output:

nginx_container (stopped)

-docker rm nginx_container (to remove the stopped container named nginx_container):

#output:

nginx_container (removed)

-docker run -d --name httpd_container -p 8081:80 -v my_volume:/usr/local/apache2/htdocs httpd (-d detached the container, --name assign the given name, -v mount the "my_volume", httpd specify the image to use for container):

#output:

561ce00d41226600b3b56d800607e3d71412fce9139819b107eac138e0b1635d

-http://localhost:8081 (to show the default page of httpd)

-create about.html with text "another website for information" in vs code on the same directory where py and dockerfile located.

-docker cp about.html httpd_container:/usr/local/apache2/htdocs/ (to copy the about.html file from host to the volume):

#output:

Successfully copied 2.05kB to httpd_container:/usr/local/apache2/htdocs/

-http://localhost:8081/about.html (this will show the content of html file):

#output:

"another website for information" will be printed on webpage

-docker stop httpd_container (to stop the running container named httpd_container):

#output:

httpd_container (stopped)

-docker rm httdp_container (to remove the stopped container named httpd_container):

#output:

httpd_container (removed)

-docker run --rm -it -v my_volume:/data alpine ls /data (--rm auto remove container after it exits, -it run container with interactive mode, -v mount the volume, alpine use alpine linux image, ls /data to list the content with directory /data):

#output:

50x.html    about.html  index.html

-docker volume rm my_volume (to remove the created volume):

#output:

my_volume (removed)
