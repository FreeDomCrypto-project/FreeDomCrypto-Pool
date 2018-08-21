INSTALL SETUP UBUNTU 16.04:




apt-get update;
apt-get dist-upgrade;
dd if=/dev/zero of=/mnt/myswap.swap bs=1M count=4000;
mkswap /mnt/myswap.swap;
swapon /mnt/myswap.swap;

!!!
nano /etc/fstab
Add the following line at the end of the file.

/mnt/myswap.swap none swap sw 0 0
Ctrl+O to save, and Ctrl+X to exit the nano editor.
!!!


apt-get install build-essential libtool autotools-dev autoconf pkg-config libssl-dev;
apt-get install libboost-all-dev git npm nodejs nodejs-legacy libminiupnpc-dev redis-server;
add-apt-repository ppa:bitcoin/bitcoin;
apt-get update;
apt-get install libdb4.8-dev libdb4.8++-dev;
curl -sL https://raw.githubusercontent.com/creationix/nvm/v0.31.0/install.sh -o install_nvm.sh;
bash install_nvm.sh;
source ~/.profile;
nvm install 0.10.48;
nvm use 0.10.48;
nvm alias default 0.10.48;
nvm use default;

sudo apt-get install screen;

screen -S rpc;

git clone https://github.com/FreeDomCrypto-project/FreeDomCrypto.git;

cd FreeDomCrypto; (goto main source link above and setup)
cd build/release/bin;
./FreeDomCryptod --allow-local-ip
Wait for Sync
./FreeDomCryptod exit or stop
./FreeDomCryptod --allow-local-ip --detach
./FreeDomCrypto-wallet-cli (Make pool Wallet than exit)
./FreeDomCrypto-wallet-rpc --wallet-file pool --password poolpwd --rpc-bind-port 38082

cd ~
git clone https://github.com/FreeDomCrypto-project/FreeDomCrypto-Pool.git
cd FreeDomCrypto-pool
npm update

!!!Start the pool!!!

node init.js

This will show all running and start accepting share for your pool

we need to now install forever so that this pool will remain running even on close of ssh

npm install forever -g
once installation done final start the pool

forever start init.js

!!!

Host the front end 

Simply host the contents of the website_example directory on file server capable of serving simple static files.

Edit the variables in the website_example/config.js file to use your pool’s specific configuration. Variable explanations:
!!!!!!!!!!!! EXAMPLE !!!!!!!!!!!!!!!!!!!!!!!!!!!


/* Must point to the API setup in your config.json file. */
var api = “http://poolhost:8117”;

/* Minimum units in a single coin, for Bytecoin its 100000000. */
var coinUnits = 1000000000000;

/* Pool server host to instruct your miners to point to. */
var poolHost = “cryppit.com”;

/* IRC Server and room used for embedded KiwiIRC chat. */
var irc = “irc.freenode.net/#monero”;

/* Contact email address. */
var email = “support@cryppit.com”;

/* Market stat display params from https://www.cryptonator.com/widget */
var cryptonatorWidget = [“XMR-BTC”, “XMR-USD”, “XMR-EUR”, “XMR-GBP”];

/* Download link to cryptonote-easy-miner for Windows users. */
var easyminerDownload = “https://github.com/zone117x/cryptonote-easy-miner/releases/”;

/* Used for front-end block links. For other coins it can be changed, for example with
Bytecoin you can use “https://minergate.com/blockchain/bcn/block/”. */
var blockchainExplorer = “http://monerochain.info/block/”;

/* Used by front-end transaction links. Change for other coins. */
var transactionExplorer = “http://monerochain.info/tx/”;




