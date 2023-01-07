# linux

```
# edit grub
sudo vim /etc/default/grub
# Add the following
GRUB_SAVEDEFAULT=true
GRUB_DEFAULT=saved

# update
sudo update-grub

# Now, the kernel you select at boot should become default
```

```
# FIFO Background read from Named Pipe and execute command
pipe=/tmp/testpipe

trap "rm -f $pipe" EXIT

if [[ ! -p $pipe ]]; then
    mkfifo $pipe
fi

while true
do
    if read line <$pipe; then
        if [[ "$line" == 'quit' ]]; then
            break
        fi
        out=`$line`
        echo $out
    fi
done
```

```
# curling from github releases
(
  set -x; cd "$(mktemp -d)" &&
  OS="$(uname | tr '[:upper:]' '[:lower:]')" &&
  ARCH="$(uname -m | sed -e 's/x86_64/amd64/' -e 's/\(arm\)\(64\)\?.*/\1\2/' -e 's/aarch64$/arm64/')" &&
  KREW="krew-${OS}_${ARCH}" &&
  curl -fsSLO "https://github.com/kubernetes-sigs/krew/releases/latest/download/${KREW}.tar.gz" &&
  tar zxvf "${KREW}.tar.gz" &&
  ./"${KREW}" install krew
)
```

```
# VNC
apt install tigervnc-scraping-server -y
vncpasswd
x0vncserver -passwordfile ~/.vnc/passwd -display :0 -fg

git clone https://github.com/novnc/noVNC.git
./noVNC/utils/novnc_proxy --vnc localhost:5900

x0vncserver -kill
```
