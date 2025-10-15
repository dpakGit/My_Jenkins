### Creating and running a parameterized Jenkins job involves the following steps:
Select or Create a Jenkins Job:
Choose an existing Jenkins job (e.g., a Freestyle project or Pipeline).
Alternatively, create a new job by navigating to "New Item" and selecting the desired project type.
Configure the Job:
Navigate to the job's configuration page. For a Freestyle project, this is typically done by clicking "Configure" on the job's main page.
Enable Parameterized Builds:
In the "General" section of the job configuration, locate and check the ✅"This project is parameterized" checkbox.
Add Parameters:
Click the "Add Parameter" dropdown button that appears after enabling parameterized builds.
Select the desired parameter type (e.g., String Parameter, Boolean Parameter, Choice Parameter, Password Parameter, File Parameter, etc.).
Configure each parameter by providing a Name, an optional Default Value, and a Description.
Use Parameters in Build Steps:
In the "Build" section of your job configuration, integrate the defined parameters into your build steps. Parameters are typically accessed as environment variables using the syntax ${PARAMETER_NAME} within shell commands, scripts, or other build tools.
Save the Job Configuration:
Apply and save the changes to your Jenkins job configuration.
Build with Parameters:
On the job's main page, you will now see a "Build with Parameters" link (instead of just "Build Now").
Click this link to trigger a build.
Provide Parameter Values:
A form will appear, displaying the defined parameters. Enter the desired values for each parameter for this specific build.
Trigger the Build:
Click the "Build" button to start the Jenkins job with the provided parameter values.
Monitor and Review:
Monitor the job execution and review the console output to ensure the parameters were correctly passed and used within the build process.
