---
title : "Create S3 bucket"
date: 2025-07-09 
weight : 1
chapter : false
pre : " <b> 3.1.1 </b> "
---
## Create bucket
1. Create an S3 bucket  
- Go to the _AWS Management Console_.
- Search for _S3_ on the interface or in the search bar
- Select S3
![S3](/images/3.S3/01-S3.png)
2. In the _S3_ interface, select _create bucket_
![S3](/images/3.S3/02-S3.png)
3. In the _Create bucket_ interface
- _Bucket name_: enter ```todo-web-frontend-ws```
![S3](/images/3.S3/03-S3.png)
- **Note**: Since _Bucket name_ is globally unique, if you use the same name as above, you will see the message: “Bucket with the same name already exists”. Therefore, you need to add some numbers at the end so that your _Bucket name_ complies with the policy.
![S3](/images/3.S3/06-S3.png)
4. In the _Block Public Access settings for this bucket_ section, turn it off and check the box _I acknowledge that the current settings might result in this bucket and the objects within becoming public._
![S3](/images/3.S3/04-S3.png)
5. Leave the remaining settings as default and select _create bucket_
![S3](/images/3.S3/05-S3.png)
6. Complete the creation of the _S3 bucket_ to store the source code.
![S3](/images/3.S3/07-S3.png)
