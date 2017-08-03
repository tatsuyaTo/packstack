# packstack

## Reference
https://www.openstack.org/software/
https://www.rdoproject.org/

## Install ansible
`yum install -y ansible`

## Generate ssh-key and copy public key
`ssh-keygen -t rsa`  
`cat ~/.ssh/id_rsa.pub | ssh root@compute01_host 'mkdir -p .ssh; cat >> .ssh/authorized_keys'`  
`cat ~/.ssh/id_rsa.pub | ssh root@compute02_host 'mkdir -p .ssh; cat >> .ssh/authorized_keys'`  

## Install
`ansible-playbook -i inventory/hosts init_node.yml`  
`ansible-playbook -i inventory/hosts packstack.yml`

## Add CirrOS instance
    openstack server create \
        --flavor FLAVOR_ID \
        --image IMAGE_ID \
        --key-name KEY_NAME \
        --user-data USER_DATA_FILE \
        --security-group SEC_GROUP_NAME \
        --property KEY=VALUE \
        INSTANCE_NAME`

    openstack server create \
        --flavor m1.small \
        --image cirros \
        --nic net-id=internal \
        --security-group default \
        cirros_third

