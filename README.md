# strongswan_config
configure a strongswan ipsec subnet with nftable and linux 4.x on debian jessie

# before install
check your system installed nftables and linux-image-4.x.x, these packages from jessie-backports,
and notice that this script will disable kernel module iptable_nat, because nftables can't work with iptable_nat.
Just type "./xxx", you can run the script xxx.

# install

run the script "install", it will install strongswan.

# configure network

run the script "network", it will open ipv4 forwarding and nat

# configure usernames and password

edit ipsec.secrets, add lines like this  username: XAUTH "xxxx", this is username and password, and
change : PSK "xxx" to some word, this is the preshared key.

edit ipsec.conf, change rightsubnet and rightsourceip to something you like, it is the subnet for you client.

run the script "config"

# start service
try the command "systemctl start strongswan", start service.
try the command "systemctl status strongswan", see status.

if everything work well, "systemctl enable strongswan", make it auto start every boot.


# things to notice
The script disable kernel module iptable_nat, so iptables maybe not work sometimes.
I don't know how to enable nftable every boot on jessie now, so you should run network after boot.
