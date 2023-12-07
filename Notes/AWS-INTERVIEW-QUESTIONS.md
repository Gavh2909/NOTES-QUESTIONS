# AWS Interview questions 

1. **Question:** What is AWS Elastic Load Balancing (ELB), and how does it enhance application availability?
   - **Answer:**
     - AWS ELB distributes incoming application traffic across multiple targets, such as EC2 instances.
     - It enhances availability by automatically detecting unhealthy targets and rerouting traffic to healthy instances.
     - ELB supports three types: Application Load Balancer (ALB), Network Load Balancer (NLB), and Classic Load Balancer.

2. **Question:** Explain the purpose of Auto Scaling in AWS.
   - **Answer:**
     - Auto Scaling dynamically adjusts the number of EC2 instances in a group based on real-time demand.
     - It helps maintain application availability and ensures optimal performance by scaling out during high demand and scaling in during low demand.
     - Auto Scaling policies define when to add or remove instances.

3. **Question:** What is Amazon RDS Multi-AZ deployment, and why is it used?
   - **Answer:**
     - Multi-AZ deployment replicates a database in a secondary Availability Zone for high availability.
     - It provides automatic failover in case of a primary database failure, enhancing database resilience.
     - RDS Multi-AZ is commonly used for production databases requiring high availability.

4. **Question:** How does AWS CloudWatch differ from AWS CloudTrail?
   - **Answer:**
     - AWS CloudWatch is a monitoring service that provides metrics and logs for AWS resources.
     - AWS CloudTrail records API calls for auditing and compliance purposes.
     - While CloudWatch is proactive monitoring, CloudTrail is reactive, focusing on API activity tracking.

5. **Question:** What is AWS Lambda, and what are its key use cases?
   - **Answer:**
     - AWS Lambda is a serverless compute service that executes code in response to events.
     - Key use cases include event-driven computing, data transformation, and real-time file processing.
     - Lambda scales automatically, eliminating the need for manual resource management.

6. **Question:** Explain the purpose of Amazon VPC (Virtual Private Cloud) peering.
   - **Answer:**
     - VPC peering connects two VPCs, allowing them to communicate using private IP addresses.
     - It facilitates resource sharing and cross-VPC connectivity without the need for internet access.
     - Peering is not transitive, and each VPC must explicitly enable and configure peering connections.

7. **Question:** What is AWS IAM (Identity and Access Management), and how does it enhance security?
   - **Answer:**
     - IAM manages user access and permissions to AWS resources.
     - It enhances security by enabling the principle of least privilege and enforcing multi-factor authentication (MFA).
     - IAM allows the creation of roles, groups, and policies to control access to AWS services.

8. **Question:** Explain the purpose of Amazon SNS (Simple Notification Service).
   - **Answer:**
     - SNS is a fully managed messaging service that enables the sending of notifications to a distributed set of subscribers.
     - It supports multiple communication protocols, including HTTP, email, and SMS.
     - SNS is often used for event-driven microservices architectures.

9. **Question:** What is AWS Elastic Beanstalk, and how does it simplify application deployment?
   - **Answer:**
     - Elastic Beanstalk is a fully managed service for deploying and scaling applications without managing infrastructure.
     - It simplifies deployment by providing a platform that automatically handles capacity provisioning, load balancing, and application health monitoring.
     - Supports various programming languages and web frameworks.

10. **Question:** Explain the concept of AWS Direct Connect.
    - **Answer:**
      - Direct Connect establishes a dedicated network connection between an on-premises data center and AWS.
      - It provides a more reliable and consistent network experience compared to internet-based connections.
      - Useful for large data transfers, sensitive workloads, and hybrid cloud scenarios.

11. **Question:** What is Amazon CloudFront, and how does it improve content delivery?
    - **Answer:**
      - CloudFront is a content delivery network (CDN) that securely delivers data, videos, applications, and APIs.
      - It improves content delivery by caching content at edge locations globally, reducing latency.
      - CloudFront integrates with other AWS services and supports custom SSL certificates.

12. **Question:** How does Amazon S3 versioning contribute to data protection and recovery?
    - **Answer:**
      - S3 versioning enables the retention of multiple versions of an object in the same bucket.
      - It enhances data protection by preventing accidental deletion or overwrites.
      - Versioning assists in recovering from unintended changes or deletions by allowing the retrieval of previous versions.

13. **Question:** Explain the purpose of AWS CloudFormation and its key components.
    - **Answer:**
      - CloudFormation is an infrastructure as code service for defining and provisioning AWS resources.
      - Templates written in JSON or YAML define the architecture, and stacks represent deployed resources.
      - Stack updates and rollbacks are managed by CloudFormation.

14. **Question:** What are AWS Lambda Layers, and how do they enhance code reuse?
    - **Answer:**
      - Lambda Layers are a way to centrally manage code and data that can be shared across multiple Lambda functions.
      - They enhance code reuse by allowing common libraries and dependencies to be included in multiple functions.
      - Layers reduce duplication, simplify updates, and promote consistency in Lambda functions.

15. **Question:** How does AWS ECS (Elastic Container Service) simplify container management?
    - **Answer:**
      - ECS is a fully managed container orchestration service for Docker containers.
      - It simplifies container management by handling the deployment, scaling, and scheduling of containers.
      - ECS integrates with other AWS services, such as Elastic Load Balancing and IAM.

16. **Question:** What is Amazon Aurora, and how does it differ from traditional relational databases?
    - **Answer:**
      - Aurora is a fully managed relational database engine compatible with MySQL and PostgreSQL.
      - It differs by providing high performance, availability, and scalability, with automatic replication across multiple availability zones.
      - Aurora offers features like Aurora Global Databases for cross-region replication.

17. **Question:** Explain the purpose of AWS Key Management Service (KMS) and customer-managed CMKs.
    - **Answer:**
      - KMS is a managed service for creating and controlling encryption keys.
      - Customer-managed CMKs allow users to have greater control over key policies and rotation.
      - KMS integrates with other AWS services to secure data at rest and in transit.

18. **Question:** What are AWS CloudWatch Alarms, and how do they support monitoring?
    - **Answer:**
      - CloudWatch Alarms monitor metrics and send notifications based on defined thresholds.
      - They support monitoring by triggering actions, such as auto-scaling or sending notifications, when conditions are met.
      - Alarms provide proactive alerts for maintaining system health and performance.

19. **Question:** How does AWS CodePipeline streamline continuous integration and continuous delivery (CI/CD)?
    - **Answer:**
      - CodePipeline is a fully managed CI/CD service that automates the build, test, and deployment phases.
      - It integrates with other AWS services, such as CodeBuild and CodeDeploy, to create end-to-end workflows.
      - CodePipeline supports the creation

