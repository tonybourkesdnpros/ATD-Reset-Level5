# ATD-Lab-Reset

This is a collection of Ansible playbooks/configs, configlets (in the form of .cfg text files), and YAML files to configure the Arista ATD lab envioronment 
for the Arista ACE Level 5 (automation) certification course lab topology (as of July 2021). 



## Getting Started

First, make sure that the arista.cvp collection is installed. (You may need to do this every time the lab environment starts up.)

    > ansible-galaxy collection list | grep cvp
    arista.cvp 3.1.1  

If it's not installed, use the <code>ansible-galaxy collection install</code> command. 
<code>ansible-galaxy collection install arista.cvp</code>

Download the ATD-Lab-Reset environment to your local system (a system that has Ansible installed, the arista.cvp collection, Python, and access to the CloudVision Portal server). 

    > git clone https://github.com/tonybourkesdnpros/ATD-Lab-Reset.git
    
This will create a new directory called ATD-Lab-Reset.

Edit the inventory.yml file to reflect the password for your particular enviroment: 

<code>           ansible_password: aristaXXXX</code>
