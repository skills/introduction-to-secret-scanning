## Step 1: Enable Secret Protection

If you check your email, you probably just got an alert from GitHub with the subject "Possible valid secrets detected". Oh no! 😮

Don't worry! We put some expired credentials in the exercise on purpose since public repositories get secret protection for free. Nice! 🕵️

In this step, you will enable secret protection on your repository. After it is enabled, you will add a new credential to see how secret protection identifies the credential and alerts you.

> [!WARNING]
> If your repository is private, you will need [GitHub Advanced Security](https://docs.github.com/en/enterprise-cloud@latest/get-started/learning-about-github/about-github-advanced-security) to continue. We recommend [changing this exercise repository to public](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/setting-repository-visibility) to enable it.

### What is a secret?

In our context, a secret (or credential) is a plain-text string, or a pair of strings, that authorizes access to a service. Examples could be AWS secret access keys/ID's, Google API keys, or GitHub Personal Access Tokens (PATs).

The GitHub Docs provides a list of [all supported patterns](https://docs.github.com/en/code-security/secret-scanning/secret-scanning-patterns#supported-secrets).

### What is secret protection?

Secret protection is a powerful tool which allows teams to identify these plain-text credentials, remove them, and create rules to prevent them from being written to GitHub in the first place.

Secret protection is available **for free for public repositories** on all plans. Enterprises that need secret protection capabilities for private repositories should review [GitHub Advanced Security](https://github.com/security/advanced-security). Not only does it include secret protection, it also provides advanced static analysis, software composition analysis (SCA), and enterprise tools to manage your entire AppSec pipeline and reduce your risk profile.

### :keyboard: Activity: Configure secret protection

1. In the header of your repository, open **Settings** in a new browser tab.

1. In the left navigation, under the **Security** section, select **Advanced Security**.

1. Scroll down past the **Code Scanning** and **Dependabot** sections until you find the **Secret Protection** section.

   > 💡 **Tip:** We also have exercises about [code scanning](https://github.com/skills/introduction-to-codeql) and [supply chain protection](https://github.com/skills/secure-repository-supply-chain)!

1. Adjust the default configuration to match the below.

   - **Secret Protection:** `enabled`
   - **Push Protection:** `disabled`

   <img width="400" alt="Secret protection configuration settings" src="../images/secret-protection-configuration-settings.png" />

### :keyboard: Activity: Commit a sensitive file

Now let's (accidentally) commit a sensitive file to see how it works. Don't worry, these are inactive credentials.

1. In the header of your repository, click the **Code** tab.

1. Above the list of files, click the **Add file** dropdown and select **Create new file**.

   <img width="350" alt="New file button" src="../images/add-new-file-button.png"/>

1. Enter the file name `credentials.yml` and copy following **inactive** example credentials into it.

   <img width="400" alt="New file button" src="../images/credentials-yml-file-creation.png"/>

   ```yaml
   default:
     aws_access_key_id: AKIAQYLPMN5HNM4OZ56B
     aws_secret_access_key: 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
     mongodb: mongodb+srv://svc-admin:kLeioeBne5lsopPf@mergington-high.avocado.mongodb.net
     output: json
     region: us-east-2
   ```

1. In the top right, use the **Commit changes...** button to commit directly to the `main` branch.

   > ❗️ **Important:** Committing to your default branch is not usually a recommended practice. We only do this to simplify the exercise.

1. With our credentials file (accidentally) shared, Mona should quickly notice it and prepare the next step.
