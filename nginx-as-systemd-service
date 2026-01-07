## install nginx

# donwload the ngix source code
```
wget https://nginx.org/download/nginx-1.29.4.tar.gz
tar -zxvf nginx-1.29.4.tar.gz
cd nginx-1.29.4
sudo apt install build-essential
sudo apt install libpcre3 libpcre3-dev libssl-dev zlib1g zlib1g-dev make
./configure --sbin-path=/usr/bin/nginx --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log --with-pcre --pid-path=/var/run/nginx.pid --with-http_ssl_module
  make
sudo make install
```

# add nginx as a systemd service
```
sudo touch /lib/systemd/system/nginx.service
nano /lib/systemd/system/nginx.service
```
# copy past the follwing code
```
[Unit]

Description=A high performance web server and a reverse proxy server
After=syslog.target network.target remote-fs.target nss-lookup.target
Wants=network-online.target

[Service]

Type=forking
PIDFile=/var/run/nginx.pid
ExecStartPre=/usr/bin/nginx -t
ExecStart=/usr/bin/nginx
ExecReload=/bin/kill -s HUP $MAINPID
ExecStop=/bin/kill -s TERM $MAINPID
PrivateTmp=true

[Install]
WantedBy=multi-user.target
```
# enable and start the service
```
sudo systemctl status nginx
sudo systemctl enable nginx
sudo systemctl status nginx
sudo systemctl start nginx
sudo systemctl status nginx
```
