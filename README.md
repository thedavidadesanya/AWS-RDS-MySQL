# Secure MySQL Deployment on AWS RDS

## Overview
This project demonstrates deploying a cost-effective and secure MySQL database
using Amazon RDS Free Tier, following AWS security best practices.

## Architecture
- Amazon RDS (MySQL 8.0)
- Default VPC
- IP-restricted Security Groups
- SQL Electron client

## Security Design Decisions
- Public access enabled for learning, restricted to a single IP
- Encryption at rest using AWS-managed KMS key
- Strong credentials stored locally (not committed)
- Automated backups enabled

## Implementation Steps
1. RDS instance creation
2. Network security configuration
3. Secure client connection via SQL Electron
4. Database and schema creation

## Validation
- Successfully connected using SQL Electron
- Created application database and tables
- Verified data access with SQL queries

## Future Enhancements
- Move RDS to private subnet
- Attach EC2 via security group reference
- Integrate with Transit Gateway for multi-VPC architecture
