# 30DaysDevOpsChallenge DAY 2: NBA Game Day Notifications/Sports Alerts System
![Sportimage](/sports.png)

## Project Overview

This project is an alert system that sends real-time NBA game day score notifications to subscribed users via Email. It leverages Amazon Simple Notification Service(SNS), AWS Lambda and Python, Amazon EvenBridge and NBA APIs to provide sports fans with up-to-date game information. The project demonstrates cloud computing principles and efficient notification mechanisms.

## Technologies Used

- **Cloud Provider**:
  Amazon Web Services (AWS)

- **Core Services**:
  - Simple Notification Service (SNS)
  - Lambda
  - EventBridge

- **External API**:
  - NBA Game API ([SportsData.io](https://sportsdata.io))

- **Programming Language**:
  - Python 3.x

- **IAM Security**:
  - Implemented least privilege policies for:
    - Lambda
    - SNS
    - EventBridge


## Steps Involved

1. Create an account with [SPORTSDATA.IO](https://sportsdata.io) to get a free NBA API key

2. Create an SNS Topic on AWS:

   - Log in to your AWS Management Console
   - Navigate to the **SNS** service
   - Click on Topics, then Create topic and choose Standard as the topic type
   - Provide a name for your topic (for example: gameday_topic) and click Create topic
   - Note the Topic ARN (Amazon Resource Name)

3. Add an Email Subscription to the SNS Topic:
   - Go to the SNS topic you just created(gameday_topic)
   - Go to Subscriptions, click Create subscription
   - Then, go to Protocol to select a protocol, in my case it is  Email
   - Provide the email address, and click the create subscription button
   - Check your email for a confirmation email. Click the link to activate the subscription

4.  Create the SNS Publish Policy
    - Open the IAM service in the AWS Management Console.
    - Navigate to Policies → Create Policy.
    - Click JSON and paste the JSON policy from gd_sns_policy.json file
    - Replace REGION and ACCOUNT_ID with your AWS region and account ID.
    - Click Next: Tags (you can skip adding tags).
    - Click Next: Review.
    - Enter a name for the policy (e.g., gd_sns_policy).
    - Review, and click Create Policy

5.  Create an IAM Role for Lambda
    - Open the IAM service in the AWS Management Console.
    - Click Roles, click Create Role.
    - Select AWS Service and choose Lambda.
    - Attach the following policies:
        - SNS Publish Policy (gd_sns_policy) (created in the previous step).
        - Lambda Basic Execution Role (AWSLambdaBasicExecutionRole) (an AWS managed policy).
    - Click Next: Tags (you can skip adding tags).
    - Click Next: Review.
    - Enter a name for the role (e.g., gd_role).
    - Review, and click Create Role.
    - Copy, and save the ARN of the role for use in the Lambda function.
    - Deploy the Lambda Function
    - Open the AWS Management Console, and navigate to the Lambda service.
    - Click Create Function.
    - Select Author from Scratch.
    - Enter a function name (e.g., gd_notifications).
    - Choose Python 3.x as the runtime.
    - Assign the IAM role created earlier (gd_role) to the function.
    - Under the Function Code section:
    - Copy the content of the src/gd_notifications.py file from the repository.
    - Paste it into the inline code editor.
    - Under the Environment Variables section, add the following:
        - NBA_API_KEY: your NBA API key.
        - SNS_TOPIC_ARN: the ARN of the SNS topic created earlier.
    - Click Create Function.

    ### Set Up Automation with Eventbridge
    - Navigate to the Eventbridge service in the AWS Management Console.
    - Go to Rules → Create Rule.
    - Select Event Source: Schedule.
    - Set the cron schedule for when you want updates (e.g., hourly).
    - Under Targets, select the Lambda function (gd_notifications) and save the rule.

    ### Test the System
    - Open the Lambda function in the AWS Management Console.
    - Create a test event to simulate execution.
    - Run the function and check CloudWatch Logs for errors.
    - Verify that SMS notifications are sent to the subscribed users.

    ### What I learned

    - Designing a notification system with AWS SNS and Lambda.
    - Securing AWS services with least privilege IAM policies.
    - Automating workflows using EventBridge.
    - Integrating external APIs into cloud-based workflows.

    ![NBA Game Updates](/image2.png)