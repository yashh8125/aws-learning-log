# Day 2: Private subnet, NAT and bastion

## What I built
- Private EC2 (no public IP) in private-subnet-1a
- NAT gateway in a public subnet + private route table
- Bastion host and SSH jump to the private instance

## What I learned
- Private instances reach out via NAT but can't be reached from outside
- Agent forwarding (`ssh -A`) lets me hop without copying the key
- The NAT's Elastic IP is what outside sites see (curl confirmed it)

## What went wrong / confusing
- NAT console now has Regional vs Zonal mode; I used Zonal
- Bastion from Sunday was terminated; had to launch a new one
- SSH timed out because my IP changed and the security group rule was stale
- Ran ssh-add inside the bastion by mistake; the key lives on the laptop

## Cost awareness
- NAT gateway ~$0.045/hour; deleted right after the test

## Questions for next time
- What does a VPC endpoint (S3 gateway) change versus a NAT?
- How would this look with Terraform?
