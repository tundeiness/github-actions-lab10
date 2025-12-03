Notice the repository name is - github-actions-lab10
Go through the repository, there is a workflow file named script-injection-test.yml
1) The workflow will trigger when a new Issue is opened
a. It has 1 job and 2 steps

Step 1 - used to checkout the repository
Step 2 - Checks the Issue title and echo a message
Go to Actions Tab and click on I understand my workflows, go ahead and enable them then do the following:
1) Create/Open a Issue with following content
a. Title - App has a bug
b. Click on Submit Issue

Check Actions tab for a new workflow trigger and check the logs
2) Create/Open another Issue with script injection in title,
a. Title - a"; ls $GITHUB_WORKSPACE"
b. Click on Submit Issue
Check Actions tab for a new workflow trigger and check the logs
