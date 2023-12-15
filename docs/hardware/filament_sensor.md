<link rel=”manifest” href=”docs/manifest.webmanifest”>

# Filament Sensor

| Specifications |
|:---------------|
| Switch: NO (normally open) |
| Voltage: 24V DC |
| Connector: JST-XH 2.54 (male, 2 pins) |  


The filament runout / break detection sensor is basically a switch inside a housing, which will be triggered and closes the contact when filament is fed through.  
The switch is NO (normally open) and the connector for plugging it into the mainboard's connector is a JST-XH2.54 (male, 2 pins).  

| Sensor's top side (mounting direction) | Sensor's bottom side | Sensor's plug |
|:--------------:|:-------------:|:-------------:|
| ![Top side](../assets/images/fil-sens-front_web.jpg) | ![Bottom side](../assets/images/fil-sens-back_web.jpg) | ![Plug](../assets/images/fil-sens-bottomview_web.jpg) |


## Installation  

The sensor is supposed to be mounted to the belonging bracket at the left hand side of the x-axis gantry.  

![Sensor mounting bracket](../assets/images/K2Pro_fil-sens_bowden_mount_web.jpg)

The arrow printed on the sensor's housing should point towards the bed, the plug will face the back of the printer.  

![Sensor mounted](../assets/images/fil-sens_K2Pro_installed_web.jpg)

After you mounted and connected, you lead the filament through it which then moves the little lever of the switch to trigger it and the electrical circuit will be closed. If the filament runs out because it broke or the spool is empty, the switch will open and the printer will pause (or only shows a warning message? I don't know yet!).  


## Spare Part

If you need to get yourself a new sensor because the one you have is broken or faulty, you don't have to get this sensor directly from Anycubic (which is about 15 to 20 bucks there), as this is actually some kind of 'generic' sensor. You can find this type of sensor for really small money at AliExpress as well for example. Just pay attention to the wiring then when connecting it.    

  
## False Positive Detections And How To Fix Them 

After using the filament runout sensor for a certain time, it may happen that you'll face false positive detections and therefore paused prints even though there was filament loaded.  
   
This might just be a small problem which probably could easily be fixed by bending the little lever of the switch inside of the sensorbox a bit more outwards, so that there's more pressure onto the filament.  
If you do so, make sure that you only bend it slightly and that the lever still triggers the switch when you lead filament through it - you don't want to bend it too much and in a way that it won't be able to trigger the switch anymore.   

You can open the case with a small flathead screwdriver or a knife. Be careful and patient when doing so though, as there's some glue applied which needs some time to come off.  
The following picture shows the inside of the sensor so that you can see the little metallic lever of the switch.  
    
![Filament runout sensor opened](../assets/images/fil-sensor_open_web.jpg)  
    

If bending the lever a bit more outwards doesn't solve your issue, use your multimeter and verify that the switch itself is actually still working correctly. If it's not and you do have some compressed air available (like in a can or if you have a compressor), try to blow into the switch a bit as it might be that some abrasion of filament got inside the switch and causing problems.  
If also that doesn't solve the issue and the switch still isn't working, you'll have to replace it. You could get yourself a spare switch and replace the broken one, or you can just get yourself a whole new filament runout sensor.      

---

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/U6U5NPB51)  
  

