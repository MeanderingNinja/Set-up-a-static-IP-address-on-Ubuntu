# Set-up-a-static-IP-address-on-Ubuntu
Instructions on how to set up a static IP address on Ubuntu. This post is assisted by ChatGTP

Setting a static IP address on Ubuntu using /etc/network/interfaces:
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

