🧠 Homework 1 — Ansible Automation Project
📘 Objective

Set up an Ansible Controller on Ubuntu and connect it to four client nodes (2 Amazon Linux 2023 and 2 Ubuntu).
Then, write a playbook with three plays to automate Apache installation, Git setup, and display a custom debug message across all clients.

🖥️ Project Overview
🧩 Tasks

Setup:

Launch one Ubuntu EC2 instance as the Ansible Controller.

Launch four client EC2 instances (2 Ubuntu + 2 Amazon Linux 2023).

Configure SSH key-based authentication between the controller and all clients.

Verify connections using the ping module.

Playbook Requirements:

PLAY 1: Deploy Apache Webserver on Ubuntu clients with a custom web page message.

PLAY 2: Install Git on all Ubuntu clients.

PLAY 3: Use the DEBUG module to display your name on all hosts using a variable.

Submission:

Push your playbook file to GitHub.

Include screenshots showing successful execution and results.

Export your output as a PDF file for submission.


### 🏗️ Architecture
```mermaid
graph TD
    You[You via AWS Console / Session Manager]
    Controller[Ubuntu Controller - Ansible]
    Ubuntu1[Ubuntu Client 1 - Ubuntu 22.04]
    Ubuntu2[Ubuntu Client 2 - Ubuntu 22.04]
    Amz1[Amazon Linux Client 1 - AMZ 2023]
    Amz2[Amazon Linux Client 2 - AMZ 2023]

    You --> Controller
    Controller --> Ubuntu1
    Controller --> Ubuntu2
    Controller --> Amz1
    Controller --> Amz2
```
---




## ✅ Plays
1️⃣ Deploy Apache Webserver on Ubuntu Clients  
2️⃣ Install Git on Ubuntu Clients  
3️⃣ Display My Name on All Hosts using Debug module  

## launch an ubuntu controller and 4 clients(2 amazon client and 2 ubuntu cleint)

<img width="1920" height="909" alt="Screenshot (654)" src="https://github.com/user-attachments/assets/0c122f46-c944-4eeb-823d-7bc6335533e8" />

## conect to the controller
<img width="1920" height="918" alt="Screenshot (655)" src="https://github.com/user-attachments/assets/bdae94bb-670c-4871-b0e0-034d8bc26974" />

## Install Ansible on Controller

- Configure the PPA on your system and install Ansible:

```bash
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo add-apt-repository --yes --update ppa:ansible/ansible
$ sudo apt install ansible
```
---
<img width="1920" height="912" alt="Screenshot (656)" src="https://github.com/user-attachments/assets/c362926b-0b7e-4a9b-b0cd-12a94fe6ddb4" />



## Generate SSH Key Pair on Controller
```bash
-ssh-keygen -t rsa
```
-Press Enter for all prompts.
<img width="1920" height="918" alt="Screenshot (657)" src="https://github.com/user-attachments/assets/b8c4acc3-a957-4a01-a500-b2bf337bdb4f" />

- share the public key with the cleints by pasting it into authorised key file on each cleint and test the connectivity from the controller.
<img width="1920" height="903" alt="Screenshot (658)" src="https://github.com/user-attachments/assets/1853d8c1-4525-43e8-b29f-59a118416496" />

## input our clients into an inventory file
<img width="1920" height="909" alt="Screenshot (661)" src="https://github.com/user-attachments/assets/dfc77807-413a-4059-92e5-bb06dd4ac996" />

## verify if all setup is correct using the ad-hoc cmd ping module
```bash
 ansible all -m ping
```
<img width="1920" height="915" alt="Screenshot (662)" src="https://github.com/user-attachments/assets/493f21b4-8ac6-4932-9ea7-ef034b1dc8aa" />

## write a playbook with three plays
   ( look above for the playbook)

## 🖥️ Verification of the playbook
```bash
 ansible-playbook multi_play.yml
```
<img width="1920" height="892" alt="Screenshot (664)" src="https://github.com/user-attachments/assets/2acbbee8-8daa-413d-8180-4138a84b57f0" />
<img width="1920" height="910" alt="Screenshot (665)" src="https://github.com/user-attachments/assets/584213e6-55da-4290-8208-04833bfa932a" />

### verify apache on the ubuntu clients
<img width="1920" height="973" alt="Screenshot (667)" src="https://github.com/user-attachments/assets/da239b9d-9ac1-4254-9ffd-faa500fa6fef" />





  

---

## 📘 Conclusion

This project successfully demonstrated the setup and automation capabilities of **Ansible** across multiple Linux environments.

Starting from launching an **Ubuntu Controller** and four clients (**2× Ubuntu**, **2× Amazon Linux 2023**), SSH keys were used for secure connectivity, and the setup was verified using the **ping ad-hoc module**.

The three-play Ansible playbook achieved the following:
1. Deployed **Apache Webserver** on Ubuntu clients with a custom welcome message.
2. Installed **Git** on Ubuntu clients.
3. Used the **Debug** module to display the user’s name across **all managed hosts**.

Through this exercise, we demonstrated how Ansible simplifies configuration management, package installation, and remote task execution with just a few lines of YAML — proving its efficiency for both small and large-scale automation.

---

## 🧩 Key Takeaways
- ✅ Learned how to configure a centralized **Ansible Controller**.  
- ✅ Practiced secure **SSH connectivity** between controller and clients.  
- ✅ Applied **ad-hoc commands** and **playbooks** for automation.    

---

## 💬 Author
**Ebsiy Anslem**  
📍 Cloud & DevOps Engineer in Training  


