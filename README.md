Autoscaling Group

## Overview
This practical demonstrates the process of creating and configuring an Auto Scaling Group (ASG) on Amazon Web Services (AWS). Auto Scaling Groups are used to automatically adjust the number of EC2 instances based on demand, improving fault tolerance, performance, and cost-efficiency.

In this exercise, we go through the following steps:
1. **Creating a Launch Template** – A reusable configuration for launching EC2 instances.
2. **Configuring an Auto Scaling Group** – Automatically manages and scales EC2 instances as per demand.
3. **Implementing Target Tracking Scaling** – Automatically adjusts instance count based on a defined metric (e.g., CPU utilization).
4. **Monitoring and Adjusting Scaling Policies** – Using Amazon CloudWatch to monitor and fine-tune settings.

## Step-by-Step Instructions

### Step 1: Create a Launch Template
A Launch Template is a reusable blueprint for launching EC2 instances with predefined settings such as AMI, instance type, key pair, etc.

1. **Navigate to Launch Templates**
    - Go to the AWS Management Console and navigate to the EC2 Dashboard.
    - From the left-hand menu, select **Launch Templates** and click **Create Launch Template**.

2. **Configure the Launch Template**
    - **Template Name**: Give a unique name (e.g., MyApp-Launch-Template).
    - **AMI (Amazon Machine Image)**: Select an AMI containing the OS and applications required.
    - **Instance Type**: Choose an appropriate instance type (e.g., `t2.micro`).
    - **Key Pair**: Select or create an existing key pair for SSH (Linux) or RDP (Windows) access.
    - **Network Settings**: Choose the VPC and subnets for deployment.
    - **Security Groups**: Select a security group allowing relevant traffic.
    - **Storage**: Configure the EBS volumes (e.g., 30 GB for root volume).
    - **IAM Role (Optional)**: Assign an IAM role if the instance needs to access other AWS services.
    - **User Data (Optional)**: Add any scripts to install software or configure the instance on launch.

3. **Review and Create**  
    Once the configuration is complete, review the settings and click **Create Launch Template**.

### Step 2: Create an Auto Scaling Group (ASG)
An Auto Scaling Group is a collection of EC2 instances managed automatically to maintain desired performance levels and handle changing demand.

1. **Navigate to Auto Scaling Groups**
    - Go to the EC2 Dashboard and select **Auto Scaling Groups** from the left-hand menu.
    - Click **Create Auto Scaling Group**.

2. **Configure the Auto Scaling Group**
    - **Auto Scaling Group Name**: Provide a unique name (e.g., MyApp-ASG).
    - **Launch Template**: Select the launch template created in Step 1.
    - **Network Settings**: Select the VPC and subnets (for high availability, select multiple subnets in different Availability Zones).
    - **Group Size**: Set the desired, minimum, and maximum number of instances.

3. **Review and Create**  
    Once settings are reviewed, click **Create Auto Scaling Group**.

### Step 3: Configure Target Tracking Scaling
Target tracking scaling automatically adjusts the number of EC2 instances based on a target metric, such as CPU utilization.

1. **Navigate to Scaling Policies**
    - In the Auto Scaling Group, navigate to the **Automatic Scaling** tab.
    - Click **Add Policy** to create a new scaling policy.

2. **Create Target Tracking Scaling Policy**
    - **Policy Type**: Select **Target Tracking Scaling**.
    - **Metric Type**: Choose **Average CPU Utilization** (you can use other metrics like network throughput or custom CloudWatch metrics).
    - **Target Value**: Set a CPU utilization target (e.g., 35%). AWS will automatically adjust instances to maintain this target.
    - **Instance Warm-up Time**: Set a warm-up period (e.g., 300 seconds) for new instances.

3. **Review and Create Policy**  
    After reviewing the policy, click **Create Policy**.

### Step 4: Monitor and Adjust Auto Scaling
1. **Monitor Scaling**  
    Use Amazon CloudWatch to monitor metrics like CPU utilization and observe how instances scale in and out.
    
2. **Tune Settings**  
    Adjust parameters such as target values or group size based on the performance of your application.

## Key Benefits of Auto Scaling
- **Hands-off Scaling**: AWS automatically manages the scaling of instances, reducing the need for manual intervention.
- **Improved Performance**: Maintains consistent performance by scaling in response to metrics like CPU utilization.

refer my uploaded file for screenshots. 

- **Cost Efficiency**: Reduces costs by terminating instances when demand decreases, ensuring you're only paying for what you need.

## Conclusion
This practical provided an in-depth understanding of how to configure and monitor an Auto Scaling Group using AWS EC2 and CloudWatch. Auto Scaling helps ensure the availability and performance of applications while optimizing costs.

