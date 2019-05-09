# Cloud workstation bootstrap

### Gcloud console

1. VPC network > Firewall rules `gcloud compute --project=xxxx firewall-rules create mosh --direction=INGRESS --priority=1000 --network=default --action=ALLOW --rules=tcp:22,udp:60000-61000 --source-ranges=0.0.0.0/0 --target-tags=mosh`
1. Add [project-wide SSH key](https://console.cloud.google.com/compute/metadata/sshKeys)
1. Launch instance with Ubuntu 18.04 and the mosh network tag
1. If static IP desired, set in VPC Network > External IP addresses

### Ansible playbook

1. `ssh mlin@hostname`
2. `sudo bash -c 'apt-get update && apt-get install git ansible -y'`
3. `sudo ansible-pull -d /etc/cloud-workstation -U https://github.com/mlin/cloud-workstation.git -C gcloud -i 'localhost,' -v`
4. Set `/etc/hostname` and/or [Dynamic DNS](https://gist.github.com/larrybolt/6295160) if desired (increase crontab frequency to */2)
5. `sudo service ssh restart`

Thereafter the playbook can be executed with `sudo /etc/cloud-workstation/update`.

# Access

- `mosh mlin@hostname`
- x2go
