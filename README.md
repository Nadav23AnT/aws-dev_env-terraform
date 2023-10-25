# Re-Deployable AWS Development Environment with Terraform
![project-dev-terraform](https://github.com/Nadav23AnT/aws-dev_env-terraform/assets/71144691/d1d2374d-0f06-480e-adbe-44e0c15f470c)

This repository provides a simple way to create a re-deployable development environment on AWS using Terraform. With this environment, you can quickly provision AWS resources and launch an EC2 instance that you can access via remote SSH using Visual Studio Code on Windows, Mac, or Linux.

## Prerequisites

Before deploying this re-deployable development environment, ensure that you have the following prerequisites in place:

1. **Visual Studio Code**: Make sure you have Visual Studio Code installed on your machine. You can download it [here](https://code.visualstudio.com/).

2. **Extensions**: Install the following extensions in Visual Studio Code:
   - [Terraform](https://marketplace.visualstudio.com/items?itemName=HashiCorp.terraform): This extension provides syntax highlighting, linting, and more for Terraform files.
   - [AWS Toolkit](https://marketplace.visualstudio.com/items?itemName=AmazonWebServices.aws-toolkit-vscode): This extension helps you work with AWS resources within VS Code.
   - [Remote - SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh): This extension allows you to connect to remote systems over SSH.

3. **AWS Credentials**: Ensure you have AWS credentials configured on your machine. You can set up AWS CLI credentials using the `aws configure` command.

## Deployment

To deploy the re-deployable AWS development environment, follow these steps:

1. Clone this repository to your local machine:

   ```shell
   git clone https://github.com/Nadav23AnT/aws-dev_env-terraform.git
   ```

2. Change to the repository directory:

   ```shell
   cd aws-dev_env-terraform
   ```

3. Initialize Terraform:

   ```shell
   terraform init
   ```

4. Plan the infrastructure changes:

   ```shell
   terraform plan
   ```

5. Apply the changes to create the AWS resources:

   ```shell
   terraform apply
   ```

6. Follow the on-screen prompts and confirm to apply the changes.

Once the deployment is complete, Terraform will provide you with information about the resources that were created, including the public IP address of the EC2 instance.

## Accessing the EC2 Instance

After deployment, you can remotely access the EC2 instance from Visual Studio Code using the following steps:

1. Open Visual Studio Code.

2. Install and configure the "Remote - SSH" extension if you haven't already.

3. Click on the "Remote Explorer" icon in the sidebar.

4. Click the "SSH Targets" icon and choose "Configure SSH Hosts."

5. Add a new SSH configuration with the following format, replacing `<public_ip>` with the actual public IP address from the Terraform output:

   ```json
   {
       "label": "AWS Dev Environment",
       "hostname": "<public_ip>",
       "username": "ec2-user",
       "port": 22,
       "identityFile": "/path/to/your/private-key.pem"
   }
   ```

6. Save the configuration.

7. In the "Remote Explorer" panel, you should now see "AWS Dev Environment." Right-click it and select "Connect to Host."

You can now access your re-deployable AWS development environment within Visual Studio Code using the "Remote - SSH" extension.

## Cleanup

To clean up and destroy the AWS resources created by Terraform when you no longer need them, you can run:

```shell
terraform destroy
```

Follow the on-screen prompts to confirm the resource deletion.

**Note:** Be cautious when using the `terraform destroy` command, as it will permanently delete the AWS resources.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
```

This addition explains how to use the "Remote - SSH" extension and emphasizes the importance of using the correct public IP from the Terraform output.
