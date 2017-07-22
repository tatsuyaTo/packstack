# packstack
`yum install -y ansible`  
`ssh-keygen -t rsa`  
`cat ~/.ssh/id_rsa.pub | ssh user@host 'mkdir -p .ssh; cat >> .ssh/authorized_keys'`  
`ansible-playbook -i inventory/hosts init_node.yml`
`ansible-playbook -i inventory/hosts packstack.yml`

