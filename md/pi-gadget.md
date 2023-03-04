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

# sudo crontab -e
* * * * * ip route del default via 192.168.23.1

# /etc/sysctl.conf
net.ipv4.ip_forward=1

# .bashrc ( append )
alias stop_wifi="sudo pkill wpa_supplicant"
alias wifi="sudo wpa_supplicant -iwlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf  -B && sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE"
alias fix_route="sudo ip route del default via 192.168.23.1"

# wifi
wpa_passphrase [ssid] [password] > /etc/wpa_supplicant/wpa_supplicant@wlan0.conf
systemctl start wpa_supplicant@wlan0.service
systemctl enable wpa_supplicant@wlan0.service

# save iptables
apt install iptables-persistent
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
iptables-save > /etc/iptables/rules.v4

# /etc/ssh/sshd_config ( edit )
PermitEmptyPasswords yes
PermitRootLogin yes

# On openwrt router, generate keypair
mkdir ~/.ssh
cd ~/.ssh
dropbearkey -t rsa -f id_dropbear

# Copy private key into authorized_keys in pi ~/.ssh/authorized_keys

# OR delete password
sudo passwd -d `whoami`
```
