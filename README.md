README

AWS Demo Page

This simple project demonstrates how to create an Amazon AWS ec2 instance, and sets up nginx with a single static webpage.
For simplicity sake, the entry point is a single Ansible playbook.

PREREQUISITES
The following items are needed before running this project
- Python 2
- Ansible 2.x
- boto, a Python library for AWS (pip install boto)
- A valid Amazon AWS account
- AWS account credentials
- An RSA keypair which has been imported into your AWS account

CONFIGURATION
Two files must be edited before running the example Ansible playbook:

conf/default.yml
  This file holds your AWS credentials, ec2 keyname, as well as other variables which you may not need to change.

ansible.cfg
  The only variable that needs to be configured is private_key_file.
  Here you must provide the path to the private RSA key used to create your example ec2 instance.

USAGE
Once the two configuration files are edited, you may invoke the playbook from Ansible like so:
ansible-playbook aws-nginx-demo-playbook.yml

Ansible will perform the following steps:
1. Create a new security group if needed
2. Create an ec2 instance with the security group applied
3. Wait for SSH to be active on the new target server
4. Install nginx
5. Configure nginx to serve a single static page which says only "Automation for the People"
6. Test that nginx is running, and that the correct page is being served
7. Output a debug line which shows the URL to verify that the playbook ran successfully

Ex.

```
TASK [debug web server] **********************************************************
ok: [n.n.n.n] => {
     "msg": "Browse to http://n.n.n.n to verify"
}
```
