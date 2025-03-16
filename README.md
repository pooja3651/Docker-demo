# Docker-demo
Writing the first docker file and running the simple hello world python file on docker.


### What is Docker ?
Docker is a containerization platform that provides easy way to containerize your applications, which means, using Docker you can build container images, run the images to create containers and also push these containers to container regestries such as DockerHub, Quay.io and so on.


Created an AmazonLinux EC2 Instance on AWS and run the below commands to install docker.

```
sudo yum update
sudo yum install docker -y
```

To verify your Docker installation run the below command

```
docker run hello-world
```

If the output says:

```
docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/create": dial unix /var/run/docker.sock: connect: permission denied.
See 'docker run --help'.
```

This can mean two things, 
1. Docker deamon is not running.
2. Your user does not have access to run docker commands.

### Start Docker daemon

Use the below command to verify if the docker daemon is actually started and Active

```
sudo systemctl status docker
```

If you notice that the docker daemon is not running, you can start the daemon using the below command

```
sudo systemctl start docker
```

### Grant Access to your user to run docker commands

To grant access to your user to run the docker command, you should add the user to the Docker Linux group. Docker group is create by default when docker is installed.

```
sudo usermod -aG docker ec2-user
```
In the above command `ec2-user` is the name of the user, you can change the username appropriately.

**NOTE:** : You need to logout and login back for the changes to be reflected.

### Docker is Installed, up and running 

Use the same command again, to verify that docker is up and running.

```
docker run hello-world
```

Output should look like:

```
....
....
Hello from Docker!
This message shows that your installation appears to be working correctly.
...
...
```


### Clone this repository and move to example folder

```
git clone https://github.com/pooja3651/Docker-demo
cd  examples
```

### Login to Docker [Create an account with https://hub.docker.com/]

```
docker login
```


### Build your first Docker Image

You need to change the username accoringly in the below command

```
docker build -t pooja3651/my-first-docker-image:latest .
```


### Verify Docker Image is created

```
docker images
```

Output 

```
REPOSITORY                         TAG       IMAGE ID       CREATED          SIZE
pooja3651/my-first-docker-image    latest    960d37536dcd   26 seconds ago   289MB
hello-world                        latest    feb5d9fea6a5   1 hours ago      13.3kB
```

### Run your First Docker Container

```
docker run -it pooja3651/my-first-docker-image
```

Output

```
Hello World!!!
```

### Push the Image to DockerHub and share it with the world

```
docker push pooja3651/my-first-docker-image
```


### DONE......



