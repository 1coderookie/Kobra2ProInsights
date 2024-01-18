<link rel=”manifest” href=”docs/manifest.webmanifest”>

# Mainboard

## TriGorilla_Spe_A_V1.0.0 (Stock) 
  
The stock mainboard is labeled as "Trigorilla_Spe_V1.0.0".   

It is a 32bit 24V mainboard with an ARM Cortex-A7 which runs at 1.2GHz and offers 8GB of internal storage capacity.  

The mainboard comes with four TMC2209 silent stepper drivers (at least that's what Anycubic states - I didn't take off the heatsinks to check if these really are genuine TMC2209 chips) which are *soldered* onto the board (they can't be swapped out!).  

It offers three USB-A connectors labeled at the PCB as "U-EXT1", "U-EXT2" and "U-FRIMWARE" (yes, typo included ;) ).  

It also offers a built in Realtek WiFi chip ([RTL8723DU](https://www.realtek.com/en/products/communications-network-ics/item/rtl8723du)) with an external antenna which is glued to the left front side of the black plastic aperture from the inside of the housing (the position is about where the label "Kobra 2 Pro" is located).   

![Mainboard TriGorilla front](../assets/images/mainboard_K2Pro_frontside_web.jpg)  
  
![Mainboard TriGorilla back](../assets/images/mainboard_K2Pro_backside_web.jpg)  

At the following picture I added labels of the connectors.  

![Mainboard labeled](../assets/images/mainboard_K2Pro_labeled_web.jpg)

The pinout of the 7 pin connector of the acceleration sensor is printed onto the PCB itself (same with some other pinouts of connectors in that row), but I'll list it here again, just in case you can't read it on your mainboard and when zooming in the picture shown above.  
So when you're looking at the connector in the direction of the picture above, the pinout (from left to right) is:  
| 5V | GND | CS | SCK | MISO | MOSI | GND |  


The USB-A connectors can be accessed from the front of the printer, you find them at the right hand side of that black plastic aperture of the frame as shown in the picture below.  

![USB-A connectors](../assets/images/K2Pro_front_USB_web.jpg)  

--- 

### Accessing The Mainboard  
If you need to access the mainboard, you need to open the housing where the mainboard is located. For doing so, you need to access the underside of the printer.  
The housing where the mainboard is located in is about 238x142mm and it's inserted in between the side rails of the base frame (see the expandable textbox below for further pictures).

Once you opened the lid, you can see that there's quite a lot of space left inside of the enclosure. If one re-routes the wires, it should be possible to add an [external MOSFET](powersupply.md#add-an-external-mosfet-mod) for the bed here.  

![Housing opened](../assets/images/mainboard_K2Pro_mobo-in-case_web.jpg)  

Please see the expandable textbox below for further instructions and illustrations about how to actually open the housing and access the PCB.  

As this might be interesting for someone who might try to access the mainboard for reverse engineering, I'd like to mention that there's a four pin SPI/UART connector on the mainboard as shown in the following picture.  

![SPI connector](../assets/images/mainboard_K2Pro_connectors_SPI_web.jpg)  

??? example "How To Open The Mainboard's Housing"  

    - When looking at the underside of the machine, you can see the housing of the mainboard being located it the front, between the outer rails of the baseframe.  
      ![Mainboard's housing](../assets/images/mainboard_K2Pro_lid_web.jpg)  
    - In the middle you can see two hex screws. These are holding the whole housing in place as they're screwed into the Y-rail in the middle, but they also hold down the lid. So take them out first.  
    - After you took out the screws, you then have to 'unclip' the lid of the housing. As you can see in the following picture, there are plastic 'noses' which rest in the belonging nothes of the housing's base part. Use a thin tool like a screwdriver or a plectrum and insert it in the slot between the housing's lid and the base part.  
      You then need to *carefully* bend the base part slightly away to make the lid come out. I'd suggest to start at one edge like show in the picture below - once you have lifted that up, it's much easier to go around the rest.  
      ![Lid unclipped](../assets/images/mainboard_K2Pro_lid-halfopen_web.jpg) 
    - Once you have released all clips, I'd recommend to unplug the flat ribbon cable of the control unit and lead it through the belonging cutout of the lid for being able to flip the lid over.  
    - Once you have done that, you can flip the lid over as shown in the following picture.  
      ![Lid flipped](../assets/images/mainboard_K2Pro_lid-open_web.jpg)  
    - Be careful and don't rip off the wire of the fan!    

    **That's it - you successfully opened the housing of the mainboard!**  

    - If you need to take out the whole mainboard now, take out the four screws located in the corners of the mainboard.  
      Then lift up the PCB in the back first, as the USB connectors are positioned in those cutouts in the front of the housing. 
    
    For **reassembling** everything, just follow the steps in reverse.  
    In addition to that, mind the following:  
    
    - Pay attention to the wires though, so that they aren't positioned between the posts where the screws will be screwed through later.    
    - Also mind the black ribbon cable of the control unit - don't forget to lead it through the belonging cutout of the lid and reconnect it to the control unit.  
    - Also make sure to reconnect the black grounding wire at the lower right corner in case you took out the PCB.  

    If you want to **take away the whole housing** to e.g. place it outside an enclosure you put the printer in, mind the following:  
    
    - You have to take off the mount which holds the control unit.  
    - You have to pull out the black plastic cap of the face of the other side's rail. That one is just stuck in the aluminum frame, so you can pull it out. Be careful to not break those little plastic posts though which are shoved into the threads of the middle parts of the 4040 rail.  
      ![Released cap](../assets/images/frame_K2Pro_cap-rail_web.jpg)  
    - See the following picture for getting an idea of how it should look like when all parts are dismounted for taking away the housing.  
      ![Released caps](../assets/images/mainboard_K2Pro_open-box_underside_web.jpg)   
    - You now have to disconnect all wires.  
    - Once you have completed this step, you can then just pull out the enclosure. It's shoved in between those two outer rails of the base frame, some plastic noses are guiding it in one of the v-slots.  
      ![Plastic nose in v-slot](../assets/images/mainboard_K2Pro_case-sliders_web.jpg)
    


??? danger "Add Ferrules To The 24V Wires!" 

    The 24V wires already come with ferrules being added. If it happens that your specific machine doesn't come with ferrules but with tinned wires instead, **it's highly advisable to cut off the tinned tips of the wires without a plug (power supply and heated bed) and add ferrules to them.**  
    Same goes for the case that a ferrule comes off - in that case, **add a new one** instead of just inserting the wire or tinning the end of it.     
    
    The reason why not using tinned ends is simple: when you are screwing down the soldered tip inside the clamp, the solder will get cracked a bit and may get deformed a bit as well.  
    When the wire gets warm due to the current and the solder gets softer, the contact may become loose which could lead to malfunction or even cause fire in the last consequence.  
    So it's always highly recommendable to just use proper ferrules!  
    ![Ferrules instead of soldered tips](../assets/images/mainboard_ferrules_web.jpg)  
  

??? info "Red Glue Across All Connectors"

    When you look at the mainboard, you'll see some red glue spread across all connectors.  
    ![Red glue](../assets/images/mainboard_K2Pro_red-glue_web.jpg)  
    That's just for securing the connnection. You can get that stuff off by carefully pulling it off. It works better if you warm up that stuff *a little bit* for making it more flexible, a hair dryer is good for that. It then becomes a bit softer and easier to be pulled off. Don't heat it up too much though as it'll become too soft then!  
    You can also use a thin screwdriver to lift up a part of that stuff and then use some tweezers to grab it.    
    
    However, be *very careful* to  
    
    - not harm the mainboard by slipping off with the screwdriver or tweezer!  
    - not overheat the mainboards of parts of it when heating up that red glue!  
    - not rip off the heatsinks of the stepper drivers!  
      This can happen really quick as they're just glued onto the stepper drivers with some thermal paste and the red glue is usually spread across the fins of the heatsinks as well!  
      So *if* you have to pull off that stuff from those connectors of the motor wiring, then *make sure that you press down the heatsink with your finger when trying to pull that stuff off!*  
      
---

### Connecting To The Printer / Mainboard

Anycubic doesn't allow any local access to the machine, neither via USB or via the inbuilt WiFi. So if you want to get access, you need to use their cloud service and APP.  

However, there are some approaches and/or solutions being worth mentioned at this point which I'll list as MODs in the following. As soon as I come across further ones, I'll add them here as well.  

---

#### MOD: RPi Zero(2)W As WiFi USB Drive
[mrfenyx](https://github.com/mrfenyx/) came up with an imho brilliant solution to avoid using a USB drive which you'd have to swap back and forth between your computer and your printer: he uses a Raspberry Pi Zero(2)W as a USB drive and which can then be accessed through your local network using WiFi. By doing so, you can just send (= copy/save) the sliced file to the RPi and then select it at the printer using the control unit.  
I personally didn't test it yet, but I'll definitely do so.  

This is the repo where you can find all the necessary information: [RPi-Zero-W-WiFi-USB](https://github.com/mrfenyx/RPi-Zero-W-WiFi-USB/)  

??? warning "Use A USB Power Blocker"

    When connecting the Raspberry Pi to the printer, make sure to use an additional USB power blocker.  
    By doing so, you make sure that neither the RPi nor the mainboard will draw power through the USB-C connector from the other device. If you don't do so, it can harm your mainboard as well as your computer.  
    
    As it's an fast and easy solution, you can get a device called "USB power blocker" for a few bucks. Attention: make sure to *not* get a "USB *data* blocker" though, it *has* to be a *power* blocker!  
    This device will then be plugged between the USB connector of the computer and the actual USB-C cable. It still allows data to be transferred, but the 5V line isn't existent. The following picture shows such a device - it's just plugged in between the printer's USB and the USB cable.  

    ![USB power blocker](../assets/images/USB_powerblocker_web.jpg)  

    However, you don't *have* to spend money on this item, as there are other ways to interrupt the 5V power line.  
    For example, you can cut the 5V wire of your USB cable, you can solder a male and a female USB connector onto a little PCB and avoid making the 5V line connection.  
    You can also simply use some electric or Kapton tape and cover the belonging pin at the USB connector of the cable like shown in the following picture.  

    ![USB pin tape attached](../assets/images/USB_taped5V_web.jpg)  

    Keep in mind though that you have to pay attention that you *only* cover the 5V pin and that you have to make sure that the tape is still in place every time you plug in the cable after you unplugged it.  

---

#### MOD: Own Server And Webinterface  

User [anjomro](https://github.com/anjomro) did some reverse engineering and created a solution where you basically set up your own server where the machine then connects to via WiFi. You then use a webinterface anjomro created, which uses the interface of the printer's firmware.  
By doing so you can then access the machine locally to a certain degree.  

This neat solution is called ["Kobra Unleashed"](https://github.com/anjomro/kobra-unleashed).  
    
---
  
### MOD: Different Mainboard 
Generally speaking, it's possible to replace the stock mainboard with a different type of board, like e.g. a board from BigTreeTech (BTT) for being able to use Klipper (for example).  
You just have to pay attention that it uses and provides 24V DC as well, as the PSU and the components like the fans etc. are running on 24V.  

Depending on the type of the board, you might have to use a different ABL sensor (and most likely a different type of control unit as well though, but I assume you'll run Klipper on it then anyway) and you probably aren't able to directly connect the acceleration sensor (you'd most likely have to connect it to the RPi where you have Klipper running onto then).  

There haven't been reports of users who changed the mainboard yet though, so I can't show you any specific solution here at this time.  

---

## Mainboard Cooling Fan
  
The following picture shows the fan of the mainboard. It's a 80x80x15mm, 24V, 0.06A type ("HSC BCY8015S24L").  

![MCU fan](../assets/images/mainboard_K2Pro_fan_web.jpg) 

As you can see, the fan is covered with a metal grille to avoid that any wires might get caught.  
The following picture shows the mounting direction of the fan.  

![MCU fan mounting direction](../assets/images/mainboard_K2Pro_fan-mounting-direction_web.jpg)  

 

---

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/U6U5NPB51)   
