### DevOps With Docker
Eeva-Maria Laiho

# Part 1

## 1.1

![Exercise 1.1](1.1.png)

## 1.2

![Exercise 1.2](1.2.png)

## 1.3

![Exercise 1.2](1.3.png)

## 1.4

Start the container: 

```docker run -d --name bashex devopsdockeruh/exec_bash_exercise```

Go inside the container: 

```docker exec -it bashex bash```

Tail the log: 

```tail -f ./logs.txt```

The secret message is: 

```"Docker is easy"```.

Exit: 

```Ctrl+C``` and ```Ctrl+P, Ctrl+Q```


## 1.5 

Create the container: 

```$ docker run -d -it ubuntu:16.04 sh -c 'echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;'```

An empty read command is added in the beginning of the shell command to wait for user to become attached before the Input website command is printed. 

Install curl:

```$ docker exec 97 apt-get -qq update``` and ```$ docker exec 97 apt-get -y -qq install curl``

Start the container with the shell process: 

```$ docker start ex1.5```

Attach to the container: 

```$ docker attach 97```

Then type ```helsinki.fi``` and hit enter.

Exit: 

```Ctrl+C``` and ```Ctrl+P, Ctrl+Q```

## 1.6

Contents of the Dockerfile:
```
FROM devopsdockeruh/overwrite_cmd_exercise

CMD ["--clock"]
```

Build the image:

```$ docker build -t docker-clock .```

Run the container:

```$ docker run docker-clock```


## 1.7

Contents of the Dockerfile:
```
FROM ubuntu:16.04 

WORKDIR /mydir
RUN apt-get update && apt-get install -y curl

CMD echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;
```

Build the image:

```$ docker build -t curler .```

Run the container:

```$ docker run -it curler```


## 1.8

Create ```logs.txt``` file in ```$(pwd)``` folder (on host).

Run the container:

```
$ docker run -v $(pwd)/logs.txt:/usr/app/logs.txt devopsdockeruh/first_volume_exercise 
```

The secret (printed in logs.txt) message:

```
Secret message is:
"Volume bind mount is easy"
```

## 1.9

Run the container:

```
$ docker run -p 8080:80 devopsdockeruh/ports_exercise 
```

Browse to ```http://localhost:8080```. 

The container responds with message ```Ports configured correctly!!```.

## 1.10

Build the container:

```
$ docker build -t frontex .
```

Run the container with port 5000 attached to:

```
$ docker run -p 5000:5000 -it frontex
```

Browse to ```http://localhost:5000```. 

The container responds with Webpack App front page.


Dockerfile:

```
FROM ubuntu:16.04 

WORKDIR /webapp

# Install prerequisites
RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash && apt install -y nodejs

# Check install
RUN node -v && npm -v

# Copy webapp directory from host to container and install packages 
COPY frontend-example-docker frontend-example-docker
RUN cd frontend-example-docker && npm install

# When container is started start node
CMD cd frontend-example-docker && npm start
```



## 1.11

Build the container:

```
$ docker build -t backex .
```

Run the container with port 8000 and volume logs.txt attached to it:

```
$ sudo docker run -it -v $(pwd)/logs.txt:/webserver/backend-example-docker/logs.txt -p 8000:8000 backex
```

Browse to ```http://localhost:8000```. 

The container responds with message 'Port configured correctly, generated message in logs.txt'. The logs.txt file is appended with timestamp and connection received message. 

Dockerfile:

```
FROM ubuntu:16.04 

WORKDIR /webserver

# Install prerequisites
RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash && apt install -y nodejs

# Check install
RUN node -v && npm -v

# Copy webapp directory from host to container and install packages 
COPY backend-example-docker backend-example-docker
RUN cd backend-example-docker && npm install

# When container is started start node
CMD cd backend-example-docker && npm start
```














