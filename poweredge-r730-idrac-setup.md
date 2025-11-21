PowerEdge R730 iDRAC Setup and Initial Linux Install Guide
Step 1: Connect and Access iDRAC
1.1 Find and connect the iDRAC port

    Connect the dedicated iDRAC Ethernet port on the back of your server to your network switch/router.

    Make sure your laptop/desktop is on the same network.

1.2 Power on the server and find the iDRAC IP address

Option A: Using the server LCD panel

    Use the arrow buttons on the server front panel to scroll through system info.

    Note the iDRAC IP address displayed.

Option B: Using your router (Linux bash commands below)

If you know your network subnet (e.g., 192.168.1.0/24), you can scan for the iDRAC device:

sudo nmap -p 443 --open 192.168.1.0/24

Look for devices with port 443 open (default iDRAC web port).

To identify Dell devices by MAC:

arp -a | grep -i dell

1.3 Access iDRAC web interface

    Open browser on your laptop/desktop.

    Navigate to:

https://<iDRAC_IP_Address>

    Login with default credentials:

username: root
password: calvin

Step 2: Secure iDRAC
2.1 Change default password

    After login, go to Configuration > User Management.

    Change password for root user to a secure one.

2.2 (Optional) Set static IP for iDRAC

If you want a fixed IP for iDRAC, do the following:

    Go to iDRAC Settings > Network > Network Interface.

    Set the IP address, subnet mask, gateway.

    Save and reboot iDRAC if needed.

Step 3: Prepare for Linux Install via iDRAC Virtual Console
3.1 Launch Virtual Console

    In the iDRAC dashboard, click Console & Media > Launch Virtual Console.

    This opens a remote desktop window showing your server screen.

3.2 Mount ISO image for OS install

    Within Virtual Console, go to Virtual Media > Connect Virtual Media.

    Browse and mount your chosen Linux ISO (e.g., Debian, Ubuntu Server).

Step 4: Install Linux on PowerEdge R730
4.1 Boot from virtual media

    Reboot the server (use the iDRAC Power Management > Reset System).

    During POST, enter BIOS (usually by pressing F2).

    Change boot order to boot from virtual media (mounted ISO).

    Save and exit BIOS.

4.2 Follow Linux installer prompts

    Proceed with your preferred Linux installation (Debian Server, Ubuntu Server, Fedora, etc.).

    Configure partitions, users, network, etc.

Step 5: Post-install tasks via SSH
5.1 Find server IP address (if using DHCP)

From your laptop, scan your network to find your server IP:

sudo nmap -p 22 --open 192.168.1.0/24

5.2 SSH into the server

ssh yourusername@<server_ip_address>

5.3 Update system packages (example for Debian/Ubuntu)

sudo apt update && sudo apt upgrade -y

Or for Fedora:

sudo dnf update -y

Bonus: Basic iDRAC CLI commands (optional)

If you have RACADM installed on a Linux machine connected to the network, you can manage iDRAC remotely:

racadm -r <iDRAC_IP> -u root -p <password> serveraction powercycle

