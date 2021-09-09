---
title: "4) Setting up AWS Login"
date: 2021-09-06T23:48:59+12:00
draft: false
---
Skip this if you've already got AWS configured with your computer. 

https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html

First, we need to get all our credentials ready. Once you've logged in:

1. On the top right, click your username and then choose the Security credentials tab.

2. In the Access keys section, choose "Create access key".

2. To view the new access key pair, choose Show. You will not have access to the secret access key again after this dialogue box closes. Your credentials will look something like this:

	Access key ID: AKIAIOSFODNN7EXAMPLE

	Secret access key: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY

3. To download the key pair, choose Download .csv file. Store the keys in a secure location. You will not have access to the secret access key again after this dialog box closes.


Now complete the following with the credentials that you've received from previous part

	$ aws configure
	AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
	AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
	Default region name [None]: ap-southeast-2
	Default output format [None]: json

