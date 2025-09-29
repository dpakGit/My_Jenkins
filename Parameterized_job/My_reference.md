[29-Sep-25 7:57 PM] Meta AI: To pass an input from the end user on which branch a job should run using "This project is parameterized" in Jenkins, you can follow these steps:

1. Add a String Parameter:
    - Go to your Jenkins job configuration.
    - Check the box next to "This project is parameterized."
    - Click on "Add Parameter" and select "String Parameter."

2. Configure the String Parameter:
    - Name: BRANCH
    - Default Value: master (or any other default branch you prefer)
    - Description: Specify the branch to run the job on (or any description that fits your needs)

3. Use the Parameter in Your Job:
    - In your job configuration, where you specify the branch (e.g., in the Source Code Management section), use the parameter ${BRANCH}.

This way, when users trigger the job, they will be prompted to enter a branch name, and the job will run on the specified branch. If they don't enter a value, it will default to master.
[29-Sep-25 8:00 PM] Meta AI: You've added an "Execute shell" build step to verify that the BRANCH parameter is being passed correctly.

The command echo $BRANCH will print the value of the BRANCH parameter to the console output. This allows you to verify that the parameter is being set correctly.

When you run the job, you should see the value of BRANCH printed in the console output. If you've specified a value for BRANCH when triggering the job, that value should be printed. If not, it should print the default value (master in this case).

You can also add more commands to your shell script to utilize the BRANCH parameter, such as checking out a specific branch or performing branch-specific actions. For example:


bash
echo "Running on branch: $BRANCH"
git checkout $BRANCH


This way, you can dynamically switch to the specified branch based on the user's input.
[29-Sep-25 8:10 PM] Meta AI: What is a String Parameter?

In Jenkins, a string parameter is a type of parameter that allows users to input a string value when triggering a job. It's a way to pass a text-based input to a job, which can then be used in the job's configuration or scripts.

Why is it used here?

In this case, a string parameter is used to allow users to input a branch name when triggering the job. By defining a string parameter named BRANCH, users can enter the name of the branch they want to run the job on. This provides flexibility and allows the job to be run on different branches without having to hardcode the branch name in the job configuration.

The string parameter is used here because:

- Branch names are typically text-based (e.g., "master", "feature/new-feature", etc.)
- Users need to be able to input a specific branch name when triggering the job
- The job needs to be able to use the input branch name in its configuration or scripts

By using a string parameter, you can decouple the branch name from the job configuration and make the job more flexible and reusable.
