## Step 2: Review and close secret scanning alerts

_You've enabled secret scanning and added a secret to test that the feature is working! :tada:_

In the last step, you enabled secret scanning on the repository and committed an AWS credential to the repository. In this step, you'll first review the secret scanning alerts. Afterward, you'll enable push protection which prevents you from accidentally writing credentials to a repository. Finally, you'll attempt to write a new credential to see how push protection works.

### :keyboard: Activity 2.1: View all secret scanning alerts

1. Open a new browser tab, and work on the steps in your second tab while you read the instructions in this tab.
2. Navigate to the **Security** tab in the top navigation bar of your repository.
3. Select **Secret scanning** in left-side navigation bar.

This page contains the list of secret scanning alerts. You can filter and sort this page based on criteria such as the alert state (open or closed), validity, and secret type. You will see three alerts listed here.

- **Amazon AWS Secret Access Key**: This is the access key you committed in the last step
- **Amazon AWS Access Key ID**: This is the key ID committed in the last step
- **GitHub Personal Access Token**: This token was already in the `credentials.yml` file before you started

### :keyboard: Activity 2.2: Review a secret scanning alert

In this activity, you will explore the alert. You'll review the validity of a secret and identify where the secret was detected in the repository.

Open the **Amazon AWS Access Key ID** alert and explore the information shown.

- **Alert status:** This section shows the current status of the alert (open or closed) and reports when the alert was first detected.

  ![Screenshot of the Amazon AWS Access Key ID alert with the currently open status highlighted.](/images/alert-status.png)

- **Alert validity state:** Displayed only for tokens where secret scanning can contact the partner platform to check whether the token is currently active. This section shows the validity state: "Active", "Inactive", or "Possibly active", and how to remediate the exposed secret. A secret has the "Possibly active" state until the partner validates that it is either active or inactive.

  ![Screenshot of the Amazon AWS Access Key ID alert with the validity state highlighted.](/images/alert-validity-state.png)

- **Secret location:** This section describes the locations where the secret was identified in your repository. If the secret exists in multiple files, secret scanning will link to each file. The committer, a link to the commit SHA, and the commit date are also included for each location. Note that you should ignore the first two locations as they are part of the definition of the course. You can see the token you added in `credentials.yml` as the third location.

  ![Screenshot of an alert with a secret location highlighted.](/images/secret-location.png)

- **Alert audit trail:** The alert audit trail contains any changes to the state of the alert as well as who made the change. In this example, the alert only has an "Opened" event so far. If the alert is closed, a new event will be added to the audit trail.

  ![Screenshot of the bottom of an alert with the audit trail highlighted.](/images/audit-trail.png)

### :keyboard: Activity 2.3: Close an alert

When secret scanning finds a secret in your repository, the first thing you should do is disable that secret on the provider side. This prevents any further use of that credential. Once the secret has been disabled, the next step is to close the alert by marking it as "Revoked". In this activity, you will open an alert that has been validated as "Inactive" by secret scanning, then mark that alert as "Revoked" in secret scanning.

1. In your other tab, return to the full list of secret scanning alerts, either using the **Secret scanning alerts** link at the top left of the alert or by using the **Security** tab as described above.
2. From the list of secret scanning alerts, open the alert titled **GitHub Personal Access Token**.
3. At the top of this alert, if the alert is marked as "Secret inactive on github.com" then secret scanning has already validated this credential and found that it is disabled. If the alert is still marked as "Possibly active secret", click the **Verify secret** button to validate it now.
5. Now we know that this secret is no longer active, we are ready to close the alert. Select the **Close as** dropdown and choose **Revoked**.
7. Enter a comment in the text box.
8. Choose **Close alert**.
   ![Screenshot of the GitHub Personal Access Token alert, the close alert options are activated and the option "revoked" is highlighted. The comment field has been filled in with "secret inactive".](/images/revoke-token.png)
9. Note that the alert now has a state of "Closed" and that the audit trail at the bottom of the alert shows that you closed the alert as revoked.

## Step 3: Enable push protection

_Way to go! You reviewed and closed a secret scanning alert! :tada:_

Up to now, you've learned how to identify secrets already stored in your repository. In this section, you will enable push protection on the repository to prevent new secrets from being written to the repository.

**What is push protection**: When someone tries to send code changes to GitHub (a push), secret scanning checks for high-confidence secrets (those identified with a low false-positive rate). Secret scanning lists any secrets it detects so the author can review the secrets and remove them or, if needed, allow those secrets to be pushed.

### :keyboard: Activity 3.1: Enable push protection

Push protection is enabled by default for all public repositories. If you're working in a public repository, you can go straight to "Activity 3.2: Attempt to push a secret." For private or internal repositories, enable push protection in the repository "Settings."

1. Open a new browser tab, and work on the steps in your second tab while you read the instructions in this tab.
2. Navigate to **Settings** on the top navigation bar.
3. Under the "Security" section on the left side, select **Code security and analysis**.
4. Scroll to the bottom of the page and select **Enable** next to "Push Protection."

### :keyboard: Activity 3.2: Attempt to push a secret

Now that push protection for secret scanning is enabled, new secrets that secret scanning has high confidence in identifying will be blocked from being written to the repository. In this activity you will commit a new credential to the repository to experience the push protection.

1. In your other browser tab, click **Code** in the top navigation bar.
2. Open the `credentials.yml` file.
3. Click the **Edit** button (pencil icon) to the right.
4. Copy and paste the following string into the end of the file:

    ```
      github-token: github_pat_<REMOVEME>11A4YXR6Y0v36CYFkuT5I1_ZRWX91c8k0waSN6x7AiVJ6zZ9ZHUQXBblBqFQpKd23V6CL7MWMPopnmBxzn
    ```

5. Delete `<REMOVEME>` from the string you just pasted. The `<REMOVEME>` string is there so secret scanning doesn't create an alert before you're able to test push protection. Your file should look like this:

    ![Screenshot of credentials.yml being edited in the GitHub web interface. A newly added github-token is highlighted.](/images/push-protection.png)

6.  Select **Commit changes...**.
7.  Select **Commit changes**.
8.  Instead of committing the updated file to your repository, a push protection alert warns you that your changes include a GitHub Personal Access Token.

> [!TIP]
> When you work in a local environment or a GitHub Codespace, secret scanning cannot block your commit. Instead, your push to GitHub is blocked.  In this case, if the secret is active then you will need to remove the secret from your branch and commit history, see [Resolving a blocked push on the command line](https://docs.github.com/en/code-security/secret-scanning/pushing-a-branch-blocked-by-push-protection#resolving-a-blocked-push-on-the-command-line).

### :keyboard: Activity 3.3: Bypass push protection

Now that you're aware of the secret in your changes, you should remove the secret and then attempt the commit again. In some cases, you may be willing to accept the risk of adding a secret to your repository. In those situations, you can choose to bypass push protection. In this activity, you will bypass push protection and write the token to your repository (don't worry, the example token is safe).

1. Select the radio button next to **It's used in tests**.
2. Click **Allow secret**.
3. A notification banner reports that you can now commit the secret.
4. Select **Commit changes...** again.
5. Select **Commit changes**.
6. Wait about 20 seconds, then refresh this page (the one you're following instructions from). A GitHub Actions workflow in the repository will run and automatically replace this contents of this `README` file with instructions for the next step.
