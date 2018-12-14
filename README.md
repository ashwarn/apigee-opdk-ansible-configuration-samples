# Apigee OPDK Ansible Configuration Sample

This repository is a template that can be used to configure Ansible to work with this Apigee OPDK 
Ansible framework. This template is configured to work with the [Apigee OPDK Ansible Inventory Samples](https://github.com/carlosfrias/apigee-opdk-ansible-inventory-samples)
so that an Ansible controller may be used to manage multiple Apigee planets. The template is documented.


# Usage

The usage of this template requires that the file be copied and modified as indicated by the inline
documentation provided in the file. The Ansible environmental variable `ANSIBLE_CONFIG` can be used
to reference an updated template file so that the Ansible environment can be set explicitly to a
particular planet. Setting a configuration to one of these files is accomplished in the following way:

    export ANSIBLE_CONFIG=~/.ansible/multi-planet-configuration/dev.cfg

## Usage Recommendations

It is recommended that you name this file in alignment with your target environment name. This means 
that Apigee planets for development, test, stage and prod should have configuration files named 
development.cfg, test.cfg, stage.cfg, and prod.cfg respectively. This also means that the inventory 
folder should contains sub-folders named development/, test/, stage/, and prod/ that hold inventory files
for the nodes in each of those environments. 

### Usage Sample 

This example configures a 5 node dev environment:

1. Copy the template file and name according to your target environment name:


    cp ~/.ansible/multi-planet-configuration/templates/apigee-opdk-configuration-template.cfg ~/.ansible/multi-planet-configuration/dev.cfg

1. Modify the new file and update the fields as indicated:


    vim ~/.ansible/multi-planet-configuration/dev.cfg
        update UPDATE_WITH_SSH_USER_NAME to your SSH user name
        update TARGET_ENVIRONMENT_NAME_CONVENTION to dev in all locations
        Save the file
     
1. Configuration target folder should look like this:     
      
         
    ~/.ansible/multi-planet-configurations/
    └── dev.cfg

1. Create the target inventory folder:

       
    cp -R ~/.ansible/inventory/templates/edge-5/ ~/.ansible/inventory/dev
       
1. Update the target inventory file as indicated in the file. The inventory folder should look this:
       
       
    ~/.ansible/inventory/dev
    └── edge-dc1
        
1. Activate the configuration like this: 


    export ANSIBLE_CONFIG=~/.ansible/multi-planet-configuration/dev.cfg
               
1. Ansible commands that are invoked after activation will use the indicated configuration. This applies
to Ansible ad-hoc commands as well. 

<!-- BEGIN Google Required Disclaimer -->

# Not Google Product Clause

This is not an officially supported Google product.
<!-- END Google Required Disclaimer -->
<!-- BEGIN Google How To Contribute -->
# How to Contribute

We'd love to accept your patches and contributions to this project. Please review our [guidelines](CONTRIBUTING.md).
<!-- END Google How To Contribute -->