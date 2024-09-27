# Introduction to AWS ECR (Elastic Container Registry)

1. What is AWS ECR?
2. Key Benefits of ECR
3. Getting Started with AWS ECR
   - Creating an ECR Repository
   - Installing AWS CLI
   - Configuring AWS CLI
4. Pushing Docker Images to ECR
5. Pulling Docker Images from ECR
6. Cleaning Up Resources

## 1. What is AWS ECR?
AWS Elastic Container Registry (ECR) is a fully managed container image registry service provided by Amazon Web Services (AWS). It enables you to store, manage, and deploy container images (Docker images) securely, making it an essential component of your containerized application development workflow. ECR integrates seamlessly with other AWS services like Amazon Elastic Container Service (ECS) and Amazon Elastic Kubernetes Service (EKS).

## 2. Key Benefits of ECR
- **Security**: ECR offers encryption at rest, and images are stored in private repositories by default, ensuring the security of your container images.
- **Integration**: ECR integrates smoothly with AWS services like ECS and EKS, simplifying the deployment process.
- **Scalability**: As a managed service, ECR automatically scales to meet the demands of your container image storage.
- **Availability**: ECR guarantees high availability, reducing the risk of image unavailability during critical times.
- **Lifecycle Policies**: You can define lifecycle policies to automate the cleanup of unused or old container images, helping you save on storage costs.

## 3. Getting Started with AWS ECR
### Creating an ECR Repository
1. Go to the AWS Management Console and navigate to the Amazon ECR service.

![Screenshot (1542)](https://github.com/user-attachments/assets/16f6c741-0661-4ecf-bc79-5c94734d8fc3)

2. Click on "Create repository" to create a new repository.
3. Enter a unique name for your repository and click "Create repository."

![Screenshot (1543)](https://github.com/user-attachments/assets/2a807bcb-227c-4aac-a918-744a3e6c8fa2)

![Screenshot (1544)](https://github.com/user-attachments/assets/dbcf0e20-da1a-4e9d-b82f-20e907c68b6f)


### Installing AWS CLI
To interact with ECR from your local machine, you'll need to have the AWS Command Line Interface (CLI) installed. Follow the instructions in the [AWS CLI User Guide](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html) to install it.
```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```
### Configuring AWS CLI
After installing the AWS CLI, open a terminal and run the following command to configure your CLI with your AWS credentials:

```
aws configure
```

Enter your AWS Access Key ID, Secret Access Key, default region, and preferred output format when prompted.

## 4. Pushing Docker Images to ECR
Now that you have your ECR repository set up and the AWS CLI configured, let's push a Docker image to ECR.

![Screenshot (1545)](https://github.com/user-attachments/assets/fe9b1dd5-71eb-408c-8d82-d3733f3d1146)


1. Build your Docker image locally using the `docker build` command:

```
docker build -t <your-image-name> <path-to-dockerfile>
```

![Screenshot (1549)](https://github.com/user-attachments/assets/4241ea16-4f35-4fec-b49a-6ab68082578c)


2. Tag the image with your ECR repository URI:

```
docker tag <your-image-name>:<tag> <your-aws-account-id>.dkr.ecr.<your-region>.amazonaws.com/<your-repository-name>:<tag>
```

3. Log in to your ECR registry using the AWS CLI:

```
aws ecr get-login-password --region <your-region> | docker login --username AWS --password-stdin <your-aws-account-id>.dkr.ecr.<your-region>.amazonaws.com
```

4. Push the Docker image to ECR:

```
docker push <your-aws-account-id>.dkr.ecr.<your-region>.amazonaws.com/<your-repository-name>:<tag>
```

## 5. Pulling Docker Images from ECR
To pull and use the Docker images from ECR on another system or AWS service, follow these steps:

1. Log in to ECR using the AWS CLI as shown in Step 3 of the previous section.
2. Pull the Docker image from ECR:

```
docker pull <your-aws-account-id>.dkr.ecr.<your-region>.amazonaws.com/<your-repository-name>:<tag>
```

![Screenshot (1551)](https://github.com/user-attachments/assets/07f8404a-aee0-42fc-9fff-aa274b13c81e)

![Screenshot (1553)](https://github.com/user-attachments/assets/d3342343-e55b-4922-b17a-81330af52f84)
