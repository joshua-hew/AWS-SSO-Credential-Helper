# AWS-SSO-Credential-Helper
Use this script to automatically convert SSO tokens into AWS Credentials (Access + Secret Key).

# Purpose
When trying to use Terraform in my origanzation, I learned that it was incompatible wth AWS SSO by default. Though there are many workarounds online, those only work if you are trying to access one AWS account, and quickly becomes a tedious or impractical when trying to authenticate across multiple AWS environments.

After a deeper investigation, I realized that if the shared '.aws/credentials' file were used in addtion to setting up sso profiles in the '.aws/config' file, then Terraform could still easily be used to deploy IaC across many AWS accounts.

# My Setup
Here is my setup for Terraform and AWS SSO:
...

# How it Works
1. Run ```aws sso login```. An AWS SSO token will be stored as a JSON Web Token (JWT) file located in '.aws/sso/cache'. 
2. Run this script
3. The script will first extract that SSO Token and exchange it with IAM credentials (Access and Secret Access Keys). [AWS Blog](https://aws.amazon.com/premiumsupport/knowledge-center/sso-temporary-credentials/) for how that works.
4. Next, the script will scan the 

