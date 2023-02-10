# Set-up-a-static-IP-address-on-Ubuntu
Instructions on how to set up a static IP address on Ubuntu. This post is assisted by ChatGTP

Setting a static IP address on Ubuntu using `/etc/network/interfaces`:

To set a static IP address on Ubuntu, follow these steps:

```
1. Open the Terminal and run the following command to open the network configuration file:

   sudo nano /etc/network/interfaces

2. In the file, find the section for your network interface (usually `eth0` or `wlan0`) and modify it to look like the following example:

   auto eth0
   iface eth0 inet static
   address 192.168.0.100
   netmask 255.255.255.0
   gateway 192.168.0.1

3. Replace the values in `address`, `netmask`, and `gateway` with the appropriate values for your network.

4. Save the file and close the text editor.

5. Restart the network service with the following command:

   sudo service networking restart

6. To verify that the static IP address has been set, run the following command:

   ip addr show eth0

Replace `eth0` with your network interface if it's different.
```
Setting a static IP address on Ubuntu using `Netplan`:
```
If the file `/etc/network/interfaces` is not present on your Ubuntu system, it's likely that your system is using `Netplan` for network configuration. To set a static IP address using `Netplan`, you can follow these steps:

1. Create a new Netplan configuration file with the following command:

   sudo nano /etc/netplan/50-cloud-init.yaml

2. In the file, add the following configuration, replacing the values for `addresses`, `gateway4`, `nameservers`, and `interface` with your network settings:

   network:
     version: 2
     ethernets:
       interface:
         dhcp4: no
         addresses: [192.168.0.100/24]
         gateway4: 192.168.0.1
         nameservers:
           addresses: [8.8.8.8, 8.8.4.4]

   Note that `interface` should be replaced with the actual name of your network interface (e.g., `eth0` or `wlan0`).

3. Save the file and close the text editor.

4. Apply the new configuration by running the following command:

   sudo netplan apply

5. To verify the static IP address, run the following command:

   ip addr show interface

Replace `interface` with the actual name of your network interface.

This should set the static IP address for your Ubuntu machine using Netplan.
```
