# packstack

## Reference
https://www.openstack.org/software/

## Install ansible
`yum install -y ansible`

## Generate ssh-key and copy public key
`ssh-keygen -t rsa`  
`cat ~/.ssh/id_rsa.pub | ssh root@compute01_host 'mkdir -p .ssh; cat >> .ssh/authorized_keys'`  
`cat ~/.ssh/id_rsa.pub | ssh root@compute02_host 'mkdir -p .ssh; cat >> .ssh/authorized_keys'`  

## Install
`ansible-playbook -i inventory/hosts init_node.yml`  
`ansible-playbook -i inventory/hosts packstack.yml`
