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

1. docker run 

![command-01](https://github.com/user-attachments/assets/dd7f8f5e-0db9-49a9-be7e-95595d39ecbf)


2. docker container ls
<img width="461" alt="image" src="https://github.com/user-attachments/assets/763512b6-3e9c-4d5c-83d5-7569a737000c">


3. docker container ls -a
<img width="471" alt="image" src="https://github.com/user-attachments/assets/da20e9e4-6797-41c9-9a1e-68895fa60852">

<img width="632" alt="image" src="https://github.com/user-attachments/assets/efc86167-d080-4ebb-a1ba-833ee9317fc1">

4. show all containers by <b> docker container ls -a </b>
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








