# Meteor Slingshot Example

## Description

This is a sample project that shows how to create an image uploader using Amazon S3, Meteor, and the [slingshot](https://github.com/CulturalMe/meteor-slingshot) package. Make sure to follow the AWS IAM Setup below before running the sample project.

## AWS IAM Setup

1. Navigate to IAM home https://console.aws.amazon.com/iam/home
2. Navigate to Users -> Create New Users
  1. Specify username
  2. Make sure generate access key is checked
  3. Show user security credentials and add to `settings.json` as `AWSAccessKeyId` and `AWSSecretAccessKey`
3. Navigate to Policies -> Create New Policy
  1. Select “Create Your Own Policy”
  2. Give it a name, description
  3. Paste the text from [This File](https://github.com/quackware/meteor-slingshot-example/blob/master/iam_files/policy_document.json) into `Policy Document` making sure to replace <bucketname> (2 occurences) with the name of your bucket you will create in step 4)
  4. Select your newly created policy (you may need to filter for it) and choose “Policy Actions” -> “Attach” and attach your user you created in step 2)
4. Navigate to s3 home https://console.aws.amazon.com/s3/home
  1. Create a bucket with a name (which you used in step 3) and select “US Standard” Region
    1. Note that the region can be different, but requires additional setup with slingshot to work
  2. Select the bucket and then click the `Properties` tab in the top right
  3. Click “Permissions” to open the dropdown
    1. Click `Add/Edit CORS configuration` and paste in the following [Cors Configuration](https://github.com/quackware/meteor-slingshot-example/blob/master/iam_files/cors_configuration.xml)
    2. Click `Edit Bucket policy` and paste in this [Bucket Policy](https://github.com/quackware/meteor-slingshot-example/blob/master/iam_files/bucket_policy.json) making sure to replace `<awsaccountid>` with your account id (found in Account Settings), `<iamusername>` with your iam user in part 2), and `<bucketname>` you created above
  4. Add your bucket name to settings.json using the `S3Bucket` key
5. You should be good to go!
