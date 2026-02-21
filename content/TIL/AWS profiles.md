---
tags:
  - cloud
  - aws
date: 20 Feb 20206
---

An AWS profile is a named configuration bundle that defines  
- **who you are**
- **how you authenticate** (optional)
- **which role you assume** (optional)
- **which region you operate in**

Here's an example
`~/.aws/credentials`
```
[personal]
aws_access_key_id = AKIA...
aws_secret_access_key = ...
```

`~/.aws/config`.
```
# config
[profile dev]
role_arn = arn:aws:iam::111111111111:role/Developer
source_profile = personal
region = us-west-2

[profile staging]
role_arn = arn:aws:iam::222222222222:role/Developer
source_profile = personal
region = us-west-2

[profile prod]
role_arn = arn:aws:iam::333333333333:role/ReadOnly
source_profile = personal
region = us-east-1
mfa_serial = arn:aws:iam::999999999999:mfa/your-user
```

Multiple profiles can use the same account, as seen here.

https://chromewebstore.google.com/detail/aws-extend-switch-roles
Is a very convenient chrome extension to switch profiles on the AWS console, it uses a format similar to the AWS config file.

Also AWS role ARNs contain the AWS account id (the numerical part before `:role/role_name`)

The `source_profile` is useful when you're doing [cross account access](https://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_cross-account-with-roles.html), otherwise it isn't necessary.