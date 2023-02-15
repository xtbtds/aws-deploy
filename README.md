# Deploy to AWS
**1. EBS application**
**2. RDS database**
  - v12 for free tier
  - templates -> free tier
  - set master username and password
  - default vpc
  - set db name
**3. ElastiCache redis**
  - cluster mode disabled
  - cache.t2.micro
  - number of replicas=0
  - new subnet group
**4. Custom security group (VPC)**
  - vpc=default vpc
  - add rule
  - port range 5432-6379
  - select created security group
**5. Apply security group to ElastiCache, RDS, EBS**
**6. Add AWS config details to .travis.yml**
  - bucket_name from S3
**7. Set environment variables in EBS**
  - EBS -> app -> configuration -> env vars
  - for db and redis set endpoints as PGHOST and REDIS_HOST
  - PGUSER, PGPASSWORD and PGDATABASE as created earlier
**8. IAM user**
  - attach all existing policies for "beanstalk"
  - copy keys
**9. AWS keys in Travis CI**
  - in your repo settings add AWS_ACCESS_KEY and AWS_SECRET_KEY
**10. Desploy on pushing to master branch**
