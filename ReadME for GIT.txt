READ ME
This is an updated fork of JJ shankles original config made to suit a more barebones configuration. 
Please note this is to be used at your own risk as any random firmware online is.
Updated to make more readable, stripped out auto bed levelling and updated pins to new naming convention.
Updated CFG with Linear Advance results, BTT PI ADXL settings, temp guide to BTT PI and added in some very basic macros.







# Updated Commit Notes
#BTT PI ADXL SPI issue resolution
BTT PI issues with ADXL345 V1.0 resolved thanks to Reddit post by kimmy2000 (https://www.reddit.com/r/BIGTREETECH/comments/14m222t/btt_pi_and_btt_adxl345_settings/) 

printer.cfg changes:
[mcu host] serial: /tmp/klipper_host_mcu
[adxl345] #BTT PI
cs_pin: host:gpio67
spi_bus: spidev0.0
axes_map: x,y,z
[resonance_tester]
accel_chip: adxl345
accel_per_hz: 70 probe_points: 117.5,117.5,10
In the "boardenv.txt" of the Pi on the SD found in the /boot folder of the BTT Pi, you need to uncomment only "overlays=spidev0_0"

#Updated CFG
This config is basic but currently includes Start print, end print and cancel print macro's 
PID, Rotation, Pressure advance and linear advance should still be done for you machine but this is a start.

# Easy life savers
https://www.klipper3d.org/G-Codes.html?h=pid#pid_calibrate_1 #Pretty much universally the first step to tuning.
https://www.klipper3d.org/Rotation_Distance.html #Rotation distance is Esteps for klipper. Mine are tight but every machine is slightly different.
https://www.klipper3d.org/Measuring_Resonances.html #You will want to do reasonances after basics are done
https://ellis3dp.com/Print-Tuning-Guide/ #Tuning guide to end most for Klipper alternatively:
https://teachingtechyt.github.io/calibration.html#intro #This is another terrific calibration tool.
https://alex.doud.io/fluidd-klipper-debian/ #Great for a basic guide to slam klipper on a laptop running debian

Start G Code:
M104 S0 
M140 S0
START_PRINT EXTRUDER=[first_layer_temperature[initial_extruder]] BED=[first_layer_bed_temperature] HEIGHT=[first_layer_height]
End G Code: 
END_PRINT
#Above needs to be added into your slicer of choice for the start and end macro's to do their job correctly.



    https://youtu.be/cAxEIdThDiQ?si=I3Z0m94othnu-e7q
    https://youtu.be/DmD5oh8iso8?si=WDGXRdOhdEx7bUyb
    https://youtu.be/EJapxNsntsQ?si=MsFeEQvg44s9uGAh
    https://youtu.be/h6g8DoTc7ys?si=VUWiUC7gbaxPZjz_
    https://youtu.be/hMG5GcRqkA4?si=Q6ng8Qcs3FRn4-Uy
