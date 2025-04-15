## Step 2: Review and close secret scanning alerts

In the last step, you enabled secret scanning on the repository and committed an AWS credential to the repository.
In this step, you'll first review the secret scanning alerts.
Afterward, you'll enable push protection which prevents you from accidentally writing credentials to a repository.
Finally, you'll attempt to write a new credential to see how push protection works.

### :keyboard: Activity: View all secret scanning alerts

1. Open a new browser tab, and work on the steps in your second tab while you read the instructions in this tab.
2. Navigate to the **Security** tab in the top navigation bar of your repository.
3. Select **Secret scanning** in left-side navigation bar.

This page contains the list of secret scanning alerts. You can filter and sort this page based on criteria such as the alert state (open or closed), validity, and secret type. You will see three alerts listed here.

- **Amazon AWS Secret Access Key**: This is the access key you committed in the last step
- **Amazon AWS Access Key ID**: This is the key ID committed in the last step
- **GitHub Personal Access Token**: This token was already in the `credentials.yml` file before you started

### :keyboard: Activity: Review a secret scanning alert

In this activity, you will explore the alert. You'll review the validity of a secret and identify where the secret was detected in the repository.

Open the **Amazon AWS Access Key ID** alert and explore the information shown.

- **Alert status:** This section shows the current status of the alert (open or closed) and reports when the alert was first detected.

  ![Screenshot of the Amazon AWS Access Key ID alert with the currently open status highlighted.](https://github.com/user-attachments/assets/1ccfece8-cbc2-46d2-9936-e3175def8252)

- **Alert validity state:** Displayed only for tokens where secret scanning can contact the partner platform to check whether the token is currently active. This section shows the validity state: "Active", "Inactive", or "Possibly active", and how to remediate the exposed secret. A secret has the "Possibly active" state until the partner validates that it is either active or inactive.

  ![Screenshot of the Amazon AWS Access Key ID alert with the validity state highlighted.](https://github.com/user-attachments/assets/0fa7e342-5af6-4c95-899f-d1fee230c9ec)

- **Secret location:** This section describes the locations where the secret was identified in your repository. If the secret exists in multiple files, secret scanning will link to each file. The committer, a link to the commit SHA, and the commit date are also included for each location. Note that you should ignore the first two locations as they are part of the definition of the course. You can see the token you added in `credentials.yml` as the third location.

  ![Screenshot of an alert with a secret location highlighted.](https://github.com/user-attachments/assets/86048e93-8995-45d3-97c3-a4a1cdd4230e)

- **Alert audit trail:** The alert audit trail contains any changes to the state of the alert as well as who made the change. In this example, the alert only has an "Opened" event so far. If the alert is closed, a new event will be added to the audit trail.

  ![Screenshot of the bottom of an alert with the audit trail highlighted.](https://github.com/user-attachments/assets/e915d138-7d74-4f0c-a39e-164c7e7de8b5)

### :keyboard: Activity: Close an alert

When secret scanning finds a secret in your repository, the first thing you should do is disable that secret on the provider side.
This prevents any further use of that credential.
Once the secret has been disabled, the next step is to close the alert by marking it as "Revoked".
In this activity, you will open an alert that has been validated as "Inactive" by secret scanning, then mark that alert as "Revoked" in secret scanning.

1. In your other tab, return to the full list of secret scanning alerts, either using the **Secret scanning alerts** link at the top left of the alert or by using the **Security** tab as described above.
2. From the list of secret scanning alerts, open the alert titled **GitHub Personal Access Token**.
3. At the top of this alert, if the alert is marked as "Secret inactive on github.com" then secret scanning has already validated this credential and found that it is disabled. If the alert is still marked as "Possibly active secret", click the **Verify secret** button to validate it now.
4. Now we know that this secret is no longer active, we are ready to close the alert. Select the **Close as** dropdown and choose **Revoked**.
5. Enter a comment in the text box.
6. Choose **Close alert**.
   ![Screenshot of the GitHub Personal Access Token alert, the close alert options are activated and the option "revoked" is highlighted. The comment field has been filled in with "secret inactive".](https://github.com/user-attachments/assets/380ed9d1-4b17-41a6-9a96-1fc28dbb91bd)
7. Note that the alert now has a state of "Closed" and that the audit trail at the bottom of the alert shows that you closed the alert as revoked.
8. With all our alerts resolved, let's ask Mona to check our progress. Add a comment asking for a review.

   ```txt
   Hello @professortocat, can you please check my repo for open alerts?
   ```
