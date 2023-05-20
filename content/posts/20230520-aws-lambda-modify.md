---
Title: "Modify and Test AWS Lambda Function on the fly"
Publishdate: 2023-05-20
categories: ["Development", "Tips"]
tags: ["AWS", "Lambda", "Serverless"]
---

## The Problem... <a name="problem"></a>
AWS Lambda provide a convenience way to quickly edit and testing code on the web console so you don't have to modify you code on you IDE then deploy it onto the AWS.

![AWS Lambda Console Editor](/img/aws-lambda/console_editor.png)

Sometime, your lambda could grow very big (due to dependency libs) and AWS will not allow you to edit it on the console anymore...

![Python Libs](/img/aws-lambda/dependency.png)

![Large Function](/img/aws-lambda/large_function.png)

There are several ways to modify the code in this situations:

# Solutions
- [1: Deploy Package (Traditional)](#package)
- [2: Dirty Install](#dirty)
- [3: AWS Cloud9](#cloud9)
- [4: AWS Toolkit](#aws-toolkit)

## Deploy Package (Traditional) <a name="package"></a>

This is the supposedly to be the correct way to publish new version on to AWS Lambda as same as how you are going to deploy the code via CICD pipeline or whatever...

What you have to do is pack you entire source code into a zip file (at root level) and upload it onto Lambda or S3 Bucket.

![Upload zip](/img/aws-lambda/zip_package.png)

When the code is uploaded it will automatically deployed as new version of the Lambda function and you can run test against it.

| Pros | Cons |
| --- | ---- |
| ✅ No surprise | ❌ Slow zip + upload |

## Dirty Install <a name="dirty"></a>

From the previous solution, we would want to avoid packing and upload the code onto Lambda from time to time. We will be keep minimal code under the Lambda function so we could still editing it on the console directly.

What we are going to do is to download the required dependencies before each function call to ensure the runtime environment can see and use them.

![Dirty Install Script](/img/aws-lambda/dirty_install.png)

The code block below is an example code stub for installing **request** library via pip before executing the code. Put it on the top of the Function code.

```
import os
import sys
import subprocess

subprocess.call('pip install requests -t /tmp/ --no-cache-dir'.split(),
    stdout=subprocess.DEVNULL, stderr=subprocess.DEVNULL)
sys.path.insert(1, '/tmp/')
import requests

# implement whatever your code after this block
```

| Pros | Cons |
| --- | ---- |
| ✅ Not taking space in Lambda Function | ❌ Introduce network cost/latency on every function call  |

## AWS Cloud9 <a name="cloud9"></a>

AWS provided a ~~Product~~ Solution for software development on AWS itself. Cloud9 is an IDE running on website (under AWS Console). The IDE instance can be access by multiple developers and update the same code at the same time like how we did on Google Office apps. The IDE also have built in Terminal to run on the virtual environment.

![Cloud9 IDE](/img/aws-lambda/cloud9.png)

As the Cloud9 is based on the EC2 service, you could configure the Cloud9 instance to sit under the network that you need to integrate you application with.

![Cloud9 VPC Config](/img/aws-lambda/cloud9_vpc.png)

Also noted that Cloud9 service itself is free, but EC2 that use to host it doesn't. The larger instance (cpu/memory) to compile/execute code will cost you more money.

Cloud9 may introduce new feature as the time you are reading, you could reference it from the AWS Cloud9 info page https://aws.amazon.com/cloud9/

| Pros | Cons |
| --- | ---- |
| ✅ No desktop installation required | ❌ Incurring EC2 Cost  |
| ✅ Can share codebase + environment with multiple collaborator at the same time |  |
| ✅ Run under actual VPC, no additional configuration needed |  |

## AWS Toolkit <a name="aws-toolkit"></a>

AWS Provide a plugin for JetBrains IntelliJ and PyCharm to manage access key/region connection between AWS and the IDE, so you can run the application against the AWS network directly

For installation steps, refer to the guide provided by AWS here:
https://docs.aws.amazon.com/toolkit-for-jetbrains/latest/userguide/setup-toolkit.html

![AWS Toolkit](/img/aws-lambda/aws_toolkit.png)

This is actually automation for executing AWS CLI over IAM and STS service which you can also do it manually and could also be use with other IDE or code editor as well.

| Pros | Cons |
| --- | ---- |
| ✅ Test your code against actual VPC | ❌ Need to reconfigure every time token is rotated  |
| ✅ Edit + Debug your code on IntelliJ / PyCharm |  |

## Closing <a name="closing"></a>

There are several workarounds for editing large Lambda code. One may fit the need for the given constraints or frequency of code changes required.

I hope this guide may give you an idea how to work around with AWS Lambda, so we can focus on productivity rather than frustrating over trivial things 🤪