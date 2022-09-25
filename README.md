<h3>
Wordpress setup using Terraform & Ansible
 </h3>

 <h2>
 Tools to be used</h2> 
Terraform, Ansible, AWS
 <h3>Change database entries ,regions and other variable in terraform.tfvars file
 And Database password in user.tfvars file </h3>
<h3>

  This script is only suitable for AWS LINUX 2 so make sure you have correct region and 
  ami id in that region.

  Make sure you have configured aws CLI in your local machine

  Ansible is installed in your local machine
  playbook_test.yml is a ansible script for LINUX 2

</h3>
  --------------------------------------------------------------------------------
 <h3> Security: </h3>
<p> EC2 will be launched in public subnet and RDS will be launched in private subnet </p>
<p> Only EC2 with defined security group can access RDS and RDS wont have internet access </p>


<----------------------------------------------------------------------------------------------------------------------->

<h2> Prerequisite </h2>
<p> Before launching Terraform template, aws cli should be installed and configured with proper access key and secret key </p>
<p> Terraform should be installed in your local machine </p>
<p> Ansible should be installed in youn local machine.
<p> Configure AWS CLI with <code> aws configure </code> if you havent configured already </p>

<------------------------------------------------------------------------------------------------------------------------>

<h2> STEPS: </h2>
1) Brief/Introduction on the project
  - explain in your own words what you are trying to implement
2) Installation or pre-requisites (steps to install)
  - AWS account
  - Setup Ansible
    - Installation steps
    - Verify ansible installation
  - Setup Terraform
    - Installation steps
    - Verify terraform installation
  - Setup Git
    - Installation steps
    - Verify git installation
  - Create a project directory & clone the repo
3) Steps that needs to be performed & actions performed during these steps
  - explain things, commands, screenshots, output screenshots, codes
  A) Create AWS key pair
    - Create a key pair
    - Download the keypair & add it to the machine/lab
    - Change the permission of the pem file
  B) Create/Download the Ansible playbook/roles to setup wordpress server
    - variables - configure
  C) Create the Terraform Configuration file - to create Ubuntu server - automate the Wordpress setup inside this server
    - Find the VPC ID & AMI - aws rss configuration
    - Create the configuration file (.tf)
      - locals - local variables
      - provider - aws - access_key, secret_key, token, region
      - resource - aws_security_group - ingress & egress
      - resource - aws_instance - ami, instance_type, vpc_security_group_ids, key_name, tags
      - provisioner - remote-exec - connection - check the SSH connectivity - using public_ip
      - provisioner - local-exec - create inventory file - add the public_ip of instance created to the inventory file
      - provisioner - local-exec - invoke the ansible-playbook (setup wordpress) - with custom inventory -i - with the instance user -u - specify the private key --private-key
      - output - print the output of newly created machine - browse this to get the WP page
  D) Create Ansible configuration to Skip Host Verification (host_key_checking)
     Da) Save your files to remote repo - git push
  E) Execute Terraform workflow
  F) Verify the WP setup - up & running - Browse - instance_ip -> screenshot of the WP page
  G) Destroy the resources - using terraform
4) Conclusion

