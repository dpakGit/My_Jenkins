

### Steps to create a Jenkins job with a Date parameter:


 **Install the Date Parameter Plugin:**

To create a Jenkins job with a Date parameter, you will typically use the "Date Parameter Plugin.

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

<br><br>
<img width="1920" height="1080" alt="Screenshot (453)" src="https://github.com/user-attachments/assets/e26aef8b-0f75-4675-8099-7c0113ef31b5" />
<br><br>

**Configure the Date Parameter:**

 - Name: Provide a unique name for your date parameter (e.g., BUILD_DATE, DEPLOYMENT_DATE).

 - Description (Optional): Add a description to explain the purpose of the parameter.

 - Date Format: Specify the desired date format using Java's SimpleDateFormat syntax (e.g., yyyy-MM-dd, dd/MM/yyyy, yyyyMMdd HH:mm:ss).

 - Default Value (Optional):

- You can set a default date using a string matching your Date Format (e.g., 2025-10-16).

- Alternatively, you can use Java coding style to set a dynamic default, such as LocalDate.now() for the current date.
- 
<br><br>
<img width="1920" height="1080" alt="Screenshot (458)" src="https://github.com/user-attachments/assets/408b3883-faee-4cef-91c3-ea3f3de8bc93" />

<br><br>
<img width="1920" height="1080" alt="Screenshot (454)" src="https://github.com/user-attachments/assets/a733c6e4-e7f9-4b67-a6d0-427c692edea7" />
<br><br>
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

<br><br>
<img width="1920" height="1080" alt="Screenshot (457)" src="https://github.com/user-attachments/assets/af17974b-9acf-4461-9c70-8e04d88bdb30" />
