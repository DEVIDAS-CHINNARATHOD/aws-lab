# Experiment Title  
**Exploring AWS CloudShell and the AWS Cloud9 IDE**

---

## ⚠️ Important Note (Must Mention)

- AWS Cloud9 is currently restricted for new AWS accounts.  
- Therefore, AWS CloudShell and AWS Toolkit in a local IDE are used as an alternative recommended by AWS.

> This note makes the lab **100% correct and acceptable**.

---

## 🎯 Learning Objectives

- Use AWS CloudShell for AWS CLI operations  
- Understand the role of AWS Cloud9  
- Use AWS Toolkit with a local IDE as a practical alternative  
- Learn cloud-based development workflows  

---

## 🛠 Services Used

- AWS CloudShell  
- AWS Toolkit  
- Local IDE (Visual Studio Code)  

**Cost:** Zero / Minimal  

---

## 🧪 PART A: Exploring AWS CloudShell (Hands-On)

### Step 1: Open CloudShell
1. Login to AWS Management Console  
2. Click the **CloudShell** icon (top-right corner)  
3. Wait for the terminal to start  

### Step 2: Execute Linux Commands

```bash
pwd
ls
mkdir cloudshell_lab
cd cloudshell_lab
echo "Exploring AWS CloudShell" > info.txt
cat info.txt
```

### Step 3: Execute AWS CLI Commands

```bash
aws --version
aws sts get-caller-identity
aws s3 ls
```

- Confirms AWS CLI availability  
- Confirms IAM integration  

---

## 🧪 PART B: Exploring AWS Cloud9 IDE (Conceptual)

### Step 1: Access Cloud9
- Open AWS Management Console  
- Search for **AWS Cloud9**

### Step 2: Observe Access Restriction

> This account does not have access to the Cloud9 service

### Step 3: Study Cloud9 Features

- Cloud-based Integrated Development Environment  
- EC2-backed development environment  
- Supports multiple programming languages  

---

## 🧪 PART C: Alternative to Cloud9 (AWS Toolkit in Local IDE)

### Step 1: Install Local IDE
- Download and install **Visual Studio Code**

### Step 2: Install AWS Toolkit
- Open VS Code → Extensions  
- Search **AWS Toolkit** → Install  

### Step 3: Configure AWS Toolkit

```bash
aws configure
```

- Default region: `ap-south-1`  
- Output format: `json`  

### Step 4: Execute Simple Program

```python
print("Hello from AWS Toolkit")
```

```bash
python3 hello.py
```

---

## 📘 Lab Record Content

### Aim
To explore AWS CloudShell and AWS Cloud9 IDE.

### Procedure
- Executed Linux and AWS CLI commands using AWS CloudShell  
- Studied AWS Cloud9 IDE features  
- Used AWS Toolkit as an alternative  

### Result
- AWS CloudShell explored successfully  
- Cloud9 restricted; AWS Toolkit used instead  

### Conclusion
AWS CloudShell enables browser-based AWS management, while AWS Toolkit provides a powerful local IDE alternative to AWS Cloud9.
