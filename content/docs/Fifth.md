---
title: "5) Deploying our React App"
date: 2021-09-06T23:48:59+12:00
draft: false
---

Here comes the fun part. 

Let's first create an S3 bucket to store our app. 

In the AWS console, search S3, then click on Create Bucket. 

![](/S3first.png) 

Then write a unique bucket name(it will complain if the name is already taken), and uncheck as per the image below.

 1. "Block all public access"
 2. "Block public access to buckets and objects granted through new public bucket or access point policies"
 3. "Block public and cross-account access to buckets and objects through any public bucket or access point policies"

![](/S3bucketconfig.png). 

Accept the warning for public access. and go to the bottom and create the bucket.

Click on the bucket, navigate to the permissions tab, edit bucket policy and paste the following. Ensure you fill in your bucket resource as per previous creation. Also note the /* ending. This policy will allow us to access S3 publicly.



	{
	    "Version": "2012-10-17",
	    "Statement": [
	        {
	            "Effect": "Allow",
	            "Principal": "*",
	            "Action": "s3:GetObject",
	            "Resource": "arn:aws:s3:::<Fill in your S3 bucket here>/*"
	        }
	    ]
	}

Under the Properties tab, at the bottom of the page find "Static Website Hosting". Click edit, edit the following, and save changes:

1. Static website hosting = enable
2. Hosting type = Host a static website
3. index document = index.html

![](/S3static.png)

The reason why we use index.html is that when we build our react app, the page generated we see is the index.html file. 


Now we go back to our react app and navigate to 'src/package.json' and paste the following under 'scripts'.

    "deploy": "aws s3 sync build/ s3://<Fill in your S3 bucket here>"

![](/packagejson.png)

What this will do is it will deploy our build to s3 automatically when we run "yarn deploy".

Now in our CLI(PowerShell/cmd/terminal). Run "yarn build" to build the app.

	yarn build 

then we run "yarn deploy" to deploy our static website to S3.

	yarn deploy


If all goes well, going back to your bucket created you should see files populated inside.

![](/S3files.png)

Going back to the "static website hosting " section as per above, You should see a bucket URL endpoint there. Click on that and you should see your website now!

![](/S3url.png)