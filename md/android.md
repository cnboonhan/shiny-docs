# android-wifi-proxy

Instructions to set up android device for VPN proxy.

```
# Connect to Wifi on phone

# Install Shelter, get up Work Profile
https://m.apkpure.com/shelter/net.typeblog.shelter

# Install Google Chrome, SimpleSSHD and GlobalProtect in Work Profile
# Install it via App Store, then Clone to Shelter

# Install Fdroid and Termux ( from Fdroid ) on Personal
https://f-droid.en.softonic.com/android

# On termux, run
pkg update
pkg install openssh iproute2 tmux avahi dnsutils traceroute openssl-tool
whoami    # Remember this
ip a      # Get Ip address of phone
passwd    # Set password

# Use this to install linux distro on termux
# https://github.com/termux/proot-distro
pkg install proot-distro
proot-distro install debian
proot-distro login debian

# Open Work Profile and run SimpleSSHD
# Copy public key on Personal Profile to ~/authorized_keys on Work Profile
# Run GlobalProtect and Login

# Disable App Management ( to prevent phone from terminating apps ) for Termux, SimpleSSHD

# Set up Privoxy for HTTP proxy on SimpleSSHD /etc/config
forward-socks5t / 127.0.0.1:1080 .
listen-address 0.0.0.0:1090

# Start privoxy
privoxy /etc/config

# Create Socks Proxy
ssh 127.0.0.1 -p 2222 -D 1080

# Connect to HTTP proxy at [ip address]:1090
```
