# Kubernetes on ESXi

## Install ESXi

I installed ESXi on an empty bare metal machine by running the ESXi installer from a boot USB disk.

To create that USB boot disk, I used [Rufus]( https://rufus.ie/ ), adding the [ESXi 6.7.0 install ISO]( https://my.vmware.com/en/web/vmware/evalcenter?p=free-esxi6 ).

![Rufus]( Rufus.png )

I booted the empty machine with the USB disk, following the installers instructions.

Once I had the ESXi up and running,

- add the (free) license key
- set the IP address of the ESXi to be fixed. ![IP](ESXi-IP.png)

- Setup the DNS
 ![DNS](ESXi-DNS.png)
