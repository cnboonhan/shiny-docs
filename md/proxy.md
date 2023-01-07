# proxy

```
# downloading with proxy using wget
wget -e use_proxy=yes -e http_proxy=192.168.49.1:8282 -e https_proxy=192.168.49.1:8282 "https://drive.google.com/uc?export=download&id=1geLF5IPEQd4oSvBh4mMHPdlTStdGQ426" -O chinese.txt
```

# downloading with proxy using curl
```
curl https://example.com -x sock5h://127.0.0.1:1080
```

# git clone with proxy 
```
git clone git@github.com:cnboonhan/conf.git -c http.sslverify=false -c http.proxy=socks5h://127.0.0.1:1080
```
