# piopengl1
c make build
google2:"raspberry pi opengl example" && "raspberry pi opengl es"

1.sudo apt-get install git cmake libglm-dev

from trying https://github.com/peepo/openGL-RPi-tutorial
2. https://developer-tech.com/news/2020/feb/03/raspberry-pi-4-opengl-es-conformant-vulkan-incoming/ read
3.https://www.cnx-software.com/2020/02/03/raspberry-pi-4-opengl-es-3-1-conformant-vulkan-drivers/ Vulkan 1.1 is available today with specification open to anyone, as well as conformance tests, and open source tools such as LunarG SDK and validation/debug/simulation/assistant layers. AMD, Arm, Imagination, Intel, NVIDIA, and Qualcomm are all said to have conformant Vulkan 1.1 drivers now. More details on Vulkan page, including links to the specifications themselves, and you may also want to read the Vulkan 1.1 presentation for a quick overview of the new Vulkan 1.1, and progress made by Vulkan in general.
4. https://benosteen.wordpress.com/2012/04/27/using-opengl-es-2-0-on-the-raspberry-pi-without-x-windows/
5.(opional since requires upgrade.. and can get sourcecode of ioquake3 from github.. here https://github.com/raspberrypi/quake3 ) https://www.raspberryconnect.com/projects/35-games/142-trying-out-opengl-on-raspberry-pi-3 TRY ioquake3 !
Activating OpenGL on the Raspberry Pi 3
To use the OpenGL drivers you will need the latest version of the Raspbian operating system. This can either be downloaded from the Raspberry Pi foundation using the Noobs SD card installer or if you are running Raspbian Jessie you can upgrade your current installation to bring it up to date.

Noobs or the latest Raspbian image can be downloaded from here

To update and existing copy of Raspbian Jessie enter the following commands into Terminal:

sudo apt-get update
sudo apt-get upgrade

 

I would recommend you use a clean installation of Noobs while trying out OpenGL software as it allows you to easily edit the Config.txt file and deactivate the drivers if your display goes blank. Just put a # infront of the entry for dtoverlay=vc4-kms-v3d

By default the OpenGL drivers are switched off as they are in testing and can cause problems with the graphics of the desktop and possibly use of the camera.

Before you activate the drivers install the graphics librarys with the command

sudo apt-get install mesa-utils

Once installed I run the glxgears program from Terminal. This shows 3 gears moving but the colours were flashing. The display shows they were running at 38 frames per second.

To activate the OpenGL drivers you need to run raspi-config from a terminal window as this option is not available in the version in the menu.

Enter the comand: sudo raspi-config
Select 7 Advance Options
A6 GL Drivers
You can now choose between

GL (Full KMS) Desktop Drivers
GL (Fake KMS) Desktop Driver
Legacy - Non-GL Driver
KMS refers to Kernel Mode-Setting,which should make the driver more efficient with better error handling, but I seem to have better compatibility with the Fake driver. The Legacy option will revert the Raspberry Pi's back to the standard graphics driver mode.

Select a driver and then OK.

You will also want to increase the memory split to at least 256mb. So choose Advance Options again and then Memory Split and enter 256 in the box and then OK.

OK then Finish and Reboot.

As the drivers are still in development there may still be a few odd things happen such as the screen going black for a second or two intermittently and having to login when the desktop loads.

Once the Desktop loaded I went into Terminal and run the glxgears program. If you get 3 gears running without the colours flickering then OpenGL is working. The display says it was running at 60 frames per second.

 

 Testing OpenGL Software
I have picked out a few games and one program that use OpenGL for my initial test on a Raspberry Pi 3, but I plan to try more. These were:

Stellarium - an Astronomy program
NeverBall - a puzzle game
NeverPutt - mini Golf game
glTron - Tron style Cycle game
OpenArea - first person shooter game
Super Tux Kart - a Mario Kart style game
Frets on Fire - a Guitar Hero style game
