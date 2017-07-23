# packstack

## Controller
`yum install -y ansible`  
`ssh-keygen -t rsa`  
`cat ~/.ssh/id_rsa.pub | ssh root@compute01_host 'mkdir -p .ssh; cat >> .ssh/authorized_keys'`  
`cat ~/.ssh/id_rsa.pub | ssh root@compute02_host 'mkdir -p .ssh; cat >> .ssh/authorized_keys'`  

## Install
`ansible-playbook -i inventory/hosts init_node.yml`  
`ansible-playbook -i inventory/hosts packstack.yml`
