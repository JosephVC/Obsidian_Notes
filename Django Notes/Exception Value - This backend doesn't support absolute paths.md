---
---


this is an AWS issue, and is resolved in the **Bucket Policies** section of **Permissions**

**{**
    **"Version": "2012-10-17",**
    **"Statement": \[**
        **{**
            **"Sid": "PublicRead",**
            **"Effect": "Allow",**
            **"Principal": "\*",**
            **"Action": \[**
                **"s3:GetObject",**
                **"s3:GetObjectVersion"**
            **\],**
            **"Resource": "arn:aws:s3:::django-ocr-tutorial-bucket/\*"**
        **}**
    **\]**
**}**

**12.12.2020 -** this error pops up when posting from the even when aws is configured well
