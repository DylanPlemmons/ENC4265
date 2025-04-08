[Home](index.md) | [Manual Assessment Memo](manual_assessment_memo.md) | [Chatbot](chatbot.md) | [Procedure Video](procedure_video.md) | [Manual](manual.md) | [Reflective Blogs](reflective_blogs.md)

# Manual 

# How to Set Up a Firewall using pfSense
- [Introduction](#Introduction)
- [Installation](#Installation)
- [Initial Configuration](#Initial-Configuration)
- [Firewall Configuration](#Firewall-Configuration)

## Introduction

In today's digital age, network security is more important than ever. Whether at home or in a business environment, protecting devices and sensitive data from cyber threats is a top priority. pfSense is an open-source firewall and router platform that provides a flexible and cost-effective way to manage and secure networks.

Developed by Netgate, pfSense is built on FreeBSD, a UNIX-like operating system known for its reliability and performance. It includes a user-friendly web interface that makes complex network configurations accessible even to those without deep technical expertise. pfSense can be installed on dedicated hardware or run in a virtual machine, making it a versatile solution for a wide range of use cases including from home networks and small businesses to large enterprise environments.

At its core, pfSense offers many features such as stateful packet filtering, network address translation (NAT), virtual private network (VPN) support, intrusion detection and prevention, traffic shaping, and captive portals. These features allow users to monitor and control network traffic, defend against unauthorized access, and ensure optimal network performance.

This manual will guide you through the process of setting up pfSense from scratch, including installation, basic configuration, and essential features to get your firewall up and running.

## Installation

First we will look into the installation steps for pfSense. For this guide I will show the steps to install using a virtual machine in VirtualBox. pfSense is very flexible and is able to be installed on another computer/server or can be used as a virtual machine and will have similar set ups.

First, download the latest version of the pfSense ISO image from the official website at https://www.pfsense.org/download/. The software for pfSense is free to use but requires an account to download the latest ISO image. 

![image.png](attachment:ba76dc22-4c3b-4910-ba25-ea2f814c02f2:image.png)

The webpage will look similar to the above screenshot. Click the download button to be transferred to the next page where you will choose the installation image.

![image.png](attachment:6777313a-c6de-45a0-ad3d-d6455691ee4a:image.png)

For this guide we are using the image type “AMD64 ISO IPMI/Virtual Machines”. Select the option that best suits your installation type and then click “Add to Cart”. Once added to the cart, you will need to follow the checkout process and either create an account or log in with an existing account. 

![image.png](attachment:b0694e29-83a4-4ca8-b0c2-b50aa5f7d703:image.png)

After the checkout process is completed, you be able to click the Download Now button to download the ISO image. Once downloaded, the image is compressed and will need to be uncompressed to use. In Windows , you will need 7zip to extract the ISO file. Open the downloaded file in 7zip then press the “Extract” button as shown in the screenshot below. If you’re using a Linux or macOS computer, the command to unzip the fill is `gunzip <filename>.gz` . This will produce the unzipped ISO file in the same directory the original file was downloaded.

![image.png](attachment:ed09a8d4-0c66-4cd8-b9b2-20a816267737:image.png)

Next, we will mount the pfSense into VirtualBox. Start by clicking the “New” button in VirtualBox. 

Choose the name you want to give the Virtual Machine then under ISO Image choose the .iso file that we decompressed. Everything else can be left as the default values and press “Finish” to create the virtual machine.

![image.png](attachment:82d45538-986b-48ee-a46f-fb352065e893:image.png)

## Initial Configuration

First, boot up the pfSense instance by pressing start on the Virtual Machine. It will go through the initial boot up process then display a “Copyright and Distribution Notice”. 

![image.png](attachment:4b8e8595-f14f-4a63-bcb1-006cb41b8c6d:image.png)

![image.png](attachment:ac827e3a-e392-40a7-88b5-033de1a21bb9:image.png)

Press the Install button on the Installer page. Choose the default options through the installer. You may be asked to install the CE edition of pfSense due to not having a license. Since we are using pfSense for personal use, we do not need to pay for a license and can choose the CE (Community Edition) of the software. When asked which version to install, choose the stable version. The beta may have issues that can cause problems so we will stay on the most stable version.

![image.png](attachment:7733c741-b0c0-4e69-90ff-47ed97afa357:image.png)

Once the installation has been completed you will reach the screen in the screenshot above. Press Reboot and the Virtual Machine will restart. When it reboots, it will restart the installation of pfSense which we do not want to do again. Close out of the VM and choose to “Power Off” the machine. Next, go into the Settings, choose Storage, select the installer instance and select to “Remove Attachment”.

![image.png](attachment:42c50391-2d91-43f4-b003-54e46b6705f6:image.png)

Now boot up the Virtual Machine and pfSense will fully boot. Once you reach the screen shown in the screenshot below, pfSense is now running.

![image.png](attachment:2a9de188-5cff-4ea0-a68a-b4ff069eec5a:image.png)

## Firewall Configuration

Now that that pfSense, we can start to configure the instance and use for various functions on our network. To configure the instance, we need to access the webConfigurator from anther machine that is on the same network. To access the webConfigurator, type in the WAN IP address assigned to the pfSense instance in the URL search bar. For instance, the IP address for my pfSense is `10.0.2.15`  but the IP may be different or can be changed.

![image.png](attachment:ec3dc8e1-4cb9-4734-963a-15d6c012a918:image.png)

To log in, the default credentials are Username = **admin** & Password = **pfsense**. Once logged in, you will reach the page as shown in the screenshot below. Press next to start the pfSense Setup.

![image.png](attachment:13f78edd-fedd-4035-a0fe-d7970df3e5ac:image.png)

Follow the Setup leaving everything as default and changing the admin password to a password of your choosing. Then select Finish, to complete the setup.

![image.png](attachment:aa445095-61c5-449a-bd3f-83a94e2d1e6c:image.png)

To configure Firewall rules, first select the dropdown menu title “Firewall” at the top of the screen. Then select “Rules” which will bring us to the Firewall Rules page. This page allows us to add different rules, change the order that they should follow, edit and delete other rules. To configure start by pressing the Add button to create a Rule.

![image.png](attachment:13c90248-d101-4174-9b0a-38011dfd3005:image.png)

![image.png](attachment:c03ec509-dbfa-42da-9c72-057b1df7850c:image.png)

![image.png](attachment:67a0a907-1b02-4e37-a61f-0b802771dfe3:image.png)

![image.png](attachment:4a55c29b-8903-4c68-8b20-c8b2447f463c:image.png)

![image.png](attachment:7727e4a4-e3a7-42d1-93ce-f0e60f9da085:image.png)
