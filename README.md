# Updated Commit Notes
# BTT PI ADXL SPI issue resolution
BTT PI issues with ADXL345 V1.0 resolved thanks to Reddit post by kimmy2000 (https://www.reddit.com/r/BIGTREETECH/comments/14m222t/btt_pi_and_btt_adxl345_settings/) 

printer.cfg changes:
- [mcu host] serial: /tmp/klipper_host_mcu
- [adxl345] #BTT PI
- cs_pin: host:gpio67
- spi_bus: spidev0.0
- axes_map: x,y,z
- [resonance_tester]
- accel_chip: adxl345
- accel_per_hz: 70 probe_points: 117.5,117.5,10
  <br/>
In the "boardenv.txt" of the Pi on the SD found in the /boot folder of the BTT Pi, you need to uncomment only "overlays=spidev0_0"
<br/>
BTT PI Cable to ADXL345:

- Black GND
- Red VCC
- Yellow CS
- White SDO
- Blue SDA
- Green SCL

# Updated CFG
This config is basic but currently includes the  Start print, end print and cancel print macro's. 
<br/>
PID, Rotation, Pressure advance and linear advance should still be done for you machine but this is a start.

# Easy life savers
- https://www.klipper3d.org/G-Codes.html?h=pid#pid_calibrate_1 #Pretty much universally the first step to tuning.
- https://www.klipper3d.org/Rotation_Distance.html #Rotation distance is Esteps for klipper. Mine are tight but every machine is slightly different.
- https://www.klipper3d.org/Measuring_Resonances.html #You will want to do reasonances after basics are done
- https://ellis3dp.com/Print-Tuning-Guide/ #Tuning guide to end most for Klipper alternatively:
- https://teachingtechyt.github.io/calibration.html#intro #This is another terrific calibration tool.
- https://alex.doud.io/fluidd-klipper-debian/ #Great for a basic guide to slam klipper on a laptop running debian

# Slicer 
Start G Code:
- M104 S0 
- M140 S0
- START_PRINT EXTRUDER=[first_layer_temperature[initial_extruder]] BED=[first_layer_bed_temperature] HEIGHT=[first_layer_height]
<br/>
End G Code:

- END_PRINT
<br/>
#Above needs to be added into your slicer of choice for the start and end macro's to do their job correctly.
<br/>
# Youtube Worth checking out on this:

- https://youtu.be/cAxEIdThDiQ?si=I3Z0m94othnu-e7q
- https://youtu.be/DmD5oh8iso8?si=WDGXRdOhdEx7bUyb
- https://youtu.be/EJapxNsntsQ?si=MsFeEQvg44s9uGAh
- https://youtu.be/h6g8DoTc7ys?si=VUWiUC7gbaxPZjz_
- https://youtu.be/hMG5GcRqkA4?si=Q6ng8Qcs3FRn4-Uy




# Addons and configuration for 3D printers

#### Installation Tutorial Video here: https://youtu.be/cAxEIdThDiQ 

#### Anycubic i3 mega S Klipper fast printing (first layer on 200 mm/s speed): https://youtu.be/GtIsCP1_Cyg 

### [Klipper configuration file for Anycubic i3 mega S](https://github.com/widapro/3d-printers/blob/master/anycubic-i3-mega-s/klipper/printer.cfg)
This config file contains settings of all printer pins (steppers, sensors) for Anycubic i3 mega S in the factory configuration

### Anycubic Mega S with TMC2208 stepper drivers with stock wire orientation (https://github.com/JJShankels/3d-printers/JJ_Anycubic_Mega_S_TMC2208_Klipper_printer.cfg)
This contains code for 3D Touch or manual mesh

### Install tested with FluiddPi (https://github.com/cadriel/FluiddPI)

Klipper firmware should be compiled for the **atmega2560**

 Config file includes
  - Configuration for **2208(2209)**, standard cable orientaion, drivers
  - Mesh bed leveling: **BLtouch** (commented out)
  - **Manual meshed bed leveling** (commented out)
  - **'virtual_sdcard'** for fast printing without gaps
  - Beeper through **M300** gcode
  - Pause/Resume through **M600** for filament change
  - **Start_Print/End_Print** g-code can be added to your slicer softwrae

 Home position is determined by 3DTouch. **Z limit switches are not used**.

 The latest version of the config reference is also available online at: [https://www.klipper3d.org/Config_Reference.html](https://www.klipper3d.org/Config_Reference.html)
<br />
<br />
<br />
**!!! Do not forget to check your configuration for: !!!**
* step_distance
* nozzle_diameter
* pressure_advance
* serial
* [bltouch]
* [virtual_sdcard]
<br />
<b>!!!</b> Also important to follow all config check from this manual before start printing: https://www.klipper3d.org/Config_checks.html
<br />
<hr />
Useful documentation for slicer/printer (not special for Klipper) calibration: https://teachingtechyt.github.io/calibration.html#intro
