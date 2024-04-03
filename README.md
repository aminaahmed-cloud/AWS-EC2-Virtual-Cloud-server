# Deploying Web Application on EC2 Instance

This guide provides step-by-step instructions to deploy a web application on an EC2 instance on AWS using Docker.

## Step 1: Create an EC2 Instance on AWS

- Log in to your AWS Management Console.
- Go to the EC2 Dashboard.
- Click on the "Launch Instance" button.
- Choose an Amazon Machine Image (AMI), instance type, configure instance details, add storage, configure security groups, and review your instance launch.
- Create a new key pair or use an existing one to connect to the instance via SSH.
  
****

<img src="https://i.imgur.com/ekLGByl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

****

<img src="https://i.imgur.com/cTSlHs0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

****

<img src="https://i.imgur.com/Naw4NA1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

****

<img src="https://i.imgur.com/msVAxrt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

****

<img src="https://i.imgur.com/p2KziOt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

****

<img src="https://i.imgur.com/WtmEvDH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

****

<img src="https://i.imgur.com/M1COLJl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

****

<img src="https://i.imgur.com/YnGsVHV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


## Step 2: Connect to the EC2 Instance with SSH

- Open a terminal window.
- Use the `ssh` command to connect to your EC2 instance using the key pair you generated or selected during instance creation. Replace `your-key.pem` and `ec2-user` with your key pair and instance user respectively:

  ```
  ssh -i /path/to/your-key.pem ec2-user@your-ec2-public-ip

  ``` 

## Step 3: Install Docker on the Remote EC2 Instance

- **Update the package index**:

  ```
  sudo yum update -y

  ```

- **Install Docker**:

  ```bash
  sudo amazon-linux-extras install docker -y
  ```

- **Start and enable the Docker service**:

  ```bash
  
   sudo service docker start
   sudo usermod -a -G docker ec2-user

  ```

## Step 4: Run Docker Container from a Private Repository

- **Log in to your Docker registry**:

   ```
   docker login your-private-registry-url

   ```
- **Pull the Docker image**:
  
   ```
   docker pull your-private-image

   ```

- **Run the Docker container**:

   ```
   docker run -d -p 80:80 your-private-image

   ```

****

<img src="https://i.imgur.com/aVRUVPw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

****

<img src="https://i.imgur.com/iQBP9u3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

****

<img src="https://i.imgur.com/flkYy9B.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


## Step 5: Configure EC2 Firewall to Access the App Externally from a Browser

- Go to the EC2 Dashboard in AWS Management Console.
- Select the security group associated with your EC2 instance.
- Edit inbound rules to allow traffic on port 80 (HTTP) or any other port your application is running on.
- Add a rule with source "0.0.0.0/0" to allow access from any IP address, or specify the IP range you want to allow.



