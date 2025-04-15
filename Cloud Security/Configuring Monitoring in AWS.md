# Lab: Monitoring Cloud Deployments with AWS

## Overview

In this lab, I will explore several AWS services used to monitor cloud environments for application health, performance, and operational insights. Monitoring is a key function in cloud deployments as it helps ensure a positive customer experience, supports developer productivity, and provides actionable data for system improvements.

Using the **AWS Management Console**, I will work with tools such as:

- **Amazon CloudWatch**
- **AWS CloudTrail**
- Other AWS observability services

These tools will help track metrics, analyze logs, set alarms, and provide visibility into the behavior and performance of deployed applications.

This lab focuses on learning how to maintain and optimize cloud resources effectively using built-in AWS monitoring capabilities.

![Lab Introduction Screenshot](./Lab%20Intro.png)


## Creating a CloudWatch Dashboard

Amazon CloudWatch Dashboards allow you to visualize key metrics and logs in a customizable, shareable interface. Below are the steps to create a basic CloudWatch Dashboard using the AWS Management Console:

### Steps

1. **Open CloudWatch Console**
   - Navigate to the **CloudWatch** service in the AWS Management Console.

2. **Create a New Dashboard**
   - In the left-hand menu, select **Dashboards**.
   - Click **Create dashboard**.
   - Enter a name for your dashboard and click **Create dashboard**.

3. **Add a Widget**
   - Choose a widget type (e.g., line, number, text).
   - Click **Next**.

4. **Select Metrics**
   - Use the **Browse** or **Search** tab to locate the metric namespace and resource (e.g., EC2 CPUUtilization).
   - Select the desired metric(s), then click **Create widget**.

5. **Arrange and Customize**
   - Resize and reposition widgets as needed.
   - You can edit titles, change time ranges, and apply filters.

6. **Save Dashboard**
   - Once all widgets are added, click **Save dashboard** in the top-right corner.

This dashboard will now give you real-time visual insight into your AWS resources' health and performance.

### Example Dashboard

![CloudWatch Dashboard Example](./CloudWatch%20Dashboard.png)
