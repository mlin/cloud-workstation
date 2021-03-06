# Cloud workstation bootstrap

### EC2 console

1. Create cloud-workstation security group: tcp 22 0.0.0.0/0, udp 60000-61000 0.0.0.0/0
1. Key Pairs: import id_rsa.pub
1. Identify bionic amd64 hvm:ebs-ssd [Ubuntu AMI](http://cloud-images.ubuntu.com/locator/ec2/) for desired region
1. Launch instance with all of the above. Check Auto-Assign Public IP, root volume size
1. Create and associate Elastic IP and DNS record if desired

### Ansible playbook

1. `ssh ubuntu@hostname`
2. `sudo bash -c 'apt-get update && apt-get install git ansible -y'`
3. `sudo ansible-pull -d /etc/cloud-workstation -U https://github.com/mlin/cloud-workstation.git -i 'localhost,' -v`
4. Set `/etc/hostname` and/or [Dynamic DNS](https://gist.github.com/larrybolt/6295160) if desired (increase crontab frequency to */2)
5. `sudo service ssh restart`

Thereafter the playbook can be executed with `sudo /etc/cloud-workstation/update`.

# Access

- `mosh mlin@hostname`
- x2go
