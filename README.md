AWS Lambda Attachment Extractor
===============================

This is a very simple project which can be used for reference when creating Lambda functions to manipulate email 
files stored to an Amazon S3 bucket, typically by an inbound SES routing rule. See 
['AWS Documentation'](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/receiving-email.html) for more information.


Use cases
---------

The original use for this project was to process DMARC reports, getting .ZIP and .GZIP attachments from emails stored in S3 and extracting the archives, resulting in .XML files, which are then uploaded to another S3 bucket for processing by another service.

The Python file doesn't perform security checks on attachments and will ignore anything which does not 
result in an .XML file. The original email is then deleted after processing takes place.

This type of processing may be very useful for extracting DMARC reports, which are sent by email service providers 
to an email address specified in the _rua_ section of your DMARC DNS record, see https://dmarc.org/overview/. You 
will then be left with a bucket of XML DMARC reports which you may wish to process manually or upload to a service such
as https://dmarcian.com/dmarc-xml/.

Getting Started
---------------

To get started, simply upload the python file to Lambda, changing the variables if required. This lambda function expects a S3 put event to trigger it, see ['this tutorial'](http://docs.aws.amazon.com/lambda/latest/dg/with-s3-example.html) for more information.
