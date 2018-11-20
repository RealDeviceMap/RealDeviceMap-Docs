###########################
Instance
###########################
.. raw:: html

   <style>
      h1:before {
         content: "RDM ";
      }
   </style>
   
| Instances control the devices. Each Instance has a specific scheduler type. Instances can have multiple devices asigned to it.

Create a new Instance
---------------------

- Open RDM in the Webbrowser and login as admin
- Go to Dashboard -> Instances and click "Add New Instance" 

  * Name: A unique name of the Instance
  * Scheduler Type: 
  
    - Circle Pokemon: Scanns for Pokemon (Nearby) at exactly the coords specified
    - Circle Pokemon: Scanns for Raids at exactly the coords specified
    
  * Scan Area: 
  
    - For Circle Scheduler: A list of coords to scann (it will scann a circle with radius 750m around these coords) 

Use `this tool <https://www.mapdevelopers.com/draw-circle-tool.php>`_ to layout circles. Example: ::

   10.0,10.0
   11.0,11.0
   ...

- Save the Instance
- Start the Device Controler for that device one
- Go to Dashboard -> Devices and click "Asign Instance" for that new device
- Select the instance and click "Assign"
- Your device should now start scanning
