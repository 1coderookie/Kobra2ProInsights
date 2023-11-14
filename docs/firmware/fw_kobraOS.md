<link rel=”manifest” href=”docs/manifest.webmanifest”>

# KobraOS (Stock) 
The official stock firmware for the **Kobra 2 Pro** is called "Kobra OS".  
Even though it's based on Klipper, sources haven't been published yet.

---

## Updating

For updating the firmware, you can either 

- download the necessary `update.swu` file at [Anycubic's firmware & software page](https://www.anycubic.com/pages/firmware-software) for the [Kobra 2 Pro](https://drive.google.com/file/d/1_4-X4O4sBbXfqrcOuRkRR2gYS6woGLUm/view) or   
- update via Anycubic's online service.  
      

<!--  
## Update Procedure

To update the firmware of your printer, copy the file `firmware.bin` onto the microSD card.  
Turn off the printer and plug the card into the cardreader which is located at the front of the frame (next to the USB connector). The card must be inserted with the contacs facing upwards.  
Then turn on your printer. You'll see a black screen with "Updating Firmware..." displayed.  
After a certain time the Anycubic logo will appear and shortly after that the regular main screen will appear.  
Shut down the printer again and take out the card (push it in a bit to unlock it and make it come out a bit, then just pull it out).  
Turn on the printer again, go to "Menu" and then "About" and check if the correct firmware version is displayed.  
If so, everything is fine. If not, check if you really copied the correct version onto the card and proceed the update again.   
   
## Default Settings 
In the following I'll list the (imho) most important settings from the `../source/Marlin/Configuration.h` and `../source/Marlin/Configuration_adv.h`. You can find these files at the GitHub repositories for the specific model (see links below).  
-->

---

## Settings
The specific settings of the machine are -due to the fact that it's closed source now- 'unknown'.  
However, now that the first `update.swu` file is available, it's possible to investigate that one.  

??? info "Special Thanks To @[lpi](https://github.com/lpi)!"  

    At this point I have to say a huge "Thank You!" to @[lgi](https://github.com/lpi) for providing me the content of the `update.swu` file!  
    I won't share the files, but I'll add the content of the two config files here in the following.  
    However, if you want to access the files by your own, you can do so by unzipping the file `update.swu` and then mount the main directory with `squashfs`.  


There are two Klipper-specific config files that can be found:  

- the file `printer.cfg` which contains the pin assignments and specific settings for the Klipper configuration and
- the file `unmodifiable.cfg` which seems to contain additional settings for the auto leveling and the probe.

I won't share any of the files, but I'll quote the content of the two config files here in the following.

---

### Printer.cfg
The following lists the content of the file `printer.cfg` (I reformatted it a bit for a better visibility, but I didn't change any settings!).  
I'll leave the settings uncommented as this point (even though certain settings are *really* tempting to be commented..), because we can't do anything to improve the settings anyway right now.  

```
[]
[printer]
kinematics : cartesian
max_velocity : 500.000000
max_accel : 20000.000000
max_z_velocity : 16.000000
max_z_accel : 5000.000000
minimum_z_position : -20.000000
square_corner_velocity : 20.000000

[stepper_x]
step_pin : PE1
dir_pin : PE0
enable_pin : !PE14
endstop_pin : !PE8
microsteps : 16
full_steps_per_rotation : 200
step_distance : 0.01
position_endstop : -5.000000
position_max : 230.000000
position_min : -5
homing_speed : 30.000000
second_homing_speed : 15.000000
homing_retract_dist : 10
virtrual_endstop : 0

[stepper_y]
step_pin : PG11
dir_pin : !PE11
enable_pin : !PG8
endstop_pin : !PE13
microsteps : 16
full_steps_per_rotation : 200
step_distance : 0.01
position_endstop : -8.000000
position_max : 230.000000
position_min : -5
homing_speed : 30.000000
second_homing_speed : 15.000000
homing_retract_dist : 10
virtrual_endstop : 0

[stepper_z]
step_pin : PG15
dir_pin : !PG14
enable_pin : !PG18
endstop_pin : PG9
microsteps : 16
full_steps_per_rotation : 200
step_distance : 0.0025
position_endstop :0.0000
position_max : 251.000000
position_min : -5
homing_speed : 8.000000
homing_retract_dist : 8
second_homing_speed : 4.000000
virtrual_endstop : 0

[extruder]
step_pin : PC1
dir_pin : PC0
enable_pin : !PG7
heater_pin : PG12
sensor_pin : PB13
microsteps : 16.000000
full_steps_per_rotation : 200
step_distance : 0.00214
nozzle_diameter : 0.400000
filament_diameter : 1.750000
sensor_type : EPCOS 100K B57560G104F
control : pid
pid_Kp : 12.206120
pid_Ki : 0.517208
pid_Kd : 72.016108
min_temp : -200
max_temp : 275
pressure_advance : 0.020000

[flow_calibration]
start_x : 20
start_y : 20
line_length : 150.000000
line_space : 5.000000
step_distance : 0.01
[tmc2209 stepper_x]
tx_pin : PE4
uart_pin : PE5
uart_address : 0
interpolate : 1
sense_resistor : 0.075
microsteps : 16
driver_sgthrs : 100
run_current : 1.4
hold_current :0.7
stealthchop_threshold : 0

[tmc2209 stepper_y]
tx_pin : PE4
uart_pin : PE5
interpolate : 1
run_current : 1.6
hold_current :0.8
uart_address : 3
sense_resistor : 0.075
microsteps : 16
driver_sgthrs : 105
stealthchop_threshold : 0

[tmc2209 stepper_z]
tx_pin : PE4
uart_pin : PE5
interpolate : 1
run_current : 1.2
hold_current :0.7
uart_address : 1
sense_resistor : 0.075
microsteps : 16
driver_sgthrs : 100
stealthchop_threshold : 99999

[tmc2209 extruder]
tx_pin : PE4
uart_pin : PE5
interpolate : 1
run_current : 0.8
hold_current : 0.4
uart_address : 2
sense_resistor : 0.075
microsteps : 16
driver_sgthrs : 10
stealthchop_threshold : 99999

[heater_bed]
heater_pin : PG17
sensor_pin : PB14
sensor_type : ATC Semitec 104GT-2
control : pid
pid_Kp : 60.965809
pid_Ki : 1.479753
pid_Kd : 627.947830
min_temp : -200
max_temp : 125

[verify_heater extruder]
max_error : 120
check_gain_time : 20
hysteresis : 5
heating_gain : 1

[verify_heater heater_bed]
max_error : 120
check_gain_time : 180
hysteresis : 5
heating_gain : 1

[fan]
pin : PG13
[heater_fan hotend_cooling_fan]
pin : PG6
heater_temp : 50
fan_speed : 1

[controller_fan board_cooling_fan]
pin : PG10
stepper : stepper_x,stepper_y,stepper_z,extruder
fan_speed : 1
idle_speed : 0
idle_timeout : 30
heater : extruder,heater_bed

[gcode_arcs]

[pause_resume]

[mcu]
mem_interface : mem_interface_DSP
[input_shaper]
shaper_type_x : mzv
shaper_freq_x : 65.200000
shaper_type_y : 2hump_ei
shaper_freq_y : 61.200000

[resonance_tester]
probe_points : 115,115,50
accel_chip_x : adxl345 X
accel_chip_y : adxl345 Y
min_freq : 1.000000
max_freq : 140.000000
accel_per_hz : 150.000000
hz_per_sec : 1.000000
max_smoothing : 0.000000

[adxl345 X]
spi_speed : 1000000
spi_bus : spi1
adxl_type : lis2dw12
axes_map : x,y,z
rate : 1600

[adxl345 Y]
spi_speed : 1000000
spi_bus : spi0
adxl_type : lis2dw12
axes_map : x,y,z
rate : 1600

[bed_mesh]
speed : 60.0
horizontal_move_z : 5.0
mesh_min : 19,19
mesh_max : 205,210
probe_count : 5,5
mesh_pps : 3,3
algorithm : lagrange

[auto_leveling]
bed_mesh_temp : 60.0
extruder_temp : 210.0
extruder_wipe_z : -2.3
move_speed : 30.0
extrude_x : 61.2
extrude_y : 0
extrude_z : 15
extrude_length : 80.0
extrude_speed : 3.0
extruder_pullback_length : 25.0
extruder_pullback_speed : 30.0
extruder_cool_down_temp : 140.0
lifting_after_completion : 15.0

[safe_z_home]
home_x_position : 38.5000
home_y_position : 185.000
speed : 150.0
z_lift : 10
z_hop : 0.0
z_hop_speed : 8.0

[probe]
pin : PB8
deactivate_on_each_sample : True
x_offset : 0.0
y_offset : 0.0
z_offset : 0
speed : 4.0
final_speed : 4.0
lift_speed : 8.0
samples : 2
sample_retract_dist : 2.0
samples_result : weighted
samples_tolerance : 0.1
samples_tolerance_retries : 2
move_after_each_sample : -2.0
z_offset_adjust : 0.25

[bed_mesh_probe]
pin : PG9
deactivate_on_each_sample : True
x_offset : 24.0
y_offset : 13.35
speed : 4.0
final_speed : 4.0
lift_speed : 8.0
samples : 2
sample_retract_dist : 5.0
samples_result : weighted
samples_tolerance : 0.1
samples_tolerance_retries : 2

[system]
language : 0
boot : 0
wifi : 1
area : 1
run_mode : 1
sound : 1
material_breakage_detection : 1
extrude_speed : 300
retract_speed : 300
retract_extrude_length : 6
screen_off_time : 20
material_breakage_retries : 2
material_breakage_interval : 3
device_model : Anycubic kobra 2 Pro
print_size : 220*220*250mm

[pid_calibrate]
test_points : 50,50,10
extruder_target_temp : 230
heater_bed_target_temp : 60
```

---

### Unmodifiable.cfg

The following lists the content of the file `unmodifiable.cfg`.  

```
[auto_leveling]
target_spot_x : 61.200000
target_spot_y : 243.800000
[probe]
z_offset_adjust : 0.25
```

---

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/U6U5NPB51)  

