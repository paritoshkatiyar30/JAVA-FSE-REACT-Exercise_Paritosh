# Assignment 1 - Git Configuration and Repository Setup

## Steps Executed

**1. Configure Git with User ID and Email**
```bash
git config --global user.name "Paritosh Katiyar"
git config --global user.email "paritoshkatiyar30@gmail.com"
```

**2. Create a New Project and Initialize Git Repository**
```bash
mkdir GitDemo
cd GitDemo
git init
```

**3. Create a File and Add Content**
Created a file named `welcome.txt` with the following content:
```text
Welcome to Git Demo!
This file was created for Assignment 1.
```

**4. Add File to Git and Check Status**
```bash
git add welcome.txt
git status
```

**5. Commit the File to Local Repository**
```bash
git commit -m "Initial commit with welcome.txt"
```

**6. Add Remote Repository and Push**
```bash
git remote add origin https://gitlab.com/paritoshkatiyar30/gitdemo.git
git push -u origin master
```

## Final Output

*(Below is the screenshot showing the successful push and the commit history on GitLab)*

![GitLab Final Output](final_output_screenshot.png) 
*(Note: Please place your attached screenshot in this folder and name it `final_output_screenshot.png` to display it here, or paste it directly if you are converting this document to a Word/PDF file).*
