# Fincra-assessment

# Deploy the kong api gateway 
## What is Kong API gateway?
According to its official documentation, Kong Gateway is a lightweight, fast, and flexible cloud-native API gateway, built for hybrid and multi-cloud, optimized for microservices and distributed architectures. 
Kong Gateway runs in front of any RESTful API and can be extended through modules and plugins. It’s designed to run on decentralized architectures, including hybrid-cloud and multi-cloud deployments.

With Kong Gateway, users can:

Leverage workflow automation and modern GitOps practices
Decentralize applications/services and transition to microservices
Create a thriving API developer ecosystem
Proactively identify API-related anomalies and threats
Secure and govern APIs/services, and improve API visibility across the entire organization.


## Technologies used
* Docker
* Nginx
* Docker-compose
* HTTPie

Please ensure that these tools above are installed.


For the purpose of this assessment, I used the Kong Gateway (OSS) mode which is an open-source package containing the basic API gateway functionality and open-source plugins.


## Steps 
1. Create an Ubuntu 20.04 LTS instance using AWS.
2. Install Docker using this command: `sudo apt install docker.io`.
3. Install Docker-compose.
4. Add your user to the sudoers group using this command: `sudo usermod -aG docker $USER`
5. Exit and ssh back into the instance, then run the command: newgrp docker to activate the changes.
6. Setup swap limit capabilities on docker by editing the /etc/default/grub file
7. Add the following string inside of the GRUB_CMDLINE_LINUX_DEFAULT variable:cgroup_enable=memory swapaccount=1
8. Save the file and reboot your instance.
9. Run sudo update-grub command.
10. Clone the repo and check the docker-compose.yml file.
11. Add docker-compose to the sudoers group.
10. Create the docker-compose file. This file contains the PostgreSQL, Kong and konga images configuration. 
10. Run the docker-compose file using `docker-compose up -d`.
11. verify the the containers are running and you access the kong admin-api through this url:http://18.133.234.14:8001

 
 # Deploy konga dashboard (using docker) for kong API administration 
 ## What is Konga-dashboard?
 According to the author, Konga is a fully featured open source, multi-user GUI, that makes the hard task of managing multiple Kong installations a breeze. It can be integrated with some of the most popular databases out of the box and provides the visual tools you need to better understand and maintain your architecture.

 ## Steps
 1. The konga dashboard is already running as a docker container and can be accessed  using this url: http://18.133.234.14:1337.
 2. Configure the kong admin api to be accessed through the konga GUI.
 3. First, create a user and include your credentials.
 4. Create a connection to the kong-admin api. Add name as kong-admin-api and http://18.133.234.14:8001 as the Kong Admin API url.


 # Configure nginx to listen to requests from specific ports externally and route to kong and konga. 
 ## Steps
 1. Ensure that nginx is installed and its service enabled.
 2. Cd into /etc/nginx/sites-enabled and create an nginx.conf file using `sudo touch nginx.conf`.
 3. Edit the nginx.conf file.
 4. Make sure to reload the nginx service after configuration of the nginx.conf file.
    `sudo systemctl reload nginx.service`
 5. Test to ensure that the nginx is configured and ports are routing to the specific endpoints.
 6. Access the kong api through this url: http://18.133.234.14/kong 
 7. Access the konga-dashboard through this url: http://18.133.234.14/konga 

Problems: the http://18.133.234.14/konga points to a page with the following "Neat! Your account is activated."
