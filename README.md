# Serverless Project on AWS

## Introduction

### Deployed a serverless web application using API Gateway,AWS Lambda,DynamoDB,and S3. Implemented secure frontend hosting with S3+CloudFront.

## Architecture 
### Below is a high-level overview of the architecture used:
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/1.Architecture.png?raw=true)

## Create a DynamoDB table with name employeeData , PK = employeeid, string
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/2.DynamoDB--Create%20table.png?raw=true)
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/3.Go%20through%20Customized%20settings.png?raw=true)
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/4.Off%20Auto%20scaling%20in%20Read%20&%20Write.png?raw=true)

## Create a IAM ROLE with Trusted Entity Lambda and Permissions Dynamodb and attach to Lambda functions
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/5.IAM--Roles--TE-Lambda.png?raw=true)
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/6.Permissions-DynamoDBFullaccess.png?raw=true)
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/7.Name%20&%20Create%20Role.png?raw=true)

## Create a Lambda FUnction, Name : insertEmployeeData , attach role and copy paste the code
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/8.Lambda--FName%20&%20Select%20Runtime.png?raw=true)
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/9.Permissions--Select%20existing%20Role%20&%20Create%20function.png?raw=true)
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/10.Lambda--Functions--insertEmployeeData%20&%20Deploy%20the%20code.png?raw=true)

## Create a Lambda FUnction, Name : getEmployee , attach role and copy paste the code
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/11.Lambda--FName%20&%20Select%20Runtime.png?raw=true)
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/12.Permissions--Select%20existing%20Role%20&%20Create%20function.png?raw=true)
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/13.Lambda--Functions--getEmployeeData%20&%20Deploy%20the%20code.png?raw=true)

## Create a API Gateway : REST API : 
### Name: Davidson-API
### API Endpoint type: Edge-Optimized (available everywhere, Region= Only for that Region)
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/14.API%20Gateway--Rest%20API--Create%20API,Name,endpoint%20&%20clict%20Create%20API.png?raw=true)
### Create Method --> Method type : POST , Lambda Function, Region: mumbai, select insertEmployeeData function --> create method
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/15.API--Resources-Create%20method.png?raw=true)
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/16.POST%20method,%20Lambda%20function-insertEmployeeData%20function%20&%20Create%20method.png?raw=true)
### Create Method --> Method type : GET , Lambda Function, Region: mumbai, select getEmployee function --> create method
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/17.GET%20method,%20Lambda%20function-GETEmployees%20function%20&%20Create%20method.png?raw=true)
### Click on API employee --> Enable CORS --> GET and POST --> Save
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/18.Enable%20CORS.png?raw=true)
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/19.Select%20GET,POST%20&%20Save.png?raw=true)
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/20.Deploy%20API.png?raw=true)
### Deploy API --> New Stage --> employeeapi
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/21.Stage,Name%20&%20Deploy.png?raw=true)
### Copy the URL and update in script.js (https://rqjq7fa3zg.execute-api.ap-south-1.amazonaws.com/employeeapi)
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/22.Copy%20invoke%20URL.png?raw=true)
### Create a Public S3 Bucket and upload index.html and script.js
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/23.Create%20Private%20General%20purpose%20Bucket.png?raw=true)
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/24.Upload%20index.html%20&%20script.js.png?raw=true)
### Create a CloudFront Distribution:
### Name : Davidson-Distribution
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/25.CloudFront--Name%20&%20Click%20Next.png?raw=true)
### Select Origin-S3 Bucket
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/26.Select%20Origin-S3%20bucket.png?raw=true)
### Have a Review
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/27.Review.png?raw=true)
### Click Create Distribution
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/28.Create%20Distribution.png?raw=true)
### Copy DNS Name
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/29.Copy%20DNS%20Name.png?raw=true)
### Paste on any Web Browser
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/30.Paste%20on%20web%20Browser.png?raw=true)
### Project Deployed
![](https://github.com/YenumulaDavidson/Serverless-Project-on-AWS/blob/main/Serverless%20Project%20IMAGES/31.Deployed.png?raw=true)





