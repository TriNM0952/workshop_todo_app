---
title : "Create CloudFront Distribution"
date: 2025-07-09 
weight : 1 
chapter : false
pre : " <b> 3.2.1 </b> "
---
## Create CloudFront Distribution and configure Distribution
1. Create CloudFront Distribution
- Go to the _AWS Console_
- Search for _CloudFront_ on the interface or in the search bar
- Select _CloudFront_
![CloudFront](/images/3.CloudFront/01-CloudFront.png)
2. In the _CloudFront_ interface, select _Create distribution_
![CloudFront](/images/3.CloudFront/02-CloudFront.png)
- In the _Create distribution_ interface
- _Distribution name_: enter ```todo-web-frontend-ws```
- Then select _Next_
![CloudFront](/images/3.CloudFront/03-CloudFront.png)
![CloudFront](/images/3.CloudFront/04-CloudFront.png)
- At this step, select _Other_
![CloudFront](/images/3.CloudFront/05-CloudFront.png)
- Scroll down to the _Origin_ section
- Enter _Custom origin_: you need to enter the URL to your _S3 website hosting_ and remove the _http://_ prefix
- Use the recommended settings
![CloudFront](/images/3.CloudFront/06-CloudFront.png)
- Then select _Next_
![CloudFront](/images/3.CloudFront/07-CloudFront.png)
- In the next step, you can choose between _Enable security protections_ (paid) or _Do not enable security protections_ (free). Then select _Next_
![CloudFront](/images/3.CloudFront/08-CloudFront.png)
- Then select _Create distribution_ to create the distribution
![CloudFront](/images/3.CloudFront/09-CloudFront.png)
- After creating the distribution, you need to wait 5-20 minutes for _Amazon CloudFront_ to deploy
- After deployment is complete, you can see the deployment time and the new URL to your interface
