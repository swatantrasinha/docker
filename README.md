# docker

Lets learn docker 

When we download docker the below two are also included : 

1. Docker CLI - command line interface with which we can interact with docker

2. Docker Desktop -  GUI where we can see our images and containers

## Docker Daemon
This is the actual docker tool and can perform actions like : 
- spin up containers
- scale up/down containers
- create or pull images

## We can create our own custom image and publish in docker-hub

## Popular Docker Commands

# 1. docker run <br />
![command-01](https://github.com/user-attachments/assets/dd7f8f5e-0db9-49a9-be7e-95595d39ecbf)

# 2. docker container ls
<br />
    <img width="461" alt="image" src="https://github.com/user-attachments/assets/763512b6-3e9c-4d5c-83d5-7569a737000c">

# 3. docker container ls -a
<br />
<img width="471" alt="image" src="https://github.com/user-attachments/assets/da20e9e4-6797-41c9-9a1e-68895fa60852">
<br/>
<img width="632" alt="image" src="https://github.com/user-attachments/assets/efc86167-d080-4ebb-a1ba-833ee9317fc1">

# 4. start and stop containers
<br />
show all containers by <b> docker container ls -a </b>
<br />
<img width="638" alt="image" src="https://github.com/user-attachments/assets/7e0335df-fbf0-4689-adda-ff7435b9d5ad">

In Docker desktop it will look like : <br />
<img width="881" alt="image" src="https://github.com/user-attachments/assets/03195f91-45a6-4e4a-82bf-1abe51bfc538">
 <br />
 We can see all containers have status as EXITED
<br />

Now to start one of these say last one "silly_moore" we will do <br />
<b> docker start silly_moore </b>

now if we do - <b> docker container ls -a </b>
<br />
it will show status as UP
<br />
<img width="650" alt="image" src="https://github.com/user-attachments/assets/9934649a-142d-4e6a-8742-8bce78a2b912">
<br />
To again stop this container we can use <br />
<b> docker stop silly_moore </b> 
<br />
<img width="637" alt="image" src="https://github.com/user-attachments/assets/11a197a0-2c12-4ced-9917-f781068e1a40">
<br />

# 5. execute docker commands inside container <br />
Lets say we want to execute inside container silly_moore so for this we need to make sure container is running. Hence if its not then use <br />
<b> docker start silly_moore </b> <br /> 
and then for execute command use below : 
<b> docker exec <container_name> ls </b> <br />
The result of ls is being shown in the terminal <br />
<img width="563" alt="image" src="https://github.com/user-attachments/assets/5f20e818-2bc0-4da8-a38d-acdd0c0a0fb1"> <br />
Here the ls content is shown in terminal and container is detached hence we are out of the container <br />
Now if we want our terminal to remain attached to the container then use <br />
<b> docker exec -it <container_name> bash </b> <br />
<img width="586" alt="image" src="https://github.com/user-attachments/assets/cf944556-abf3-4d3f-a29c-91782915402b"> <br />

Here we can see after exec command we are still in container and we can do ls to see  <br />
<img width="593" alt="image" src="https://github.com/user-attachments/assets/0a0b3de5-3691-4564-9f99-0b26be33a924"> <br />













