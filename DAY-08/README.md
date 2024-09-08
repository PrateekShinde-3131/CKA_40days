# Kubernetes Deployment and ReplicaSet Exercise:
This repository demonstrates the use of Kubernetes Deployments and ReplicaSets with a focus on managing multiple replicas, updating Pods, and utilizing Kubernetes rollout history for reverting changes. It includes YAML files and instructions for hands-on practice.

## Prerequisites
- A running Kubernetes cluster (Local/Remote)
- kubectl command-line tool installed
- Basic understanding of Kubernetes concepts like Pods, ReplicaSets, and Deployments

## Exercise Overview
 ### 1. ReplicaSet   
 
 - Create a ReplicaSet: Create a ReplicaSet based on the nginx image with 3 replicas.
 - Update the ReplicaSet: Update the number of replicas from 3 to 4 using a YAML file and scale it to 6 using the command line.

 ### 2. Deployment
  - Create a Deployment: Create a Deployment named nginx with 3 replicas. The Pods should use the nginx:1.23.0 image and have the label 
     tier=backend. The Pod template should have the label app=v1.
  - Update the Deployment: Update the nginx image to nginx:1.23.4 and scale the Deployment to 5 replicas.
  - Rollout History and Reversion: Use rollout history to verify changes and revert the Deployment back to the original version with the image nginx:1.23.0.

  ### 3. Troubleshooting
Includes troubleshooting for common YAML mistakes, such as label mismatches and improper API versions.

## Steps:
 ###  1. Create a ReplicaSet with Nginx Pods
 ``` kubectl apply -f replicaset-nginx.yaml ```  
 To update the number of replicas:
 - Modify the YAML file to increase replicas to 4 and apply the change.
 To scale replicas using the command line:
 ``` kubectl scale replicaset nginx-replicaset --replicas=6 ```
 
 ### 2. Create and Manage Deployments
 Create a deployment using the YAML file:
 ``` kubectl apply -f deployment-nginx.yaml ```
 
 To update the image:
 ``` kubectl set image deployment/nginx nginx=nginx:1.23.4 ```
 
 To scale the Deployment:
 ``` kubectl scale deployment nginx --replicas=5 ``` 
 
 Check the rollout status:
 ``` kubectl rollout status deployment/nginx ```
 
 View rollout history:
 ``` kubectl rollout history deployment/nginx ```
 
 Rollback to the previous version:
 ``` kubectl rollout undo deployment/nginx --to-revision=1 ```
 
 ### 3. Troubleshooting YAML
 Ensure your YAML files follow the correct schema. Here are two corrected YAML examples with explanations for common errors:
 - Incorrect apiVersion or misplaced replicas field
 - Mismatched matchLabels and template labels
