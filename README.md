# ECE 6460 Examples Repository - Fall 2023

This repository contains the instructions for setting up a PC with Ubuntu 20.04 and ROS Noetic to follow along with the ECE 6460 lecture videos and implement the corresponding programming homework assignments.

## Computer Setup Instructions

There are two recommended options to get a computer set up properly for the course.
The first is to natively install Ubuntu 20.04 on either an empty hard drive, or on a separate partition of a hard drive.
The second is to install VMWare Player in an existing Windows installation and then set up a virtual machine (VM) with Ubuntu 20.04 installed on it.
After setting up the operating system, all the software required for the class can be installed using a provided script.

### Operating System Setup

Regardless of whether a native installation or virtual machine is selected, the Ubuntu installation disk image needs to be downloaded.
To do so, download the latest desktop image of Ubuntu version 20.04 LTS from Ubuntu's website: [https://releases.ubuntu.com/20.04/](https://releases.ubuntu.com/20.04/). After the download is complete, then either use it to create a VM or create a USB installation drive to install it natively.

To install natively:
- Create a bootable USB flash drive to install Ubuntu by following the instructions found here: [https://ubuntu.com/tutorials/create-a-usb-stick-on-windows](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows).
- Restart the computer and boot from the flash drive.
- Install Ubuntu!  This step depends on whether you're installing on a separate partition or on the entire hard drive.  If you want to install Ubuntu next to Windows, you can use the Windows disk management utility to resize your existing Windows installation and create a new, second partition.  Ubuntu can then be installed on this new partition.  However, be careful when doing this, and back up any important files just in case something happens to your original Windows installation.

To set up a virtual machine:
- Download and install VMWare player for Windows from [https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html](https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html).
- Create a VM by following along with this walkthrough video: [https://youtu.be/H5p4uQ-kdGw](https://youtu.be/H5p4uQ-kdGw).
The video depicts setting up an Ubuntu 18.04 virtual machine, but everything works the same for Ubuntu 20.04. Just be sure you are using a 20.04 desktop image file instead of the one you see in the video.
- During the setup process, you will have to add this line to the bottom of your `.bashrc` script:
```
export SVGA_VGPU10=0
```

### Software Setup

Once the operating system is set up properly in a native installation or VM, it is time to set up the software. This includes installing ROS, Git, the Visual Studio Code IDE, and binaries for the supporting code that will be used during the course.

To do this, first download the script that automates the software installation, and save it somewhere in your Ubuntu filesystem:
[software_setup_ece6460.bash](https://onedrive.live.com/download?resid=B7FCF91CEE77A2BE%219351&authkey=!AFOCKGNbNQr5TXM)

Then, open a terminal with `Ctrl-Alt-T`, `cd` to the location where `software_setup_ece6460.bash` is saved, and enter the following commands to first make the script executable, and then actually run it:

```
chmod +x software_setup_ece6460.bash
./software_setup_ece6460.bash
```
This will take a while to complete and require downloading a fair amount of packages. Once it is done though, reboot the PC and everything should be ready!

## Running the Demo Programs

The following demo programs preview some of the material covered during the course, and can also be used to test a PC's setup after installing the OS and course software.
To run the demos that use recorded data, you will have to download the referenced bag files from the [OneDrive Folder](https://1drv.ms/f/s!Ar6id-4c-fy3yDMMXjcEX7lZRzkx?e=J0cv1t)

### ACC and Programmed Route Following

Open a new terminal and enter the following command:

```
roslaunch avs_lecture_launch sim_launch.launch
```

### Lane Keeping

Open a new terminal and enter the following command:

```
roslaunch avs_lecture_launch lane_keep_sim.launch
```

### OU Campus Autonomous Driving Playback

Open a new terminal and start up the software:

```
roslaunch avs_lecture_launch offline_launch.launch
```

Then open another terminal, change the directory to where you put the `campus_drive_083019.bag` file, and then enter the following command:

```
rosbag play --clock campus_drive_083019.bag
```

### Camera/LIDAR Overlay
Open a new terminal and start up the software:

```
roslaunch avs_lecture_camera_lidar_fusion camera_lidar_fusion.launch
```

Then open another terminal, change the directory to where you put the `cepton_camera_fusion.bag` file, and then enter the following command:

```
rosbag play --clock cepton_camera_fusion.bag
```
