Configuring project-based matrix authorization in Jenkins allows for fine-grained control over user and group permissions at the individual project level. This strategy provides more flexibility than global matrix-based security, where permissions apply across all projects.

### Steps to configure project-based matrix authorization:

Note : Before following the below steps create users.


- Navigate to Manage Jenkins > Users

<br><br>
<img width="1920" height="1080" alt="Screenshot (481)" src="https://github.com/user-attachments/assets/dc583f88-da7b-41c4-80b8-a8ac89ea6d42" />
<br><br>

**Step -1: Install the Matrix Authorization Strategy Plugin:**

- Navigate to Manage Jenkins > Manage Plugins.

- Go to the Available tab and search for "Matrix Authorization Strategy". 

- Install the plugin without restarting Jenkins.


**Step -2: Enable Project-based Matrix Authorization Globally:**

- Navigate to Manage Jenkins > Security.

- In the Authorization section, select Project-based Matrix Authorization Strategy. 

- Add users/groups and define their global permissions. Typically, users might receive `Overall Read` permission at this stage, with more specific permissions defined at the project level.
   It is recommended to initially grant minimal permissions, such as `"Overall Read`," to authenticated users/users.

  <br><br>
  <img width="1920" height="1080" alt="Screenshot (488)" src="https://github.com/user-attachments/assets/44b1a86a-8d3a-42b8-a4c1-7dd30299d122" />
  <br><br>
  
  **Step -3: Configure Project-Specific Permissions:**

- Navigate to a specific Jenkins job or project you want to secure.

- Click on Configure.

- Under the General section, check the box for `Enable project-based security`.

 **You can then choose to:**
 
**Inherit permissions from parent ACL**: This option makes the project inherit the global permissions defined in step 2.

**Define a custom ACL for this project**: This allows you to add users/groups and define specific permissions (e.g., Job Build, Job Configure, Job Read, Job Delete) for that particular project, overriding global settings for those users/groups on this project.

- Add users/groups and assign specific permissions for that job (e.g., Build, Cancel, Read, Configure).
<br><br>
<img width="1920" height="1080" alt="Screenshot (486)" src="https://github.com/user-attachments/assets/48c0fab2-b3b6-478a-8e24-57677c44235e" />
<br><br>

**Save Changes:**

- Save the global security configuration and then save the individual project configurations to apply the changes.

#### Important Considerations:

- **Global vs. Project-Specific**: Understand the distinction between global permissions (applying to the entire Jenkins instance) and project-specific permissions (applying only to a particular job).

- **Permissions Hierarchy**: Project-specific permissions can override global permissions for the same user/group on that particular project.

- **Security Best Practices**: It is generally recommended to grant minimal permissions globally and then elevate specific permissions at the project level as needed. Avoid granting extensive permissions to anonymous users.


#### Key Features and Benefits:

**Granular Control**: Define specific permissions for users or groups on a per-job basis.

**Enhanced Security**: Restrict access to sensitive projects or jobs, ensuring only authorized individuals can perform certain actions.

**Flexibility**: Combine global permissions with project-specific overrides to create a tailored authorization structure.

**Scalability**: Manage permissions effectively in environments with numerous jobs and diverse user roles.
