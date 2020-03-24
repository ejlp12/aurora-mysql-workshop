# Getting started

!!! Tip "Create an AWS account"

    In order to complete the hands-on content on this site, you'll need an AWS Account. We strongly recommend that you use a personal account or create a new AWS account to ensure you have the necessary access and that you do not accidentally modify corporate resources. Do not use an AWS account from the company you work for unless they provide sandbox accounts just for this purpose.

!!! Warning 
    Your account must have the ability to create new IAM roles and scope other IAM permissions.

## Create an IAM user (with admin permissions)

If you don't already have an AWS IAM user with admin permissions, please use the following instructions to create one:

1. In the AWS Management Console, on the **Services** menu, click **IAM**.
2. In the left navigation pane, Click **Users** and then click **Add User**.
3. Enter a **User Name**, select **AWS Management Console access**, enter a **Custom Password**, and click **Next:Permissions**.
4. Click **Attach existing policies directly**, select **AdministratorAccess**, and click **Next:review**.
5. Click **Create User**
6. In the left navigation page, click **Dashboard** and use the **IAM users sign-in link** to login as the admin user you just created.

## Setup Cloud9 IDE

This workshop requires you to run commands or scripts you will need to install AWS CLI & text editor on your machine or alternatively you can launch [AWS Cloud9](https://aws.amazon.com/cloud9/) instance which will provide you with a cloud-based integrated development environment (IDE) that lets you write, run, and debug your code with just a browser. 

!!! Warning
    The Cloud9 workspace should be built by an IAM user with Administrator privileges, not the root account user. Please ensure you are logged in as an IAM user, not the root account user.

??? Tip 
    Ad blockers, javascript disablers, and tracking blockers should be disabled for the cloud9 domain, or connecting to the workspace might be impacted. Cloud9 requires third-party-cookies. You can whitelist the specific domains.

Below are the instructions for launching an instance:

- In the AWS Management Console, on the **Services** menu, click **[Cloud9](https://console.aws.amazon.com/cloud9)**.
- Click **Create environment** on the right side.
- Enter a **Name** (eg. `ecs-workshop`) and click **Next** step.
- Leave all the defaults and click **Next step**.
- Click **Create environment**.
- The environment will open automatically after it has been provisioned. Browse back to the AWS Cloud9 console and you can click **Open IDE** on the environment you created to access it at anytime.