#Docker Compose Lab
**Installing Docker, docker compose, and BookStack**

## **Installing Docker**
**For this part of the assignment it was mainly copy and paste from [Ubuntu docker install](https://docs.docker.com/engine/install/ubuntu/)**
**The exact code I used was**
**'''**
**sudo apt update**
**sudo apt install ca-certificates curl**
**sudo install -m 0755 -d /etc/apt/keyrings**
**sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc**
**sudo chmod a+r /etc/apt/keyrings/docker.asc**
**sudo tee /etc/apt/sources.list.d/docker.sources <<EOF**
**Types: deb**
**URIs: https://download.docker.com/linux/ubuntu******
**Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")**
**Components: stable**
**Signed-By: /etc/apt/keyrings/docker.asc**
**EOF**
**sudo apt update**
**'''**
**A screenshot documenting the completion of this step**
**obsidian://open?vault=CYB-3353&file=Pasted%20image%2020251116211356.png**

**Once this was completed, I downloaded the docker packages**
**'''**
**sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin**
**'''**
### **BookStack Setup**
**After the initial setup, I found the bookstack docker-compose.yml file from[Docker-compose.yml](https://github.com/linuxserver/docker-bookstack)**
**Below is the exact contents of the .yml**
**'''**
**---**
**services:**
  **bookstack:**
    **image: lscr.io/linuxserver/bookstack:latest******
    **container_name: bookstack**
    **environment:**
      **- PUID=1000**
      **- PGID=1000**
      **- TZ=Etc/UTC**
      **- APP_URL=**
      **- APP_KEY=**
      **- DB_HOST=**
      **- DB_PORT=3306**
      **- DB_USERNAME=**
      **- DB_PASSWORD=**
      **- DB_DATABASE=**
      **- QUEUE_CONNECTION= #optional**
    **volumes:**
      **- /path/to/bookstack/config:/config**
    **ports:**
      **- 6875:80**
    **restart: unless-stopped**
**'''**
**A screenshot of the .yml file in my distribution**
**obsidian://open?vault=CYB-3353&file=Pasted%20image%2020251116234537.png**

**Before anything is done with the .yml file, a bookstack directory was created using** 
**'''**
**mkdir bookstack**
**'''**
**Once the directory is made and the .yml file has been successfully copied, I can now start the container using** 
**'''**
**sudo docker compose up -d**
**'''**
**Then access BookStack by [Bookstack localhost site](http://localhost:6875)**



