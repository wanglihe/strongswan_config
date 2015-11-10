# strongswan_config
configure a strongswan ipsec subnet with nftable and linux 4.2 on debian jessie

# before install
check your system installed nftables and linux-image-4.2.0, these packages from jessie-backports,
and then disable kernel module iptable_nat, enable nf_nat, because nftables can't work with iptable_nat.
