#############################
Installation
#############################

The follwing guide applies to RDM-UIControl and needs to be run on MacOS. Install Xcode10 and get a Jailbroken device with Poke++ to get started. You can run multiple devices. Follow these instructions for each device in a new folder.

Setting up Poke++
-----------------

- Fake Location: On
- Time to Save Location: Startup/Forever
- Enable Workder Mode: On
- URL: http://localhost:8080/data (**yes always localhost!**)
- Frequency (Seconds): 1
- Fake Location Fetch: On
- URL: http://localhost:8080/loc (**yes always localhost!**)


Setting up iSpoofer
-------------------

- Fake Location: Of
- URL: http://localhost:8080/data (**yes always localhost!**)

Setting up the Xcode project
----------------------------

- Clone the project git clone https://github.com/123FLO321/RealDeviceMap-UIControl 
- Go into that folder
- Run pod install (go grab a coffee while you run this the first time)
- Open the Xcode Project (open RealDeviceMap-UIControl.xcworkspace)
- Open RealDeviceRaidMap-UIControl -> RealDeviceMap-UIControl -> RealDeviceMapUITest.swift
- Edit uuid to match your devices uuid (get the id with Window -> Devices and Simulators -> Devices -> Your Device -> Identifier)
- Edit backendURLBaseString to your server where RDM is running on. 
- It needs to acces the WebHook server by default running at port 9001. 
- Check if you can acces that url on your phone. If it says "File / does not exist" it works.
- Fix code signing issues and bundle id conflicts (type update in #boto-spam on our Discord)
- Close Xcode and edit run.py 
- Edit \`device_id\` to match the one in the Xcode project
- If you use iSpoofer install idevicelocation and edit and run spoof.py (python2 spoof.py)

Now start run.py with python2 (python2 run.py) and it should open Pogo. If you get device is not asigned to an instance follow the Instances wiki on RDM.
