# demo_rha
The overall goal of this project is to provide a tangible example of the 
power of ansible automation. In this particular instance we are using 
ansible to provision an EC2, Create a security group, and then installing
and configuring Apache (with firewalld enabled).

Then to cleanup we are using a tear down role to undo all of the things we 
have just done.

## Playbook information:
The `demobuild` playbook is what kick's off the creation of the ec2 and
security group. It also generates a static inventory and places it in
`/tmp/inventory' using the public ip address of the previously created EC2.

The `demodestroy.yml` is a role designed to undo all of the things by means
of thermonuclear destruction (delete). 

The `playbooks` directory is where all of the intial testing playbooks and
configurations are saved for record keeping / notes. A lot of the playbooks
in the playbooks directory are executable and can be run with a `./` Be aware 
that the path to ansible-playbook is defined as `/usr/local/bin/ansible-playbook`
so you may have to change the path depending on your systems.

The `ansible.cfg` has a few parameters uncommented:
`inventory` - The inventory path is defined as `/tmp/inventory`
`remote_user`  is defined as `ec2-user`
`private_key_file` is defined as `~/.ssh/demo.pem`
`host_key_checking` is set to `false`

## Assumptions:
Ansible 2.9.10 is installed.

Authors: 
  jonny@redhat.com
  mholmes@redhat.com
