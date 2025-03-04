# Cloudifytests Infrastructure Installation Steps


This document provides the steps for installing the Cloudifytests product from AWS Marketplace.

## Prerequisites
1.  **kubectl –** A command line tool for working with Kubernetes clusters.

2.  **eksctl –** A command line tool for working with EKS clusters that automates many individual tasks.

3.  **AWS CLI configured with your Access Key and Secret Access Key**

4.  **Minimum requirements to run application on the cluster:-**

      *You need 4vCPU machine and 4gb ram*

## Installation Steps
   
-  [**Install Kubectl in your local environment.**](https://kubernetes.io/docs/tasks/tools/)

-  [**Install Eksctl in your local environment**](https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html)

-  [**Install AWS CLI in your local environment**](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)


### Cloning the cluster

       git clone https://github.com/CloudifyLabs/Cloudifytests_charts.git
       
       cd Cloudifytests_charts
       
                
### Quick Launch 
       
This repository comes with a quick launch script (quicklaunch.sh) that automates the process of deploying the application to a Kubernetes cluster.

##### ***Please note that the quick launch script assumes that you have kubectl and helm installed on your machine, and that you have access to a Kubernetes cluster.***


#### You will be prompted to enter the following information:

|    Field          |Description   |      Required / Optional    |
| :------------------:|:-----------------------:|:-----------------:|
| **Namespace Name**    |The name of the namespace to be created.|***Required***|
| **AWS Access Key**    |The Access Key for your AWS Account.|***Required***|
| **AWS Secret Key**    |The Secret Key for your AWS Account.|***Required***|
| **Ingress Host**      |The Hostname for the Ingress.|***Required***|
| **S3 Bucket name**    |The name of S3 bucket to use.|***Required***|
| **AWS Default Region**|The default region for your AWS Account.|***Required***|
| **AWS ECR Image**     |The name of the ECR image repository to use. |***Required***|
| **Tag for sessionbe** |The tag for SessionBe Image|***Required***|
| **Tag for sessionui** |The tag for SessionUI Image|***Required***|
| **Tag for smcreate**  |The tag for SmCreate Image|***Required***|
| **Tag for smdelete**  |The tag for SmDelete Image|***Required***|
| **Cluster Name**      |The name of your Kubernetes Cluster.|***Required***|
      
All of the fields listed above must be provided by the user in order for the script to run correctly.

#### To launch Cloudify Tests using the Quick Launch method, run the following command:

      
        ./quicklaunch.sh
       

Once the script has completed execution, the application will be deployed to your Kubernetes cluster in the specified namespace. You can use the LoadBalancer URL to access the application or you can use by port-forwarding method. 

#### Port forward the service [Optional]
   
         kubectl port-forward --namespace <your namespace name> service/cloudifytests-nginx 9000:80
   
