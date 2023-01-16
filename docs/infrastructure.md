# Project Infrastructure 

The High level Structure is built on 3 main Services From Amazon Web Services:
   1. Relational Database Service. (RDS)
   1. Simple Storage Service. (S3)
   1. Elastic Beanstalk. (EB)


# Configuring RDS 

This is used by the project to store user metadata, such as user credentials. You can access this database from your application running either locally or on the cloud. Here are the steps to follow:

|      Field                         |        Value                            |
|------------------------------------|-----------------------------------------| 
|  Creation Method                   |   Standard Create, Easy Create          |
|  Engine Option                     |   PostgreSQL 12 or 13                   |
|  Templates                         |   Free Tier                             |
|  DB Identifier, Username, Password |   Your Choice                           |
|  Instance Configuration            |   Burstable Classes with Minimal Size   |
|  Database Name                     |   Postgres                              |
|  Connectivity                      |                                         |
|  VPC and Subnet                    |   Default                               |
|  Public Access                     |   YES                                   |
|  VPC Security Group                |   Default                               |
|  Availability Zone                 |   No Preferences                        |
|  Database Port                     |   5432                                  |
| initial database name              |   postgres                              |



# Configurtion S3

|      Field                         |        Value                            |
|------------------------------------|-----------------------------------------| 
|  Bucket Name                       |   Choose a unique name                  |
|  AWS Region                        |   Default                               |
|  Object Ownership                  |   ACLs enabled Bucket owner preferred   |
|  Block all public access           |   No Create a public S3 bucket          |


1. Add Bucket Policy to Allow other AWS to connect to the bucket
```
{
"Version":"2012-10-17",
"Statement":[
  {
      "Sid":"Stmt1625306057759",
      "Principal":"*",
      "Action":"s3:*",
      "Effect":"Allow",
      "Resource":"arn:aws:s3:::[bucket-name]/*"
  }
]
}
```

1. Add CORS config
```
[
 {
     "AllowedHeaders": [
         "*",
         "Content-Type",
         "Authorization",
         "Access-Control-Allow-Origin",
         "Access-Control-Allow-Headers",
         "Access-Control-Allow-Methods"
     ],
     "AllowedMethods": [
         "POST",
         "GET",
         "PUT",
         "DELETE",
         "HEAD"
     ],
     "AllowedOrigins": [
         "*"
     ],
     "ExposeHeaders": []
 }
]
```

# Configure EB
1. cd to API directory
1. eb init
1. eb create --single --keyname mykeypair --instance-types t2.medium
1. `npm install`
1. `npm run start`
1. go to EB on Website console and Add Enviornmental Variables for each varabile in set_env.sh
1. `eb use [env-name]`
1. `git add -A`
1. `git commit -m "basic deploy"`
1. `eb deploy`