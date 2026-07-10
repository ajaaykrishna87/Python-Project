# 🚀 Deploy a Python Flask Application on AWS EC2

This project demonstrates how to create a simple Python Flask application, push it to GitHub, and deploy it on an AWS EC2 Ubuntu instance.

---

# 📖 Project Overview

In this project, you will learn how to:

- Create a Python virtual environment
- Build a simple Flask web application
- Manage the project using Git
- Push the project to GitHub
- Launch an AWS EC2 Ubuntu instance
- Clone the repository on EC2
- Install project dependencies
- Configure AWS Security Groups
- Run the Flask application and access it through a web browser

---

# 🛠 Prerequisites

Before starting, ensure you have:

- AWS Account
- GitHub Account
- Ubuntu/Linux System
- Python 3.12+
- Git Installed
- AWS EC2 Ubuntu Instance
- SSH Key Pair (.pem)

---

# 📁 Project Structure

```
Python-Project/
│── app.py
│── requirements.txt
│── README.md
└── venv/
```

---

# Step 1 - Create the Project Directory

```bash
mkdir Python-Project
cd Python-Project
```

---

# Step 2 - Create a Python Virtual Environment

```bash
python3 -m venv venv
```

---

# Step 3 - Activate the Virtual Environment

```bash
source venv/bin/activate
```

You should see:

```bash
(venv)
```

---

# Step 4 - Install Flask

```bash
pip install flask
```

---

# Step 5 - Create the Flask Application

Create a file named `app.py`.

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "Hello World from AWS EC2!"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

---

# Step 6 - Generate the Requirements File

```bash
pip freeze > requirements.txt
```

---

# Step 7 - Test the Application Locally

```bash
python3 app.py
```

Expected output:

```
Running on http://127.0.0.1:5000
Running on http://<YOUR_LOCAL_IP>:5000
```

Open your browser:

```
http://127.0.0.1:5000
```

---

# Step 8 - Initialize Git Repository

```bash
git init
```

---

# Step 9 - Check Git Status

```bash
git status
```

---

# Step 10 - Stage the Files

```bash
git add .
```

---

# Step 11 - Commit the Project

```bash
git commit -m "Initial commit"
```

---

# Step 12 - Rename the Branch

```bash
git branch -M main
```

---

# Step 13 - Create a GitHub Repository

Create a new repository on GitHub.

Do **not** initialize it with:

- README
- .gitignore
- License

---

# Step 14 - Add the Remote Repository

Using HTTPS:

```bash
git remote add origin https://github.com/<YOUR_GITHUB_USERNAME>/<REPOSITORY_NAME>.git
```

Or using SSH:

```bash
git remote add origin git@github.com:<YOUR_GITHUB_USERNAME>/<REPOSITORY_NAME>.git
```

---

# Step 15 - Push the Repository

```bash
git push -u origin main
```

---

# ☁️ AWS Deployment

## Step 16 - Launch an EC2 Instance

Launch an Ubuntu EC2 instance.

Ensure the Security Group allows:

- SSH (22)
- Custom TCP (5000)

---

## Step 17 - Connect to the EC2 Instance

```bash
ssh -i <YOUR_KEY_PAIR>.pem ubuntu@<EC2_PUBLIC_IP>
```

---

## Step 18 - Update Ubuntu

```bash
sudo apt update
```

---

## Step 19 - Install Git

```bash
sudo apt install git -y
```

---

## Step 20 - Install Python Virtual Environment

```bash
sudo apt install python3-venv -y
```

---

## Step 21 - Clone the Repository

```bash
git clone https://github.com/<YOUR_GITHUB_USERNAME>/<REPOSITORY_NAME>.git
```

---

## Step 22 - Navigate to the Project

```bash
cd <REPOSITORY_NAME>
```

---

## Step 23 - Create the Virtual Environment

```bash
python3 -m venv venv
```

---

## Step 24 - Activate the Virtual Environment

```bash
source venv/bin/activate
```

---

## Step 25 - Install Project Dependencies

```bash
pip install -r requirements.txt
```

---

## Step 26 - Run the Flask Application

```bash
python3 app.py
```

Expected output:

```
* Running on all addresses (0.0.0.0)
* Running on http://127.0.0.1:5000
* Running on http://<EC2_PRIVATE_IP>:5000
```

---

# Step 27 - Configure the Security Group

Add the following inbound rule:

| Type | Protocol | Port | Source |
|------|----------|------|--------|
| Custom TCP | TCP | 5000 | 0.0.0.0/0 |

---

# Step 28 - Access the Application

Open your browser:

```
http://<EC2_PUBLIC_IP>:5000
```

You should see:

```
Hello World from AWS EC2!
```

> **Note:** The EC2 **Private IP** is only accessible from within the same AWS VPC. To access the application from your local machine, use the **Public IPv4 Address** of the EC2 instance.

---

# 📸 Output

```
Hello World from AWS EC2!
```

---

# 🛠 Technologies Used

- Python 3
- Flask
- Git
- GitHub
- AWS EC2
- Ubuntu Linux
- SSH


---

# 👨‍💻 Author

**Ajaay Krishna**
