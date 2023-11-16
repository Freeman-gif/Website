# HW5


---
### Step 1:
1. Go to AWS.com click top right create an AWS Account.
2. regesiter with your school or personal email, choose basic support plan

### Step2(after regesiter) Apply credit:
1. Login as Root User with your email!
2. Then you should see the console dashboard 

1. On the Top right of the user name, click and there should be a drop down menu![[Pasted image 20230807201333.png]]
2. click Billing dashboard![[Pasted image 20230807201430.png]]
3. click credit on the left menu and then click redeem credit to apply credit and this where  we can add our credit ![[Pasted image 20230807201604.png]]![[Pasted image 20230807201642.png]]

### Billing Preference:
1. Click Billing Preference in the Billing Dashboard ![[Pasted image 20230807201846.png]]
2. Click Alert Preferences![[Pasted image 20230807202014.png]]optional Choose Receive AWS Free Tier alerts , enable Receive CloudWatch billing alerts and click update:![[Pasted image 20230807202220.png]]
3. check and update invoice deilvery preferences by email![[Pasted image 20230807202401.png]]
### Create Alarms:
1. in search bar serch Cloudwatch![[Pasted image 20230807202526.png]]
2. in the Overview page, click 'Create alarms' ![[Pasted image 20230807202628.png]]![[Pasted image 20230807203351.png]]
3. on top right, click region list and set to ohio![[Pasted image 20230807203449.png]]
4. Change region to to virgina ![[Pasted image 20230807203603.png]]
5. click create alarm ![[Pasted image 20230807203706.png]] and then select Metric ![[Pasted image 20230807203727.png]]
6. in select metric page ![[Pasted image 20230807203837.png]]select Billing![[Pasted image 20230807203856.png]]and then select Total Estimated Charge![[Pasted image 20230807203946.png]]select USD ![[Pasted image 20230807204025.png]] and then select metric ![[Pasted image 20230807204049.png]]
7. In the Specify metric and condition page, make sure set the condition and the period, then in the condition, set the threshold for the charge ![[Pasted image 20230807204401.png]] This would notice you when threshold value is exceed. Then click next
8.   Add notification, choose new topic, add an email for notification and then create topic ![[Pasted image 20230807204735.png]] you should recive an email 
9. after hit next, set the Alarm name and description ![[Pasted image 20230807205326.png]]
10. hit next, and you should have a report of everything your set up![[Pasted image 20230807205446.png]] Check and create alarm
11. Now we have the alarm![[Pasted image 20230807205717.png]]
**Note: East Coast is always cheaper!!!**
---
### AWS S3, EC2 and CLI:
Key word note: 
S3 is an object storage that we can store data:
- Object - Data(files)
- Object Keys - A unique identifier for an object
- Bucket - A container for object
- Bucket Policy - create rule for access 

1. Top left search S3 and click it ![[Pasted image 20230807210551.png]] note: S3 is **Global**
2. Click create bucket ![[Pasted image 20230807210709.png]], create bucket name and select ACLs disabled, block all access, disable the versioning. and then create bucket ![[Pasted image 20230808173714.png]]
3. Once create bucket you should able to unload/create folder to place the file in the bucket, ![[Pasted image 20230809001531.png]]
4. Bucket Permission able to grant access to the other users![[Pasted image 20230809001630.png]]
	1. click edit bucket policy to edit the Permission ![[Pasted image 20230809001848.png]]
	2. Add resource to select bucket ![[Pasted image 20230809002104.png]]
	3. set condition for specific user etc![[Pasted image 20230809002235.png]]
5. Upload:
	1. drag the file into the upload page and the upload ![[Pasted image 20230810000820.png]]
	2. click the specific object in the bucket, we would able to see the 
		1. URI: Where the file located at. 
		2. ARN: permission informations

#### EC2:
![[EC2]]
1. Launch EC2:
	1. search EC2, click instance on left Menu, then launch instance
	2. create the instance with the name and tags. select the type of instance we need and os system.   ![[Pasted image 20230809004319.png]]Key pair is important for validate the user's shh to AWS account![[Pasted image 20230809004604.png]]it will generate a pem file and make sure save the ssh key in a secure folder.
	3. after launch the instance, we should able to see the instance in the instance page ![[Pasted image 20230809005224.png]]
	4. Click ID and it will give the information for the current instance ![[Pasted image 20230809005307.png]]
	5. click security button, we can change the security rule in Security groups![[Pasted image 20230809005454.png]]
		1. Edit inbound Rule and Outbound Rule 
2. **AWS Key and Secret Access Key**:
	1. in the search bar search key word IAM
	2. Add user name from the user page:![[Pasted image 20230809005933.png]]it allow us to add multiple user use resources
	3. set permissions for the user ![[Pasted image 20230809010147.png]] then we can create user
	4. once user create, we can check user security credentials by click user's name  ![[Pasted image 20230809011839.png]], at here we can create access key for the user ![[Pasted image 20230809012004.png]]. save the access key and security key 
3. AWS CLI:
	1. go to this link https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html and download Command line installer for Mac. Follow instruction, copy the download code into command script![[Pasted image 20230809012957.png]]
	2. use AWS CLI:
		1. configure CLS output by use aws configure function then enter the access key and secret key created earlier ![[Pasted image 20230809013259.png]]
4. access server
	1. SSH method access EC2
		1.  Change permission to read and write for the pem file download from the AWS earlier and then in the terminal type ssh -i filelocation and the use the instance ip locaiton as the ec2 user name 
			1. ![[Pasted image 20230809013801.png]]exit to get out ec2 server 
	2. CLI method:
		1. in the teminal type aws ec2-instance-connect ssh --instance-id(instance id) --private-key-file (ssh pem file)![[Pasted image 20230809014435.png]]
#### Load data to EC2:
1. once login EC2 in terminal do curl -O https://bootstrap.pypa.io/get-pip.py, then wrong the get-pip.py file ![[Pasted image 20230809015828.png]]then pip install boto3, boto3 
2. create.py file:
	1. vi hw5.py
	2. then use bucket name and key name from s3
	3. ![[Pasted image 20230809234904.png]]
3. connect ec2 to s3
	1. aws configure (access key and secret key)![[Pasted image 20230809235514.png]]
4. execute it by python3 hw5.py ![[Pasted image 20230809021749.png]]
5. print the content, use ['Body'].read from boto3 ![[Pasted image 20230809235954.png]]![[Pasted image 20230809235937.png]]

Empty bucket then delete bucket






##### Key words:
1. instance: Where the computing is done, we can choose various instance types with different CPU, memory etc...
	1. we can use ssh to the instance 
	2. we need to configure our instance including user permission and security group to open/close certain port 


---
#### TAGS