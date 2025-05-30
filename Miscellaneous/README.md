Authentication and Autherization :

| Aspect            | Authentication                   | Authorization                       |
| ----------------- | -------------------------------- | ----------------------------------- |
| Question Answered | "Who are you?"                   | "What are you allowed to do?"       |
| Happens First?    | ✅ Yes                            | 🚫 Only after authentication        |
| Involves?         | Credentials (password, ID, etc.) | Permissions, roles, access policies |
| Example           | Logging into a system            | Accessing admin panel after login   |


AWS Cloud Formation Templates:

  Think of it as "Infrastructure as Code (IaC)" — instead of manually clicking through the AWS console to set up your resources (like EC2, S3, RDS, etc.), you write a template that defines everything you want, and 
  CloudFormation sets it up for you.

 Example: template for EC2 Instance -- we can follow the documentation for creating templates, Yaml or Json format can be used.

AWSTemplateFormatVersion: '2010-09-09'
Description: A simple EC2 instance

Parameters:
  InstanceType:
    Type: String
    Default: t2.micro
    Description: EC2 instance type

Resources:
  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: !Ref InstanceType
      ImageId: ami-0abcdef1234567890 # Example AMI ID
      Tags:
        - Key: Name
          Value: MyInstance

Outputs:
  InstanceId:
    Description: The Instance ID
    Value: !Ref MyEC2Instance

   
