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

### 1. docker run <br />
![command-01](https://github.com/user-attachments/assets/dd7f8f5e-0db9-49a9-be7e-95595d39ecbf)

### 2. docker container ls
<br />
    <img width="461" alt="image" src="https://github.com/user-attachments/assets/763512b6-3e9c-4d5c-83d5-7569a737000c">

### 3. docker container ls -a
<br />
<img width="471" alt="image" src="https://github.com/user-attachments/assets/da20e9e4-6797-41c9-9a1e-68895fa60852">
<br/>
<img width="632" alt="image" src="https://github.com/user-attachments/assets/efc86167-d080-4ebb-a1ba-833ee9317fc1">

### 4. start and stop containers
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

### 5. execute docker commands inside container <br />
Lets say we want to execute inside container silly_moore so for this we need to make sure container is running. Hence if its not then use <br />
<b> docker start silly_moore </b> <br /> 
and then for execute command use below : 
<b> docker exec <container_name> <command> </b> <br />
The result of ls is being shown in the terminal <br />
<img width="563" alt="image" src="https://github.com/user-attachments/assets/5f20e818-2bc0-4da8-a38d-acdd0c0a0fb1"> <br />
Here the ls content is shown in terminal and container is detached hence we are out of the container <br />
Now if we want our terminal to remain attached to the container then use <br />
<b> docker exec -it <container_name> bash </b> <br />
<img width="586" alt="image" src="https://github.com/user-attachments/assets/cf944556-abf3-4d3f-a29c-91782915402b"> <br />

Here we can see after exec command we are still in container and we can do ls to see  <br />
<img width="593" alt="image" src="https://github.com/user-attachments/assets/0a0b3de5-3691-4564-9f99-0b26be33a924"> <br />

Note: Press Control + D to get out of container <br />

### 6. images in local machine
<br />
<b> docker images </b> 
<br /> or <br />
<b> docker image ls </b> 
<br />
<img width="503" alt="image" src="https://github.com/user-attachments/assets/8688df8e-4d50-49cf-985a-00ebe791790d"> <br />

Note: The above command is only to see images in local machine , we can go to dockerhub to see list of all images 
like node, postgress, redis, python, ngnix etc <br />

We can use these images <br /> 
<b> docker run -it node </b> <br />
It will say unable to find locally and then it will start pulling images from docker hub <br />
and it would spin up container automatically where node js is running <br />
<img width="538" alt="image" src="https://github.com/user-attachments/assets/9c993b24-64a0-4e14-bb5e-2fb2dfb188b1">
<br />
We can use this as node js terminal <br />
<img width="202" alt="image" src="https://github.com/user-attachments/assets/ab2b7001-4545-4a5a-9f8f-9e70b4942d59"> <br />
Now since node images is also pullled in our local machine so if we exit from container using Control + D and then type <br />
<b> docker container ls -a </b> <br />
We can see node is also there with ubuntu <br />
<img width="728" alt="image" src="https://github.com/user-attachments/assets/d10917e7-d827-474a-a6a5-9a462eca74e1"> </br >

### 6. Port Mapping
<br />
The container port is different then browser port so need PORT-Mapping <br />
docker run -it p <my-port>:<container-port> <container-image>
<br />


### 7. Environment Variables
<br />
Say we have two environment variables
key1 and key2 with values value1 and value2 respectively <br />

> docker run -it p <my-port>:<container-port> -e key1=value1 -e key2=value2 <container-image>

<br />

### 8. Dockerize Application

# Step1 : initialize 
> npm init

# Step2: install express
> npm i express

# Step3: create file main.jsand then write below code in main.js
<br />

```javascript
const express= require('express');
const app= express();

const PORT= process.env.PORT || 8000;

app.get('/', (req,res) => {
    return res.json({message: 'hey I am node js in container'})
})
app.listen(PORT, () => console.log(`Server started on port ${PORT}`))

```

Now we have a node application with files like package.json, main.js, package-lock.json
to dockerize it we will create docker file

# Step4: create docker file and write below code in it

```javascript
# ----------- FROM ubuntu: choose base image as ubuntu on top of which we will install node js -----------#

# FROM ubuntu

#----------- install node js on ubuntu -----------#

# RUN apt-get update
# RUN apt-get install -y curl
# RUN curl -sL https://deb.nodesource.com/setup_18.x | bash -
# RUN apt-get upgrade -y
# RUN apt-get install -y nodejs

# ----- Below one line is alternative to above all the lines -----#
FROM node:alpine

# ----- Node js is installed and now copy files ----- #
WORKDIR /usr/app

COPY package.json package.json
COPY package-lock.json package-lock.json
COPY main.js main.js

RUN npm install

# ----- declare entry point -----#
ENTRYPOINT [ "node","main.js" ]
`
```

# Step5: build the image 
Build Docker Image with below command
> docker build -t mynodeapp .

<br />
<img width="904" alt="image" src="https://github.com/user-attachments/assets/9f1fe6f7-80de-4991-8da1-38914158a1af">
<br />

So the image is build <br />
In Docker Desktop we can see our image <b> "swatantra-node-app"  </b> <br />
<img width="1104" alt="image" src="https://github.com/user-attachments/assets/9fe87cb9-0f4b-4183-8dad-994163fb6df9">
<br />
This image is not in docker-hub but in our local machine and we can run it as below :
<br />


# Step6: run  the container
<br />
 > docker run -it -p 8000:8000 swatantra-node-app 
<br />

<img width="958" alt="image" src="https://github.com/user-attachments/assets/08339157-263a-41b0-890f-1cb3eb79f40d">
<br />
Now if we send a <b>GET</b> request via postman with URL - <b> localhost:8000 </b> then  we will get the response <br />
<img width="806" alt="image" src="https://github.com/user-attachments/assets/3f2ab2a0-4097-466a-9ab5-05c3d0364cff">
<br />

# Step7: use of env varibale

Now lets see how to use env varibale. In out application we are using 
> const PORT= process.env.PORT || 8000;

So PORT is from environment variable <br />

> docker run -it -e PORT=4000 -p 4000:4000 swatantra-node-app

<img width="1046" alt="image" src="https://github.com/user-attachments/assets/cff87a70-1037-4cce-8f47-50b5659780af">
<br />
Now if we use POST and hot <b> GET </b>  request with URL - <b> localhost:4000 </b> it will work <br />
<img width="489" alt="image" src="https://github.com/user-attachments/assets/718e1c9f-4504-4123-a8d8-5511f84e5a78">
<br />

Note: In Docker layer caching is followed <br />


# Step8: Publish Image to Docker Hub
<br />

- login to <b> https://hub.docker.com/ </b>
- Click on <b> Create Repository </b> 
- give a name - <b> swatantra-repo </b>
- Select Visibility as <b> Public </b>
- Click on <b>Create</b>

After Click on "Create", we can see on right side <br />
> docker push swatantrasinha/swatantra-repo:tagname
<br />

<img width="466" alt="image" src="https://github.com/user-attachments/assets/64c3ebeb-6cf8-41b3-8a31-a865b64a3bea">
<br />
So we need to create an image with name <b> swatantrasinha/swatantra-repo </b>
<br />
so we will go back to our terminal <br />
earlier we gave command :  "docker build -t mynodeapp ." (See Step 5)
<br />
now we will give - 
> docker build -t swatantrasinha/swatantra-repo .
<br />
<img width="955" alt="image" src="https://github.com/user-attachments/assets/e2a91c51-4b14-457e-9f53-93e6ced0c8a7">
<br />
In docker desktop we can see "swatantrasinha/swatantra-repo" <br />
<img width="910" alt="image" src="https://github.com/user-attachments/assets/bda9a0cb-4188-49a1-a9f2-40f2f69a870f">
<br />
Finally we will push it <br />
> docker push swatantrasinha/swatantra-repo
<br />

<img width="917" alt="image" src="https://github.com/user-attachments/assets/3cf60e88-12c6-4b2b-b318-2321c1390f59">

Note: if we are not logged in then before push it may ask to login 
<br />
 Finally, wee can see its pushed in docker-hub
 <img width="1094" alt="image" src="https://github.com/user-attachments/assets/96750dfc-9968-483c-a45c-4be7d0792287">
 <br />
 


























