# Single-Page Web App Deployment with CloudFormation

This CloudFormation template automates the deployment of a single-page web application using AWS services such as S3, CloudFront, and Route 53. The template creates the necessary resources and configures them to host a static website with a custom domain name, SSL/TLS encryption, and email-related DNS records.

## Description

The template provisions the following resources:

- An S3 bucket to store the static website files
- A CloudFront distribution to serve the website with low latency and SSL/TLS encryption
- A Route 53 hosted zone and DNS records for the custom domain name
- An S3 bucket for storing access logs
- An ACM certificate for the custom domain name
- IAM policies and roles for secure access to resources
- Email-related DNS records (MX, DKIM, SPF) for the custom domain

## Usage

1. Prerequisites:
   - An AWS account with sufficient permissions to create the required resources
   - A custom domain name registered with a domain registrar
   - A Route 53 hosted zone for the custom domain name

2. Create a new CloudFormation stack using this template.

3. Provide the following parameters:
   - `DomainName`: The custom domain name for your website (e.g., example.com)
   - `HostedZoneId`: The ID of the Route 53 hosted zone for your domain
   - `MXRecords`: A comma-separated list of MX records for your domain (default values provided)
   - `BucketName`: A globally unique name for the S3 bucket to store your website files

4. Review and create the stack. CloudFormation will provision the resources and configure them according to the template.

5. After the stack creation is complete, upload your website files to the S3 bucket.

6. Access your website using the custom domain name. CloudFront will serve the content with low latency and SSL/TLS encryption.

## ACM Certificate

The template automatically creates an ACM certificate for your custom domain name using DNS validation. The certificate is used to enable SSL/TLS encryption for the CloudFront distribution.

Make sure your Route 53 hosted zone is properly configured and accessible for the ACM certificate validation process to complete successfully.

## Email Setup

The template includes DNS records for setting up email services:

- MX records: Point to the email service provider's mail servers
- DKIM records: Used for email authentication and integrity verification
- SPF record: Specifies the mail servers authorized to send emails on behalf of your domain

Make sure to configure your email service provider to use these DNS records for proper email delivery and authentication.

## Cleanup

To delete the resources created by this template, simply delete the CloudFormation stack. CloudFormation will handle the deletion of all the associated resources, including the ACM certificate.

**Note:** Deleting the stack will not delete the Route 53 hosted zone and the custom domain name. You need to delete them separately if no longer needed.

## License

This template is released under the [MIT License](https://opensource.org/licenses/MIT).
