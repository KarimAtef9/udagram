# Pipeline Process


## Run Project Locally
Before getting into deployment process, we need to check for the project locally, to confirm that everything is working fine.
we need to create our local database using postgres.
then, we need to install our backend dependencies, connecting it to the database and try running the server.
finally, we install the frontend dependencies, and run it checking for pre-existing bugs.
If we found any issues, then we need to fix it first, otherwise we can start our deployment process on AWS.


## AWS Configuration
1- Create AWS IAM user with administration security group and save its credentials.

2- Create database from AWS RDS, ensure for public access, and add all traffic in inbound rules.
   test with postgres://postgres:postgres@<database_link>:5432/postgres in postbird (Successfully connected!)

3- Create EB environment and application for hosting the backend api server, and managing load balance,
   the environment node version must match the project version.
   we must set our used environment variables used within the api (contains AWS credentials, database connection, and needed information)
   then we need to build our api to generate the Archive.zip file to be uploaded to EB.
   now we can deploy our api to AWS EB.
   API link: http://udagram-karim.us-east-1.elasticbeanstalk.com/
   
3- Create S3 bucket for hosting our frontend, enable static web hosting, set directory to index.html, and update our policy.
   S3 link: S3 link: http://project3-udagram.s3-website-us-east-1.amazonaws.com/


## Circleci Configuration

1- Create github repo, upload the project, and connect it to Circle CI.

2- Our pipeline process start by installing the project dependencies as node js

3- Then, our building phase starts by building our frontend & backend dependencies

4- Finally, we move to deploying process, starting by deploying our frontend, then setting environment variables used by our backend, and then we deploy our backend API.

