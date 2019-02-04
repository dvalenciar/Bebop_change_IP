# Bebop_change_IP

## Single Drone 

By default the Bebop-Drone is configured with the ip address **192.168.42.1** in order to change it you need to do:


1.  Turn on your drone and wait until the drone booted 

2.  Press the on/off button 4 times 

3.  Connect your computer to the drone's access point
 
4.  Open a new terminal in your computer and run:
  ```
  adb connect 192.168.42.1:9050
  adb shell mount -o remount,rw /
  adb shell 
  cd sbin
  vi broadcom_setup.sh
  ```
  Type *i* to star to writing. Change the ip adrress and press *esc* to stop writing, finally  type *wq* to exit 
  
5. Finally restart the drone 


## Multiple Drones Bebops

These are the instructions to connect multiple drones to the same network, as shown in this figure

![](https://github.com/dvalenciar/Bebop_change_IP/blob/master/Figure.jpg)

1 . Change the IP of each Drone

Change the IP of each Drone following  the instructions mentioned [above](https://github.com/dvalenciar/Bebop_change_IP/blob/master/README.md#single-drone). These IP should be in the same range  (e.g. Drone_1 --> 192.168.42.11  Drone_2--> 192.168.42.22     Drone_3 -->192.168.42.33)


**Do the following for each Drone**

2. Connect your computer to the drone's access point 

3. Press the on/off button 4 times 

4.  Open a new terminal in your computer and run:

  ```
  adb connect 192.168.42.11:9050  (careful here, put the correct IP that  you have changed in step 1)
  adb shell mount -o remount,rw /
  adb shell 
  cd bin
  cd onoffbutton
  vi shortpress_5.sh
  ```
   Copy the next lines 
  ```
  #!/bin/sh
	 BLDC_Test_Bench -M 2 >/dev/null
	 iwconfig eth0 mode managed essid YOUR_NETWORK (careful here, put the correct name of your network)
	 ifconfig eth0 192.168.42.11 netmask 255.255.255.0 up  (careful here, put the correct IP of the Drone)
	 route add default gw 192.168.42.1
  ```
   Press esc to stop writing and wq to exit 
  
   
5. Make the file executable 
  ```
  chmod 777 shortpress_5.sh
  ```
6. Restart the drone 



7. **Very Important**

   To connect the Drone to the network, all you have to do is press the  on/off button 5 times in a row.
   If everything is correct, the drone will emit a sound and connect to your Wi-Fi network.




Do this to all your Drones. When You finish, You should be able to ping all the Drones from your computer 
  
  
  
  
