**Authentication and Autherization :**

| **Aspect**            | **Authentication**                  | **Authorization**                       |
| -----------------   | -------------------------------- | ----------------------------------- |
| Question Answered   | "Who are you?"                   | "What are you allowed to do?"       |
| Happens First?      | ✅ Yes                            | 🚫 Only after authentication        |
| Involves?           | Credentials (password, ID, etc.) | Permissions, roles, access policies |
| Example             | Logging into a system            | Accessing admin panel after login   |


**AWS Cloud Formation template:**
  
  We can think of it as Infrastructure as Code (IaC) — instead of manually clicking through the AWS console to set up your resources (like EC2, S3, RDS, etc.), you write a template that defines everything you want, and CloudFormation sets it up for you.

Example: Create EC2 instance, we can use JSON or YAML for writing templates.

 **Metrics and Traces**

 | Feature        | CloudWatch Metrics (what happened)| CloudWatch Traces (X-Ray) (Why its happened)|
| --------------  | ------------------------          | --------------------------------- |
| Type            | Numeric time-series data          | End-to-end request tracking       |
| Scope           | Resource-level                    | Application-level (requests)      |
| Best For        | Alerts, dashboards                | Debugging, tracing latency/errors |
| Auto-collected  | Yes, for AWS services             | Yes, with X-Ray enabled           |
| Example         | CPU = 80%                         | API Gateway → Lambda → DynamoDB   |

*how they work together*

| Task                                         | Tool                         |
| -------------------------------------------- | ---------------------------- |
| CPU > 90% alarm                              | CloudWatch Metric            |
| Figure out why a request is slow             | CloudWatch Trace (X-Ray)     |
| Visualize request flow between microservices | Trace map                    |
| Monitor Lambda invocations over time         | Metric                       |
| See what part of a Lambda took time          | Trace (segments/subsegments) |

