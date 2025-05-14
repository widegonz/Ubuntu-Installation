# Ubuntu-Installation

This repository is to help you know how to install Ros2 Humble.

## 0. Content
  1. PC Setup
  2. ROS Installation
  3. References

## 1.  PC Setup
# En las imágenes aparecerá Ubuntu 18 pero es el mismo proceso para instalar ubuntu 22.04
# Installing Ubuntu 22.04 version and ROS Humble
Ubuntu Installation: https://youtu.be/wIj7sHK0SkQ?si=t1UHW8nSEUa0G_Qe
## Create a bootable Ubuntu USB
  1. Click in the given link, then scroll down until the "Past releases and other flavours" section. Right there you will click on 22.04 version. Finally, download the Desktop Image file and remember the location of it. 
https://www.releases.ubuntu.com/22.04/
  2. Download Rufus, a free and open source USB stick writing tool. (https://rufus.ie/) You may find some versions, pick the standard and newest one. 
  3. Launch rufus and set like any of the images below. Then click on the START button and the download of the ISO file on the USB will begin. (Note: The difference between the two images is in the Partition Scheme, you should use MBR if your computer was made before 2010, otherwise, you should use GPT).

![image](https://github.com/user-attachments/assets/e5ade336-5928-41d8-a010-1ce1457fe477)

![image](https://github.com/user-attachments/assets/61be5d51-1c54-4a1d-a8a2-c614d0f26f5a)


## Make a partition for Ubuntu

  1. Open the command prompt (cmd) and type diskmgmt.msc
  2. Choose the storage in the Volume Column that will be used to make the partition to store Ubuntu OS and right click on it, then press Shrink Volume button.

![image](https://github.com/user-attachments/assets/49e1d836-2f6d-4ae6-bbaf-20f2d9673bd6)


  3. Assign the appropriate amount of storage for Ubuntu. Ubuntu's page recommend at least 50 GB, and you also should think about the programs you will use in that OS.
  4. Click on the Shrink button.

![image](https://github.com/user-attachments/assets/b542b080-7cda-4df2-ae56-673ae9da7137)


  5. After that, you can check the partition was made, and it does not have any number, and it is unallocated.

![image](https://github.com/user-attachments/assets/2d1f5a20-95b5-4162-bf7d-614f5e88a60a)


## Install Ubuntu

  1. You will have to restart or reboot your PC or laptop with the USB with Ubuntu ISO plugged in.
  2. Once your computer is getting started, you need to press F12 to access to the BIOS. If your computer does not access to the BIOS with F12, please look for the correct button needed to be pressed.
  3. When BIOS is open, in the left hand section, you will see the bootable devices that the computer recognize. Please select the USB.
  4. Ubuntu will boot, and you will see an icon that says "Install Ubuntu", select that button.
  5. After that, you have to set some feauters of the system such as the language. The following images show those easy steps. Note: It is recommended to click the Normal Installation option. 
  6. After select the Normal installation, it will ask you the Installation Type, you have to select the option "Something else" which allows you to use the previous made partition.

![image](https://github.com/user-attachments/assets/18bc02bf-06e5-4d9a-b719-6dc802e26027)

![image](https://github.com/user-attachments/assets/5642eb49-ff5c-467d-a58a-49b915c75556)

![image](https://github.com/user-attachments/assets/f56a3bc4-ff86-42f4-bcbe-14b01302812d)

![image](https://github.com/user-attachments/assets/193cde16-4bf8-44b9-b92b-468bf4d4ea38)

![image](https://github.com/user-attachments/assets/32ec72cc-3470-4bf2-b903-56c0b9229e98)

  7. In the displayed list, look for the the "empty space" or "free space". You will know which one you should select based on the size of the partition you made, because it will have an approx size of the partition made.
  8. Then, click on the ‘+’ button under the list.

![image](https://github.com/user-attachments/assets/dad3482e-cc69-4af3-b66b-c087e79a40b5)


  9. A pop up window will apper, do not change the size, select the option "logical", and the option "The point where this space starts", and in the last one, look for the "/" option in the desplegable list.
  10. Then click on the Okay button, and that pop up window will close.
  11. Select the storage you just made, then select the Install now button, and click on Continue in the pop up window. 

![image](https://github.com/user-attachments/assets/ef7e39ec-a94c-4d3c-b9ed-a47ff1da92f2)
![image](https://github.com/user-attachments/assets/589e3e0f-149e-44ce-81df-ddc6c9a1155e)


  12. You will need to select your country and time zone, and complete the blank spaces. After that, click on Continue and Ubuntu will installed.
  13. Finally, restart your PC.
![image](https://github.com/user-attachments/assets/de884502-d309-4dc9-ad59-a80226a09897)
![image](https://github.com/user-attachments/assets/ff6f17ee-719b-4082-afc6-4b1b97bd5f65)
![image](https://github.com/user-attachments/assets/b151c38a-c157-48e8-a9a3-16133ff9d53a)
![image](https://github.com/user-attachments/assets/354e66d1-a96d-42ad-b1ad-0fbaf8e11196)


  14. From now on, every time you turn your laptop on, you will be asked about the OS you will use.
  15. Before install ROS Humble, be sure you have internet access in your Ubuntu OS.

## 2. Install ROS Humble
  ROS 2 Installation: https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debs.html
  1. Open the terminal. You can do that clicking on the square made of 9 points in the left-bottom corner, and searching the "Terminal" word.
  2. Set locale
     
Make sure you have a locale which supports UTF-8. If you are in a minimal environment (such as a docker container), the locale may be something minimal like POSIX. We test with the following settings. However, it should be fine if you’re using a different UTF-8 supported locale.Make sure you have a locale which supports UTF-8. If you are in a minimal environment (such as a docker container), the locale may be something minimal like POSIX. We test with the following settings. However, it should be fine if you’re using a different UTF-8 supported locale.
  
    locate
    sudo apt update && sudo apt install locales
    sudo locale-gen en_US en_US.UTF-8
    sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
    export LANG=en_US.UTF-8
    
    locale  # verify settings
  3. Setup sources
You will need to add the ROS 2 apt repository to your system.

First ensure that the Ubuntu Universe repository is enabled.
     
    sudo apt install software-properties-common
    sudo add-apt-repository universe
Now add the ROS 2 GPG key with apt.

    sudo apt update && sudo apt install curl -y
    sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

Then add the repository to your sources list.

    echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
  4. Install ROS 2 packages

Update your apt repository caches after setting up the repositories.

    sudo apt update

ROS 2 packages are built on frequently updated Ubuntu systems. It is always recommended that you ensure your system is up to date before installing new packages.

    sudo apt upgrade

Desktop Install: ROS, RViz, demos, tutorials.

    sudo apt install ros-humble-desktop

  5. Environment setup

Set up your environment by sourcing the following file.

    # Replace ".bash" with your shell if you're not using bash
    # Possible values are: setup.bash, setup.sh, setup.zsh
    source /opt/ros/humble/setup.bash


## Important programs that you may need to download

  1. terminator (https://shanepark.tistory.com/313)

    sudo apt-get install terminator
## 3. References
- Ubuntu Installation: https://youtu.be/wIj7sHK0SkQ?si=t1UHW8nSEUa0G_Qe
- ROS 2 Installation: https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debs.html

