---
title: "6) Setting up Cloudfront"
date: 2021-09-06T23:48:59+12:00
draft: false
---

You may have noticed that the S3 link is unsecure using http:// . We will remedy this using CloudFront!

Navigate to CloudFront service, and create distribution. 

Under "Origin Domain" find and choose your S3 bucket. You should see a lot of things populated.

Under "Default cache behaviour", find "viewer protocol policy" and tick "Redirect HTTP to HTTPS"
![](/Cprotocol.png)

Now create the Cloudfront.

Wait a bit.

Once deployed, copy the domain name of your CloudFront distribution and navigate there. 

You should see an error. But why? 

Looking at our S3 static website URL and the origin we can see a discrepancy. The S3 URL we hit includes the ".s3-website" in the URL whereas Cloudfront doesn't. So this need to be changed. 

Again, click on the Cloudfront distribution and navigate to the 'Origins' tab. Find the origin we had and click edit.

![](/Corigin.png)

Go back to S3 and copy the S3 static website URL we were hitting and paste that in "origin domain" and save changes. 

Wait a bit.

Now accessing the Cloudfront URL we should hit our website!