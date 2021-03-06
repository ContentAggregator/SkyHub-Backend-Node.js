# Node.js 8.x and NPM

## NVM
    For unix machines, we recommend you to intall node.js and npm using nvm using this tutorial

    https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-16-04

    sudo apt-get update
    sudo apt-get install build-essential libssl-dev

    mkdir nvm
    curl -sL https://raw.githubusercontent.com/creationix/nvm/v0.31.0/install.sh -o install_nvm.sh

    nano install_nvm.sh           to test the the existance of the file
    bash install_nvm.sh
    ~/.nvm
    ~/.profile
    source ~/.profile

    nvm ls-remote
    nvm install 8.1.4
    nvm use 8.1.4
    node -v                  show show the 8.x version

    nvm ls
    nvm alias default 8.1.4
    nvm use default

# Redis

    TUTORIAL:     https://www.linode.com/docs/databases/redis/deploy-redis-on-ubuntu-or-debian


    1. sudo apt-get install software-properties-common

    2. sudo apt-get update
    3. sudo apt-get install redis-server

    4. redis-cli
        127.0.0.1:6379>ping
        >> PONG

### Configure Redis `see the tutorial`
### Configure Persistence Options from the tutorial `see the tutorial`
### Basic System Tuning `see the tutorial`

### Distributed Redis `see the tutorial`

## Redis Password (authentication)

    TUTORIAL https://stackoverflow.com/questions/7537905/redis-set-a-password-for-redis

    1. nano /etc/redis/redis.conf
    2. uncomment # requirepass my_cool_redis_password     by removing the #
    3.

    warning: You need a strong password for Redis !!!

## restart Redis
   `sudo service redis-server restart`

## allow redis port firewall

   ### redis.conf
    TUTORIAL https://stackoverflow.com/a/13928537/6516672

   1. `nano /etc/redis/redis.conf`
   2. replace `bind 127.0.0.1` with `bind 0.0.0.0`
   3. `service redis-server restart`

   ###firewall (probably not required)
   1. `sudo iptables -A INPUT -p tcp --dport 6379 --jump ACCEPT`
   2. `iptables-save`


### upload database

   1. `cd /var/lib/redis`
   2. copy and replace `appendonly.aof`
   3. copy and replace `dump.rdb`


# SCRIPTS

   ## EMAIL for email install
        1. https://rianjs.net/2013/08/send-email-from-linux-server-using-gmail-and-ubuntu-two-factor-authentication
        2. https://serverfault.com/a/672182

# No-IP DUC for non-static IPs (aka dynamic IPs)

   TUTORIAL: http://www.noip.com/support/knowledgebase/installing-the-linux-dynamic-update-client/

   1. `cd /usr/local/src`
   2. `wget http://www.no-ip.com/client/linux/noip-duc-linux.tar.gz`
   3. `tar xzf noip-duc-linux.tar.gz`
   4. `cd no-ip-2.1.9`
   5. `make`
   6. `make install`

   7. `sudo /usr/local/bin/noip2 -C`   (dash capital C, this will create the default config file) to set the account

        The interval options is in minutes ( I think )

   8. /usr/local/bin/noip2    to run the application


## RUN APP IN BACKGROUND as a Background Application ...
   ```
   nohup npm run start &
   disown -h %1
   ```