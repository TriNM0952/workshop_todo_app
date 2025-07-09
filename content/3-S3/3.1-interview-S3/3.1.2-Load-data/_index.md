---
title : "Upload Data and Configuration"
date: 2025-07-09 
weight : 2 
chapter : false
pre : " <b> 3.1.2. </b> "
---
## Upload Data

- Currently, we don't have any _object_
![S3](/images/3.S3/08-S3.png)
- We need to upload the frontend source to S3
- In VS Code, open the frontend source, open the terminal and run the command:
  ```aws s3 sync build/ s3://todo-web-frontend-ws --delete```
- *Note*: Please adjust the path according to the location of your frontend folder
- After running, your source will be uploaded to S3
![S3](/images/3.S3/014-S3-Load-data.png)
![S3](/images/3.S3/015-S3-Load-data.png)

## Configuration
- Select _permission_ in the _bucket_, scroll down to the _bucket policy_ section and select _edit_.
![S3](/images/3.S3/017-S3-Load-data.png)
- Then configure S3 as follows:
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowPublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": ["s3:GetObject"],
      "Resource": ["arn:aws:s3:::todo-web-frontend-ws/*"]
    }
  ]
}
```
- Then select _save changes_
![S3](/images/3.S3/018-S3-Load-data.png)
- Next, select _Properties_, scroll down to _Static website hosting_ and select edit
![S3](/images/3.S3/019-S3-Load-data.png)
- Select _enable_
![S3](/images/3.S3/S20-S3-Load-data.png)
- For _Index document_, enter index.html
- For _Error document_, enter index.html
- Then click _Save change_
![S3](/images/3.S3/021-S3-Load-data.png)
- In the _Static website hosting_ section, you will see the _Bucket website endpoint_, which is the URL to your static frontend
![S3](/images/3.S3/022-S3-Load-data.png)
- You can now access your static frontend on S3
