# aws_gota
aws_gota

S3 -  need to set up a Rule that trigger actions 
  SQL statement - > SELECT * , timestamp() as timestamps FROM 'GOTA/gota_test'


Lambda
  see test.zip + test.yaml  - this function will take the iot event and append the data to a csv file stored in an S3 bucket

Roles(see files)
  AWSLambdaBasicExecutionRole
  S3_ObjectFullAccess
  AmazonS3FullAccess

IoT Rules
test_iot
define a sql and topic publish to the IoT -> GOTA/gota_test'
   SQL statement - > SELECT * , timestamp() as timestamps FROM 'GOTA/gota_test'
define bucket name and key (file stored on S3 bucket) Ex.: test_iot.json

  Roles
   -aws-iot-rule-gota_s1_Sense-action-1-role-LavSur_S3
   {
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Allow",
        "Action": "s3:PutObject",
        "Resource": "arn:aws:s3:::ghotrix/GHOTRIX/LavSur/gota_s1/data_sense//*"
    }
}

-aws-iot-rule-test_iot-action-1-role-LavSur_S3
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Allow",
        "Action": "s3:PutObject",
        "Resource": "arn:aws:s3:::gotaproject/*"
    }
}

 -S3_ghotrix_put
 

  {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": "s3:PutObject",
            "Resource": "arn:aws:s3:::ghotrix/*"
        }
    ]
}
  
