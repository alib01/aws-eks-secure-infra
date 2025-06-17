# aws-eks-secure-infra
# AWS EKS + RDS + ALB + Secure SFTP Architecture

## 📌 Project Overview
This project provisions a production-ready AWS infrastructure that includes:

- **Amazon EKS** with Managed Worker Nodes
- **Amazon RDS** (MySQL) for persistent backend storage
- **Application Load Balancer (ALB)** for external UI access
- **AWS Transfer Family SFTP** with:
  - S3 as backend
  - Lambda-based password authentication
- **CloudWatch** for centralized logging and alerting
- **AWS Config, GuardDuty, SecurityHub** for continuous compliance
- **SNS** for alert delivery (security findings & CloudWatch alarms)

## 🧱 Architecture Diagram


## 🔧 Tech Stack
| Component       | AWS Service |
|----------------|-------------|
| Container Orchestration | Amazon EKS |
| Database        | Amazon RDS |
| UI Exposure     | Application Load Balancer |
| Secure File Transfer | AWS Transfer Family (SFTP) + Lambda |
| Monitoring      | Amazon CloudWatch |
| Security        | AWS Config, GuardDuty, SecurityHub |
| Notifications   | Amazon SNS |

## 📂 Infrastructure Breakdown
### 🐳 EKS Cluster
- Deployed using eksctl
- Managed node group with auto-scaling
- Kubernetes dashboard secured via IAM roles

### 💾 RDS
- Multi-AZ MySQL
- Encrypted storage
- Security Group tied to cluster nodes only

### 🌐 ALB
- Targets exposed via Kubernetes Ingress Controller
- HTTPS with ACM

### 🔐 SFTP + S3
- AWS Transfer Family with S3 backend
- Lambda function for dynamic password authentication

### 🛡️ Security
- Config Rules for compliance auditing
- GuardDuty enabled across regions
- SecurityHub consolidating all findings
- All alerts sent to SNS → Email

### 🔔 Monitoring
- CloudWatch Dashboards and Alarms (e.g., CPU, memory, DB connections)
- Logs stored in CloudWatch Log Groups

## 🚀 Deployment
All infrastructure provisioned via:
- [ ] Terraform (preferred)
- [ ] AWS CDK
- [ ] Manual for selected resources (e.g., Transfer Family setup)

## 📬 Outputs
- ALB DNS for UI
- SFTP Server Endpoint
- SNS Topic Subscriptions

## 📚 Learnings
- Multi-layer security in AWS
- Fine-grained IAM access for Kubernetes workloads
- Real-world monitoring and alerting design
