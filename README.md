GitHub Access Auditor


Description:

The GitHub Access Auditor is a comprehensive solution designed to automate the process of auditing user access permissions for GitHub repositories within an organization. This project leverages shell scripting, AWS EC2 instances, and secure access methods to provide a robust tool for managing and auditing repository access.

Key Features:
Shell Script Automation: A shell script automates the retrieval and display of user access details for a specified GitHub repository.
AWS EC2 Integration: Utilizes an AWS EC2 instance to run the script, ensuring scalability and efficiency.
Secure Access with PEM Files: Connects to the EC2 instance securely using MobaXterm and a PEM file, ensuring that private keys remain protected and accessible only by authorized users.
GitHub Integration: Clones the target repository from GitHub using the git clone command to access and execute the script.
Permission Management: Adjusts file permissions using chmod to ensure the script executes without issues.
User Access Audit: Executes the script to identify and list all users who have read access to the specified GitHub repository, providing detailed information about their permissions.
Usage Scenario:
This project is ideal for organizations that need to regularly audit and manage access permissions to their GitHub repositories. By automating the process, the GitHub Access Auditor helps maintain security compliance and ensures that only authorized personnel have access to sensitive code and data.

Setup Instructions:
Upload Script to GitHub: Begin by uploading your shell script to a GitHub repository.
Create an EC2 Instance: Set up an AWS EC2 instance to run the script.
Connect to EC2: Use MobaXterm and your PEM file to securely connect to the EC2 instance.
Clone Repository: Clone the GitHub repository containing your script using the git clone command.
Set Permissions: Use chmod 777 to grant execution permissions to the script.
Run the Script: Execute the script with the repository owner and name as arguments to audit user access.
Detailed Steps:
Upload the Script:

Save the script as list_users_with_read_access.sh and push it to your GitHub repository.
Create an EC2 Instance:

Launch an EC2 instance in AWS if you don't already have one.
Connect to EC2:

Use MobaXterm to connect to your EC2 instance with your PEM file.
Clone the Repository:

On the EC2 instance, clone your GitHub repository:
git clone https://github.com/<your_github_username>/<your_repository>.git
cd <your_repository>

Set Script Permissions:

Grant execute permissions to the script:
chmod 777 list_users_with_read_access.sh

Execute the Script:

Run the script with the repository owner and name as arguments:
./list_users_with_read_access.sh <repo_owner> <repo_name>

Explanation of the Shell Script:
GitHub API URL:

The API_URL variable stores the base URL for the GitHub API.
GitHub Username and Personal Access Token:

The USERNAME and TOKEN variables store your GitHub username and personal access token, which are used for authentication.
User and Repository Information:

The REPO_OWNER and REPO_NAME variables are set to the script’s first and second arguments, representing the repository owner and name.
Function to Make a GET Request:

The github_api_get function sends an authenticated GET request to the GitHub API using curl.
Function to List Users with Read Access:

The list_users_with_read_access function retrieves the list of collaborators with read access (pull permission) to the specified repository using the GitHub API and jq to parse the JSON response.
Main Script Execution:

The script checks if the required arguments (repository owner and name) are provided.
It then calls the list_users_with_read_access function to list users with read access to the specified repository.
Replace placeholders (<your_github_username>, <your_personal_access_token>, <your_repository>, <repo_owner>, <repo_name>) with your actual GitHub username, personal access token, repository name, repository owner, and repository name.

By following these steps, you can efficiently manage and audit user access to your organization's GitHub repositories, ensuring enhanced security and operational efficiency.
