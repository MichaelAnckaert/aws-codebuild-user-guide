# Test and Debug Locally with the CodeBuild Agent<a name="use-codebuild-agent"></a>

 This topic provides information about how to run the AWS CodeBuild agent and subscribe to notifications about new versions of the agent\. 

## Test and Debug on a Local Machine with the CodeBuild Agent<a name="use-codebuild-agent"></a>

 You can use the AWS CodeBuild agent to test and debug builds on a local machine\. To use the agent: 

1.  Download the [codebuild\.sh](https://github.com/aws/aws-codebuild-docker-images/blob/master/local_builds/codebuild_build.sh) script\. 

1.  Run the script and specify your container images and output directory: 

   ```
   codebuild_build.sh [-i image_name] [-a artifact_output_directory] [options]
   ```

 The CodeBuild agent is available from [https://hub\.docker\.com/r/amazon/aws\-codebuild\-local/](https://hub.docker.com/r/amazon/aws-codebuild-local/)\. Its Secure Hash Algorithm \(SHA\) signature is `2c2b0a6b3595abfb5408cfa263d91ef280a910e2a03e920f65c3ffb9a97d0550`\. You can use this to identify the version of the agent\. To see the agent's SHA signature, run the following command: 

```
docker inspect amazon/aws-codebuild-local
```

## Receive Notifications for New CodeBuild Agent Versions<a name="receive-codebuild-agent-notifications"></a>

 Amazon SNS can notify you when new versions of the AWS CodeBuild Agent are released\. Use the following procedure to subscribe to these notifications\. 

 ** To subscribe to the CodeBuild Agent notifications:** 

1.  Open the Amazon SNS console at [https://console\.aws\.amazon\.com/sns/v3/home](https://console.aws.amazon.com/sns/v3/home)\. 

1.  In the navigation bar, if it's not already selected, change the region to **US East \(N\. Virginia\)**, if it not already selected\. You must select this region because the SNS notifications that you are subscribing to are created in this region\. 

1.  In the navigation pane, choose **Subscriptions**\. 

1.  Choose **Create subscription**\. 

1.  In the **Create subscription** dialog box: 

   1.  For **Topic ARN**, use the following Amazon Resource Name \(ARN\): 

      ```
      arn:aws:sns:us-east-1:850632864840:AWS-CodeBuild-Local-Agent-Updates
      ```

   1.  For **Protocol** choose **Email** or **SMS**\. 

   1.  For **Endpoint** choose where to receive the notifications: 
      +  If you choose **Email**, type an email address\. 
      +  If you choose **SMS**, type a phone number, including area code\. 

   1.  Choose **Create subscription**\. 

1.  If you choose **Email**, you'll receive an email asking you to confirm your subscription\. Follow the directions in the email to complete your subscription\. 

 When a new version of the CodeBuild agent is released, subscribers receive notifications\. If you no longer want to receive these notifications, use the following procedure to unsubscribe\. 

 ** To unsubscribe from CodeBuild agent notifications:** 

1.  Open the Amazon SNS console at [https://console\.aws\.amazon\.com/sns/v3/home](https://console.aws.amazon.com/sns/v3/home)\. 

1.  In the navigation pane, choose **Subscriptions**\. 

1.  Select the subscription and then from **Actions**, choose **Delete subscriptions**\. When you are prompted to confirm, choose **Delete**\. 