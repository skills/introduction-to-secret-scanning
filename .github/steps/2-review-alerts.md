## Step 2: Review and close secret scanning alerts

In the last step, you enabled secret protection and committed an AWS credential to the repository. Now, let's review our open secret scanning alerts, verify if an exposed secret is still active, and then close an alert.

### :keyboard: Activity: Triage secret scanning alerts

1. In the header of your repository, click the **Security** tab.

2. In the left navigation, select the **Secret scanning** option.

3. Notice various options in the header bar that can help triage our alerts.

   <img width="400" alt="list of filtered open alerts" src="https://github.com/user-attachments/assets/2926c12f-2d39-4ea1-a8dd-816442f332b4" />

4. Click the **Provider** dropdown and select `Amazon AWS` to filter the view. Notice only 2 of the 3 entries are listed now.

   <img width="400" alt="list of filtered open alerts" src="https://github.com/user-attachments/assets/8623dec7-5199-4c5b-8c5e-1b812106a510" />

### :keyboard: Activity: Review a secret scanning alert

1. In the list of open alerts, select the `Amazon AWS Access Key ID` alert. This will open a details page with more information.

2. At the top of the page, we can quickly view the alert status, when it was opened, the exposed secret, and some remediation steps.

   <img width="400" alt="image" src="https://github.com/user-attachments/assets/61700b67-234c-47ae-a4de-552be25cc2bf" />

3. Scroll down slightly to the **Detected in X locations** area. Notice that secret protection doesn't create duplicate alerts for the same secret found across multiple locations, for example in our learning issue.

   <img width="400" alt="image" src="https://github.com/user-attachments/assets/2516d6ff-8472-4f46-92d7-dd919ff82f16" />

### :keyboard: Activity: Check an alert's validity

Some common services provide options to verify the validity of a secret. In these cases, GitHub can automatically perform a check.

1. Return back to the full list of secret scanning alerts.

2. In the list of open alerts, select the `GitHub Personal Access Token` alert.

3. Near the top, click the **Verify secret** button to perform a check. If the button is not visible, GitHub likely already performed a verification.
   <img width="400" alt="image" src="https://github.com/user-attachments/assets/9a1fc239-c4b3-43f3-b69b-1abcff1ad6cf" />

4. Scroll down to the end to view the **Audit Log** to see when GitHub last verified this exposed secret.

   <img width="400" alt="image" src="https://github.com/user-attachments/assets/f498a011-1a19-4009-9829-d879d4e9c8db" />

### :keyboard: Activity: Close an alert

1. When secret protection finds a secret in your repository, the first thing you should do is **disable that secret with the provider**. You should assume it has been exposed.

2. With the secret now inactive, we can update the status of our alert. In the top right, select the **Close as** dropdown.

   > 🚨 **Caution:** Do **NOT** close an open alert without performing remediation steps. This simply hides the problem and provides a false sense of security. It might even trigger additional alerts with your cybersecurity department. 🤦

3. Choose the `Revoked` option and enter a useful description of your remediation steps in the comment box. This is important so the audit log can later provide critical information if an investigation is required. Then choose **Close alert**.
   ![Screenshot of the GitHub Personal Access Token alert, the close alert options are activated and the option "revoked" is highlighted. The comment field has been filled in with "secret inactive".](https://github.com/user-attachments/assets/380ed9d1-4b17-41a6-9a96-1fc28dbb91bd)

4. The alert status now displays `Closed` and the audit trail includes our explanation.

   <img width="400" alt="image" src="https://github.com/user-attachments/assets/9a1c1bdb-eba7-4ec1-866a-a6ce6df37d8d" />

   <img width="400" alt="image" src="https://github.com/user-attachments/assets/5fc49f77-3bdc-444a-9f01-e30610d940ae" />

5. With at least one of our alerts resolved, let's add a comment to inform Mona we are done with this step, so she can share the next one.

   ```txt
   Hello @professortocat, I've resolved some alerts. What's next?
   ```
