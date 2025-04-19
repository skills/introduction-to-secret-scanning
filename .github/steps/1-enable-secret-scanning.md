## Step 1: Enable Secret Scanning

In this step, you will enable secret scanning on your repository. Once secret scanning is enabled, you will add a new credential to see how secret scanning identifies the credential.

**What is a secret**:
In the context of secret scanning, a secret (or credential) is a plain-text string, or a pair of strings, that authorizes a user to access a service.
Examples could be AWS secret access keys/ID's, Google API keys, or Stripe API tokens.
The GitHub Docs provides a list of [all supported patterns](https://docs.github.com/en/code-security/secret-scanning/secret-scanning-patterns#supported-secrets).

### :keyboard: Activity: Enable secret scanning

For public repositories, secret scanning is enabled by default. If you're working in a public repository, you can skip to the next activity.

For private or internal repositories, secret scanning is available with [GitHub Advanced Security](https://docs.github.com/en/enterprise-cloud@latest/get-started/learning-about-github/about-github-advanced-security).

1. Open a new browser tab, and work on the steps in your second tab while you read the instructions in this tab.
2. In your newly created repository, select **Settings** from the top navigation bar.
3. Under the **Security** section on the left side, select **Code security**.
4. Scroll to the bottom of this page and find the **Secret Protection** area. Click the **Enable** button.
5. If **push protection** automatically enabled, click the **Disable** button.

> [!IMPORTANT]
> When you enable secret scanning, you may receive an email notification about credentials in your repository. Don't worry! The tokens in this Skills repository are inactive. There is no risk to your environment.

### :keyboard: Activity: Commit a token

Now that you have secret scanning enabled in this repository, let's commit a new token to see how it works. You'll commit an AWS key and access ID to the repository. Don't worry, this is an inactive token that can't be used to log in to AWS.

1. You should continue to work on activities in a second browser tab.
2. Click the **Code** tab in your repository.
3. Display the `credentials.yml` file.
4. Click the Edit button to the right.

   ![A screenshot of credentials.yml on the GitHub web interface with the edit button outlined](https://github.com/user-attachments/assets/22025708-306a-4577-96d4-9296bc218a03)

5. Copy the following text and paste it at the bottom of the `credentials.yml` file.

   ```yaml
   default:
     aws_access_key_id: AKIAQYLPMN5HNM4OZ56B
     aws_secret_access_key: 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
     output: json
     region: us-east-2
   ```

6. Click **Commit changes...** at the top right. The "Commit changes" window is displayed. Leave the defaults configured, and click **Commit changes** to commit directly to the `main` branch.
7. With the file committed, Mona should be busy checking your work. After reviewing, she'll provide feedback and the next learning step.
