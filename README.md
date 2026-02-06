# Secure MySQL Deployment on AWS RDS

## Overview
This project demonstrates the deployment of a cost-effective and security-focused
MySQL database using Amazon RDS. The goal was to design a database layer that is
easy to manage, encrypted by default, and protected using network-level controls,
while remaining eligible for AWS Free Tier usage.

The database was successfully accessed using a SQL client (SQL Electron) and
documented with architecture diagrams and validation screenshots.

## Architecture
The architecture consists of an Amazon RDS MySQL instance deployed inside an
AWS VPC. Although public access is enabled for learning purposes, inbound access
is strictly restricted using security groups to allow connections only from a
trusted IP address.

<img width="661" height="361" alt="rds architecture drawio" src="https://github.com/user-attachments/assets/16a7d602-8114-4189-b899-9fc79c4d2a47" />

### Key Components
- Amazon RDS (MySQL 8.0)
- VPC with private subnet placement
- Security group enforcing least-privilege access
- SQL Electron client for database connectivity

## Security Design Decisions

Several security best practices were intentionally applied during deployment:

- **No public IP address**: The RDS instance does not receive a public IP. Access
  is provided through the RDS endpoint and controlled by security groups.
- **IP-restricted access**: Inbound MySQL traffic (TCP 3306) is limited to a single
  trusted client IP.
- **Encryption at rest**: Data is encrypted using the default AWS-managed KMS key.
- **Strong authentication**: A non-default master username and strong password
  were used. Credentials are not stored in the repository.
- **Automated backups**: Backups are enabled with a one-day retention period to
  balance cost and recoverability.
  
## Implementation Summary
1. Created a MySQL RDS instance using Free Tier–eligible resources.
2. Configured storage, backups, and encryption settings.
3. Applied a security group restricting database access to a single IP.
4. Retrieved the RDS endpoint and connected using SQL Electron.
5. Created an application database and tables to validate functionality.

## Validation & Testing
Connectivity and functionality were verified through the following steps:

- Successful connection to the RDS endpoint using SQL Electron
- Creation of a custom database and table schema
- Execution of SQL queries to confirm read/write access

Screenshots documenting each validation step are included in the repository.
![SQL Electron Connection](screenshots/sql-electron-connected.png)
![Database Created](screenshots/create-database.png)

## Trade-offs & Limitations
- Public access was enabled to allow direct client connectivity during development.
- The database is not yet integrated with an application layer (EC2 or container).
- No read replicas or Multi-AZ deployment were used to minimize cost.

## Future Enhancements
This project is designed to evolve into a larger, production-style architecture:

- Move RDS to fully private subnets
- Disable public access entirely
- Attach the database VPC to an AWS Transit Gateway
- Allow access only from application VPCs
- Integrate with EC2 or containerized services

These enhancements are explored further in the Transit Gateway multi-VPC project.

## Skills Demonstrated
- AWS RDS provisioning and management
- Secure network design using security groups
- Database connectivity and validation
- Cost-aware cloud architecture
- Infrastructure documentation and diagramming

