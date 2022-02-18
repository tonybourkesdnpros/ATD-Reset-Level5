# ATD-Lab-Reset

This is a collection of Ansible playbooks/configs, configlets (in the form of .cfg text files), and YAML files to configure the Arista ATD lab envioronment 
for the Arista ACE Level 5 (automation) certification course lab topology (as of July 2021). 

This will **only** work on the ATD Level 5 labs (and perhaps Level 4), but you can modidfy the YAML files and playbooks to suit other environments. 

The playbooks/configs/YAML files will set the Level 5 lab environment to the baseline configlet assignments: 

The playbooks will set the configlets. It will create containers (but does not delete them). 

This does **not** create the change control or execute the change control. At this time, that must be done manually by an administrator. 

## Getting Started

Make sure the CVP Ansible modules are installed 

    ansible-galaxy collection install arista.cvp

You will also (as of September 2021) update the cvprac Python library

    pip install cvprac --upgrade

Now that the environment is ready, clone the ATD-Lab-Reset repo to the ATD VS-Code environment (Terminal). 

    > git clone https://github.com/tonybourkesdnpros/ATD-Lab-Reset.git
    
This will create a new directory called ATD-Lab-Reset.

Edit the inventory.yml file to reflect the password for your particular enviroment: 

<code>           ansible_password: aristaXXXX</code>

## The Playbooks

There are currently three different Ansible playbooks, but we only care about the 

* CVP-lab-reset.yml


### CVP-lab-reset.yml

This playbook resets the lab to the default container topology and all devices to the default configlets. It **does not** delete any configlets that have been uploaded or added in other ways. 

    > ansible-playbook playbooks/CVP-lab-reset.yml

### Execute Change Control

Create a change control with the tasks that the playbook triggered and excute the change control. 
    
