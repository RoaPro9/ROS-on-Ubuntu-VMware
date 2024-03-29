# ROS-on-Ubuntu-VMware-For-windows
A walkthrough on installing ROS kinetic on Ubuntu 16.
### <ins>Steps:</ins>
* Install VMware.
* Download Ubunto.
* Create your new VM.
* Setup.
* Install ROS kinetic.
* Lunch ROS.

## <ins> Install VMware. </ins>

### What is VMware Workstation pro?
VMware Workstation is a line of Desktop Hypervisor products which lets users run virtual machines, containers and Kubernetes clusters.

### How do VMware Workstation pro work?
VMware Workstation workby using special functions in modern 64-bit x86 CPUs to create fully isolated, secure virtual machines that encapsulate an operating system and its applications. The VMware virtualization layer maps physical hardware resources to a virtual machine's virtual resources, so each virtual machine has its own CPU, memory, disks, and I/O devices, as well as the full equivalent of a standard x86 machine. VMware Workstation installs onto the host operating system and provides broad hardware support by inheriting device support from the host.

### Download the VMware Workstation pro for<ins> windows</ins> link:
https://www.vmware.com/go/getworkstation-win

### Download the VMware Workstation pro for<ins> Linux</ins> link:
https://www.vmware.com/go/getworkstation-linux




## <ins> Download Ubunto: </ins>
Ubuntu Desktop is a Linux distribution developed by Canonical, and it’s one of the most popular distributions, thanks to its ease of use. It’s also one of the top choices for people who are getting started with Linux. 

### Download The Ubuntu distribution using this link:
https://ubuntu.com/download


## <ins> Create your new VM.</ins>

Open VMware and then Click on "Create a New Virtual Machine" 

![image](https://user-images.githubusercontent.com/70070721/177861451-b49c20a0-5c7e-4d88-a62e-dbcfc1c24315.png)

Click on 'Custom (Advanced) then on 'Next'

![image](https://user-images.githubusercontent.com/70070721/177862428-aa969d7c-1e63-4c98-aeba-c8cdf4721a49.png)

Choose 'Workstation 16' for the Hardware then on 'Next'

![image](https://user-images.githubusercontent.com/70070721/177862435-70469cea-de5a-4de8-9b0a-c0ddcbb9ab5e.png)

Make sure to choose the right Ubunto Image in our case the ubunto-16 then on 'Next'

![image](https://user-images.githubusercontent.com/70070721/177862438-7ab864e1-1b32-446e-a056-71914dab06bf.png)

Enter your personal information then on 'Next'

![image](https://user-images.githubusercontent.com/70070721/177865237-47d2e787-9209-42b0-9427-1f3dc2fe89ec.png)

![image](https://user-images.githubusercontent.com/70070721/177865357-61fc0b76-ec49-47df-975e-c1c3298afa7b.png)

For the processors set 2 for each to get total of 4 processors  then on 'Next'

 ![image](https://user-images.githubusercontent.com/70070721/177865388-76bb05e2-8309-4ffe-9228-9d56d41b83e9.png)
 ![image](https://user-images.githubusercontent.com/70070721/177865639-25dd1e3a-3492-4ae2-9800-3c79cf58cf0f.png)
 
Make sure to choose 'Use network address translation (NAT)' so you can connect to your computer network

![image](https://user-images.githubusercontent.com/70070721/177865683-a6cc5c25-1995-4c24-b03d-fa3560b036ac.png)

Select I/O Controller Type 'LSI Logic' 

![image](https://user-images.githubusercontent.com/70070721/177866136-109ccc84-e78e-4d18-9345-bedd39fab2cd.png)

Select Disk Type 'SCSI' 

![image](https://user-images.githubusercontent.com/70070721/177866139-8b23d6aa-1de8-4722-ba0a-ddf45214c4e0.png)

Selecta  Disk 'creat a new virtual disk' 

![image](https://user-images.githubusercontent.com/70070721/177866141-1c1405fb-f81b-4a4c-a890-b46d91b3c598.png)

Secify the disk capacity 'split virtual disk into multiple file'

![image](https://user-images.githubusercontent.com/70070721/177866142-77ce909d-26e3-421f-b33f-cb82b7cf0526.png)

Click on 'Next'

![image](https://user-images.githubusercontent.com/70070721/177866149-d113a64a-ae01-49d7-9685-d838238f6455.png)

Finally Click on 'Finsh'

![image](https://user-images.githubusercontent.com/70070721/177866156-cbe3fd1e-c34a-427d-b433-8ceebc6765ac.png)


For now, you can wait until all files are set. It may take a few minutes, don't worry!

![image](https://user-images.githubusercontent.com/70070721/177867882-aca8bb28-6c94-42be-a9c2-ea3e85ba02b6.png)


## <ins> Setup.</ins>
Sign in to your account with the same password you used previously.
Open your Terminal to start updating the apt
```console
sudo apt-get update
```
```console
sudo apt-get upgrade
```
```console
sudo apt install build-essential dkms linux-headers-$(uname -r)
```
it wil ask you to enter either Y/N , Enter 'Y'

Then powr off your VM ,
Click on 'Edit Virtual Machine Settings' on the right
![image](https://user-images.githubusercontent.com/70070721/177869969-1fcd27fa-00f2-43dd-b77d-d60068d3772e.png)

then Click on CD/DVD 2 (SATA) then Choos 'Use ISO image file' then the ubunto 16 image
![image](https://user-images.githubusercontent.com/70070721/177870070-de6d815d-541b-45e6-8571-9d513715aef3.png)

then Click on CD/DVD (SATA) then Choos 'Use ISO image file' then the ubunto 16 image then on 'Ok'

![image](https://user-images.githubusercontent.com/70070721/177870142-9ba076b5-b4de-4372-96b6-aa0aec595ffb.png)

## <ins> Install ROS kinetic.</ins>
### Installation
ROS Kinetic ONLY supports Wily (Ubuntu 15.10), Xenial (Ubuntu 16.04) and Jessie (Debian 8) for debian packages.
 
### Setup your sources.list


```console
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

```
### Set up your keys

if you haven't already installed curl
```console
sudo apt install curl 
```
```console
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -

```
### Installation
First, make sure your Debian package index is up-to-date:


```console
sudo apt-get update
```
Desktop-Full Install: (Recommended) : ROS, rqt, rviz, robot-generic libraries, 2D/3D simulators, navigation and 2D/3D perception
```console
sudo apt-get install ros-kinetic-desktop-full

```
To find available packages, use:
```console
apt-cache search ros-kinetic


```
### Environment setup
It's convenient if the ROS environment variables are automatically added to your bash session every time a new shell is launched:

```console
echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc

```
```console
source ~/.bashrc

```
If you have more than one ROS distribution installed, ~/.bashrc must only source the setup.bash for the version you are currently using.

If you just want to change the environment of your current shell, instead of the above you can type:


```console
source /opt/ros/kinetic/setup.bash

```
If you use zsh instead of bash you need to run the following commands to set up your shell:


```console
echo "source /opt/ros/kinetic/setup.zsh" >> ~/.zshrc
source ~/.zshrc
```
### Dependencies for building packages
Up to now you have installed what you need to run the core ROS packages. To create and manage your own ROS workspaces, there are various tools and requirements that are distributed separately. For example, rosinstall is a frequently used command-line tool that enables you to easily download many source trees for ROS packages with one command.

To install this tool and other dependencies for building ROS packages, run:
```console
sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential
```
#### Initialize rosdep
Before you can use many ROS tools, you will need to initialize rosdep. rosdep enables you to easily install system dependencies for source you want to compile and is required to run some core components in ROS. If you have not yet installed rosdep, do so as follows.
```console
sudo apt install python-rosdep

```
With the following, you can initialize rosdep.



```console
sudo rosdep init
rosdep update
```
### Build farm status
Create the catkin root and source folders:
```console
sudo apt-get install ros-kinetic-catkin

mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/
```
Configure the catkin workspace by issuing a first “empty” build command:
```console
catkin_make
cd ~/catkin_ws/src

```



## <ins> Lunch ROS.</ins>
Launching ROS on a project from @Smart_methods for a robotic arm , Clone Github repository. 
```console
git clone https://github.com/smart-methods/arduino_robot_arm.git 
```
Check the dependencies:
```console
cd ~/catkin_ws

rosdep install --from-paths src --ignore-src -r -y
```
```console
sudo apt-get install ros-kinetic-moveit

sudo apt-get install ros-kinetic-joint-state-publisher ros-kinetic-joint-state-publisher-gui

sudo apt-get install ros-kinetic-gazebo-ros-control joint-state-publisher

sudo apt-get install ros-kinetic-ros-controllers ros-kinetic-ros-control
```

Finally, update your .bashrc script with the information about the new workspace:
```console
sudo nano ~/.bashrc
```

at the end of the (bashrc) file add the follwing line
Make sure to change the username
```console
(source /home/roamohamed/catkin_ws/devel/setup.bash)
```
then 
ctrl + o
```console
source ~/.bashrc

```
The final command to finally launch the project
```console
roslaunch robot_arm_pkg check_motors.launch

```
![image](https://user-images.githubusercontent.com/70070721/177879052-3e528fea-1509-4f44-9b6f-4624328cef66.png)



