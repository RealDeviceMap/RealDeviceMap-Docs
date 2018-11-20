#############################
Installation
#############################

| This guide assumes you have the :doc:`requirements installed<requirements>` and a :doc:`device setup<devicesetup>`.
| If you want to run multiple devices, follow these instructions for each device in a new folder.

Setting up the Xcode project
----------------------------

- Clone the project::

    git clone https://github.com/123FLO321/RealDeviceMap-UIControl 

  ``tip`` if you will be running multiple devices you should name this folder something recognizable ie::

    git clone https://github.com/123FLO321/RealDeviceMap-UIControl iphoneSE1

- Go into that folder::
    
    cd RealDeviceMap-UIControl
    or
    cd iphoneSE1
    
- Run (go grab a coffee while you run this the first time)::

    pod install
    
- Open the Xcode Project (open RealDeviceMap-UIControl.xcworkspace)
- Open RealDeviceRaidMap-UIControl -> RealDeviceMap-UIControl -> config.swift
- Edit UUID to be something unique (ie iphoneSE1). This will be how you identify which phone is which in your dashboard later on.
- Edit backendURLBaseString to your server where RDM is running on. It needs to acces the WebHook server by default running at port 9001.
- Check if you can acces that url on your phone. If it says "File / does not exist" it works.
- Fix code signing issues and bundle id conflicts (type update in #boto-spam on our Discord)

   - need to add these steps here

- Close Xcode and edit run.py 
- Edit \`device_id\` to match your devices UUID (not the same as in config.swift above)

   - get the UUID in Xcode with Window -> Devices and Simulators -> Devices -> Your Device -> Identifier
  
- Now start run.py with python2::

    python2 run.py

- It should now take a couple minutes to build and eventually open Pogo. If you get device is not asigned to an instance follow the :doc:`Instances instructions<../realdevicemap/instances>`.
