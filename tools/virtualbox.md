# Virtualbox Command-line

Start VM in **headless** mode

	VBoxManage startvm "Virtuanux" --type headless

Change VM to be started in **headless** by default

	VBoxManage modifyvm "Virtuanux" --defaultfrontend headless

Pause running VM

	VBoxManage controlvm "Virtuanux" pause --type headless

Resume running VM

	VBoxManage controlvm "Virtuanux" resume --type headless

Poweroff VM

	VBoxManage controlvm "Virtuanux" poweroff --type headless


Convert disk image from **VDI** to **RAM**

	vbox-img convert 
		--dstformat RAM --srcformat VDI  
		--srcfilename raspbian-stretch-lite-2018-11-13-attuor1.vdi
		--dstfilename raspbian-stretch-lite-2018-11-13-attuor2.img 

Attach **USB** drive

    VBoxManage controlvm "Virtuanux" usbattach 468876e6-1642-4faa-bbca-358c5295079e

Compact hdd image

    VBoxManage modifymedium disk Ubuntu.vdi --compact

> In order to **compact** to give best results you need to 
use **zerofree -v <partition\>** to fill unused blocks with 
zeros. You can't do that on root filesystem if it is mounted 
so it is adviced to restart your system, press ESC until you 
get to GURB, then select **Advanced options for Ubuntu** and 
then **Recovery Mode**. Once recovery system starts select 
**Drop to root shell prompt**. Give your user password and 
go....


