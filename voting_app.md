# documentation for deploying the Example Voting App:
Voting App Deployment - Detailed Documentation
This guide provides detailed, step-by-step instructions to deploy the Example Voting App using Python, Redis, and Flask. Follow the instructions below to get started.

Step 1: Prepare Your System
🖥️ 1. Update Package List
```bash
sudo apt update -y
```
After this it Updates the list of available packages from all repositories.

Why it matters: Ensures your system has the latest package information, preventing outdated software installations.

 2. Install Required Development Tools
  ```bash
sudo apt install -y libmariadb-dev gcc g++ build-essential python3-dev dh-python
  ```
it Installs development tools and libraries needed for building software and compiling code.

Explanation:

libmariadb-dev: Development libraries for MariaDB.

gcc/g++: The GNU C and C++ compilers.

build-essential: Essential tools for building packages.

python3-dev: Header files for Python.

dh-python: Packaging helper for Python.

3. Install Git
```
sudo apt install git -y
```
it Installs Git version control system.

4. Verify Git Installation
```bash
git -v
```
it Displays the current version of Git installed on your system.

 5. Clone the Voting App Repository
```bash
git clone https://github.com/dockersamples/example-voting-app.git
```
it Clones the Example Voting App repository from GitHub to your local machine.

Set Up the Environment
6. Change Directory to the Cloned Repo
```bash
cd example-voting-app/
```
it Changes the current directory to the example-voting-app folder.

 7. Navigate to the vote/ Folder
```bash
cd vote/
```
 8. Install Python 3 Virtual Environment Package
```bash
sudo apt install python3-venv
```
it Installs the python3-venv package to enable Python virtual environments.

9. Create a Virtual Environment
```bash
python3 -m venv myenv
```
What it does: Creates a virtual environment named myenv.

 10. Activate the Virtual Environment
```bash
source myenv/bin/activate
```
What it does: Activates the myenv virtual environment.

 11. Install Flask
```bash
pip3 install flask
```
What it does: Installs Flask, a micro web framework for Python.

 12. Run the Voting App
```bash
python3 app.py
```
Now Configure Additional Services
 13. Install Redis
```bash
sudo apt install redis-server
```
What it does: Installs Redis, an in-memory data store that can be used for caching and session management.

14. Install Redis Python Client
```bash
sudo pip install redis
```
Now Finalize and Test
 15. Restart the Flask App
```bash
python3 app.py
```
 16. Set File Permissions for app.py
 ```bash
chmod +x app.py
```
17. Check App Ownership
```bash
sudo chown ubuntu:ubuntu app.py
```
What it does: Changes the ownership of app.py to the ubuntu user.

 18. View the App in the Browser
  ```bash
 browser and visit http://127.0.0.1:5000. You should see the voting app running.
  ```

Now Troubleshooting



now visit app at http://127.0.0.1:5000 and interact with it.

Image
