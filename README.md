<h1>
Wordpress setup using Terraform & Ansible
 </h1>

 <h2>
 Tools to be used</h2> 
<h3>Terraform, Ansible, AWS</h3>
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
<p>1) Brief/Introduction on the project</p>
<p>  - explain in your own words what you are trying to implement</p></p></p>
<p>2) Installation or pre-requisites (steps to install)</p></p>
<p>  - AWS account</p>
<p>  - Setup Ansible</p>
<p>    - Installation steps</p>
<p>    - Verify ansible installation</p>
<p>  - Setup Terraform</p>
<p>    - Installation steps</p>
<p>    - Verify terraform installation</p>
<p>  - Setup Git</p>
<p>    - Installation steps</p>
<p>    - Verify git installation</p>
<p>  - Create a project directory & clone the repo</p>
<p>3) Steps that needs to be performed & actions performed during these steps</p>
<p>  - explain things, commands, screenshots, output screenshots, codes</p>
<p>  A) Create AWS key pair</p>
<p>    - Create a key pair</p>
<p>    - Download the keypair & add it to the machine/lab</p>
<p>    - Change the permission of the pem file</p>
<p>  B) Create/Download the Ansible playbook/roles to setup wordpress server</p>
<p>    - variables - configure</p>
<p>  C) Create the Terraform Configuration file - to create Ubuntu server - automate the Wordpress setup inside this server</p>
<p>    - Find the VPC ID & AMI - aws rss configuration</p>
<p>    - Create the configuration file (.tf)</p>
<p>      - locals - local variables</p>
<p>      - provider - aws - access_key, secret_key, token, region</p>
<p>      - resource - aws_security_group - ingress & egress</p>
<p>      - resource - aws_instance - ami, instance_type, vpc_security_group_ids, key_name, tags</p>
<p>      - provisioner - remote-exec - connection - check the SSH connectivity - using public_ip</p>
<p>      - provisioner - local-exec - create inventory file - add the public_ip of instance created to the inventory file</p>
<p>      - provisioner - local-exec - invoke the ansible-playbook (setup wordpress) - with custom inventory -i - with the instance user -u - specify the private key --private-key</p>
<p>      - output - print the output of newly created machine - browse this to get the WP page</p>
<p>  D) Create Ansible configuration to Skip Host Verification (host_key_checking)</p>
<p>     Da) Save your files to remote repo - git push</p>
<p>  E) Execute Terraform workflow</p>
<p>  F) Verify the WP setup - up & running - Browse - instance_ip -> screenshot of the WP page</p>
<p>  G) Destroy the resources - using terraform</p>
<p>4) Conclusion</p>

