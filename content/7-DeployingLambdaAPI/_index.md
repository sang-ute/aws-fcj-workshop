---
title: "Deploying Lambda function and API Gateway"
date: "`r Sys.Date()`"
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

### Introduction

When building modern applications, **serverless architectures** allow you to focus entirely on writing code while letting the cloud provider manage infrastructure.  
In AWS, two key services make this possible:

- **Amazon API Gateway** – A fully managed service for creating, publishing, and securing APIs at scale.
- **AWS Lambda** – A compute service that runs your code on demand, without provisioning or managing servers.

Together, they enable the creation of **serverless APIs** where requests are routed through API Gateway and processed by Lambda functions.

---

### Why Serverless?

With traditional applications, you have to:

- Provision servers.
- Maintain operating systems.
- Handle scaling and failover.
- Pay for idle capacity.

With API Gateway + Lambda:

- **No server maintenance** – AWS runs the compute for you.
- **Automatic scaling** – Your code scales up and down automatically based on requests.
- **Pay per execution** – You only pay when your code runs.
- **Fast deployments** – Push new features without touching infrastructure.

---

### How It Works

1. **Client Sends Request**  
   A user or application sends an HTTP request to your API Gateway endpoint.

2. **API Gateway Routes the Request**  
   API Gateway matches the request to a configured route and passes it to the corresponding AWS Lambda function.

3. **Lambda Executes Business Logic**  
   The Lambda function processes the request — such as reading from DynamoDB, calling another API, or running AI inference — then returns a response.

4. **API Gateway Sends Back the Response**  
   API Gateway returns the processed response to the client.

---

### Benefits for This Project

By using API Gateway and Lambda, we:

- Avoid managing backend servers.
- Scale automatically during traffic spikes.
- Deploy new endpoints quickly during the lab.
- Keep costs low for development and testing.

{{% notice tip %}}
If you’re following the lab exercises, you will integrate your Lambda functions with API Gateway to handle all backend logic — a fully **serverless backend**.
{{% /notice %}}

[Go next and see](7.1-indexFaceFunction/) to see how you can deploy RESTFUL API
