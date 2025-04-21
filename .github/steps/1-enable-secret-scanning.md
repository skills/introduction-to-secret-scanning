## Step 1: Enable Secret Protection

If you check your email, you probably just got an alert from GitHub with the subject "Possible valid secrets found". Oh no! 😮

Don't worry! We put some expired credentials in the exercise on purpose since public repositories get secret protection for free. Nice! 🕵️

In this step, you will enable secret protection on your repository. After it is enabled, you will add a new credential to see how secret protection identifies the credential and alerts you.

> [!WARNING]
> If your repository is private, the you will need [GitHub Advanced Security](https://docs.github.com/en/enterprise-cloud@latest/get-started/learning-about-github/about-github-advanced-security) to continue. We recommend to simply [change this exercise repository to public](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/setting-repository-visibility) to enable it.

### What is a secret?

In the context of secret protection, a secret (or credential) is a plain-text string, or a pair of strings, that authorizes access a service.
Examples could be AWS secret access keys/ID's, Google API keys, or Stripe API tokens.
The GitHub Docs provides a list of [all supported patterns](https://docs.github.com/en/code-security/secret-scanning/secret-scanning-patterns#supported-secrets).

### :keyboard: Activity: Configure secret protection

1. Open a new browser tab and navigate to your newly made repository (your copy of this exercise). Then, work on the steps in your second tab while you read the instructions in this tab.
2. In header of your repository, navigate to the **Settings** tab.
3. In the left navigation, under the **Security** section, select **Code Security**.
4. Scroll down past the **Code Scanning** and **Dependabot** sections until you fine the **Secret Protection** section.
   > 💡 **Tip:** We also have exercise to learn those!
5. Adjust the default configuration to match the below.

   - **Secret Protection:** `enabled`
   - **Push Protection:** `disabled`

   <img width="400" alt="Secret protection configuration settings" src="https://github.com/user-attachments/assets/7b999e54-dbf4-400d-8730-17b96bc06de1" />

### :keyboard: Activity: Commit a token

Now let's commit a new token to see how it works. Don't worry, this is an inactive credential.

1. In the header of your repository, click the **Code** tab.

2. In the list of files, click on the `credentials.yml` file to preview it.

3. Above the content preview, click the **Edit** button.

   ![A screenshot of credentials.yml on the GitHub web interface with the edit button outlined](https://github.com/user-attachments/assets/f3f1be19-0073-4a44-abf4-e72f5334785c)

4. Copy the following inactive credentials into the `credentials.yml` file.

   ```yaml
   default:
     aws_access_key_id: AKIAQYLPMN5HNM4OZ56B
     aws_secret_access_key: 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
     output: json
     region: us-east-2
   ```

5. In the top right, use the **Commit changes...** button to commit directly to the `main` branch.

   > ❗️ **Important:** Committing to your default branch is not usually a recommended practice. We only do this to simplify the exercise.

6. With our credentials file updated, Mona should be busy preparing the next step. You should also receive another alert email.
