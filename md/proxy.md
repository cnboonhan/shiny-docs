# Useful Proxy Commands 
```
# downloading with proxy using wget
wget -e use_proxy=yes -e http_proxy=192.168.49.1:8282 -e https_proxy=192.168.49.1:8282 "https://drive.google.com/uc?export=download&id=1geLF5IPEQd4oSvBh4mMHPdlTStdGQ426" -O chinese.txt

# downloading with proxy using curl
curl https://example.com -x sock5h://127.0.0.1:1080

# git clone with proxy 
git clone git@github.com:cnboonhan/conf.git -c http.sslverify=false -c http.proxy=socks5h://127.0.0.1:1080

# ssh -L [LOCAL_IP:]LOCAL_PORT:DESTINATION:DESTINATION_PORT [USER@]SSH_SERVER
# In this forwarding type, the SSH client listens on a given client port and tunnels any connection to that port to the specified port on the remote SSH server, which then connects to a port on the destination machine. 
ssh -L 1090:127.0.0.1:1090 -J cnboonhan@10.3.141.1 root@192.168.42.129 -p 8022 

# enable GatewayPorts on sshd_config on remote for 0.0.0.0 on server
# ssh -R [REMOTE:]REMOTE_PORT:DESTINATION:DESTINATION_PORT [USER@]SSH_SERVER
# In this forwarding type, the SSH server listens on a given server port and tunnels any connection to that port to the specified client port on the local SSH client, which then connects to a port on the destination machine. The destination machine can be the local or any other machine.
ssh root@192.168.1.1 -R 0.0.0.0:6080:0.0.0.0:6080 -p 22

# create SOCKS proxy from external ssh
ssh -t -R 127.0.0.1:2222:127.0.0.1:22 cnboonhan@10.3.141.1 'ssh cnboonhan@127.0.0.1 -p 2222 -D 1080'

# Use Host DNS for VirtualBox
VBoxManage modifyvm "<VM name>" --natdnshostresolver1 on

# Restart routing when network interfaces change for VirtualBox in crontab
ping 8.8.8.8 -c 1 || systemctl restart systemd-networkd
```
