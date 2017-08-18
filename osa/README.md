# Openstack-Ansible

## For initial configuration
    yum install -y bridge-utils iputils lsof lvm2 ntp ntpdate openssh-server sudo tcpdump
    echo 'bonding' >> /etc/modules-load.d/openstack-ansible.conf; echo '8021q' >> /etc/modules-load.d/openstack-ansible.conf

## NetworkManager
    nmcli c add type vlan ifname eth1.10 dev eth1 id 10
    nmcli c add type bridge ifname br-mgmt
    nmcli c mod bridge-br-mgmt bridge.stp no
    nmcli c mod bridge-br-mgmt ipv4.method manual ipv4.addresses 172.29.236.11/22
    nmcli c mod vlan-eth1.10 connection.master br-mgmt connection.slave-type bridge
    nmcli c up bridge-br-mgmt
    nmcli c up vlan-eth1.10
    nmcli c sh vlan-eth1.10
    nmcli c mod vlan-eth1.10 802-3.mtu 1450

    nmcli c add type vlan ifname eth1.20 dev eth1 id 30
    nmcli c add type bridge ifname br-storage
    nmcli c mod bridge-br-storage bridge.stp no
    nmcli c mod bridge-br-storage ipv4.method manual ipv4.addresses 172.29.244.11/22
    nmcli c mod vlan-eth1.20 connection.master br-vxlan connection.slave-type bridge
    nmcli c up bridge-br-storage
    nmcli c up vlan-eth1.20
    nmcli c sh vlan-eth1.20
    nmcli c mod vlan-eth1.20 802-3.mtu 1450

    nmcli c add type vlan ifname eth1.30 dev eth1 id 30
    nmcli c add type bridge ifname br-vxlan
    nmcli c mod bridge-br-vxlan bridge.stp no
    nmcli c mod bridge-br-vxlan ipv4.method manual ipv4.addresses 172.29.240.11/22
    nmcli c mod vlan-eth1.30 connection.master br-vxlan connection.slave-type bridge
    nmcli c up bridge-br-vxlan
    nmcli c up vlan-eth1.30
    nmcli c sh vlan-eth1.30
    nmcli c mod vlan-eth1.30 802-3.mtu 1450

    nmcli c add type bridge ifname br-vlan
    nmcli c mod bridge-br-vlan bridge.stp no
    nmcli c mod System\ eth1 connection.master br-vlan connection.slave-type bridge
    nmcli c up bridge-br-vlan
    nmcli c up System\ eth1
    nmcli c mod System\ eth1 802-3.mtu 1450
