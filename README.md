OpenStack-Docker-Team-4
=======================

Configure OpenStack with docker and deploy a 3 tier application

Steps:
  1.  Install OpenStack
  
  2.  Install Docker 
  
  3.  Install Docekr-Heat plugin using link https://github.com/openstack/heat/tree/stable/icehouse/contrib/docker 
      a. Copy contents of above directory to /usr/heat diretory
      b. update PATH_DIRS variable in heat.conf file to include the path /usr/heat/docker
      
  4. pull following images from docker registry 
      a. https://registry.hub.docker.com/u/rishineo/wordpress_fil2
      b. https://registry.hub.docker.com/u/rishineo/mysql_dbpass
      
  4. Start Docker deamon to listen at some specific port number. (We need this in specify in Heat template - docker_endpoint)
  
  5. Use the Heat template (two-tier-app.yaml) in the repository
  
  6. Go to Orchestration->Stacks
      a. Click on Create Stack
      b. Upload the above mentioned yaml file
      c. launch
  
  7. Once the stack has been created successfully, go to the overview page and note down the IP of 'blog' resource.
      This is the private IP where our presentation layer is hosted and this is been connected to a database layer in another container.
      
  8. List the docker process running. for that use sudo docker ps
  
  9. go into the mysqldb container.
      a. type mysql
      b. execute following commands
        1. create database wordpress;
  
  10. Access the IP of the 'blog' container in the browser.
