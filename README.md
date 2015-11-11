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
change xxx in the line : PSK "xxx" to some word, this is the preshared key, don't delete the doulbe quote.

edit ipsec.conf, change rightsubnet and rightsourceip to something you like, it is the subnet for your client.

run the script "config" with arg of your server ip address.
example: ./config 10.2.3.4

# about service
The service can be modified by these commands:
try the command "systemctl start strongswan", start service.
try the command "systemctl stop strongswan", start service.
try the command "systemctl status strongswan", see status.
try the command "systemctl enable strongswan", make it auto start from next boot.
try the command "systemctl disable strongswan", make it not start from next boot.


# things to notice
The script disable kernel module iptable_nat, so iptables maybe not work sometimes.

I don't know how to enable nftable every boot on jessie now, so you should run "network" after boot.

nft seems runs with bugs, after run the script "network" many times, the nftables add "masquerade"
many times. run "nft list ruleset" to see the result. If you want clean nftables, just run
"nft flush ruleset".
