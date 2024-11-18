# Test CI/CD Using GitHub and AWS Lambda

![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

## Setup

1. Prerequisites
   1. Create a Lambda function to be updated under this CI/CD workflow.
   2. Create a ECR registry where builded image will be pushed.
   3. Setup GitHub's repository variables which are interpolated in workflow.
2. Create a stack for GitHub's OIDC provider with the given CloudFormation template.
   Stack name example: {namespaces or product name}-{environment}-{main feature}-{sub feature}
   - pn-prod-cicd-oidc
   - ns-dev-network-api
3.

## Notes

### Creating a Lambda Function

> ![IMPORTANT]
> To create a Lambda function from a container image, build your image locally and upload it to an Amazon Elastic Container Registry (Amazon ECR) repository.
>
> — [Create a Lambda function using a container image](https://docs.aws.amazon.com/lambda/latest/dg/images-create.html)

### OIDC Provider

GitHub's OIDC provider is a service that allows GitHub Actions workflows to access resources in cloud providers without storing long-lived credentials as secrets. It uses OpenID Connect (OIDC), an authentication protocol, to securely exchange short-lived tokens between GitHub and the cloud provider.

**Advantages:**

- Enhanced security: Reduces risk of credential exposure
- Improved management: Automates credential rotation
- Flexible access control: Enables fine-grained access policies

### GitHub OIDC Thumbprint

- Thumbprint usually verifies GitHub's identity during login.
- Not used for special case of GitHub Actions to AWS login. (Like using a different security system)
- A value is still needed in configuration, even if it's just a placeholder.

## References

- Deploy
  - [Deploy Python Lambda functions with container images](https://docs.aws.amazon.com/lambda/latest/dg/python-image.html)
- OIDC
  - [About Security Hardening with OpenID Connect](https://docs.github.com/en/actions/security-for-github-actions/security-hardening-your-deployments/about-security-hardening-with-openid-connect)
  - [Configuring AWS Credentials Using GitHub's OIDC Provider](https://github.com/aws-actions/configure-aws-credentials?tab=readme-ov-file#oidc)
  - [Configuring OpenID Connect in Amazon Web Services](https://docs.github.com/en/actions/security-for-github-actions/security-hardening-your-deployments/configuring-openid-connect-in-amazon-web-services)
