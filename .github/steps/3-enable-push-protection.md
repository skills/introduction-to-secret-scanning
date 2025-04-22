## Step 3: Enable push protection

In this section, you will configure your repository to prevent new secrets from being exposed.

### What is push protection?

When someone tries to send code changes to GitHub (a push), secret scanning checks for high-confidence secrets. Secret scanning lists any secrets it detects so the author can review the secrets and remove them or, if needed, allow those secrets to be pushed.

### :keyboard: Activity: Configure push protection

> [!IMPORTANT]
> We disabled push protection in our first step for learning practice. It is normally enabled by default for all public repositories.

1. In the header of your repository, click the **Settings** tab.
2. In the left navigation, under the **Security** section, select **Code Security**.
3. Scroll down past the **Code Scanning** and **Dependabot** sections until you find the **Secret Protection** section.
4. Adjust the default configuration to match the below.

   - **Secret Protection:** `enabled`
   - **Push Protection:** `enabled`

   <img width="400" alt="Secret protection configuration settings" src="https://github.com/user-attachments/assets/4ecbc9a5-f1b2-4b68-8a1e-667dee7a7661" />

### :keyboard: Activity: Attempt to push a secret

Now that secret push protection is enabled, let's give it a test!

1. In the header of your repository, click the **Code** tab.
2. In the list of files, click on the `credentials.yml` file to preview it.
3. Above the content preview, click the **Edit** button.
4. Copy the following inactive secret to the file, removing the `<REMOVE_ME>` text. It should look like the below screenshot.

   ```txt
     github-token: github_pat_<REMOVE_ME>11A4YXR6Y0v36CYFkuT5I1_ZRWX91c8k0waSN6x7AiVJ6zZ9ZHUQXBblBqFQpKd23V6CL7MWMPopnmBxzn
   ```

   ![Screenshot of credentials.yml being edited in the GitHub web interface. A newly added github-token is highlighted.](https://github.com/user-attachments/assets/728f3502-bd0b-4ea7-a956-af9c3e606439)

5. In the top right, use the **Commit changes...** button to **try to** commit directly to the `main` branch. Instead of committing the updated file, a push protection alert appeared. Nice! 🥰

   <img width="400" alt="image" src="https://github.com/user-attachments/assets/19099848-4191-4fd7-b52b-be521d7f356c" />

> [!IMPORTANT]
> Secret Push Protection only scans while _**pushing**_ to GitHub. It cannot check your local commits. If you have a secret in a local commit and it is several commits deep, you will need to remove the secret from your branch's commit history. See [resolving a blocked push on the command line](https://docs.github.com/en/code-security/secret-scanning/pushing-a-branch-blocked-by-push-protection#resolving-a-blocked-push-on-the-command-line).

### :keyboard: Activity: Bypass push protection

In some cases, you may write code that looks similar to a secret and a commit is incorrectly blocked. For example writing tests for an authorization process. In those situations, you can choose to bypass push protection. Let's practice that.

1. Select the radio button next to `It's used in tests`. Notice the description, matches our current learning use case.

   <img width="400" alt="image" src="https://github.com/user-attachments/assets/04b51b50-c93b-4bce-ab2a-988ab42e8db2" />

2. Click **Allow secret**. A notification banner reports that you can now try committing again.

3. In the top right, use the **Commit changes...** button to commit directly to the `main` branch.

4. With the file updated, Mona should be busy checking your work. After checking, she'll provide feedback and the final review. Nice work! You are all done! 🎉
