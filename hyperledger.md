

Hyperledger 
========

---
**NOTE**

 "Hyperledger is an open sourced community of communities to benefit an ecosystem of Hyperledger based solution providers and users focused on blockchain related use cases that will work across a variety of industrial sectors.
  – Brian Behlendorf, Executive Director of Hyperledger." 
 
---

## Hyperledger Setup

#### install Curl

1.sudo apt-get install curl

#### install go language

2.sudo apt-get install golang-go <br />

#Setup Go Path <br />

3.export GOPATH=$HOME/go <br />

4.export PATH=$PATH:$GOPATH/bin <br />

#### Install Docker for Ubuntu

 **Docker-ce** - Base package which makes all the necessary files available for the docker container to run properly. <br />
 
 **Docker-compose**- Base package which makes all the necessary files available for the docker container to run properly. <br />
 

5.curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - 

 
6.sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

 
7.sudo apt-get update

 
8.apt-cache policy docker-ce

  
9.sudo apt-get install -y docker

 
10.sudo apt-get install docker-compose

 
11.sudo systemctl status docker
  
  
#Check Docker Version

12.docker-compose --version

#Running Docker Daemon

13.dockerd

#### Install node.js and npm <br />

curl sL https://deb.nodesource.com/setup_8.x | sudo -E bash - <br />

#Check node version and NPM version
$ node -version <br />
$ npm -version <br />

####  Enter the fabric-samples directory and install the platform specific binaries
$ cd fabric-samples <br />
$ curl -sSL https://goo.gl/byy2Qj | bash -s 1.0.5 <br />

If everything goes well you will see the above output on your screen. <br />
To have a look on the download binaries execute the following from your terminal: <br />
$ cd bin <br />
$ ls <br />

Enter into the first-network directory <br />
$ cd ../ <br />
$ cd first-network <br />
$ ls <br />

Generate the required certificates and articates for your first network <br />
$ ./byfn.sh -m generate <br />

To see the generate certificates use the following command: <br />
$ ls <br />
$ cd crypto-config <br />
$ ls <br />

Create your first network using the following command <br />
$ cd ../ <br /> <br />
$ ./byfn.sh -m up <br />

Check the generates images and running containers using the following command: <br />
$ docker images <br />
$ docker ps <br />

To bring down the created network executed the following command <br />
$ ./byfn.sh -m down <br />

You can check the created images have been removed using the following: <br />
$ docker images <br />

 Move to the fabcar directory <br />
$ cd ../ <br />
$ ls <br />
$ cd fabcar <br />

 Install the node modules using the following command <br />
$ sudo npm install <br />

Install grpc module for communication with Hyperledger Fabric using the following command: <br />
$ sudo npm install grpc <br />

Start the Hyperledger Fabric network for fabcar by executing the following command: <br />
$ ./startFabric.sh <br />

To enroll the users firstly you have to enroll an Admin that will help to enroll other users with
Hyperledger Fabric network of Fabcar. <br />
$ node enrollAdmin.js <br />
![enrolladmin first then add register user](assets/images/enrolljs.jpg)

You can find the private and public key for admin using the following <br />
$ ls <br />
$ cd hfc-key-store/ <br />
$ ls <br />
![enter image description here](assets/images/enrolljs.jpg)
Enroll the user to query and invoke fabcar network (As Hyperledger Fabric is a permissioned
blockchain that is why firstly we have to register the user using its certificate) <br />
$ cd ../ <br />
$ node registerUser.js <br />
![enter image description here](assets/images/enrolljs.jpg)

Query the Fabcar network using the following command (To access the ledger state) <br />
$ node query.js <br />
![enter image description here](assets/images/queryjs.jpg)
