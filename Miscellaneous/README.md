Authentication and Autherization :

| Aspect            | Authentication                   | Authorization                       |
| ----------------- | -------------------------------- | ----------------------------------- |
| Question Answered | "Who are you?"                   | "What are you allowed to do?"       |
| Happens First?    | ✅ Yes                            | 🚫 Only after authentication        |
| Involves?         | Credentials (password, ID, etc.) | Permissions, roles, access policies |
| Example           | Logging into a system            | Accessing admin panel after login   |


AWS Cloud Formation template:
  
  We can think of it as Infrastructure as Code (IaC) — instead of manually clicking through the AWS console to set up your resources (like EC2, S3, RDS, etc.), you write a template that defines everything you want, and CloudFormation sets it up for you.

Example: Create EC2 instance, we can use JSON or YAML for writing templates.

