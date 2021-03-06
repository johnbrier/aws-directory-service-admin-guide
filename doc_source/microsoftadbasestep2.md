# Step 2: Create Your Microsoft AD Directory in AWS<a name="microsoftadbasestep2"></a>

You can use three different methods to create your directory\. You can use the AWS Management Console procedure \(recommended for this tutorial\) or you can use either the AWS CLI or AWS Tools for Windows PowerShell procedures to create your directory\.

**Method 1: To create your Microsoft AD directory \(AWS Management Console\)**

1. Open the AWS Directory Service console at [https://console\.aws\.amazon\.com/directoryservice/](https://console.aws.amazon.com/directoryservice//)\.

1. In the AWS Directory Service console navigation pane, choose **Directories**\.

1. Choose **Set up directory**, and then choose **Microsoft AD**\.

1. On the **Directory details** page, provide the following information:

   + For **Edition**, select either **Standard** or **Enterprise** edition\. For more information about editions, see [AWS Directory Service for Microsoft Active Directory](what_is.md#microsoftad)\. 

   + For **Directory DNS**, type **corp\.example\.com**\.

   + For **NetBIOS name**, type **corp**\.

   + For **Admin password**, type the password you want to use for this account and type the password again in **Confirm password**\. This **Admin** account is automatically created during the directory creation process\. The password cannot include the word *admin*\. The directory administrator password is case sensitive and must be between 8 and 64 characters in length, inclusive\. It must also contain at least one character from three of the following four categories:

     + Lowercase letters \(a\-z\)

     + Uppercase letters \(A\-Z\)

     + Numbers \(0\-9\)

     + Non\-alphanumeric characters \(\~\!@\#$%^&\*\_\-\+=`|\\\(\)\{\}\[\]:;"'<>,\.?/\)

   + For **Description**, type **AWS DS Managed**\.

   + For **VPC**, choose the option that begins with **AWS\-DS\-VPC** and ends with **\(10\.0\.0\.0/16\)**\.

   + For **Subnets**, choose the **10\.0\.128\.0/20** and **10\.0\.144\.0/20** public subnets\.

1. Choose **Next Step**\.

1. Review the directory information and make any necessary changes\. If the information is correct, choose **Create Microsoft AD**\.

1. Creating the directory takes 20 to 40 minutes\. Once created, the **Status** value changes to **Active**\.

1. Choose **Done**\.

**Method 2: To create your Microsoft AD \(Windows PowerShell\) \(Optional\)**

1. Open Windows PowerShell\.

1. Type the following command\. Make sure to use the values provided in Step 4 of the preceding AWS Management Console procedure\.

   `New-DSMicrosoftAD -Name corp.example.com –ShortName corp –Password P@ssw0rd –Description “AWS DS Managed” - VpcSettings_VpcId vpc-xxxxxxxx -VpcSettings_SubnetId subnet-xxxxxxxx, subnet-xxxxxxxx`

**Method 3: To create your Microsoft AD \(AWS CLI\) \(Optional\)**

1. Open the AWS CLI\.

1. Type the following command\. Make sure to use the values provided in Step 4 of the preceding AWS Management Console procedure\.

   `aws create-microsoft-ad --name corp.example.com --short-name corp --password P@ssw0rd --description "AWS DS Managed" --vpc-settings VpcId= vpc-xxxxxxxx,SubnetIds= subnet-xxxxxxxx, subnet-xxxxxxxx`