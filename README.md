# ATD-Lab-Reset

This is a collection of Ansible playbooks/configs, configlets (in the form of .cfg text files), and YAML files to configure the Arista ATD lab envioronment 
for the Arista ACE Level 5 (automation) certification course lab topology (as of July 2021). 

This will **only** work on the ATD Level 5 labs (and perhaps Level 4), but you can modidfy the YAML files and playbooks to suit other environments. 

The playbooks/configs/YAML files will set the Level 5 lab environment into one of three configurations (more comming later): 

* Default
* eBGP-based underlay (for MP-BGP EVPN VXLAN)
* OSPF-based underlay (for MP-BGP EVPN VXLAN)

The playbooks will set the configlets, upload any that need to be uploaded, and attach them to devices. It will create containers (but does not delete them). 

This does **not** create the change control or execute the change control. At this time, that must be done manually by an administrator. 

## Getting Started

First, make sure that the arista.cvp collection is installed. (You may need to do this every time the lab environment starts up.)

    > ansible-galaxy collection list | grep cvp
    arista.cvp 3.1.1  

If it's not installed, use the <code>ansible-galaxy collection install</code> command. 

    > ansible-galaxy collection install arista.cvp

You will also (as of September 2021) update the cvprac Python library

    > pip install cvprac --upgrade

Now that the environment is ready, clone the ATD-Lab-Reset repo to the ATD VS-Code environment (Terminal). 

    > git clone https://github.com/tonybourkesdnpros/ATD-Lab-Reset.git
    
This will create a new directory called ATD-Lab-Reset.

Edit the inventory.yml file to reflect the password for your particular enviroment: 

<code>           ansible_password: aristaXXXX</code>

## The Playbooks

There are currently three different Ansible playbooks: 

* CVP-default.yml
* CVP-eBGP.yml
* CVP-OSPF.yml

### CVP-default.yml

This playbook resets the lab to the default container topology and all devices to the default configlets. It **does not** delete any configlets that have been uploaded or added in other ways. 

### CVP-eBGP.yml

This playbook configures the lab with an eBGP-based underlay that encompasses DC1 and DC2, along with the configuration for the DCI switch to connect them. It doesn't have the MP-BGP overlay or any Tenant networks. 

### CVP-OSPF.yml

This playbook configures the lab with an OSPF-based underlay that encompasses DC1 and DC2, along with the configuration for the DCI switch to connect them. It doesn't have the MP-BGP overlay for any Tenant networks. 

## The Vars Files

The vars file contains the configlet locations, the container topology, and the configlet to device associations, all described in YAML. 


    
