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

Start the container: ```docker run -d --name bashex devopsdockeruh/exec_bash_exercise```

Go inside the container: ```docker exec -it bashex bash```

Tail the log: ```tail -f ./logs.txt```

The secret message is: ```"Docker is easy"```.

Exit: ```Ctrl+C``` and ```Ctrl+P, Ctrl+Q```


## 1.5 

Create the container: ```docker run -d -it --name ex1.5 ubuntu:16.04 sh -c "echo 'Input website:'; read website; echo 'Searching ...'; sleep 1; curl http://$website"```

Start the container: ```docker start ex1.5```

Attach to the ontainer: ```docker attach ex1.5```

Install curl: 
