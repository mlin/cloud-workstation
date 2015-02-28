# Cloud workstation bootstrap

1. Create cloud-workstation security group: tcp 22 0.0.0.0/0, udp 60000-61000 0.0.0.0/0
1. Create an EC2 keypair
1. Identify hvm:ebs-ssd [Ubuntu AMI](http://cloud-images.ubuntu.com/locator/ec2/) for desired version and region
1. Launch instance with all of the above. Check Auto-Assign Public IP, root volume size
1. Create and associate Elastic IP
1. Set DNS record
1. Set [Auto Recovery](https://aws.amazon.com/blogs/aws/new-auto-recovery-for-amazon-ec2/)
