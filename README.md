# Bebop_change_IP

## Single Drone 

By default the Bebop-Drone is configured with the ip address **192.168.142.1** in order to change it you need to do:


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
 
  Type i to star to writing  
  Change the ip adrress 
  Press esc to stop writing and wq to exit 
  exit in the terminal  
 ```
5. Finally restart the drone 


## Multiple Drones Bebops

![](https://github.com/dvalenciar/Bebop_change_IP/blob/master/Figure.jpg)
