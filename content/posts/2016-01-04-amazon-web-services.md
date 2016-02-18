---
title: "Setting up for Amazon Web Services"
date: "2016-01-03"
description: "This is an introduction for getting set up to use Amazon Web Services"
categories:
    - "Education"
    - "Explanation"
    - "Tutorial"
tags:
    - "AWS"
---

In this post I will guide you through setting up the appropriate accounts and software on your local system to interact with AWS.

There are a few things you need to work with AWS

- AWS account & IAM user
- Access & secret keys
- AWS CLI Installation on your local machine
- S3cmd Installation on your local machine
- Optional: S3 IAM role

## Creating an AWS Account
The first and easiest step is signing up for an AWS account.  (You may skip this section if you already have an AWS account setup)

https://aws.amazon.com

Click on the "Sign Up" button on the top right hand corner.
Then follow the directions to create an account.
You'll need an email address, an active credit card, and access to a telephone to complete your registration.

{{% img src="/media/aws-signup.png" class="third right" alt="aws sign up" %}}


After completing you should see the registration confirmation page.

{{% img src="/media/aws-registration-confirmation.png" class="third right" alt="aws registration confirmation" %}}

From here click on the "Launch Management Console" button to start the AWS management console.

{{% img src="/media/aws-management-console.png" class="third right" alt="aws management console" %}}


## Creating an IAM user

The next step is create an IAM user.  This is a [best practice](http://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) suggested by Amazon to isolate your master credentials, and most importantly your billing information, from your interactions with AWS.  If you happen to lose access or leak the credentials to an IAM user, you can easily revoke the IAM user rather than risk having your entire AWS account compromised.

- Login to AWS console
- From the main console page, select "IAM"  (Identity and Access Management) under "Administration and Security" section.

> If you are not familiar with what IAM is, Identity and Access Management is an Amazon tool for managing credentials and access to services in your account in a very customizable and granular fashion.  For more information, Amazon provides a great [introduction](http://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) to IAM.

{{% img src="/media/aws-iam.png" class="third right" alt="aws iam" %}}


- From the IAM pane, click "Users" and then click "Create New Users".  
  - Ensure that the checkbox for "generate an access key for each user" is checked.  Click create.
- Then you have two options for downloading your access key and secret access key.
  - You can click "Show user security credentials" and copy and paste, or you can click "download credentials".  

Once you have saved the access and secret keys, you may safely close that web page.


> NOTE: Amazon no longer displays your secret keys so you must ensure that you keep your access key and secret key pair in a safe place.  I recommend using a Password Manager tool like Keepass or 1Password.

At this point you will return to the user listing page.
Click on the newly created user, and then scroll down to "Permissions" and click on "Attach Policy".  For test cases you can choose "AdministratorAccess".  Then click the button "attach policy" in the lower right hand corner.  In production you would select more granular permissions to grant to a user.

Optional but highly recommended for additional security, you should enable [MFA (multi-factor authenticaiton)](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa.html) on your AWS master account as well as any priviledged IAM user accounts.

Your IAM user should now be setup correctly and ready to be used.

If you wish to login to AWS console with your IAM user account, you will need to use the custom URL listed on the main IAM dashboard, displayed at "IAM users sign-in link".


## Access Keys

Access keys consist of an access key ID (like `AKIAIOSFODNN7EXAMPLE`) and a secret access key (like `wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY`).  You use access keys to sign programmatic requests that you make to AWS whether you're using the AWS SDK, REST, or Query APIs.

Access keys are also used with command line interfaces (CLIs). When you use a CLI, the commands that you issue are signed by your access keys, which you can either pass with the command or store as configuration settings on your computer.


## AWS CLI installation

The AWS CLI is a way to interact with AWS from the command line.  You will be able to perform most operations that you would can do on the AWS Web GUI.  You will be able to programmatically interface with AWS.

- Mac OS X

Homebrew is the easiest way to get AWS CLI installed on Mac OS X.

`brew install awscli`

- Windows

For information on installing AWS CLI on Windows, see this link:
http://docs.aws.amazon.com/cli/latest/userguide/installing.html

## s3cmd

For transferring files to S3, I recommend a CLI tool called [s3cmd](http://s3tools.org/s3cmd).  

- Mac OS X

Homebrew makes it very easy to install s3cmd on Mac OS X.

`brew install s3cmd`


- Windows

http://s3tools.org/kb/item12.htm

> **Does s3cmd work on Windows?**

> Yes, however, being written in Python, s3cmd requires Python 2.4+ for Windows to be installed and also it requires the Python library date-util.

> Alternatively, you can try [S3Express](http://www.s3express.com/). S3Express is a "native" Windows command line program, that works out of the box and does not require any additional library or software to run. S3Express is a commercial program. It's very compact and has very small footprint: the entire program is less than 5MB. S3Express is perfect for uploading, querying, listing Amazon S3 objects via the command line on Windows.

### s3cmd configuration

Run `s3cmd --configure`

Use the Access Key you generated above for the IAM user account (or alternatively for a dedicated S3 IAM account) and it will be placed within your s3cmd configuration file `.s3cfg`.

Visit http://s3tools.org/s3cmd-howto for more details.


### s3cmd usage

See s3cmd documentation: http://s3tools.org/usage  for more details.

`s3cmd ls` to list all your buckets.

`s3cmd ls s3://bucketName` to list contents of a bucket `bucketName`.

To copy a file to S3: `s3cmd-1.0.0/s3cmd put --recursive --preserve --acl-public hugo_gh_blog.modified/public/index.html s3://blog.storypath.com/ `

To copy multiple files to S3:
`s3cmd put --recursive --preserve --acl-public public/* s3://blog.storypath.com/`

To "rsync" a directory to S3:
`s3cmd sync --exclude '.DS_Store' --delete-removed --recursive --acl-public /path/to/public/* s3://s3BucketName/`

- `sync`  *Conditional transfer* — only files that don’t exist at the destination in the same version are transferred by the [s3cmd sync](http://s3tools.org/s3cmd-sync) command. By default a md5 checksum and file size is compared. This is similar to the unix rsync command, with some exceptions.
- `--exclude` tells s3cmd to exclude files to sync.  Regex arguments accepted.
- `--delete-removed` tells s3cmd to remove remote files with no corresponding local file (part of sync).
- `--recursive` tells s3cmd to recurse into subdirectories and folders.
- `--acl-public` tells s3cmd to make the resources public, read-only.



## S3 IAM role

AWS also has a [use case](http://docs.aws.amazon.com/IAM/latest/UserGuide/IAM_UseCases.html#UseCase_S3) for using an IAM role for S3.  This use case is mainly geared towards groups of people, and not typically applied for individual use.  




## Conclusion

This was a quick introduction on getting setup for AWS.  It covered some basic steps to use and interface with AWS.  If you want to learn more, I highly recommend the AWS documentation listed below.

### Additional Resources

Getting Started with AWS  
http://docs.aws.amazon.com/gettingstarted/latest/awsgsg-intro/gsg-aws-intro.html

AWS Pricing -
http://aws.amazon.com/pricing/

Hosting a Static Website with AWS
http://docs.aws.amazon.com/gettingstarted/latest/swh/website-hosting-intro.html

AWS IAM Best Practices
http://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html

AWS Avoid Deleteing IAM Resources in Use - 
https://aws.amazon.com/about-aws/whats-new/2016/01/the-iam-console-now-helps-you-avoid-accidentally-deleting-resources-in-use/

[link-1]: http://docs.aws.amazon.com/gettingstarted/latest/swh/website-hosting-intro.html
