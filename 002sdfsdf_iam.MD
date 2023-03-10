# Identity and Access Management

## What is it?
IAM is a core AWS Service that helps you control access to resources.          
You create resources such as an S3 Bucket or an Object.           
Users perform actions on resources like S3::CreateBucket.          
Authorization to peform an action depends on a policy.     

policy document
```
{
    "Version": "2012-10-17",  // use this date. why? who knows
    "Statement": [            // need this
        {
            "Sid": "CreateFunction", // arbitrary id name
            "Effect": "Allow",       // either allow or deny
            "Action": [
                "lambda:CreateFunction"   // have the ability to create a lambda function
,            ],
            "Resource": "*"   // used for limiting scope
        }
    ]
}
```
All actions are compared to the policy document associated with the user.     

## Types of AWS Security
1. IAM
2. Amazon GuardDuty: aggregates all logs (CloudTrail, DNS, etc.,) and monitors them via ML algos.    
3. Amazon Macie: use ML and pattern matching of existing libraries of data or create your own.
4. AWS Config: works with other resources. config other resources and how you want them to work.
5. AWS CloudTrail: logging every api and all the data, services attached to them.

## Benefits of IAM
1. Grainular control over data and scalable security.
2. Automated tasks reduce human configuration errors.
3. The most comprehensive compliance controls to meet compliance standards.
4. Build the highest standards for data and security privacy. Encrypt, move and manage data.

## IAM Users vs Roles
The two are similar.  Both have permissions and policies, however, roles are assumable by anyone who needs it.  Furthermore, roles are typically temporary.  Let's say a dev needs access to a particular service at a given time.  They would be a candidate for a role.  

![web_v_workenvironment](/assets/users_roles.png)


## IAM Group
1. A set of IAM users
2. Groups allow you to specify specific permissions
3. Groups cannot be nested
4. Users can belong to multiple groups

## IAM Role
1. Permissions are for a limited time
2. They are aquired at run-time
3. They consist of a Trust Policy (who do you trust to do it), then the IAM Policy.
4. Important. The user is not assigned the role. The user assumes the role via an api call that verifies the user's token, and then the policy is executed.


## Ways to create a function
Keeping with this CreateFunction theme, there are three ways to create one.    
1. AWS console.  The most common way.     
2. CLI     
3. Programmatically using AWS SDK     

So how does AWS know who the user is?  It does through Access Key & Secrete Access Key.    
These are created when your user account is created.

   

A default root account is created.  Shouldn't be used or shared.   
Put users in Groups and apply ```least privilege``` principle.    
Groups cannot be nested, but users can belong to different groups     
Users DO NOT have to belong to a group

## IAM Policy
Users or Groups can be assigned a JSON policy.  This is an admin user. They can perform all actions and have access to all resources
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "*",
            "Resource": "*"
        }
    ]
}
```

## Creating the first user.  
We don't want to use the root user.  Best practice is to create a new user, then create and add them to an admins group, granting them AdministratorAccess     
Grant the user AWS Management Console access.  This will allow them to sign in.  You can either auto generate a password, or create one.  Moreover, you can require the user to reset the password over a given period of time.   

## How to grant policy access
One way is to use the Policies in Access Management.  These policies are pre-defined policies created by AWS. Just select the ones you want applied to the group or user.  Group is prefered.    
Once a policy is selected you can see the details using the permissions (policy summary) and see how it's setup looking at the JSON file.  All the JSON files start with Version "2012-10-17"    
## Create a custom policy
In Policies select Create Policy.  This allows you to either create a custom JSON policy or select from a number of services.

## Password policy
Two ways to create: 1) password policy, 2) MFA or Multi Factor Authentication    
A password policy can require a min pw length, req spec char types, allow/not allow users to change passwords, and require users to change passwords over a period of time, and can prevent password reuse.     
MFA is recommended. A second code is sent to a separte device (e.g., phone, computer, security fob device/third party).  Authy is a service you can use on your computer.

## Setup password Policy
In Access Management to go Account Settings > Edit.    
Setup MFA now. In IAM look to the top right corner of page and select current user.  That will give you access to Security Credentials.  Look for MFA device and select it.  Now we're given three options: authenticator app, security key (usb), and hardware TOTP token (3rd party stand alone device).

## Accessing AWS - 3 ways
1) AWS management console (including MFA token)  
2) AWS CLI (protected by access keys)
3) AWS SDK (used for writing code protected by key access)
Keys are generated through the AWS console.     
Users manage their own keys.    
Access Key ID looks like a username     
Secret Access Key looks like a password

## Installing CLI on Mac
CLI must be installed. Google install aws on mac.  Follow install instructions.    
Open terminal check install: aws --verson    
To create an access key to go IAM > users > select an IAM user then Security Credentials    
Scroll to Access Keys > Create access key.  A pop up will show with the access key. Copy it. The key will not be show again.     
Back to terminal type `aws configure` enter. It will ask for the access key.  Next it will ask for the screte access key.   
It will ask for the default region name.    
DONE   
Now test in terminal. Type `aws iam list users`??
