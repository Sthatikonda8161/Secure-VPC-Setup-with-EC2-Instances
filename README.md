# Secure-VPC-Setup-with-EC2-Instances
🚀 Day 1 in my DevOps journey:
- Mastering AWS VPC configurations for secure and efficient networking! 🛡️ Today, you will be able to tackled the challenge of accessing a private subnet's EC2 server from a public subnet using an Application Load Balancer (ALB) and a bastion jump host, all while ensuring robust security measures. Here's a breakdown of the steps I followed:

1️⃣ Set up the VPC: Created a custom VPC with public and private subnets using the AWS Management Console or AWS CLI.

 ![image](https://github.com/Sthatikonda8161/Secure-VPC-Setup-with-EC2-Instances/assets/136583514/e5bb69ca-8a48-4812-9236-244cf65ffc12)
- Create Custom VPC.
- availability Zones (AZs): 2.
- No.of Public subnets: 2
- No.of Private subnets: 2

2️⃣ Configure NAT Gateway or NAT Instance: Implemented a NAT Gateway or NAT Instance in the public subnet to allow instances in the private subnet to initiate outbound traffic to the internet.

- No.of NAT gateways: 1 per availability Zones (AZs)
  
3️⃣ Launch EC2 Instances: Launched two EC2 instances in private subnets, ensuring proper security groups and IAM roles.

4️⃣ Create a bastion host (Jump Host): Deployed a bastion host in the public subnet to securely access instances in the private subnet within your "Project VPC".

5️⃣ Set up Network ACLs: Configured Network ACLs to control traffic at the subnet level, providing an additional layer of security beyond security groups.

6️⃣ Configure ALB: Created an Application Load Balancer (ALB) to distribute incoming traffic to the EC2 instances in the private subnet.

7️⃣ Test Connectivity: Verified connectivity by accessing the private EC2 instances through the ALB via the bastion host.
