<link rel=”manifest” href=”docs/manifest.webmanifest”>

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/U6U5NPB51)  

---  
# KobraOS (Stock) 
The official stock firmware for the **Kobra 2 Plus** is called "Kobra OS". Even though it's based on Klipper, sources haven't been published yet.  
KobraOS is locked, you can't access the settings or configuration files (at least not without using 'tools' or workarounds). Furthermore, the USB ports don't allow a local connection to a computer and the printer can't be accessed directly via local WiFi either, one has to use the APP and cloud service of Anycubic.  

It has to be noted that there are different revisions of the mainboards that are being used (please see the according chapter "Mainboard"), as they use different versions and configurations of the KobraOS. One probably wouldn't notice a difference if using them side by side, but there is one huge difference: besides different `printer.cfg` settings, the KobraOS for the "Trigorilla Spe **B**_v1.0.x" seems to be the same as the one being used in the Kobra 3 - and for that one there is a modded KobraOS available. With that modified KobraOS, you gain access to the printer via your regular Mainsail UI or Fluidd UI, can access and change the `printer.cfg`, control the machine etc.  

So when looking at the following sections, either about the settings of the stock `pritner.cfg`, tools to access the KobraOS or even about the modified KobraOS version I mentioned, always make sure to *check the type of mainboard* that's being used in your particular printer before you attempt any further steps.  

---

## Update Procedure

For updating the firmware, you can either 

- ~~download the necessary `update.swu` file at [Anycubic's firmware & software page](https://www.anycubic.com/pages/firmware-software)~~  
  **UPDATE: Anycubic decided to not offer the update files on their support page anymore.**  
  (See the expandable textbox below though if you're looking for those offline files.. ;) )      
- update via Anycubic's online service.  
      
??? info "Firmware Files For Executing Offline Updates"  

    User [hedgehogform](https://codeberg.org/hedgehogform/) created a repository where he offers all `update.swu` files for the Kobra 2 Pro, Plus and Max that have been released by Anycubic. You can find the files [here](https://codeberg.org/hedgehogform/Anycubic-Kobra-2-Series-Firmware).  

---

## Settings "Trigorilla A v1.0.0"
The specific settings of the machine are -due to the fact that it's closed source now- supposed to be 'unknown'.  
However, when the first `update.swu` file became available, it was possible to access and investigate the files `printer.cfg` and `unmodifiable.cfg`.  

??? info "Special Thanks To [lpi](https://github.com/lpi)!"  

    At this point I have to say a huge "Thank You!" to [lpi](https://github.com/lpi) for providing the content of the `update.swu` file to me!  
    I won't share the files, but I'll quote the content of the two config files here in the following.  
    However, if you want to access the files by your own, you can do so by unzipping the file `update.swu` and then mount the main directory with `squashfs`.  


There are two Klipper-specific config files that can be found:  

- the file `printer.cfg` which contains the pin assignments and specific settings for the Klipper configuration and
- the file `unmodifiable.cfg` which seems to contain additional settings for the auto leveling and the probe.

I won't share any of the files, but I'll quote the content of the two config files here in the following.

??? info "Files Of The Kobra 2 Plus & Max"  

    Just in case you own a Kobra 2 Plus or Max, you can find the content of the belonging files quoted in expandable textboxes below.   
    Besides that, if you own a Kobra 2 Plus, check out my comprehensive [Kobra2Plus Insights](https://1coderookie.github.io/Kobra2PlusInsights/) infosite instead.   

---

### Printer.cfg
The following lists the content of the file `printer.cfg` (I added blank lines between the sections for a better visibility, but I didn't change any settings!).  
I'll leave the settings uncommented as this point, because we can't do anything to improve the settings anyway right now.  

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

??? info "Printer.cfg Of The Kobra 2 Plus"  

    ```
    []
    [printer]
    kinematics : cartesian
    max_velocity : 500.000000
    max_accel : 10000.000000
    max_z_velocity : 16.000000
    max_z_accel : 3000.000000
    minimum_z_position : -20.000000
    square_corner_velocity : 15.000000
    
    [stepper_x]
    step_pin : PE1
    dir_pin : PE0
    enable_pin : !PE14
    endstop_pin : !PE8
    microsteps : 16
    full_steps_per_rotation : 200
    step_distance : 0.01
    position_endstop : -5.000000
    position_max : 330.000000
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
    position_endstop : -5.000000
    position_max : 330.000000
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
    position_endstop : 0.0
    position_max : 401.000000
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
    pid_Kp : 12.723368
    pid_Ki : 0.489360
    pid_Kd : 82.701890
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
    hold_current : 0.7
    stealthchop_threshold : 0
    
    [tmc2209 stepper_y]
    tx_pin : PE4
    uart_pin : PE5
    interpolate : 1
    run_current : 1.8
    hold_current : 1.0
    uart_address : 3
    sense_resistor : 0.075
    microsteps : 16
    driver_sgthrs : 105
    stealthchop_threshold : 0
    
    [tmc2209 stepper_z]
    tx_pin : PE4
    uart_pin : PE5
    interpolate : 1
    run_current : 1.8
    hold_current : 1.0
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
    pid_Kp : 70.769227
    pid_Ki : 1.134122
    pid_Kd : 1103.999942
    min_temp : -200
    max_temp : 105
    
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
    shaper_freq_x : 60.200000
    shaper_type_y : 2hump_ei
    shaper_freq_y : 49.200000
    
    [resonance_tester]
    probe_points : 165,165,50
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
    mesh_max : 305,310
    probe_count : 7,7
    mesh_pps : 3,3
    algorithm : lagrange
    
    [auto_leveling]
    bed_mesh_temp : 60.0
    extruder_temp : 210.0
    extruder_wipe_z : -2.3
    move_speed : 30.0
    extrude_x : 66
    extrude_y : 0
    extrude_z : 15
    extrude_length : 80.0
    extrude_speed : 3.0
    extruder_pullback_length : 25.0
    extruder_pullback_speed : 30.0
    extruder_cool_down_temp : 140.0
    lifting_after_completion : 15.0
    
    [safe_z_home]
    home_x_position : 40.00000
    home_y_position : 280.00000
    speed : 150.0
    z_lift : 10
    z_hop : 15.0
    z_hop_speed : 8.0
    
    [probe]
    pin : PB8
    deactivate_on_each_sample : True
    x_offset : 0.0
    y_offset : 0.0
    z_offset : 0.000
    speed : 4.0
    final_speed : 4.0
    lift_speed : 8.0
    samples : 2
    sample_retract_dist : 2.0
    samples_result : weighted
    samples_tolerance : 0.1
    samples_tolerance_retries : 2
    move_after_each_sample : -2.0
    z_offset_adjust : 0.2
    
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
    device_model : Anycubic kobra 2 Plus
    print_size : 320*320*400mm
    
    [pid_calibrate]
    test_points : 100,100,5
    extruder_target_temp : 230
    heater_bed_target_temp : 60
    ```

??? info "Printer.cfg Of The Kobra 2 Max"  

    ```
    []
    [printer]
    kinematics : cartesian
    max_velocity : 500.000000
    max_accel : 10000.000000
    max_z_velocity : 16.000000
    max_z_accel : 3000.000000
    minimum_z_position : -20.000000
    square_corner_velocity : 15.000000
    
    [stepper_x]
    step_pin : PE1
    dir_pin : PE0
    enable_pin : !PE14
    endstop_pin : !PE8
    microsteps : 16
    full_steps_per_rotation : 200
    step_distance : 0.0125
    position_endstop : -5.000000
    position_max : 430.000000
    position_min : -5
    homing_speed : 30.000000
    second_homing_speed : 15.000000
    homing_retract_dist : 10
    virtrual_endstop : 0
    
    [stepper_y]
    step_pin : PG11
    dir_pin : PE11
    enable_pin : !PG8
    endstop_pin : !PE13
    microsteps : 16
    full_steps_per_rotation : 200
    step_distance : 0.0125
    position_endstop : -8.000000
    position_max : 430.000000
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
    position_endstop : 0.0
    position_max : 501.000000
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
    pid_Kp : 15.551640
    pid_Ki : 0.682089
    pid_Kd : 88.644347
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
    hold_current : 0.7
    stealthchop_threshold : 0
    
    [tmc2209 stepper_y]
    tx_pin : PE4
    uart_pin : PE5
    interpolate : 1
    run_current : 1.9
    hold_current : 1.0
    uart_address : 3
    sense_resistor : 0.075
    microsteps : 16
    driver_sgthrs : 105
    stealthchop_threshold : 0
    
    [tmc2209 stepper_z]
    tx_pin : PE4
    uart_pin : PE5
    interpolate : 1
    run_current : 1.8
    hold_current : 1.0
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
    pid_Kp : 68.748474
    pid_Ki : 0.868036
    pid_Kd : 1361.219778
    min_temp : -200
    max_temp : 105
    
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
    shaper_freq_x : 54.600000
    shaper_type_y : 2hump_ei
    shaper_freq_y : 49.400000
    
    [resonance_tester]
    probe_points : 215,215,50
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
    mesh_min : 19, 19
    mesh_max : 405,410
    probe_count : 7,7
    mesh_pps : 3,3
    algorithm : lagrange
    
    [auto_leveling]
    bed_mesh_temp : 60.0
    extruder_temp : 210.0
    extruder_wipe_z : -2.0
    move_speed : 30.0
    extrude_x : 394
    extrude_y : 0
    extrude_z : 15
    extrude_length : 80.0
    extrude_speed : 3.0
    extruder_pullback_length : 25.0
    extruder_pullback_speed : 30.0
    extruder_cool_down_temp : 140.0
    lifting_after_completion : 15.0
    
    [safe_z_home]
    home_x_position : 371.000000
    home_y_position : 361.000000
    speed : 230.0
    z_lift : 10
    z_hop : 15.0
    z_hop_speed : 8.0
    
    [probe]
    pin : PB8
    deactivate_on_each_sample : True
    x_offset : 0.0
    y_offset : 0.0
    z_offset : 0.0000
    speed : 4.0
    final_speed : 4.0
    lift_speed : 8.0
    samples : 2
    sample_retract_dist : 2.0
    samples_result : weighted
    samples_tolerance : 0.1
    samples_tolerance_retries : 2
    move_after_each_sample : -2.0
    z_offset_adjust : 0.2
    
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
    boot :0
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
    device_model : Anycubic kobra 2 Max
    print_size : 420*420*500mm
    
    [pid_calibrate]
    test_points : 100,100,5
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

??? info "Unmodifiable.cfg Of The Kobra 2 Plus" 

    ```
    [auto_leveling]
    target_spot_x : 64.300000
    target_spot_y : 339.200000
    
    [probe]
    z_offset_adjust : 0.2
    ```
    
??? info "Unmodifiable.cfg Of The Kobra 2 Max"  

    ```
    []
    [auto_leveling]
    target_spot_x : 394.200000
    target_spot_y : 440.100000
    
    [probe]
    z_offset_adjust : 0.2
    ```

---

### MOD: Modify Firmware And Settings  
Due to the great work of various community members, it is now possible to acess and modify the firmware as well as the settings.  
I'll list the solutions I'm aware of in the following - if you came across further solutions which aren't listed here, please reach out and let me know, so that I can add them here.  

**Thanks to everyone who took the time and effort to make this happen!**

!!! warning "Backup The Stock Settings And Be Careful About Changing Settings!"  

    Even though this should be a no-brainer, make a backup of the stock settings before attempting to change anything!  
    Besides, be very careful when changing any settings - changing the wrong settings could do harm and might result in a non-booting device!  
    If you don't know what you're doing, don't play around!  
    Don't assume the tools listed in the following are foolproof!   
    Read the Klipper documentation attentively to understand the settings and if in doubt, better don't change anything!

---

#### Various Tools For Modifying KobraOS
The following repository offers various tools for accessing, rooting and modifying the stock firmware.  
Please read the according descriptions at the repository about what can be done.  

[Anycubic Kobra 2 Series Tools](https://codeberg.org/hedgehogform/Anycubic-Kobra-2-Series-Tools) by [hedgehogform](https://codeberg.org/hedgehogform/)

---

#### Changing Settings 
Due to the work of [daksimpson](https://klipper.discourse.group/u/daksimpson) it's possible to change settings in the abovementioned files `printer.cfg` and `unmodifiable.cfg`.  
For this, no root access is necessary.  

**Warning:**  
**This way of changing settings in the `printer.cfg` still seems to work, but you have to know what you're doing! This solution is not foolproof at all! Changing the wrong setting can leave you with a bricked unit!**  
 
Please read [this post in the Klipper discourse group](https://klipper.discourse.group/t/printer-cfg-for-anycubic-kobra-2-plus-pro-max/11658/107) for further instructions!  

---

#### Custom Webserver

Tools and code which is needed to build a custom webserver: [Anycubic Kobra 2 Custom Webserver](https://github.com/AGG2017/ACK2-Webserver) by [AGG2017](https://github.com/AGG2017) 

---

#### Custom Webserver & Webinterface

Webinterface which uses the interface of the KobraOS and a custom webserver: [Kobra Unleashed](https://github.com/anjomro/kobra-unleashed) by [anjomro](https://github.com/anjomro)
    
---

#### Bedmesh  

For being able to transfer the data of the bedmesh to a graphical output, one has to get access to the according data. User [zhnecssd](https://github.com/zhnecssd) describes his way of getting the data and generate a bedmesh view from it [here](https://github.com/zhnecssd/3D-Printer-Bed-Leveling-Mesh-Visualizer).  

---

## Settings "Trigorilla B v1.0.x"
The specific settings of the machine are -due to the fact that it's closed source now- supposed to be 'unknown'.  


<!--
However, when the first `update.swu` file became available, it was possible to access and investigate the files `printer.cfg` and `unmodifiable.cfg`.  

??? info "Special Thanks To [lpi](https://github.com/lpi)!"  

    At this point I have to say a huge "Thank You!" to [lpi](https://github.com/lpi) for providing the content of the `update.swu` file to me!  
    I won't share the files, but I'll quote the content of the two config files here in the following.  
    However, if you want to access the files by your own, you can do so by unzipping the file `update.swu` and then mount the main directory with `squashfs`.  


There are two Klipper-specific config files that can be found:  

- the file `printer.cfg` which contains the pin assignments and specific settings for the Klipper configuration and
- the file `unmodifiable.cfg` which seems to contain additional settings for the auto leveling and the probe.

I won't share any of the files, but I'll quote the content of the two config files here in the following.

??? info "Files Of The Kobra 2 Plus & Max"  

    Just in case you own a Kobra 2 Plus or Max, you can find the content of the belonging files quoted in expandable textboxes below.   
    Besides that, if you own a Kobra 2 Plus, check out my comprehensive [Kobra2Plus Insights](https://1coderookie.github.io/Kobra2PlusInsights/) infosite instead.  
    
-->

---

### Printer.cfg
The following lists the content of the file `printer.cfg` for the "Trigorilla Spe **B** v1.0.5" mainboard of a Kobra 2 Pro.  
I'll leave the settings uncommented as this point, because we can't do anything to improve the settings anyway right now.  

```
[virtual_sdcard]
path: /useremain/app/gk/gcodes/

[mcu]
serial : /dev/ttyS3
restart_method : command
baud : 576000

[printer]
kinematics : cartesian
max_velocity:500             
max_accel:20000      
max_accel_to_decel:20000      
square_corner_velocity:20.0   
max_z_velocity:16            
max_z_accel:5000              
device_type: Anycubic Kobra 2 Pro
print_size: 220*220*250mm

[stepper_x]
step_pin : PA5
dir_pin : PA4
enable_pin : !PC3
microsteps : 16
full_steps_per_rotation:200  
rotation_distance :32
position_endstop :-5
position_min : -5
position_max : 230
homing_speed : 30
homing_retract_dist:10
second_homing_speed:15
endstop_pin : ^!PA6

[stepper_y]
step_pin : PC4
dir_pin : !PA7
enable_pin : !PC3
microsteps : 16
full_steps_per_rotation:200  
rotation_distance :32
position_endstop : -8
position_min : -8
position_max : 230
homing_speed : 30
homing_retract_dist:10
second_homing_speed:15
endstop_pin : ^!PC5

[stepper_z]
step_pin : PC9
dir_pin : !PC6
enable_pin : !PC3
microsteps : 16
rotation_distance :8
full_steps_per_rotation:200  
endstop_pin : probe:z_virtual_endstop
position_min :-12
position_max : 252
homing_speed: 8
homing_retract_dist:8
second_homing_speed: 4

[extruder]
max_extrude_only_distance : 100.0
step_pin : PC14
dir_pin : PC15
enable_pin : !PC3
microsteps : 16
full_steps_per_rotation:200  
rotation_distance :6.848
nozzle_diameter : 0.400
filament_diameter : 1.750
max_extrude_cross_section:50
heater_pin : PA1
sensor_type : NTC 100K MGB18-104F39050L32
sensor_pin : PC1
control : pid
pid_Kp : 12.206120
pid_Ki : 0.517208
pid_Kd : 72.016108
min_temp : -200
min_safe_temp : 185
min_extrude_temp : 170
max_safe_temp : 260
max_temp : 275
pressure_advance: 0.02

[heater_bed]
heater_pin : PA0
sensor_type : NTC 100K MGB18-104F39050L32
sensor_pin : PC0
control : pid
pid_Kp : 54.027
pid_Ki : 0.770
pid_Kd : 248.182
min_temp : -200
min_safe_temp : 45
max_safe_temp : 110
max_temp : 120 

[tmc2209 stepper_x]
uart_pin : PA3
uart_address : 3
run_current : 1.4
hold_current:0.7
sense_resistor: 0.0750
stealthchop_threshold :0
interpolate : True

[tmc2209 stepper_y]
uart_pin : PA3
uart_address : 1
run_current : 1.5
hold_current:0.8
sense_resistor: 0.075
stealthchop_threshold :0
interpolate : True

[tmc2209 stepper_z]
uart_pin : PA3
uart_address : 2
run_current : 1.2
hold_current:0.7
sense_resistor: 0.0750
stealthchop_threshold : 99999
interpolate : True

[tmc2209 extruder]
uart_pin : PA3
uart_address : 0
run_current : 0.8
hold_current:0.4
sense_resistor: 0.0750
stealthchop_threshold : 99999
interpolate : True

[probe]
pin : PB8
x_offset:24.0  
y_offset:13.35    
speed : 4.0
final_speed : 4.0
lift_speed : 8.0 
samples: 2 
sample_retract_dist: 15 
samples_result: weighted 
samples_tolerance: 0.1 
samples_tolerance_retries:2 

[bed_mesh]
speed: 60
horizontal_move_z:15
mesh_min: 19,19
mesh_max: 205,210
probe_count: 5,5    
mesh_pps: 3,3
algorithm: lagrange

[safe_z_home]
home_xy_position: 40,207    
speed: 150
z_hop: 5 
z_hop_speed: 8.0

[verify_heater extruder]
max_error: 120
check_gain_time:30
hysteresis: 5
heating_gain:1

[verify_heater heater_bed]
max_error: 120
check_gain_time:300
hysteresis: 5
heating_gain:1

[controller_fan controller_fan]
pin : PB10
fan_speed : 1

[heater_fan extruder_fan]
pin : PB2

[custom_temperture_fan]

[fan]
pin : PB1

[output_pin power_pin]
pin:PB4
value:1
shutdown_value:0

[pid_calibrate]
homing_first: 1
move_xy_position: 50,50
move_z_up: 5
fan_speed : 1

[lis2dw12]
spi_speed: 5000000
cs_pin: PB12
spi_software_sclk_pin:PB13
spi_software_mosi_pin:PB15
spi_software_miso_pin:PB14
rate:400
axes_map: z,x,y

[lis2dw12 bed]
spi_speed: 5000000
cs_pin: PD2
spi_software_sclk_pin:PC12
spi_software_mosi_pin:PC10
spi_software_miso_pin:PC11
rate:400
axes_map: x,y,z

[resonance_tester]
accel_chip_x: lis2dw12 
accel_chip_y: lis2dw12 bed
probe_points:110, 110, 20  
min_freq : 1
max_freq : 140
accel_per_hz : 150
test_freq_start: 70
test_freq_end: 80

[pause_resume]
pause_position: 200,200
z_up: 10

[filament_switch_sensor filament_sensor]
pause_on_runout: False
switch_pin: ^!PC13
[buttons] 

[leviQ2]
base_button_position: 60,240
wiping_position: 20.0,-5.0 
button_push_down_count: 2 
platform_offset: 25     
bed_temp: 60           
extru_temp: 210             
extru_end_temp: 140    
to_zero_speed: 100         
extru_out: 50
extru_out_speed: 3        
extru_in: 5
extru_in_speed: 10        
button_push_down: 5        
calibration: 0            
z_up: 15                
z_offset_factor: 0.13     
leviQ2_pin: PA8

[ota]
fw_max_size: 40960 
fw_sector_size: 8192 
fw_ota_sector_offset: 22 

[gcode_arcs]
resolution:1.0

[input_shaper]
shaper_freq_x: 72.2
shaper_freq_y: 58.0
shaper_type_x: mzv
shaper_type_y: 2hump_ei
```

---


### MOD: Rinkhals (Modified KobraOS)  
[jbatonnet](https://github.com/jbatonnet) came up with a modded KobraOS of the Kobra3 called [Rinkhals](https://github.com/jbatonnet/Rinkhals), which seems to also work fine with the Kobra 2 Pro/Plus/Max printers that use the newer board revisions, labeled as "Spe **B** v_1.0.x".  
Rinkhals allows you to e.g. access your printer via your local network and the regular Mainsail or Fluidd UI, change settings of the `printer.cfg`, create and display bedmeshes etc. Basically you'll have a KobraOS without the limitations of the KobraOS.    

!!! warning "Only Suitable For Trigorilla B v1.0.x Boards!"  

    Before attempting to flash and use the modified KobraOS, make sure to check which kind of mainboard your printer is using!  
    It is crucial that you have a type "Spe B" board, please see the chapter "Mainboard" for further information!  

---


[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/U6U5NPB51)  

