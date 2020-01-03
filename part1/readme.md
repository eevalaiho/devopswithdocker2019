### DevOps With Docker
Eeva-Maria Laiho

# Part 1

## 1.1

![Exercise 1.1](1.1.PNG)

## 1.2

![Exercise 1.2](1.2.PNG)

## 1.3

To start the container:
```docker run -it devopsdockeruh/pull_exercise```

The script asks for password, that is ```basic```.

After typing the password the script prints:
```
You found the correct password. Secret message is:
"This is the secret message"
```

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

```$ docker run -d -it --name ex1.5 ubuntu:16.04 sh -c "read x; echo 'Input website:'; read website; echo 'Searching ...'; sleep 1; curl http://$website"```

An empty read command is added in the beginning of the shell command to wait for user to become attached before the Input website command is printed. 

Install curl:

```$ docker exec ex1.5 apt-get -qq update``` and ```$ docker exec ex1.5 apt-get -y -qq install curl```

Start the container with the shell process: 

```$ docker start ex1.5```

Attach to the container: 

```$ docker attach ex1.5```

To get and print http://helsinki.fi content first hit enter and then type ```helsinki.fi``` and hit enter.

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









