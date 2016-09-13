redis:
/usr/local/bin/redis-server /etc/redis/redis.conf

!!password

mongodb:
 ./bin/mongod --dbpath=./db --logpath=./log/mongodb.log --fork
 ./bin/mongod --dbpath=./db --logpath=./log/mongodb.log --fork --auth


nginx:   /usr/local/nginx/conf/
配置文件：
     /usr/local/nginx/conf/nginx.conf

vim /usr/lib/systemd/system/nginx.service 

[Unit]
Description=nginx - high performance web server
Documentation=http://nginx.org/en/docs/
After=network.target remote-fs.target nss-lookup.target

[Service]
Type=forking
PIDFile=/usr/local/nginx/logs/nginx.pid
ExecStartPre=/usr/local/nginx/sbin/nginx -t -c /usr/local/nginx/conf/nginx.conf
ExecStart=/usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf
ExecReload=/bin/kill -s HUP $MAINPID
ExecStop=/bin/kill -s QUIT $MAINPID
PrivateTmp=true

[Install]
WantedBy=multi-user.target


systemctl start nginx.service




./configure --prefix=/usr/local/php  --enable-fpm --with-mcrypt --enable-mbstring --disable-pdo --with-curl --disable-debug 

--disable-rpath --enable-inline-optimization --with-bz2  --with-zlib --enable-sockets --enable-sysvsem --enable-sysvshm --

enable-pcntl --enable-mbregex --with-mhash --enable-zip --with-pcre-regex --with-mysql --with-mysqli --with-gd --with-

jpeg-dir



php-fpm:
service php-fpm start









openresty:
nginx -p `pwd`/ -c conf/nginx.conf

























