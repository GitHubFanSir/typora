git使用代理


全局代理，写入配置
需要密码
git config --global http.proxy http://user:password@ip:port
git config --global https.proxy https://user:password@ip:port

不需要密码
git config --global http.proxy http://ip:port
git config --global https.proxy https://ip:port

例如：
git config --global https.proxy http://127.0.0.1:1080
git config --global https.proxy https://127.0.0.1:1080

git config --global http.proxy 'socks5://127.0.0.1:1080' 
git config --global https.proxy 'socks5://127.0.0.1:1080'

清除配置
git config --global --unset http.proxy
git config --global --unset https.proxy

临时代理
ALL_PROXY=socks5://127.0.0.1:8888 git clone https://github.com/some/one.git




​     

---------------------