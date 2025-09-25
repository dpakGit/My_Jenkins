### To set up Jenkins email notifications without SMTP credentials, you can use a dummy SMTP server or a free email service that provides SMTP access. Here are a few options:

Option 1: Use a dummy SMTP server

1. Install the Jenkins "Mailer Plugin" if it's not already installed.
2. In Jenkins, go to "Manage Jenkins" > "Configure System" > "Extended E-mail Notification" or "E-mail Notification" section.
3. For SMTP server, enter localhost or 127.0.0.1.
4. Set the port to a high number like 2525 (you can choose any available port).
5. You can leave the username and password fields blank.

Option 2: Use a free email service

Some free email services like Gmail or Outlook provide SMTP access. You can use these services to send emails from Jenkins. Keep in mind that you might need to allow less secure apps or generate an app password.

1. Create an account on a free email service (e.g., Gmail).
2. Enable SMTP access and note down the SMTP server, port, and credentials.
3. In Jenkins, go to "Manage Jenkins" > "Configure System" > "Extended E-mail Notification" or "E-mail Notification" section.
4. Enter the SMTP server, port, username, and password.

Some popular SMTP settings:

- Gmail: smtp.gmail.com (port 587 or 465)
- Outlook: smtp.office365.com (port 587)

Option 3: Use a testing tool

You can also use a testing tool like Mailtrap or MailHog, which provide a fake SMTP server for testing purposes. These tools allow you to test email notifications without actually sending emails.

1. Create an account on Mailtrap or MailHog.
2. Get the SMTP server and port details.
3. Configure Jenkins to use the SMTP server and port.

By using one of these options, you can set up Jenkins email notifications for practice without needing actual SMTP credentials.


### How to Setup Jenkins Email Notification : https://devopscube.com/setup-jenkins-email-notification/
