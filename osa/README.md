# Openstack-Ansible

## For initial configuration
    yum install -y bridge-utils iputils lsof lvm2 ntp ntpdate openssh-server sudo tcpdump
    echo 'bonding' >> /etc/modules-load.d/openstack-ansible.conf; echo '8021q' >> /etc/modules-load.d/openstack-ansible.conf

## NetworkManager
    nmcli c add type vlan ifname eth1.10 dev eth1 id 10
    nmcli c add type bridge ifname br-mgmt
    nmcli c mod bridge-br-mgmt bridge.stp no
    nmcli c mod bridge-br-mgmt ipv4.method manual ipv4.addresses 172.29.236.13/22
    nmcli c mod vlan-eth1.10 connection.master br-mgmt connection.slave-type bridge
    nmcli c up bridge-br-mgmt
    nmcli c up vlan-eth1.10
    nmcli c sh vlan-eth1.10



