https://notes.kodekloud.com/docs/Jenkins-For-Beginners/Automation-and-Security/Jenkins-Authorization-Matrix-Authorization-Strategy

### Following are some practice questions on Jenkins Project-based Matrix Authorization Strategy:

Scenario-based Questions:

**1. Scenario:** You have a Jenkins instance with multiple projects. You need to grant a specific user, "dev_user," the ability to build and view only "Project A" and "Project B," but no other projects. Additionally, "dev_user" should not be able to configure or delete any projects. How would you configure the Project-based Matrix Authorization Strategy to achieve this?

**2. Scenario:** You have a Jenkins instance with a folder structure: TeamX/ProjectAlpha and TeamY/ProjectBeta. You want to grant "qa_team" group global "Overall/Read" permission, but restrict them to "Job/Build" and "Job/Read" only within TeamX/ProjectAlpha. How would you set up the permissions using Project-based Matrix Authorization Strategy and inheritance?
Scenario: A new developer, "new_dev," joins your team. They need to be able to create, configure, and build new jobs within a specific folder called "Sandbox," but should not have any global permissions to create or configure jobs outside of this folder. How would you configure the security to grant these specific permissions?

**Conceptual Questions:**

1. Explain the key difference between "Matrix-based security" and "Project-based Matrix Authorization Strategy" in Jenkins.      When would you choose one over the other?

2. What is the purpose of the "Inherit permissions" option within the Project-based Matrix Authorization Strategy? Describe a    situation where you might choose to disable or modify this inheritance.

3. How does the "anonymous" user and "authenticated" user interact with the Project-based Matrix Authorization Strategy? What    permissions should generally be assigned to these special users?

4. If a user belongs to multiple groups, and each group has different permissions assigned for a specific project, how does      Jenkins determine the final set of permissions for that user?

**Configuration Questions:**

1. Outline the steps required to enable and configure the Project-based Matrix Authorization Strategy in Jenkins for a new       project.

2. List at least three different permissions related to "Job" that can be configured within the Project-based Matrix             Authorization Strategy. Explain what each permission allows a user to do.

3. Describe how you would verify that the permissions you configured using the Project-based Matrix Authorization Strategy       are working as intended for a specific user.
