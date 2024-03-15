## Socks Shop Deployment on Kubernetes (.md)

**# Project Overview**

This project deploys the Socks Shop microservices application on a Kubernetes cluster using Infrastructure as Code (IaC) for automation and efficiency. The deployment leverages modern DevOps practices and tools to ensure a quick, reliable, and secure process.

**# Technology Stack**
The following technologies were used to complete this project:

* **IaC Tool:** Terraform: [https://www.terraform.io/](https://www.terraform.io/)
* **CI/CD Tool:** GitHub Actions
* **Cloud Provider:** AWS
* **Kubernetes Cluster:** AWS EKS
* **Monitoring and Logging:** Prometheus, Grafana, Elasticsearch, Kibana

**# Folder Structure**

```
.
├── README.md         # Project documentation
├── .github
│   └── workflows    # Directory containing workflow definition files
├── terraform
    ├── terraform-images # Directory for infrastructure setup images
│   ├── main.tf       # Main Terraform configuration file
│   ├── variables.tf  # Terraform variables file
│   └── ...          # Additional Terraform configuration files (modules, etc.)
└── kubernetes
    ├── k8s-images       # Directory for logging and monitoring images
    ├── manifests-logging  # Directory for logging deployment YAML files
    ├── manifests-monitoring     # Directory for monitoring service YAML files
    └── ...          # Additional Kubernetes configuration files (ingresses, secrets, etc.)
```


**# IaC Documentation (Terraform)**

This section describes the Terraform configurations used to provision the infrastructure for the Socks Shop application on your Kubernetes cluster.

* **Resources:**
The Terraform files within the `terraform` directory define the following resources:

| Resource | Description|
| ---------|------------|
| Provider | defines the AWS provider configuration.|
| VPC Module | defines the resources needed to create a Virtual Private Cloud (VPC) with public and private subnets, NAT gateways, and DNS settings|
| EKS Cluster Module | defines the resources needed to create an EKS cluster within the previously created VPC.|
| Cluster Name | defines a local value named cluster_name|


**Please refer to the specific Terraform code files within the `terraform` directory for detailed configuration specifics.**

**# CI/CD Workflow Documentation (GitHub Actions)**

This section explains the workflow defined in the `.github/workflows` directory. This workflow automates the deployment process triggered by code changes in your repository.

* **Trigger:** The workflow is triggered on pushing to master.
* **Jobs:** The workflow contains a job named terraform and deploy to eks. This job performs the following tasks:
  * Checks out your code from the GitHub repository.
  * Configuring aws credentials, login to Amazon ECR, building the application, installing kubectl and terraform, running Terraform to provision infrastructure, deploying the application to the Kubernetes cluster.
 
**# Kubernetes**
The files within the `kubernetes` directory contain the logging and monitoring manifest files as well as a readme for implementing promethus and grafana. The manifest file for the complete application, and ingress file are also included. For test purposes, the secrets are stored using github's secret service.

**# Conclusion**

This documentation provides an overview of the tools, technologies, and processes used to deploy the Socks Shop application on a Kubernetes cluster using Terraform and automated workflows (Github Actions). Refer to the specific code files and additional resources mentioned throughout this document for a deeper understanding of the implementation details.
