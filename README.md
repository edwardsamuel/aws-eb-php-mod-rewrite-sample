# PHP with mod_rewrite Sample Project on AWS Elastic Beanstalk

This is a sample PHP web application to be run  in **AWS Elastic Beanstalk**.
The intention of the app is to answer a question in [stackoverflow.com](http://stackoverflow.com/questions/31324251/red-alert-aws). The question is how to use `mod_rewrite` in AWS Elastic Beanstalk using PHP environment, which uses Apache as web server at the time of writing this app.

Note: This app is **NOT** secure. Don't use it in actual/production environment. Please destroy the AWS Elastic Beanstalk environment after you tried this app.

The app contains some PHP files:

 - `index.php`: Home page
 - `phpinfo.php`: Print `phpinfo()`
 - `searchPage.php`: Print `$_SERVER` and `$_REQUEST` variable

How to create PHP environment on AWS Elastic Beanstalk:

1. Open [AWS Elastic Beanstalk Web Console](https://console.aws.amazon.com/elasticbeanstalk/home).
2. Click **Create a New Environment**.
3. Fill the Application Information.
4. Choose **Create web server** and attach appropriate IAM role.
5. In **Environment Type** page:
	1. Choose **Predefined configuration**: **PHP**. Make sure you configuration is **64bit Amazon Linux 2015.03 v1.4.3 running PHP 5.6** or any other compatible configuration.
	2. Environment type **Load balancing, auto scaling**.
	3. Click **Next**.
6. In **Application Version** page:
	1. Choose **Upload your own** and select the zip file of this app (can be downloaded [here](https://github.com/edwardsamuel/aws-eb-php-mod-rewrite-sample/archive/master.zip)).
	2. Choose **Fixed** and fill the param with **1**.
	3. Click **Next**.
7. Fill the Environment Information.
8. In **Additional Resources**, check on **Create this environment inside a VPC**.
9. Fill the Configuration Details.
10. Fill the Environment Tags.
11. Fill the VPC Configuration. Make sure your **ELB visibility** is **External**.
12. Check the Review Information.
13. Deploy and wait until finish.

What you can check in this app:

 - `http://<your-env-url>.elasticbeanstalk.com/aws-eb-php-mod-rewrite-sample-master/index.php`: Check for successful PHP deployment.
 - `http://<your-env-url>.elasticbeanstalk.com/aws-eb-php-mod-rewrite-sample-master/phpinfo.php`: Check for your PHP environment. You can make sure your `mod_rewrite` is enabled here.
 - `http://<your-env-url>.elasticbeanstalk.com/aws-eb-php-mod-rewrite-sample-master/searchPage.php?crs_category=business`: Original PHP script for `mod_rewrite` test.
 - `http://<your-env-url>.elasticbeanstalk.com/aws-eb-php-mod-rewrite-sample-master/category/business/`: `mod_rewrite` test. This url will be handled by `searchPage.php`.

