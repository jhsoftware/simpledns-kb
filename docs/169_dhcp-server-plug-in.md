---
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2019-01-01
modified-utc: 2021-10-29
---
# DHCP Server plug-in

This plug-in is a DHCP server which provides IPv4 addresses and settings to local computers and devices. The DHCP data is also used to serve DNS requests (forward and reverse) making it very simple to locate any local DHCP client by name on a local network.

On the "Plug-In Settings" tab, enter the DHCP settings to be used (explained below):

![](img/169/1.png)

- **Server IP**  
Select which local IP address you want to serve DHCP on.
- **Subnet mask**  
Shows the IP subnet mask for the selected server IP address.  
This subnet mask will automatically be provided to DHCP clients.
- **DNS suffix**  
The DNS suffix domain name assigned the DHCP clients.  
(Client's full domain name in DNS will be &lt;machine name&gt;.&lt;DNS suffix&gt;)
- **Assign IP addresses to clients with no reservation**  
Specify the range of IP addresses (a.k.a. "DHCP scope") to dynamically assign IP addresses to DHCP clients from.
- **DHCP Options...**  
Click this button to configure default DHCP options (see below).
- **Reservations...**  
Click this button to configure DHCP reservations (see below).
- **Update host records (A) in local forward zones**  
When checked, Simple DNS Plus will create/update an A-record for each new/updated DHCP lease.  
Requires a local forward primary zone for the DNS suffix or a parent name.  
This is only needed if you have multiple DNS servers hosting the DNS suffix and you want A-records for the DHCP leases automatically transferred to secondary DNS servers.
- **Update reverse records (PTR) in local reverse zones**  
When checked, Simple DNS Plus will create/update a PTR-record for each new/updated DHCP lease.  
Requires a local reverse primary zone for the IP addresses assigned by the DHCP service.  
This is only needed if you have multiple DNS servers hosting reverse DNS for the IP address range and you want PTR-records for the DHCP leases automatically transferred to secondary DNS servers.

### DHCP Options dialog

The DHCP Options dialog can be accessed in 3 ways - from the main DHCP Plug-in dialog (see above) for setting the default options or from the DHCP Lease dialog (see) - either as options for a single lease or as options for a group of leases.

- **Lease Period tab**  
Specify how long DHCP clients are allowed to use their assigned IP address.  
This is the maximum time the client computer may use the IP address without getting the lease renewed.  
Typically after half the lease period has elapsed, the client computer will attempt to renew the lease.

![](img/169/2.png)
- **IP routing tab**  
Specify the default gateway IP address (typically your Internet router) and/or static routing table entries to assign to DHCP clients:

![](img/169/3.png)
- **DNS servers tab**  
Specify the DNS servers to assign to DHCP clients:

![](img/169/4.png)
- **TFTP / Boot file tab**  
These options are typically used in combination with a [TFTP server](https://simpledns.plus/plugin-tftp) to enable PXE / disk less booting of PCs, provisioning IP phones, etc.  
An example of this is provided in [How to serve a network based Debian Linux installation with Simple DNS Plus](/kb/73).

![](img/169/5.png)

### DHCP Reservations dialog (list of reservations)

Reserve IP addresses for specific clients based on computer/device name or hardware address (network card MAC address).  
To determine a computers hardware address on Windows NT4/2000 and later, run "IPCONFIG /ALL" from a command prompt, and see "Physical Address".

![](img/169/6.png)

### DHCP Reservation dialog (individual reservation)

For each reservation, you can specify an alternate set of options - either for the individual reservation or for a group of reservations.  
For MAC based reservations, you can optionally specify a host name that will be assigned to the client (through the DHCP response and in local DNS data).

![](img/169/7.png)

### View

The DHCP Server plug-in also has a "view" in the main Simple DNS Plus window (open from View menu), where you can see current and optionally expired DHCP leases:

![](img/169/8.png)

The list can be sorted by clicking the column headers.

To manually delete a DHCP lease, right click on the lease and select "Delete" from the pop-up menu. In order to prevent IP-address conflicts (two or more computers having the same address), it is important that the computer for the deleted lease is also rebooted or removed from the network.  
Generally, it is not necessary to delete leases manually, as computers automatically release their leases when shut down properly.

Older Apple/Mac clients and some devices which do not supply a computer name in the DHCP request will show with their hardware address as the name.  
To rename these, right click on the lease and select "Rename". The new name will be associated with the client's hardware address (MAC), and remembered as long as you run Simple DNS Plus even if the IP address changes.

To configure a Windows computer to get its IP address from a DHCP server, configure it to "Obtain an IP address automatically" in TCP/IP protocol settings (under network properties).

If your server computer is connected to multiple local networks, you can use multiple DHCP server plug-in instances.

NOTE: When multiple DHCP leases are active for the same client name, DNS will resolve to the IP address of the DHCP lease that expires last (newest). This ensures that DNS resolves correctly for laptops and other devices moving between wired and wireless connections.

