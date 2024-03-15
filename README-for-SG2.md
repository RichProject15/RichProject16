# Security Group Setup on AWS with CloudFormation

## Overview
This CloudFormation template automates the creation of security groups on AWS for specified VPCs and subnets. It allows you to define rules for inbound and outbound traffic to secure your network infrastructure.

## Resources
The template creates the following security groups:

### RichCFWebServerSG
- **Description**: Allows access on ports 80, 22, and 3389.
- **Group Name**: RichCFWebServerSG
- **Ingress Rules**:
  - Port 80 (HTTP) from any IP address (0.0.0.0/0)
  - Port 22 (SSH) from any IP address (0.0.0.0/0)
  - Port 3389 (RDP) from any IP address (0.0.0.0/0)
- **Tags**:
  - Name: RichCFWebServerSG
  - Purpose: A security group for the web server and more
  - Project: Project for ICTCLD505 AT2 Part 3
  - Owner: Richard
- **VPC ID**: vpc-0eef41bbfec980a05

### RichCFWebServerHTTPS
- **Description**: Allows access on port 443 (HTTPS).
- **Group Name**: RichCFWebServerHTTPS
- **Ingress Rules**:
  - Port 443 (HTTPS) from any IP address (0.0.0.0/0)
- **Tags**:
  - Name: RichCFWebServerHTTPS
  - Purpose: A security group for just HTTPS for the web server
  - Project: Project for ICTCLD505 AT2 Part 3
  - Owner: Richard
- **VPC ID**: vpc-0eef41bbfec980a05

### RichCFDatabaseSG
- **Description**: Allows access to MySQL database on RDS.
- **Group Name**: RichCFDatabaseSG
- **Ingress Rules**:
  - Port 3306 (MySQL) from the security group RichCFWebServerSG
- **Tags**:
  - Name: RichCFWebServerSG
  - Purpose: A security group for the MySQL database on RDS
  - Project: Project for ICTCLD505 AT2 Part 3
  - Owner: Richard
- **VPC ID**: vpc-0eef41bbfec980a05

## Outputs
The template exports the following security group IDs:

- RichCFWebServerSG: Exported as !Ref RichCFWebServerSG
- RichCFWebServerHTTPS: Exported as !Ref RichCFWebServerHTTPS
- RichCFDatabaseSG: Exported as !Ref RichCFDatabaseSG
