# CICD-Using-AWS-Cloud-services---code-commit-code-build-code-deploy-and-code-artifact
CICD-Containers

Aim: The main objective of this project is to deploy a complete CI-CD pipeline using PAAS & SAAS services offered by AWS.
![image](https://user-images.githubusercontent.com/102613218/229357121-45314fec-e4ef-450b-8e6b-72853a00caf9.png)


AWS services involved:
- Code commit
- Code pipeline
- Code build
- Code artifact
- AWS systems manager
- Elastic beanstalk
- Sonar cloud
- Amazon S3
- RDS

Continuous integration process:

Step 1: Code commit - This involves either creating a new repository to store source code or migrating source code from an existing repository like github
![image](https://user-images.githubusercontent.com/102613218/229357249-784fd833-f024-4c59-accc-a161e0131001.png)

Step 2: Code artifact - setting up code artifact repository to store dependencies for maven
![image](https://user-images.githubusercontent.com/102613218/229358199-de1897d1-47d6-4294-9923-9266e2866143.png)

Step 3: Configure required parameters in aws parameter store
![image](https://user-images.githubusercontent.com/102613218/229358214-20d7b3e2-4e8a-4063-8cb3-799746ec7773.png)


Step 4: Code build job configuration - writing a build spec file(this will use dependencies from code artifact)
to perform mvn test, code analysis with checkstyle and sonarqube analysis.
![image](https://user-images.githubusercontent.com/102613218/229358246-f8babb96-b123-40d1-bfe2-59fc684950c2.png)

Step 5: If quality gates are passed, then invoke code build job to build & store the artifact.
The final artifact generated is stored in Amazon S3
![image](https://user-images.githubusercontent.com/102613218/229358311-3db27d44-bfc0-46b9-98c6-2aa306de25c9.png)

The complete CI pipeline flow
![image](https://user-images.githubusercontent.com/102613218/229358332-8fa53ce3-ee7b-411d-93c7-35ba6f64c2ab.png)
![image](https://user-images.githubusercontent.com/102613218/229358340-0d3abdd3-94d6-48d5-ad0e-57f1bc0238bf.png)
![image](https://user-images.githubusercontent.com/102613218/229358345-60bb759d-fb01-4d74-9585-a997593c0e84.png)
![image](https://user-images.githubusercontent.com/102613218/229358351-ca9ae8ef-b67c-4301-8b4b-addbfcb1833d.png)

Artifact gets uploaded in S3
![image](https://user-images.githubusercontent.com/102613218/229358358-5f868883-7b3e-401e-8198-2bd215d226af.png)

Continuous delivery pipeline:

Step 6: Build job to build the artifact to be deployed to ELB with a RDS
![image](https://user-images.githubusercontent.com/102613218/229358967-91e673f8-6ebd-4493-a50c-dbc562c6195d.png)
(BuildAndReleaseSpec)

Step 6: Deploy the artifact in a elastic beanstalk coupled with RDS
![image](https://user-images.githubusercontent.com/102613218/229358994-91a6198e-0e04-49ff-89e4-0db178692f26.png)
![image](https://user-images.githubusercontent.com/102613218/229359007-a63a214a-051d-4fef-9832-26e270e736a2.png)
![image](https://user-images.githubusercontent.com/102613218/229359021-fcb72804-b95a-4bfe-99be-53b24b99e744.png)
![image](https://user-images.githubusercontent.com/102613218/229359025-edc9424a-aa48-44cc-b7c0-d7bb2d08b8f0.png)
![image](https://user-images.githubusercontent.com/102613218/229359037-1965084d-a06f-48b1-b343-1fdb182edc06.png)
![image](https://user-images.githubusercontent.com/102613218/229359052-4018ad62-2306-4e70-9aec-ebc6620dca27.png)


Step 7: Software testing - configure a software testing job with selenium.
![image](https://user-images.githubusercontent.com/102613218/229359073-58b5cd7e-af78-4dab-b7c3-87d7589c2f7c.png)
![image](https://user-images.githubusercontent.com/102613218/229359089-36ae5e85-d79a-4b4b-ac41-cdd9ac63c5d5.png)
![image](https://user-images.githubusercontent.com/102613218/229359094-0b495524-85e7-41e6-8537-9137504afa0b.png)








