# Setting-Cloudfront-for-s3-as origin

Amazon CloudFront is a global content delivery network (CDN) service built for high-speed, low-latency performance, security, and developer ease-of-use.
We can set Cloudfront to different origins as Ec2 instance, S3 bucket

## Table of Contents

1. Create S3 bucket
2. Host a website in S3 bucket
3. Create Cloudfront
 
Now, let’s get into it!

# Step 1 Create S3 bucket

Go to Amazon S3 and click on "create bucket"

![image](https://user-images.githubusercontent.com/100774483/159635003-84bca3a4-6f2e-4767-99e9-1713f6e0b82d.png)


Provide the details and proceed to create bucket

![image](https://user-images.githubusercontent.com/100774483/159635220-a51629a5-d19d-471f-aae4-e2479b865d8b.png)


![image](https://user-images.githubusercontent.com/100774483/159635320-b1988e10-9bb4-4c9f-835a-a92d825a4d5d.png)


# Host a website in S3 bucket

The bucket is created, we are proceeding to upload the site contents to S3 now.

1. Select the bucket and click on upload

![image](https://user-images.githubusercontent.com/100774483/159635717-66223c62-7a1e-4259-9322-499b7f5f8040.png)

2. select file by clicking "add files" and upload them

![image](https://user-images.githubusercontent.com/100774483/159635879-e0e3ffcb-9dfc-4bd2-9479-fc0c099b2cd7.png)

3. Site contents are uploaded now.

![image](https://user-images.githubusercontent.com/100774483/159636540-e5aa2600-5790-4ed8-928f-893203aef6e4.png)


4. Enable "static webshodting" for s3 bucket

Go to properties

![image](https://user-images.githubusercontent.com/100774483/159636697-684a7a2d-f82c-412f-b49c-84f8f0562c24.png)

Scroll down to "Static website hosting" and click edit

![image](https://user-images.githubusercontent.com/100774483/159636827-9a783f31-7d8b-4ecf-999e-44a974cd188b.png)


Enable "static web histing" and mention the index file on "Index document" the click on "save changes"

![image](https://user-images.githubusercontent.com/100774483/159637906-15867bb1-9aa9-4b32-96f1-342bd19c8f43.png)



# Step 3 : Create Cloudfront

Go to cloudfron service and click on "create Distribution"

![image](https://user-images.githubusercontent.com/100774483/159639055-0bc671ea-a77d-4f0d-942f-c8772b3f5280.png)


Choose the S3 bucket created as origin 

![image](https://user-images.githubusercontent.com/100774483/159639401-e004735a-3c1f-4fd0-b1c3-b9b342b5c6be.png)

For S3 bucket access, select "Yes use OAI (bucket can restrict access to only CloudFront)" and select the "Origin access identity" from drop down. Also select "Yes, update the bucket policy" below. So that a new bucket policy will create for accessing the files on bucket.


![image](https://user-images.githubusercontent.com/100774483/159639746-43f077d9-cc88-40ca-a894-4a2e75dd31d7.png)

We can select "HTTP to HTTPS redirectio" while creating the cloudfront (optional)

![image](https://user-images.githubusercontent.com/100774483/159640419-c6154ef5-566e-494e-bed3-fdf382bc0f07.png)

If we wnat to use a domain instead of the distribution url, we need to mention the domain here, (optional)

![image](https://user-images.githubusercontent.com/100774483/159640906-34817232-e23f-4ca5-a46d-946ca5c89c39.png)


Im going to use "cloud.jibin.online" as an alternative domain name and selecting the SSL i have created for it.


After these all, proceed to create distribution

![image](https://user-images.githubusercontent.com/100774483/159641196-522b2e34-6933-4f8f-82c7-538124081b02.png)

Now, the Cloudfront distribution has been creted.

![image](https://user-images.githubusercontent.com/100774483/159641566-4c83f70b-d084-49e5-9d00-25237bc4779d.png)

We can use the "Dis"tribution domain name" to load the website now.

![image](https://user-images.githubusercontent.com/100774483/159642541-d3456518-e192-424a-a03d-4c13712b6968.png)


![image](https://user-images.githubusercontent.com/100774483/159642672-29bb1b7c-103e-4ee5-b7e8-584086de7942.png)


Pointing the cname record on route53 now,

1. Go to Route53
2. Select the hosted domain
3. Click "create record"

![image](https://user-images.githubusercontent.com/100774483/159643653-c24670c4-d675-47b9-ade4-de15084126d4.png)

Mention the record name as we provided while creating cloudfron distribution. Set the "record type" as "A" and enable "alias". 
Select "Route traffic to" as "Alias to cloudfron distrubution" and select the distribution we created on "Choose distribution" then proceed to create the record.

Now, we can use the alternative domain instead of the distribution URL. Please chekc the screenshot below. I have added te alternative domain as "cloud.jibin.online"

![image](https://user-images.githubusercontent.com/100774483/159644911-1fec614f-82f1-4818-a3aa-507e9b4333ce.png)


# Conclusion

In this tutorial we discussed how to set a cloudfront for an S3 origin. The goal is to get you started on using Amazon CloudFront for for high-speed, low-latency performance, security, and developer ease-of-use as it is cheap and easy to do.


