### Task :
Here's a more elaborate question:

Explain the steps to configure a Jenkins job to accept a branch name as input from the user at runtime. Describe how to define a parameter for the branch name and how to verify that the parameter is being passed correctly to the job. Additionally, provide an example of how to use the parameter in a build step, such as echoing the branch name to the console output.

OR

How can you configure a Jenkins job to accept user input for specifying the branch to run the job on, and verify that the branch parameter is being passed correctly ?

OR, in a more concise way:

How to pass a branch name as a parameter in a Jenkins job and verify its value ? 



#### Here are the steps to configure a Jenkins job to accept a branch name as input from the user at runtime:

Step 1: Configure the Jenkins Job

- Go to the Jenkins job configuration page
- Scroll down to the "General" section

Step 2: Add a String Parameter

- Check the box next to "This project is parameterized"
- Click on "Add Parameter" and select "String Parameter"
- Configure the string parameter:
    - Name: BRANCH
    - Default Value: master (or any other default branch)
    - Description: Specify the branch to run the job on
 
Step 3: Use the Parameter in Your Job:
- In your job configuration, where you specify the branch (e.g., in the Source Code Management section - Branch Specifier box),
  use the parameter ${BRANCH} .

Step 4: Add a Build Step to Verify the Parameter

- Scroll down to the "Build" section
- Click on "Add build step" and select "Execute shell"
- In the command field, enter the following:

bash
echo "Running on branch: $BRANCH"
git checkout $BRANCH

The command echo "Running on branch: $BRANCH" will print the value of the BRANCH parameter to the console output. This allows you to verify that the parameter is being set correctly.

Step 5: Save and Run the Job

- Save the job configuration
- Run the job and enter a branch name when prompted
- Verify that the branch name is printed to the console output

By following these steps, you can configure a Jenkins job to accept a branch name as input from the user at runtime and verify that the parameter is being passed correctly.

Note : - In Step 2, you might want to specify that the string parameter should be named exactly as BRANCH (all uppercase) to match the usage in the subsequent steps.

#### Here are some ways to add error handling or logging to the shell build step:

Example 1: Simple Error Handling

bash
echo "Running on branch: $BRANCH"
git checkout $BRANCH
if [ $? -ne 0 ]; then
  echo "Error: Failed to checkout branch $BRANCH"
  exit 1
fi

This will check the exit status of the git checkout command and print an error message if it fails.

Example 2: Logging and Error Handling

bash
echo "Running on branch: $BRANCH"
git checkout $BRANCH 2>&1 | tee checkout.log
if [ $? -ne 0 ]; then
  echo "Error: Failed to checkout branch $BRANCH. See checkout.log for details."
  exit 1
fi

This will log the output of the git checkout command to a file named checkout.log and print an error message if it fails.

Example 3: More Robust Error Handling

```
echo "Running on branch: $BRANCH"
if ! git checkout $BRANCH; then
  echo "Error: Failed to checkout branch $BRANCH"
  git status
  exit 1
fi
```

This will print the git status output if the checkout fails, which can help with debugging.

These are just a few examples, and you can customize the error handling and logging to fit your specific needs.
