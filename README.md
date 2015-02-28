# Cloud workstation bootstrap

## Launch actions in EC2 console

1. Create cloud-workstation security group: tcp 22 0.0.0.0/0, udp 60000-61000 0.0.0.0/0
1. Create an EC2 keypair, `chmod go-rwx` local copy
1. Identify hvm:ebs-ssd [Ubuntu AMI](http://cloud-images.ubuntu.com/locator/ec2/) for desired version and region
1. Launch instance with all of the above. Check Auto-Assign Public IP, root volume size
1. Create and associate Elastic IP
1. Set DNS record
1. Set [Auto Recovery](https://aws.amazon.com/blogs/aws/new-auto-recovery-for-amazon-ec2/)

## Ansible playbook

1. `ssh -i /path/to/key.pem ubuntu@hostname`
2. sudo bash -ex -c 'add-apt-repository ppa:rquillo/ansible -y && apt-get update && apt-get install ansible -y'
3. sudo ansible-pull -d /etc/cloud-workstation -u https://github.com/mlin/cloud-workstation.git
