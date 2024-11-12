# Github Self Hosted Runner Setup and Auto Deployement
To automate the build, test, and deploy process on your self-hosted GitHub Actions runner whenever changes are pushed to the main branch, you can create a GitHub Actions workflow. 
## Prerequisites
- Github with Repository and Code to Deploy
- Server Setted Up for that Deployement

## Setup Instructions
### Access Your Repository Settings
- Go to your GitHub repository.
- Click on Settings > Actions > Runners.
- Click New self-hosted runner.

### Download and Configure the Runner on Your Server
- Connect to your server where you want to set up the runner.
- In the terminal, navigate to the directory where you want to install the runner, for example:
```sh
cd /var/www/html/
```
### Copy the download link from GitHub (provided in the setup instructions on the GitHub page) and download it:
```sh
curl -o actions-runner-linux-x64-<version>.tar.gz -L https://github.com/actions/runner/releases/download/v<version>/actions-runner-linux-x64-<version>.tar.gz
```
### Extract the Runner
```sh
tar xzf actions-runner-linux-x64-<version>.tar.gz
```
### Configure the Runner
Run the configuration command (replace YOUR_TOKEN with the token generated on GitHub):
```sh
./config.sh --url https://github.com/your-username/your-repo --token YOUR_TOKEN
```
### Install And start the service
#### To set up the runner as a systemd service, use:
```sh
sudo ./svc.sh install
```
#### Start the Runner
```sh
sudo ./svc.sh start
```
## Test the Workflow
Push changes to your main branch and check the Actions tab on GitHub to see the workflow in action on your self-hosted runner.
