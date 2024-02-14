# Secure-VPC-Setup-with-EC2-Instances

### Mastering AWS VPC configurations for secure and efficient networking! 🛡️ Today, you will be able to tackled the challenge of accessing a private subnet's EC2 server from a public subnet using an Application Load Balancer (ALB) and a bastion jump host, all while ensuring robust security measures. Here's a breakdown of the steps I followed:

1️⃣ Set up the VPC: Created a custom VPC with public and private subnets using the AWS Management Console or AWS CLI.

 ![image](https://github.com/Sthatikonda8161/Secure-VPC-Setup-with-EC2-Instances/assets/136583514/e5bb69ca-8a48-4812-9236-244cf65ffc12)

- Create Custom VPC.
- availability Zones (AZs): 2.
- No.of Public subnets: 2
- No.of Private subnets: 2
- For VPC endpoints, if your instances must access an S3 bucket, keep the S3 Gateway default. Otherwise, instances in your private subnet can't access Amazon S3. So you can keep the default if you might use an S3 bucket in the future. If you choose None, you can always add a gateway VPC endpoint later on.
- Choose Create VPC.

2️⃣ Configure NAT Gateway or NAT Instance: Implemented a NAT Gateway or NAT Instance in the public subnet to allow instances in the private subnet to initiate outbound traffic to the internet.

3️⃣ Launch EC2 Instances: Launched two EC2 instances in private subnets, ensuring proper security groups and IAM roles.

- Create an Auto Scaling group
- launch EC2 Instances in your private subnets.
- which is a collection of EC2 instances with a minimum of 1, maximum of 4, and desired size of 2. 

4️⃣ Create a bastion host (Jump Host): Deployed a bastion host in the public subnet to securely access instances in the private subnet within your "Project VPC".

- launch Bastion host EC2 Instance in your public subnet.
- This must be in your VPC(Project VPC).
- Allow SSH
- Download the keyvaluepair.
- Auto assign Public IP.
- Create Host.
- cp file.pem into your Bastion host by using the scp command.
  
```
scp -i </location of/file.pem> <location of/file.pem> ubuntu@<Public Ip>: /home/ubuntu
```
- SSH into bastion host.

```
ssh -i </location of /file.pem> ubuntu@<Public Ip>
```
- ls ,Once cp is successfully done you will be able to see the file.pem in the bastion host server.

```
ssh -i <file.pem> ubuntu@<Private Ip>
```
- Now you will be in EC2 Instance which in your private subnet.

- Deploy your application.

5️⃣ Set up Network ACLs: Configured Network ACLs to control traffic at the subnet level, providing an additional layer of security beyond security groups.

- Set up an internet gateway to allow internet access for instances in the public subnet. Configure NAT gateway or NAT instance to enable outbound internet access for instances in the private subnet. Create appropriate route tables and associate them with the subnets.

6️⃣ Configure ALB: Created an Application Load Balancer (ALB) to distribute incoming traffic to the EC2 instances in the private subnet.

- Create a target group for your EC2 Instances.
- Create a Application load balancer.
- 
- which distributes traffic evenly across the instances in your target group.

7️⃣ Test Connectivity: Verified connectivity by accessing the private EC2 instances through the ALB via the bastion host.

- Now your able to access your servers in your private subnet in your secured VPC.

![vpc-example-private-subnets](https://github.com/Sthatikonda8161/Secure-VPC-Setup-with-EC2-Instances/assets/136583514/9795a659-f368-447c-8959-f09331a527c6)

