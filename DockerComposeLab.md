#Docker Compose Lab
**Installing Docker, docker compose, and as my application of choice, BookStack**

 ## **Installing Docker**
  For this part of the assignment it was mainly copy and paste from [Ubuntu docker install](https://docs.docker.com/engine/install/ubuntu/)
  The site contains all the necessary code in order to implement docker itself on a distribution.
  The exact code used to set up docker's repository was:
  
  '''
  sudo apt update
  sudo apt install ca-certificates curl
  sudo install -m 0755 -d /etc/apt/keyrings**
  sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
  sudo chmod a+r /etc/apt/keyrings/docker.asc
  sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
  Types: deb
  URIs: https://download.docker.com/linux/ubuntu
  Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
  Components: stable
  Signed-By: /etc/apt/keyrings/docker.asc
  EOF
  sudo apt update
  '''

  Once the initial setup is complete, it is now possible to download the package that contains docker fully, and the command to do that is 
  
  '''
  sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
  '''
  **Here is a screenshot documenting the completion of this step**
    obsidian://open?vault=CYB-3353&file=Pasted%20image%2020251116211356.png
  
 ### **BookStack Setup**
 I chose the BookStack application to download using the docker containers because it seemed pretty cool in concept; It arranges files into shelves, chapter, and    pages, it is to supposedly imitate a digital library.
 After the initial setup, I found the bookstack docker-compose.yml file from[Docker-compose.yml](https://github.com/linuxserver/docker-bookstack)
 Before anything is done with the .yml file, a bookstack directory is created using:

 '''
 mkdir bookstack
 '''
 
 Below is the exact contents of the .yml file: 

 '''
 ---
 services:
   bookstack:
     image: lscr.io/linuxserver/bookstack:latest
     container_name: bookstack
     environment:
       - PUID=1000
       - PGID=1000
       - TZ=Etc/UTC
       - APP_URL=
       - APP_KEY=
       - DB_HOST=
       - DB_PORT=3306
       - DB_USERNAME=
       - DB_PASSWORD=
       - DB_DATABASE=
       - QUEUE_CONNECTION= #optional
     volumes:
       - /path/to/bookstack/config:/config
     ports:
       - 6875:80
     restart: unless-stopped
  '''
  
  A screenshot of the .yml file within my distribution:
  obsidian://open?vault=CYB-3353&file=Pasted%20image%2020251116234537.png


 Once the directory is made and the .yml file has been successfully copied, I can now start the container using: 

 '''
 sudo docker compose up -d
 '''
 
Then access BookStack by [Bookstack localhost site](http://localhost:6875)
That link just demonstrates the site that I am able to get to when my container is up, once the container is down, the site is nonoperational.

The hardest part I would say was finding all the right fields to fill out in the environment part of the docker-compose.yml file. Anyways, here is my documentation for installing docker, docker-compose, and BookStack on my distribution. 




