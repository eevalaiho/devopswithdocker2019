### DevOps With Docker
Eeva-Maria Laiho

# Part 1

# 1.1

![Exercise 1.1](1.1.PNG)

# 1.2

![Exercise 1.2](1.2.PNG)

# 1.3

To start the container:
```$ docker run -it devopsdockeruh/pull_exercise```

The script asks for password, that is ```basic```.

After typing the password the script prints:
```
You found the correct password. Secret message is:
"This is the secret message"
```

# 1.4

To start the container
```$ docker run -d --name bashex devopsdockeruh/exec_bash_exercise```

To go inside the container
```$ docker exec -it bashex bash```

To tail the log
```$ tail -f ./logs.txt```

This will print the secret message ```"Docker is easy"``` along with some timestamps.

To exit tailing and the container ```Ctrl+C``` and ```Ctrl+P, Ctrl+Q```
