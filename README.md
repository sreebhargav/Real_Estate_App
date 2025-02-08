# 🏢 Real Estate Listing Web Application

This project is a **Real Estate Listing Web Application** built with a **Django** backend and a **React** frontend. The application is deployed on **Amazon Web Services (AWS)** using **Elastic Beanstalk**, **RDS** (PostgreSQL), and **S3** for storage. The infrastructure is designed to be **highly available**, **scalable**, and **secure**.

**Live Demo:** [Real Estate Listing App](http://reactappfe-env.eba-t5m7gmfr.us-east-1.elasticbeanstalk.com/)

---

## 📄 Table of Contents
- [📚 Introduction](#-introduction)
- [📊 Infrastructure Overview](#-infrastructure-overview)
- [🚀 AWS Resource Configuration](#-aws-resource-configuration)
  - [🌐 Virtual Private Cloud (VPC)](#-virtual-private-cloud-vpc)
  - [🔒 Security Groups](#-security-groups)
  - [🚀 Elastic Beanstalk Configuration](#-elastic-beanstalk-configuration)
    - [🌱 Frontend Deployment (React)](#-frontend-deployment-react)
    - [💻 Backend Deployment (Django)](#-backend-deployment-django)
  - [📂 Amazon RDS (PostgreSQL)](#-amazon-rds-postgresql)
  - [📁 Amazon S3 Configuration](#-amazon-s3-configuration)
  - [🔍 Logging and Monitoring](#-logging-and-monitoring)
  - [📑 CloudFormation](#-cloudformation)
- [🚀 Future Considerations](#-future-considerations)
- [📅 Appendix](#-appendix)
- [📚 Getting Started](#-getting-started)
- [🌐 License](#-license)

---

## 📚 Introduction
This documentation outlines the step-by-step configuration and deployment process of a **minimal Real Estate Listing Web Application** on the **AWS** platform. The application includes:

- **Django** backend for managing listings and user interactions.
- **PostgreSQL** database hosted on **Amazon RDS**.
- **React** frontend for the user interface.
- **Elastic Beanstalk** for deploying both frontend and backend.
- **S3** for storing frontend assets and user-uploaded images.

The entire infrastructure is designed for **high availability**, **scalability**, and **security**.

---

## 📊 Infrastructure Overview
The architecture follows a **multi-tiered design** leveraging the following AWS services:

- **Amazon VPC**: Custom virtual private cloud with public and private subnets.
- **Elastic Beanstalk**: Managed service for deploying frontend and backend applications.
- **Amazon RDS (PostgreSQL)**: Managed relational database service.
- **Amazon S3**: Storage for frontend assets and user-uploaded images.
- **AWS IAM**: Identity and Access Management for security roles.
- **AWS CloudWatch**: Logging and monitoring services.
- **AWS Auto Scaling**: Ensures high availability and scalability.
- **AWS CloudFormation**: Infrastructure as Code for automated deployments.
- **AWS Athena & Glue**: Services for querying and processing logs.

---

## 🚀 AWS Resource Configuration

### 🌐 Virtual Private Cloud (VPC)
- **Two public subnets** for the React frontend and Elastic Load Balancer.
- **Two private subnets** for the Django backend and PostgreSQL database.
- **Internet Gateway** for public access.
- **NAT Gateway** for secure internet access from private subnets.

### 🔒 Security Groups
- **Frontend Security Group**: Allows inbound traffic on ports **80/443** from the internet.
- **Backend Security Group**: Allows inbound traffic on ports **8000** and **8080** from the frontend.
- **Database Security Group**: Allows PostgreSQL connections on port **5432** from the backend.

### 🚀 Elastic Beanstalk Configuration

#### 🌱 Frontend Deployment (React)
- The React application is **dockerized** and deployed to Elastic Beanstalk.
- **CI/CD** pipeline using **GitHub Actions** automates deployments on pushes to the master branch.
- Configuration uses **Dockerrun.aws.json**.
- Load balancer and auto-scaling group (2 to 4 instances) are set up.

#### 💻 Backend Deployment (Django)
- The Django application is also **dockerized** and deployed to a separate Elastic Beanstalk environment.
- Environment variables for PostgreSQL connections are provisioned.
- The backend security group restricts access to the database.

### 📂 Amazon RDS (PostgreSQL)
- **Multi-AZ deployment** ensures high availability.
- Hosted in **private subnets** for security.
- **Automatic backups and snapshots** are enabled for disaster recovery.

### 📁 Amazon S3 Configuration
- S3 buckets store **user-uploaded images** and **frontend assets**.
- IAM roles configured to allow Django to upload images.
- Bucket policy allows **public read access** for images.

### 🔍 Logging and Monitoring
- **AWS CloudWatch** logs both backend and frontend activities.
- Elastic Beanstalk health monitoring enabled.
- **AWS Athena** is used to analyze logs.

### 📑 CloudFormation
- The infrastructure is managed using **AWS CloudFormation** (Infrastructure as Code).

---

## 🚀 Future Considerations

To further enhance the scalability, security, and maintainability of the application, future improvements could include:

- **AWS Web Application Firewall (WAF)**: Protection against common web attacks.
- **Amazon Aurora**: Optimized database for better scalability and failover.
- **CodePipeline Integration**: For more robust CI/CD automation.
- **Multi-region failover** using **Route 53 DNS failover** for higher availability.

---

## 📅 Appendix

- **S3 link to images**: [S3 Image Link](#)

---

## 📚 Getting Started

### 📅 Prerequisites
- **Node.js** and **npm** for the React frontend.
- **Python** and **pip** for the Django backend.
- **Docker** for containerization.
- **AWS CLI** configured with proper IAM roles.

### 🔄 Running Locally

1. **Clone the repository:**
```bash
git clone https://github.com/your-username/real-estate-app.git
cd real-estate-app
```

2. **Frontend Setup (React):**
```bash
cd frontend
npm install
npm start
```

3. **Backend Setup (Django):**
```bash
cd backend
pip install -r requirements.txt
python manage.py runserver
```

---

## 🌐 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.



