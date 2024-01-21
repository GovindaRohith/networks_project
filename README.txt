To start: 
first run the pox controller by the following command
rohith@rohithpc:~/pox$ ./pox.py log.level --DEBUG misc.ip_loadbalancer --ip=10.0.1.1 --servers=10.0.0.1,10.0.0.2
head to mininet/mininet/examples
$ sudo python3 ./miniedit.py 
next run the mininet by the topolgy given in photo topo.png
while setting up topolgy:
right click on controller set up and refer pic controller_config.png
click edit -> prefernces and refer pic edit_prefernces.png
after topolgy
click run down in miniedit window


commands:
xterm h1 h2 --> for servers
python3 -m http.server 80  --> to set up server to give response


xterm h3 --> for client as many as u want
now generate load by using wrk tool refer commands below


References:: 
rohith@rohithpc:~/pox$ ./pox.py log.level --DEBUG misc.ip_loadbalancer --ip=10.0.1.1 --servers=10.0.0.1,10.0.0.2

refer :

https://www.youtube.com/watch?v=RjE_QF1CEFk&t=812s

sudo python3 ./miniedit.py 

python3 -m http.server 80

curl http://10.0.1.1:80


wrk: This is the command to execute the wrk tool.

-t2: This flag sets the number of threads to 2. It means the tool will use 2 threads to simulate concurrent connections to the server.

-c100: This flag sets the number of HTTP connections to 100. It means each thread will open and maintain 100 connections to the server.

-d30s: This flag sets the duration of the test to 30 seconds. The load test will run for 30 seconds.

-R2000: This flag sets the request rate to 2000 requests per second. This means the tool will try to maintain a constant rate of 2000 requests per second throughout the test.

--latency: This flag instructs wrk to print detailed latency statistics.

http://10.0.0.1:80: This is the target URL for the load test. It indicates that the test is being performed on an HTTP server running at the specified IP address (10.0.0.1) and port (80).

wrk -t2 -c100 -d30s -R2000 --latency http://10.0.0.1:80
wrk -t2 -c100 -d30s  http://10.0.1.1:80
wrk -t2 -c100 -d30s -R2000 --latency http://10.0.0.1:80



ip_loadbalancer.py