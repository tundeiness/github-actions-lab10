Notice the repository name is - github-actions-lab10. Go through the repository, there is a workflow file named script-injection-test.yml

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



TASK 2

Make changes to the workflow to mitigate the script Injection attack.

Create/Open another Issue with script injection in title
a. Title - a"; ls $GITHUB_WORKSPACE"
b. Click on Submit Issue
Check Actions tab for a new workflow trigger and check the logs.


TASK 3



Script injection attacks in GitHub Actions can occur when a workflow improperly handles user input or external data, allowing an attacker to inject malicious code that gets executed within the workflow.

This type of vulnerability is particularly concerning because it can potentially expose sensitive information, manipulate the workflow, or even compromise the runner executing the workflow.

How Script Injection Can Happen in GitHub Actions:
Untrusted Input: Using inputs from pull requests, issue comments, or other sources controlled by users without proper sanitization.

Environment Variables: Injecting untrusted data into environment variables that are later used in a script or command.

Workflow Commands: GitHub Actions supports a set of workflow commands (like ::set-env or ::add-path) that can be used to dynamically set environment variables, paths, etc. If an attacker can control the data that gets interpreted as a workflow command, they can alter the behavior of the workflow.



TASK 4


Mitigation Strategies:
Validate and Sanitize Inputs: Always validate and sanitize user inputs or data fetched from external sources. Be cautious with data from pull requests, especially from forks.

Use Built-in Token and Permissions: GitHub Actions provides a GITHUB_TOKEN with limited permissions by default. Avoid using high-permission personal access tokens if possible.

Limit Workflow Permissions: Explicitly set the permissions for the GITHUB_TOKEN in your workflow to only what is necessary for the tasks at hand.

Avoid Exposing Sensitive Information: Be careful not to echo sensitive information in your logs. Treat all output as potentially visible.

Use Trusted Actions: Prefer actions that are well-maintained, versioned, and from reputable sources. Pin actions to a full length commit SHA to avoid unexpected changes.

Code Reviews: Implement a code review process for changes to workflows to catch potentially malicious changes.

Regular Audits: Regularly audit your workflows and actions for vulnerabilities and keep them updated.

Limit Runner Exposure: For self-hosted runners, ensure they are used only by trusted repositories as they have more access to your network.

Be Aware of Workflow Command Injection: GitHub has deprecated some workflow commands (like set-env and add-path) due to security issues. Always use the latest and safest methods for setting environment variables and paths.

By following these best practices, you can significantly reduce the risk of script injection attacks in your GitHub Actions workflows. Remember that security is an ongoing process, and keeping up to date with GitHub's recommendations and updates is crucial.


