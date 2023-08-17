<h2>Setting Up GitHub</h2>
First create a new repo this is where we will upload the app/This will be our staging environment
<br><br>
Upload the app files to the new repo
<br><br>
Make sure you get your token from GitHub for the repo that you have created (Jenkins will need this later)
<h2>IAM</h2>
Before you can test the code in Jenkins make sure you set up the correct IAM Permissions
<br><br>
you need  2 roles, one for Beanstalk and one for the EC2
<br><br>
add AWSElasticBeanstalkWebTier,workerTier,MulticontainerDocker as the permissions
<br><br>
This has to be done before you run it bc it will control who has access to what
<h2>Jenkins</h2>
login to Jenkins
<br><br>
Create a new item
<br><br>
Link the new repo using the token created earlier
<br><br>
<b>ERROR</b>
<br><br>
![Screenshot 2023-08-17 153134](https://github.com/kevingonzalez7997/Deploy_1.1/assets/59447523/1602f6a3-b693-4101-a30f-7f3e95c7514f)
<br><br>If there is an error, open log files and inspect
<br><br>
In this case there were a few lines pointing towards the error such as
<ul>
  <li>ImportError while importing test module </li>
  <li>Hint: make sure your test modules/packages have valid Python names.</li>
  <li>from application import app ModuleNotFoundError: <b>No module named 'application'</b></li>
  <li>ERROR test_app.py</li>
</ul>
It seemed like a file wasn't found in test_app.py
<br>Open test_app.py to see what it is doing
<br><b>"from application import app"</b> is another hint
<br> lastly compared working V1 to V1.1 and we can clearly see that app.py should be application.py
<br>rename and restest
<br><br>
If test runs are successful you can run in AWS
<h2>AWS</h2>
Create an application to start!!
<br><br>
Give it a name
<br><br>
pick the platform (python 3.9)
<br><br>
upload the zipped file (from the new repo) make sure you zip without the parent folder!
<br><br>
select ElasticEC2 
<br><br>
pick default vpc
<br><br>
select az
<br><br>
Lastly, you have to finish setting up some settings for your EC2 instance such as root volume type and size
<br><br>
While the EC2 instance is pending the running state, it is important not to forget to close your eyes and pray to increase the launch probability! 

