# Apple2-IO-RPi
Apple II expansion card using a Raspberry Pi for I/O

![Image of Board](/Hardware/Apple2IORPi.jpg)

## Purpose
The purpose of this project is to provide I/O for an Apple II series 8 bit computer via a Raspberry Pi Zero W which is powered by the Apple II expansion bus. Initially this is storage via virtual ProDOS compatible drive. There is also support for executing Linux commands from the Apple II via a rudimentary console. Next might be adding virtual serial card support over wifi. Future enhancements could use the RPi for more complex processing as per request from the Apple II. For example, the Apple II could request a web page or application and the RPi could calculate this in Apple II hi-res graphics mode and send the image data back to the II for display purposes.

## Project Status
This is an early stage project. Currently four prototype revisions have been assembled and tested. It is now possible for the Apple II to boot from and write to a virutal hard drive image stored on the RPi in any slot and execute simple commands on the RPi via an Apple II application. The code has no error handling or tests yet and is incomplete.

## Roadmap
1. DONE - Build initial prototype that reads/writes virtual hard drive
2. DONE - Create firmware to make the card a bootable device
3. DONE - Fix board with updated second prototype PCB
4. DONE - Add ProDOS clock support
5. DONE - Add simple RPi command execution (does not keep context between commands yet)
6. DONE - Create new schematic/PCB with faster data transfera
7. DONE - Add hardware support for in-system firmware updates
8. DONE - Add multi-page firmware support
9. DONE - Add boot menu
10. DONE - Add RPi command in firmware
11. Add firmware update software
12. Add proper ProDOS clock driver (currently just directly sets values on block reads)
13. Add directory context to RPi command execution 
14. Add full terminal emulation 
15. Add support for direct file read/write without drive image
16. Add web service call support
17. Proxy VNC connection, rendering as Apple II compatible graphics

## Setup
1. Have PCBs made from the gerber and drill files in the Hardware folder or email me for a board
2. Solder chips, header and capacitors in place
3. Attach Raspberry Pi Zero W facing outward from the card
4. Install Raspberry Pi OS on microSD card https://www.raspberrypi.org/software/
5. Configure wifi in boot/wpa_supplicant.conf https://howtoraspberrypi.com/how-to-raspberry-pi-headless-setup/
6. Add empty ssh file boot (for ssh access over wifi)
7. Put microSD card in the RPi
8. Install the expansion card into the Apple II
9. Power on the Apple II
10. Update firmware with utility (not written yet) or use EPROM programmer
11. sudo apt install git golang
12. git clone https://github.com/tjboldt/Apple2-IO-RPi.git
13. cd Apple2-IO-RPi
14. go get
15. go build
16. ./Apple2-IO-RPi Apple2-IO-RPi.hdv
18. Setup the Driver as a service or to autostart via cronjob (crontab -e then add the line @reboot /home/pi/Apple2-IO-RPi/RaspberryPi/Apple2-IO-Rpi /home/pi/Apple2-IO-RPi/RaspberryPi/Apple2-IO-RPi.hdv > /home/pi/Apple2-IO-RPi/RaspberryPi/Apple2-IO-RPi.log)

## Similar Project
If you prefer having Apple II peripherals control a Raspberry Pi rather than simply using the Raspberry Pi to provide storage, network access and processing to the Apple II, have a look at David Schmenk's excellent [Apple2Pi](https://github.com/dschmenk/apple2pi) project. 
