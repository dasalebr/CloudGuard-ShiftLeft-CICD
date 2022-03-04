# Sysdig integration with Jenkins CICD pipeline:

## ![header image](warning.jpeg) This demo contains Malware so please do not use in a production environment and Handle with Care


Sysdig Secure is a framework that will enable you to access all the various blades that CloudGuard offers quick and easy for integration within your pipeline.
CloudGuard ShiftLeft will allow you to scan source code, Docker container images and serverless deployment packages, Terraform templates, and more. 
The ShiftLeft binary or Docker container will integrate posture management and SAST to your CI/CD deployment pipelines for any CI server!

The ShiftLeft Binary can be installed on Windows, Linux or MacOS with the proper API key. Please try at : https://sysdig.com/company/start-free/
 
> docker pull checkpoint/shiftleft

Sysdig image scanning and static code analysis for code and container images will scan for CVEs, CWEs, Malware and credentials 


## The following blades are currently available for use within the framework:
                                                                                       
### Git code-scan	      

The code-scan blade provides Source-code security and visibility into the risk analysis of projects in Git repositories.

> shiftleft code-scan 

### iac-assessment	

The iac-assessment blade will scan Infrastructure-as-code templates, enabling DevOps and security teams to identify insecure configurations	

> shiftleft iac-assessment 

### image-scan	   

The image-scan blade will scan Docker container images for security risks and vulnerabilities

> shiftleft image-scan 



![header image](shifleftcicd.png) 

[![header image](shift.png)](https://www.youtube.com/watch?v=UAZixZ7ddbQ&feature=youtu.be "ShiftLeft")


#### Please add your Sysdig API key and add them to Jenkins using secret text and SECURE_API_TOKEN.

### The scan result for the source code scan:

> ShiftLeft is capable of finding CVEs, credentials and Malware!

