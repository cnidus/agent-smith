# QS-USB-NTNX
This is a basic project to help streamline the installation and basic config of Cumulus Linux to support a Nutanix cluster.

# Why do we need this?
Open Networking switches come from the factory installed with only a bootloader, similar to pxe. This enables the switch to be network booted and the customer chooses a Network Operating System seperately, similar to the way servers are traditionally purchased and installed in large envrionments.

By contrast, traditional network devices come with a NOS pre-installed and sometimes with a basic config. Nutanix nodes also come pre-imaged and ready to be configured.

This project aims to close the install-overhead gap and also customize the initial configuration to suit a Nutanix cluster in factory state. Overall the goal is to improve the out-of-the-box initial setup experience of a Nutanix pod using Cumulus networking.

# What it does
The project has 3 primary functions:

* Build a bootable USB drive containing all components
* Install Cumulus Linux on the switch using usb waterfall of the ONIE bootloader.
* Configure the switch(es) with a base config using Zero Touch Provisioning (ZTP)

Further details on the ONIE process can be found at: http://www.onie.org

Further details on Cumulus ZTP can be found here: https://docs.cumulusnetworks.com/display/DOCS/Zero+Touch+Provisioning+-+ZTP#ZeroTouchProvisioning-ZTP-ZeroTouchProvisioningUsingUSB(ZTP-USB)

# QuickStart: Using the tool

* Building the USB
* Install/Config of switches.
1) Insert the USB into 1g mgmt/OOB switch (if present)
2) Power on the mgmt switch

The switch will boot into ONIE and install the image from the USB drive. After successful installation the switch will reboot and start Cumulus Linux.
Most switches will run fans at full speed until a fan-control process spins them down, this happens during CumulusLinux boot, so this is a good indication of successful completion of the install.

When Cumulus first boots, it will run Zero Touch Provisioing (ZTP). This process looks for a script presented via DHCP options, or on a USB drive, in our case it uses the same USB drive.

The ZTP script <UP TO HERE> 
