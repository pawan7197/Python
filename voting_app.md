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

⚙️ 2. Install Required Development Tools
Copy
Edit
```
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
What it does: Installs Git version control system.

Why it matters: Git is required to clone the source code from GitHub.

🔍 4. Verify Git Installation
git -v
What it does: Displays the current version of Git installed on your system.

Why it matters: Ensures that Git was successfully installed.

🌐 5. Clone the Voting App Repository

git clone https://github.com/dockersamples/example-voting-app.git
What it does: Clones the Example Voting App repository from GitHub to your local machine.

Why it matters: Downloads the source code of the app to run locally.

Step 2: Set Up the Environment
📂 6. Change Directory to the Cloned Repo

cd example-voting-app/
What it does: Changes the current directory to the example-voting-app folder.

Why it matters: You need to be inside this directory to work with the app's code.

📂 7. Navigate to the vote/ Folder
cd vote/
🧑‍💻 8. Install Python 3 Virtual Environment Package

sudo apt install python3-venv
What it does: Installs the python3-venv package to enable Python virtual environments.

Why it matters: A virtual environment isolates your Python dependencies to avoid conflicts with the system Python installation.

🌱 9. Create a Virtual Environment

python3 -m venv myenv
What it does: Creates a virtual environment named myenv.

Why it matters: This ensures that dependencies are isolated within the project, preventing system-wide conflicts.

🧑‍💻 10. Activate the Virtual Environment

source myenv/bin/activate
What it does: Activates the myenv virtual environment.

Why it matters: Ensures that all Python commands and package installations are done within the isolated environment.

📥 11. Install Flask

pip3 install flask
What it does: Installs Flask, a micro web framework for Python.

Why it matters: Flask is required to run the voting app.

🚀 12. Run the Voting App

python3 app.py
Step 3: Configure Additional Services
🛠️ 13. Install Redis

sudo apt install redis-server
What it does: Installs Redis, an in-memory data store that can be used for caching and session management.

Why it matters: Redis is used to improve performance by storing and retrieving session data.

📦 14. Install Redis Python Client

sudo pip install redis
Step 4: Finalize and Test
🔄 15. Restart the Flask App

python3 app.py
🔒 16. Set File Permissions for app.py
chmod +x app.py
🔑 17. Check App Ownership

sudo chown ubuntu:ubuntu app.py
What it does: Changes the ownership of app.py to the ubuntu user.

Why it matters: Ensures you have the right permissions to modify and run the file.

🌍 18. View the App in the Browser
Open your browser and visit http://127.0.0.1:5000. You should see the voting app running.

Step 5: Troubleshooting

Conclusion
🎉 Congratulations! You have successfully set up the Example Voting App! This app uses Flask and Redis to implement a voting system, and you've now set it up with all necessary dependencies.

You can now visit your app at http://127.0.0.1:5000 and interact with it. Feel free to modify the code, customize the app, or deploy it to a production environment.

Image
