# Raspberry Pi Gadget
```
# dnsmasq.conf
interface=usb0
bind-dynamic
domain-needed
bogus-priv
dhcp-range=192.168.23.100,192.168.23.200,255.255.255.0,12h

# dhcpcd.conf ( append )
interface usb0
static ip_address=192.168.23.1
static routers=192.168.23.1
static
domain_name_servers=8.8.8.8

# /boot/cmdline.txt
console=serial0,115200 console=tty1 root=PARTUUID=1489b6de-02 rootfstype=ext4 fsck.repair=yes rootwait modules-load=dwc2,g_ether

# /boot/config.txt ( append )
dtoverlay=dwc2
```
