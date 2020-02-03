#############################
Installation
#############################

| This guide assumes you have the :doc:`requirements installed<requirements>` and a :doc:`device setup<devicesetup>`.
| If you want to run multiple devices, follow these instructions for each device in a new folder.

Setting up the Xcode project
----------------------------

- Clone the project::

    git clone https://github.com/RealDeviceMap/RealDeviceMap-UIControl 
    cd RealDeviceMap-UIControl

- Run (go grab a coffee while you run this the first time)::

    pod install
    
- Open the Xcode Project (open RealDeviceMap-UIControl.xcworkspace)
- Fix code signing issues and bundle id conflicts:

   .. thumbnail:: ../images/XcodeHelp1.jpg
      :title: Xcode code signing step 1
          
   .. thumbnail:: ../images/XcodeHelp2.png
      :title: Xcode code signing step 2
      
   .. thumbnail:: ../images/XcodeHelp3.png
      :title: Xcode code signing step 3

- Close Xcode
- Run Manager::

    cd Manager
    swift run RDMUICManager -builds 3 -timeout 300 -more flags
    
- Add new Devices:

    - Get the Device UUID from Xcode `Devices and Simulators` Screen
    - Set the Device Name to something unique you can recognise (e.g. SE1)
    - Edit backendURLBaseString to your server where RDM is running on. It needs to acces the WebHook server by default running at port 9001.
    - Doublecheck if you can acces that url on that phone. If it says "File / does not exist" it works.

- It should now take a couple minutes to build and eventually open Pogo. If you get device is not asigned to an instance follow the :doc:`Instances instructions<../realdevicemap/dashboard/instances>`.
