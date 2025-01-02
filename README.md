# AWS_instance_Launch
Automate Instance launching using python

## Step 1: Set Up AWS Resource with Credentials
To begin, you'll need to establish a connection to AWS EC2 by setting up your credentials. Using boto3.resource, connected to the EC2 service in the region. Here’s how you can configure it:
```bash
import boto3

myec2 = boto3.resource(
    "ec2",
    region_name="<region>", # Replace with your desired region
    aws_access_key_id="<access_key>", # Replace with your access key
    aws_secret_access_key="<secret_access_key>" # Replace with your private key
)
```
This step establishes the foundational connection to interact with EC2 resources.

## Step 2: Launching an EC2 Instance
Now that we are connected to AWS, it’s time to launch our EC2 instance. In this step, automated the process of creating a t2.micro instance using a predefined Amazon Machine Image (AMI). Here’s how to do it:
```bash
def osLaunch():
    myid = myec2.create_instances(
        ImageId='ami-0fd05997b4dff7aac',  # Replace with your AMI ID
        InstanceType='t2.micro',
        MinCount=1,
        MaxCount=1
    )
    return myid
```
Running `osLaunch()` triggers the creation of an EC2 instance and returns its metadata

## Step 3: Tracking Instances with a List
Once the instances are launched, it’s crucial to track them. I maintain a global `list (myosList)` where I store the instance IDs of launched instances. This keeps things organized and ensures easy access to the instance information:
```bash
myosList = []  # Declaring an empty list
myos = osLaunch()  # Launching an OS
print(myos)  # Checking the returned value
myosList.append(myos[0].id)  # Storing the instance ID
```



