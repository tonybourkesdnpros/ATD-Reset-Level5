# ATD-Lab-Reset (Level 5)

This is a collection of Ansible playbooks/configs, configlets (in the form of .cfg text files), and YAML files to configure the Arista ATD lab envioronment 
for the Arista ACE Level 5 (automation) certification course lab topology (as of July 2021). 

This will **only** work on the ATD Level 5 labs (and perhaps Level 4), but you can modidfy the YAML files and playbooks to suit other environments. 

The playbooks/configs/YAML files will set the Level 5 lab environment to the baseline configlet assignments: 

The playbooks will set the configlets. It will create containers (but does not delete them). 

This does **not** create the change control or execute the change control. At this time, that must be done manually by an administrator. 

## Getting Started

Because of an issue discovered with the Ansible collection arista.cvp version 3.3.1, you will need to downgrade your environment to 3.3.0. 

    ansible-galaxy collection install arista.cvp:==3.3.0

Now that the environment is ready, clone the ATD-Lab-Reset repo to the ATD VS-Code environment (Terminal). 

    > git clone https://github.com/tonybourkesdnpros/ATD-Reset-Level5.git
    
This will create a new directory called ATD-Reset-Level5.

Edit the inventory.yml file to reflect the password for your particular enviroment: 

<code>           ansible_password: aristaXXXX</code>

## The Playbooks

There is one playbook in the directory: This is the CVP-lab-reset playbook. 

* CVP-lab-reset.yml

### CVP-lab-reset.yml

This playbook resets the lab to the default container topology and all devices to the default configlets. It **does not** delete any configlets that have been uploaded or added in other ways. 

    > ansible-playbook playbooks/CVP-lab-reset.yml

### Execute Change Control

Create a change control with the tasks that the playbook triggered and excute the change control. 
    
