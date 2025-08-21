# Backend Address Book JS - CD
The backend is equipped with basic functionalities, including the ability to add, retrieve, edit, and delete information, by connecting to  MongoDB Atlas.

### Setting up
```
nvm list
nvm use <version>

cd project_working_dir
npm install # install all dependencies

npm install mongodb
```

### 1. Set up MongoDB Atlas 
By using the cloud database, you are now testing the application in a local deployment scenario without using alocal database.
Set up account here: https://cloud.mongodb.com/
- Enter username and password for your database
- Obtain connection string and store in .env (this will contain your username and password as parameters)

Run the application:
```
npm start
```

### 2. Set up AWS Elastic Beanstalk for Deployment
We will deploy the backend of the address book application to AWS ELastic Beanstalk, then setup Github actions to automate deployment.

AWS Elastic Beanstalk is a fully managed orchestration service within AWS that makes deployingweb applications simple. It handles the complexities of infrastructure setup, scaling, anddeployment, allowing developers to focus on writing code.

#### Configuring Service Access
We need to setup the following:
1. Elastic Beanstalk --> Service role (IAM role)
   1. Create and operate EC2 for servers
   2. Set up load balancers
2. EC2 --> EC2 instance profile (wrapper around IAM role, allows EC2s to assume role)
   1. Retrieve app code from S3

As an orchestration service, Elastic Beanstalk needs to interact with various other AWS services.For example, it manages the creation and operation of EC2 instances (the servers running theapp), sets up load balancers, and so on. To do these securely, we need to explicitly grant ElasticBeanstalk the necessary permissions through an
IAM role , which is called the “service role” -essentially, a set of permissions.
On the other hand, the EC2 instance also require permissions to perform certain tasks, such as retrieving our application’s code (which we will upload later) from S3. We configure these permissions through an “EC2 instance profile”, which is a wrapper around an IAM role -essentially, another set of permissions.

To create new instance profile/IAM role: 
https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/iam-instanceprofile.html#iam-instanceprofile-create

iam > Roles > Create Role
