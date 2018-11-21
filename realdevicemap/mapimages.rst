##########
Map Images
##########
| This guide assumes you have a working RDM installed.

.. contents::
   :local:
   
On Linux
========

- find the volume name (usually named rdm_images or realdevicemap_images)::

   docker volume ls

- find it's "Mountpoint" (probably something like /var/lib/docker/volumes/rdm_images/_data)::

   docker volume inspect rdm_images
   
- add images to egg, gym, pokemon, pokestop and unkown_egg in there
- restart rdm to create raid images from the compose/rdm folder::

   docker-compose down && docker-compose up -d

On MacOS
========

- stop rum docker-compose down 
- edit docker-compose.yml
- change ::

   images:/perfect-deployed/realdevicemap/resources/webroot/static/img 
   
  to ::
  
   /absolut/path/to/images:/perfect-deployed/realdevicemap/resources/webroot/static/img 
   
- go to that folder (e.g.: /absolut/path/to/images)
- add images to egg, gym, pokemon, pokestop and unkown_egg in there 
- restart rdm to create raid images (from the compose/rdm folder)::

    docker-compose down && docker-compose up -d

On Windows
==========
- (todo)

Example Images
==============
- example images can be found `here <https://cdn.discordapp.com/attachments/473886293647163412/498616112448012298/example_images.zip>`_ (extract all contents from example images into the volume path) (Icons by `Icons8 <https://icons8.com/>`_)