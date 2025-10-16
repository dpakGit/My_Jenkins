

### Steps to create a Jenkins job with a Date parameter:


- Steo -1

To create a Jenkins job with a Date parameter, you will typically use the "Date Parameter Plugin.

 **Install the Date Parameter Plugin:**

  - Navigate to "Manage Jenkins" > "Manage Plugins."
  
  - Go to the "Available" tab and search for "Date Parameter."
  - Select the plugin and click "Install without restart" or "Download now and install after restart."

 **Create or Configure a Jenkins Job:**
 
   - Create a new Jenkins job (e.g., a Freestyle project or Pipeline).
   - Alternatively, navigate to an existing job you wish to modify and click "Configure."


**Enable Parameterized Build:**

  - In the job configuration, locate the "General" section.

  - Check the box labeled "This project is parameterized."

**Add a Date Parameter:**

   - Click the "Add Parameter" dropdown menu.

   - Select "Date Parameter."

**Configure the Date Parameter:**

 - Name: Provide a unique name for your date parameter (e.g., BUILD_DATE, DEPLOYMENT_DATE).

 - Description (Optional): Add a description to explain the purpose of the parameter.

 - Date Format: Specify the desired date format using Java's SimpleDateFormat syntax (e.g., yyyy-MM-dd, dd/MM/yyyy, yyyyMMdd HH:mm:ss).

 - Default Value (Optional):

- You can set a default date using a string matching your Date Format (e.g., 2025-10-16).

- Alternatively, you can use Java coding style to set a dynamic default, such as LocalDate.now() for the current date.

**Save the Job Configuration:**
 
 - Click "Apply" and then "Save" to save your changes.


**Build with Parameters:**

Now, when you click "Build with Parameters" for this job, you will see a date picker input field for your configured Date parameter, allowing you to easily select a date before triggering the build.
Utilize the Parameter in Build Steps:
Within your build steps (e.g., "Execute shell" or "Windows batch command"), you can access the value of the Date parameter using its name (e.g., $BUILD_DATE or %BUILD_DATE% on Windows).

```
    echo "Building for date: $BUILD_DATE"
    # Further actions using the date parameter
```
