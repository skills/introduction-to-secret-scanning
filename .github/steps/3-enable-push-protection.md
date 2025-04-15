## Step 3: Enable push protection

_Way to go! You reviewed and closed a secret scanning alert! :tada:_

Up to now, you've learned how to identify secrets already stored in your repository. In this section, you will enable push protection on the repository to prevent new secrets from being written to the repository.

**What is push protection**: When someone tries to send code changes to GitHub (a push), secret scanning checks for high-confidence secrets (those identified with a low false-positive rate). Secret scanning lists any secrets it detects so the author can review the secrets and remove them or, if needed, allow those secrets to be pushed.

### :keyboard: Activity: Enable push protection

Push protection is enabled by default for all public repositories. If you're working in a public repository, you can go straight to "Activity 3.2: Attempt to push a secret." For private or internal repositories, enable push protection in the repository "Settings."

1. Open a new browser tab, and work on the steps in your second tab while you read the instructions in this tab.
2. Navigate to **Settings** on the top navigation bar.
3. Under the "Security" section on the left side, select **Code security and analysis**.
4. Scroll to the bottom of the page and select **Enable** next to "Push Protection."

### :keyboard: Activity: Attempt to push a secret

Now that push protection for secret scanning is enabled, new secrets that secret scanning has high confidence in identifying will be blocked from being written to the repository. In this activity you will commit a new credential to the repository to experience the push protection.

1. In your other browser tab, click **Code** in the top navigation bar.
2. Open the `credentials.yml` file.
3. Click the **Edit** button (pencil icon) to the right.
4. Copy and paste the following string into the end of the file:

   ```txt
     github-token: github_pat_<REMOVEME>11A4YXR6Y0v36CYFkuT5I1_ZRWX91c8k0waSN6x7AiVJ6zZ9ZHUQXBblBqFQpKd23V6CL7MWMPopnmBxzn
   ```

5. Delete `<REMOVEME>` from the string you just pasted. The `<REMOVEME>` string is there so secret scanning doesn't create an alert before you're able to test push protection. Your file should look like this:

   ![Screenshot of credentials.yml being edited in the GitHub web interface. A newly added github-token is highlighted.](https://github.com/user-attachments/assets/728f3502-bd0b-4ea7-a956-af9c3e606439)

6. Select **Commit changes...**.
7. Select **Commit changes**.
8. Instead of committing the updated file to your repository, a push protection alert warns you that your changes include a GitHub Personal Access Token.

> [!TIP]
> When you work in a local environment or a GitHub Codespace, secret scanning cannot block your commit. Instead, your push to GitHub is blocked. In this case, if the secret is active then you will need to remove the secret from your branch and commit history, see [Resolving a blocked push on the command line](https://docs.github.com/en/code-security/secret-scanning/pushing-a-branch-blocked-by-push-protection#resolving-a-blocked-push-on-the-command-line).

### :keyboard: Activity: Bypass push protection

Now that you're aware of the secret in your changes, you should remove the secret and then attempt the commit again. In some cases, you may be willing to accept the risk of adding a secret to your repository. In those situations, you can choose to bypass push protection. In this activity, you will bypass push protection and write the token to your repository (don't worry, the example token is safe).

1. Select the radio button next to **It's used in tests**.
2. Click **Allow secret**.
3. A notification banner reports that you can now commit the secret.
4. Select **Commit changes...** again.
5. Select **Commit changes**.
6. Wait about 20 seconds, then refresh this page (the one you're following instructions from). A GitHub Actions workflow in the repository will run and automatically replace this contents of this `README` file with instructions for the next step.
