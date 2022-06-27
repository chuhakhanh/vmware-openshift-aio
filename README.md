# vmware-openshift-aio

## Setup
### Get data
    git clone https://github.com/chuhakhanh/vmware-openshift-aio
    git pull --branch master https://github.com/chuhakhanh/vmware-openshift-aio
    cd vmware-openshift-aio
    cp -u config/hosts /etc/hosts
    cp config/2022_03.repo /etc/yum.repos.d/
    yum install -y sshpass 
    ssh-keygen
### Setup virtual machines cluster: create, destroy 

    ansible-playbook -i config/inventory setup_openshift_lab_environment.yml -e action="create"
    ansible-playbook -i config/inventory setup_openshift_lab_environment.yml -e action="destroy" 
    chmod u+x ./script/key_copy.sh; ./script/key_copy.sh config/inventory
    ansible-playbook -i config/inventory prepare_all_node.yml
    
### Setup openshift software cluster
    ansible-playbook -i config/inventory setup_openshift_software_cluster.yml

