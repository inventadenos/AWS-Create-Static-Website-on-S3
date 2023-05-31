# AWS-Create-Static-Website-on-S3
Create a Static Website Using Amazon S3 with CloudFront for edge distribution and Route 53 DNS hosting


AWS Services and Resources you’ll need
1. Amazon S3
2. CloudFront
3. Route53
4. Certificates Manager
5. Webfiles
6. Registered Domain Name

STEPS

AMAZON S3

1. Click create a bucket and use your registered domain name as the bucket name in S3.
2. Enable Access Control Lists
3. Disable Block all public access
4. Create bucket
5. Go to Properties tab on the bucket and scroll down to static web hosting; click edit and enable this option
6. Go to permissions tab on the bucket and edit Access Control Lists. Select list option for objects and read option for bucket ACL for everyone. Save your changes
7. Inside the bucket, click upload files and upload all the required Webfiles. 
8. Select all uploaded files and on the action tab, choose the Make public using ACL option


AMAZON CERTIFICATES MANAGER
1. Click the Request tab
2. Enter your fully qualified domain name and click request
3. If you already have a hosted zone in Route53, go to step 4 here or else execute steps 1-3 in the ROUTE53 section before you move to step 4 here.
4. Once the status to displays issued, click the certificate and click the create records in Route53 tab

CLOUDFRONT
1. Select create distribution
2. Select your S3 bucket name from the list as your origin domain
3. Enter a name for the origin (any name will do)
4. Scroll down to settings and select the price class you want to pay for
5. Select your custom SSL certificate from the drop down
6. Under Default root object, enter index.html and click create distribution
7. Wait for the distribution to become enabled

ROUTE53 - (start from step 5 if you already have a hosted zone)
1. Click create a hosted zone in route 53
2. Enter your domain name and select public hosted zone type
3. Click create hosted zone
4. Continue from step 3 in your CERTIFICATES MANAGER SECTION 
5. Enter your hosted zone and click create record
6. Choose simple routing policy option and hit next
7. Click define simple record
8. Leave the subdomain record name section blank and select alias to CloudFront distribution from the dropdown menu
9. Click define simple record.
10. Wait until it is active.

Done!  - enter your domain name on your browser to confirm the website is up and accessible.

Terminate Your Resources

1. Select CloudFront distribution and disable. Wait a while for it to be available then delete
2. Select your certificate in Certificates Manager and delete
3. Delete the 3 records you created in Route53
4. Delete your Webfiles first and then the folders before deleting the S3 bucket
5. Done

