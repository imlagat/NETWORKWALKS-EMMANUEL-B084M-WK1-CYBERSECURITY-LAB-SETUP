# NETWORKWALKS-EMMANUEL-B084M-WK1-CYBERSECURITY-LAB-SETUP
This is  hacking lab setup for my cybersecurity internship

**Installing Kali Linux on VirtualBox on macOS**
This README documents how to set up Kali Linux in a VirtualBox virtual
machine on a Mac for learning Linux, networking, and cybersecurity
fundamentals.
Safety: Use Kali Linux only on systems and networks you own or
have explicit permission to test.

**1. Prerequisites**
- A Mac with enough free disk space and memory.
- Oracle VirtualBox.
- The official Kali Linux ISO.
- A stable internet connection.
Processor compatibility:
On an Intel Mac, download the macOS/Intel
VirtualBox installer and an x86-64 Kali image.
Apple Silicon Macs
require a compatible ARM image and virtualization setup; an x86-64 ISO
may not run natively.
**2. Install VirtualBox**
1. Visit https://www.virtualbox.org/wiki/Downloads.
2. Download the macOS installer that matches your Mac's processor.
3. Open the downloaded .dmg file and follow the installer.
4. If macOS asks you to approve system software, follow the
   instructions shown in System Settings → Privacy & Security.
5. Open VirtualBox to verify that it launches.
   
**3. Download Kali Linux**
1. Visit https://www.kali.org/get-kali/.
2. Select an image suitable for your Mac and chosen installation
   method.
3. For a manual installation, download the Installer ISO. You can
   also use a prebuilt VirtualBox image if available.
4. If a checksum is provided, verify the downloaded file.
**4. Create a virtual machine**
1. Open VirtualBox and click New.
2. Name the VM Kali Linux.
3. Choose Linux and the appropriate Debian 64-bit option, if
   available.
4. Allocate RAM and CPU cores while leaving enough resources for macOS.
5. Create a virtual hard disk with enough space for Kali and the tools
   you plan to use. Dynamically allocated storage is a convenient
   option.
6. Finish creating the VM.
Options can vary by VirtualBox version and Mac processor.
**5. Attach the Kali ISO**
1. Select the VM and open Settings → Storage.
2. Select the empty optical drive.
3. Click the disc icon and choose the downloaded Kali ISO.
4. Save the settings.
**6. Install Kali Linux**
1. Select the VM and click Start.
2. Choose Graphical install or the recommended installer option.
3. Select your language, location, and keyboard layout.
4. Set a hostname. A domain name can usually be left blank for a
   personal lab.
5. Create a user account and strong password when prompted.
6. For disk partitioning, select the guided option for the VM's
   virtual disk. Make sure you are not selecting a physical Mac
   drive.
7. Confirm the partition changes for the virtual disk.
8. Select the software/components you need.
9. Install the boot loader to the VM's virtual disk if prompted.
10. Finish installation and reboot. If the installer starts again, eject
    the ISO from the virtual optical drive.
11. Log in using the account you created.
    
**7. Update Kali**
Open a terminal and run:
sudo apt update
sudo apt full-upgrade -y
Restart the VM if required.

**8. Configure networking**
Choose the network mode required for your lab.
NAT
- Usually provides outbound internet access through the Mac.
- Useful for installing updates.
- Does not automatically make Kali directly reachable from other
  devices on the local network.
Bridged Adapter
- Connects the VM through the Mac's physical network interface.
- Kali may receive an IP address on the same network as the Mac.
- Network policies or Wi-Fi limitations can affect bridging. Use it
  only on a trusted network where you have permission.
**NAT Network using 10.0.0.0/24 (if required)**
1. Shut down the Kali VM.
2. In VirtualBox, open Tools → Network or File → Tools → Network
   Manager, depending on the version.
3. Open NAT Networks and create a network.
4. Set the network CIDR to 10.0.0.0/24 if required by your lab.
5. Enable DHCP if the lab expects VirtualBox to assign addresses
   automatically.
6. Open Kali VM → Settings → Network.
7. Enable the adapter and choose NAT Network as the attachment
   type. Select the network you created.
8. Start Kali and check its network details.
   
Use these commands in Kali:
ip address
ip route
ping -c 4 1.1.1.1
Check that the subnet does not conflict with another network. NAT
Network and Bridged networking are different modes; select the one
required for the exercise.
**10. Enable clipboard and drag-and-drop (optional)**
If your lab requires these features:
1. Shut down Kali.
2. Open Kali VM → Settings → General → Advanced.
3. Set Shared Clipboard and Drag'n'Drop to the required
   direction, such as Bidirectional, if available.
4. Start Kali and test the features.
   
These features may require compatible Guest Additions or guest
integration packages. Support depends on the VirtualBox and guest
versions. Consult the official documentation if they do not work. For
security, enable sharing only when needed.
10. Verify the installation
Run the following commands in Kali:
cat /etc/os-release
uname -r
ip address
ip route
Confirm that Kali boots, the network settings match your lab
requirements, and internet access works when expected.

**11. Create a snapshot**
After installation and updates:
1. Open the VM's Snapshots section.
2. Create a snapshot named Fresh Kali Installation.
A snapshot lets you return to a known-good state after experiments.
**Troubleshooting**
- VM does not start: Check that your VirtualBox version and Kali
  image match your Mac's processor.
- No internet: Check the adapter mode, NAT Network configuration,
  DHCP, and ip route.
- Installer starts again: Eject the Kali ISO from the virtual
  optical drive.
- Clipboard/drag-and-drop fails: Check guest integration support
  and the VM's Advanced settings.
- Poor performance: Reduce allocated resources if macOS becomes
  sluggish and check available disk space.
  
**References**
- VirtualBox downloads: https://www.virtualbox.org/wiki/Downloads
- VirtualBox user manual: https://www.virtualbox.org/manual/
- Kali Linux downloads: https://www.kali.org/get-kali/
- Kali documentation: https://www.kali.org/docs/
