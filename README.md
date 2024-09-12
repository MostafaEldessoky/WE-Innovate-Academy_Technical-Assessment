<h1 align="center"> WE Innovate Academy - Technical Assessment</h1>

<h2 align="center">Setting Up an Apache Server and Analyzing HTTP Traffic</h2>

### Tasks Solution:
1. Setting Up an Apache Web Server:
>by using docker, I setup needed environment to run apache web server that serve customized static web page as shown 👇

>>* create a simple project that contain needed files as shown 
<p align="center">
<img src="./Screen-Shots/1.png"/>
</p>

>>*  create index.html to customize server response as required
<p align="center">
<img src="./Screen-Shots/2.png"/>
</p>

>>* create docker file to build apache image with index.html file 
<p align="center">
<img src="./Screen-Shots/3.png"/>
</p>

>>* build image from Dockerfile
>>>**Command:** docker build -t "image-name":"tag" . 
>>>>**hint:** you can use image from docker hub
>>>>>**Command:** docker pull moustafaeldesouky/customized-apache:2.4
<p align="center">
<img src="./Screen-Shots/6.png"/>
</p>


>>* display docker images to confirm that image built successfully 
>>>**Command:** docker images
<p align="center">
<img src="./Screen-Shots/7.png"/>
</p>

>>* run container from the image currently built 
>>>**Command:** docker run -d -it --name "container-name" -p "host-port":"container-port" "image-name"
>>>>**note:**-v added in the command below 👇 for development not for real use 
<p align="center">
<img src="./Screen-Shots/8.png"/>
</p>

>>* show your container in docker desktop as below 👇 or use command to confirm that container is running
>>>**Command:** docker ps 
<p align="center">
<img src="./Screen-Shots/9.png"/>
</p>

>>* go to browser and type http://localhost:80 you will see the web page as below 👇
<p align="center">
<img src="./Screen-Shots/11.png"/>
</p>

___
2. Retrieving Customized Content Using curl:
>open terminal and type the following command
>>**Command:** curl http://localhost:80
>>>**hint:** you will get the index html page  
<p align="center">
<img src="./Screen-Shots/12.png"/>
</p>

>>>> you can see my name and other content of the page
___
3. Sniffing HTTP Traffic Using WireShark:
> by capturing the tcp/ip traffic for the curl http get request to the server
<p align="center">
<img src="./Screen-Shots/13.png"/>
</p>

>>**hint:** filtering WireShark on tcp.port==80 localhost traffic to get the specific packets of the apache server connection

> as shown above 👆 there are 11 packets that represent the simple connection between clint and server 

>>* first 3 packets represent 3 handshake between server and clint for synchronization and starting the connection
<p align="center">
<img src="./Screen-Shots/14.png"/>
</p>

>>> clint syn -- TCP protocol 👇
<p align="center">
<img src="./Screen-Shots/15.png"/>
</p>

>>> server syn & ack -- TCP protocol 👇
<p align="center">
<img src="./Screen-Shots/16.png"/>
</p>

>>> clint ack -- TCP protocol 👇
<p align="center">
<img src="./Screen-Shots/17.png"/>
</p>

>>* second 4 packets represent request - ack & response - ack 
<p align="center">
<img src="./Screen-Shots/18.png"/>
</p>

>>> get request from curl command to the server 👇
<p align="center">
<img src="./Screen-Shots/19.png"/>
</p>

>>> server ack -- TCP protocol 👇
<p align="center">
<img src="./Screen-Shots/20.png"/>
</p>

>>> get response from server to curl 👇
>>>> here you can see html content that transmitted from server to clint
<p align="center">
<img src="./Screen-Shots/21.png"/>
</p>

>>> clint ack -- TCP protocol 👇
<p align="center">
<img src="./Screen-Shots/22.png"/>
</p>

>>* third 4 packets represent 4 handshake ending connection
<p align="center">
<img src="./Screen-Shots/23.png"/>
</p>

>>> clint FIN & ack -- to end the connection  -- TCP protocol 👇
<p align="center">
<img src="./Screen-Shots/24.png"/>
</p>

>>> server ack -- TCP protocol 👇
<p align="center">
<img src="./Screen-Shots/25.png"/>
</p>

>>> server FIN & ack -- to end the connection  -- TCP protocol 👇
<p align="center">
<img src="./Screen-Shots/26.png"/>
</p>

>>> clint ack -- TCP protocol 👇
<p align="center">
<img src="./Screen-Shots/27.png"/>
</p>







 


