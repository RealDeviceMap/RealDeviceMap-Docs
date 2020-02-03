############
Installation
############
| This guide assumes you have the :doc:`requirements installed<requirements>`.

.. contents::
   :local:

RDM Setup Process using Docker (any OS)
-----------------

- Create a GitHub acces token:
   
    Create a token with [repo] and [read:packages] here https://github.com/settings/tokens/new and copy the token
    
- Log into GitHub Package cloud (using your username as username and the token you created as password)::

    docker login docker.pkg.github.com/realdevicemap/realdevicemap 

- Create a new folder for your compose files and RealDeviceMap::

    mkdir compose/rdm
    
- Switch into that folder::

    compose/rdm

- Get the composer file::

    wget https://raw.githubusercontent.com/RealDeviceMap/RealDeviceMap/master/docker-compose.yml

- Edit the file::

    nano docker-compose.yml

- If you are using the RDM included docker database

  - Edit the values for \`DB_USERNAME\` & \`DB_PASSWORD\` and \`MYSQL_USER MYSQL_PASSWORD\`. Recommend using \`rdmuser\` as the username and a secure password. The username and password should match in both sections.
  - Edit the value for \`MYSQL_ROOT_PASSWORD\` to a secure password for the root user.
  - Everything else can stay at default
  - if you run a database on port 3306 already (and not using it for this project): 
  
    - edit 3306:3306 to 3307:3306 for example. The db will then be accessible on the host (localhost) at port 3307
    
  - Start the docker Database Server::
        
        docker-compose up -d db 

- If you are using an existing database

    - Edit the values for \`DB_HOST\`, \`DB_DATABASE\`, \`DB_USERNAME\` & \`DB_PASSWORD\` to match your existing database configuration.
    - Remove or comment out the following lines/sections from the document::
    
        depends_on:
        - db
        
        ...
        
          db:
            image: mysql
            command: --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
            container_name: realdevicemap-db
            restart: unless-stopped
            environment:
              MYSQL_ROOT_PASSWORD: YourStrongRootPassw0rd!
              MYSQL_DATABASE: rdmdb
              MYSQL_USER: rdmuser
              MYSQL_PASSWORD: YourStrongPassw0rd!
            ports:
              - 3306:3306
            volumes:
              - data:/var/lib/mysql
            #     - /etc/localtime:/etc/localtime:ro

- Start the RealDeviceMap Server (don't add -d the first time so we can get the token)::

    docker-compose up rdm 
    
- Visit http://localhost:9000 (or whatever the server ip/hostname to your VPN is) and create an admin account with the access-token you see in the output of that command
- The map will start at 0,0 (blue ocean)
- Click Dashboard -> Settings and edit the start location
- RDM is now running on your system 🍻
- (you can now press Ctrl-C to stop in attached mode and start it again with: :: 

   docker-compose up -d rdm 

RDM Setup Process using SwiftEnv (Ubuntu only)
-----------------

- Install SwiftEnv::

    git clone https://github.com/kylef/swiftenv.git ~/.swiftenv
    echo 'export SWIFTENV_ROOT="$HOME/.swiftenv"' >> ~/.bash_profile
    echo 'export PATH="$SWIFTENV_ROOT/bin:$PATH"' >> ~/.bash_profile
    echo 'eval "$(swiftenv init -)"' >> ~/.bash_profile

- Clone RealDeviceMap::

   git clone https://github.com/RealDeviceMap/RealDeviceMap
   cd RealDeviceMap

- Install required Swift version::

   swiftenv install
   
- Start RealDeviceMap:
   
   - Start RDM with default settings::
   
      swift run
      
   - Remember to add Enviroment variables as needed::
   
      DB_PASSWORD=x swift run

- Visit http://localhost:9000 (or whatever the server ip/hostname to your VPN is) and create an admin account with the access-token you see in the output of that command
- The map will start at 0,0 (blue ocean)
- Click Dashboard -> Settings and edit the start location
- RDM is now running on your system 🍻

What Next?
----------

- Setup :doc:`Map Images <mapimages>`
- Setup one or more :doc:`RealDeviceMap-UIControl Device Controllers<../realdevicemapui/index>`
