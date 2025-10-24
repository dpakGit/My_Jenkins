### Steps to add a user to the Matrix Authorization Strategy in Jenkins:

Step 1: Add User

1. Go to the Jenkins dashboard and click on Manage Jenkins.
2. Go to the Security section and click on "Users".
3. Click on "+ Create Users" and add a new user.
<br><br>
<img width="1920" height="1080" alt="Screenshot (481)" src="https://github.com/user-attachments/assets/42f69984-d604-401f-9d9a-dafa62902c4b" />
<br><br>  
   
Step 2: Install the Matrix Authorization Strategy plugin

1. Go to the Jenkins dashboard and click on Manage Jenkins.
2. Click on Manage Plugins.
3. Search for Matrix Authorization Strategy in the plugin repository.
4. Install the plugin and restart Jenkins if prompted.

Step 3: Configure Matrix Authorization Strategy

1. Go to the Jenkins dashboard and click on Manage Jenkins.
2. Click on Configure Global Security/Security.
3. Scroll down to the Authorization section.
4. Select Matrix-based security as the authorization strategy.

Step 4: Add a user to the Matrix

1. In the Matrix Authorization Strategy section, click on Add user or group.
2. Enter the existing username or group name already created,in the User/group to add field.
3. Click Add.

Step 4: Configure permissions for the user

1. Once the user is added to the matrix, you can configure their permissions by checking the boxes next to the specific permissions you want to grant.
2. You can grant permissions for various aspects of Jenkins, such as:
    - Overall (e.g., administer, read)
    - Job (e.g., build, configure, delete)
    - Agent (e.g., configure, create, delete)
    - View (e.g., create, delete, read)
3. Select the permissions you want to grant to the user.

Step 5: Save changes

1. Once you've configured the user's permissions, click Save to save the changes.

The user should now have the specified permissions and be able to access Jenkins accordingly.
