# Cloud DevOps Capstone

# Project Title: Capstone project for Udacity's "Cloud DevOps Engineer" Nanodegree Program.
This is the Cloud DevOps Nanodegree final project  from Udacity Implementation of blue/green development of "Hello World" website in AWS EC2 Instance by means of Jenkins.

# Objective
•	Working in AWS
•	Using Jenkins to implement Continuous Integration and Continuous Deployment
•	Building pipelines
•	Working with Ansible and CloudFormation to deploy clusters
•	Building Kubernetes clusters
•	Building Docker containers in pipelines

# Tools
•	Git & GitHub
•	AWS & AWS-CLI
•	Python3
•	Flask framework.
•	pip3
•	Pylint
•	Docker & Docker-Hub Registery
•	Jenkins
•	Kubernetes CLI (kubectl)
•	EKS
•	CloudFormation
•	BASH

# Development
development of "Hello World" website in AWS EC2 Instance by means of Jenkins.

# Project steps
•	Development
•	Jenkins
•	Setup Kubernetes Cluster
•	CI/CD Pipeline
•	EC2 instance with proper IAM roles
•	Jenkins installed (also Blue Ocean plugin used)
•	Docker installed
•	eksctl installed (aws cli v2 used)

# Cluster created by EKSCTL commend which creates cloud formation:
eksctl create cluster 
--name capstonecluster 
--version 1.16 
--region us-east-1 
--nodegroup-name standard-workers 
--node-type t2.small 
--nodes 2 
--nodes-min 1 
--nodes-max 3 

#Project created based on guidance from: https://medium.com/@andresaaap/jenkins-pipeline-for-blue-green-deployment-using-aws-eks-kubernetes-docker-7e5d6a401021


