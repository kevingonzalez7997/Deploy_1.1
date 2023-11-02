### Kevin Gonzalez 
### August 17, 2023


# Purpose

This project's purpose is to develop a URL Shortener application efficiently using Jenkins for source code management, building, and testing, and AWS Elastic Beanstalk for simplified deployment and scaling. By automating development and deployment processes, we aim to create a user-friendly URL Shortener, showcasing the power of modern DevOps practices

### Setting Up GitHub
GitHub, a prominent version control platform, is where Jenkins retrieves code through cloning. It offers essential tools for version tracking, collaborative coding, and efficient code repository management

First, create a new repository; this will serve as SCM for the application.

Next, upload the application files to the new repository.

Make sure to obtain your GitHub token for the repository you've created (Jenkins will need this later).

### IAM (Identity and Access Management)

Before you can test the code in Jenkins, ensure you set up the correct IAM permissions.

You need to configure two roles: one for Beanstalk and another for EC2.

Add AWSElasticBeanstalkWebTier, workerTier, and MulticontainerDocker as the required permissions.

This must be done before you run the code, as it controls access to resources.

### Jenkins
Jenkins, an open-source automation server, plays a crucial role in building, testing, deploying code, and distributing workloads. In this context, a dedicated node is responsible for automating the build and test steps within the infrastructure

1. Create a new item.

2. Link the new repository using the token created from Git Hub.

3. Run build if errors occur refer to troubleshooting 

### ElasticBean Stalk
1. Create an application to start.

3. Choose the platform (python 3.9).

4. Upload the zipped file from the new repository, ensuring you zip it without the parent folder.

5. Select ElasticEC2.

6. Pick the default VPC.

7. Choose the availability zone.

8. launch

### Troubleshooting: Error

If an error occurs during execution, follow these steps:

1. Check log files and inspect any error messages.

2. In one case, a few lines were pointing to the error:

    - ImportError while importing test module.
    - Hint: make sure your test modules/packages have valid Python names.
    - from application import app ModuleNotFoundError: No module named 'application'.
    - ERROR test_app.py.

3. It appeared that a file wasn't found in test_app.py.

4. Open test_app.py to review its contents.

5. The line "from application import app" provides another clue.

6. Compare a working V1 to V1.1, and it becomes clear that app.py should be named application.py.

7. Rename the file and retest.

If test runs are successful, you can proceed to run in AWS.

While the EC2 instance is pending the running state, don't forget to close your eyes and hope for an increased launch probability!

![Screenshot 2023-08-17 155820](https://github.com/kevingonzalez7997/Deploy_1.1/assets/59447523/bf4fdb12-9544-4b56-874a-4190c3967007) <br><br>
![Deploy_v1 2](https://github.com/kevingonzalez7997/Deploy_1.1/assets/59447523/05cfc7c6-9683-4312-8125-84ad65aca0a8)
