###########################
Deploy
###########################
.. include:: ../../formatting.rst
.. contents::
  :local:

Build realdevicemap/realdevicemap docker image
------------------------------------------------
Run this in the RDM folder: ``sh .jenkins/build.sh new-tag``

Use the new tag in the .yml
----------------------------
Edit ``docker-compose.yml`` and change ``latest`` to ``new-tag``
