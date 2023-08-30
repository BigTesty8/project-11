# ANSIBLE CONFIGURATION MANAGEMENT – AUTOMATE PROJECT 7 TO 10  (Project-11)
### INSTALL AND CONFIGURE ANSIBLE ON EC2 INSTANCE
#### Update Name tag on your Jenkins EC2 Instance to Jenkins-Ansible. We will use this server to run playbooks.
- In your GitHub account create a new repository and name it ansible-config.
  
- Install Ansible with the sudo apt update and sudo apt install ansible command
  
Configure Jenkins build job to save your repository content every time you change it,this will solidify your Jenkins configuration skills acquired in Project 9.
- Create a new Freestyle project ansible in Jenkins and point it to your ‘ansible-config-mgt’ repository.
  
- Configure Webhook in GitHub and set webhook to trigger ansible build.
  
- Configure a Post-build job to save all (**) files, like you did it in Project 9.
  
Test your setup by making some change in README.MD file in master branch and make sure that builds starts automatically and Jenkins saves the files (build artifacts) in following folder
ls /var/lib/jenkins/jobs/ansible/builds/<build_number>/archive/
Note: Trigger Jenkins project execution only for /main (master) branch.
#### Diagram of ansible version and saved files of build artifacts
![](https://github.com/BigTesty8/project-11/assets/137091610/12742361-17a7-4588-b658-54918ee91d94)
#### Step 2 – Prepare your development environment using Visual Studio Code
- After you have successfully installed VSC, configure it to connect to your newly created GitHub repository.
  
- Clone down your ansible-config-mgt repo to your Jenkins-Ansible instance
git clone <ansible-config repo link>
  ## BEGIN ANSIBLE DEVELOPMENT
In your ansible-config-mgt GitHub repository, create a new branch that will be used for development of a new feature.
Tip: Give your branches descriptive and comprehensive names, for example, if you use Jira or Trello as a project management tool – include ticket number (e.g. PRJ-145) in the name of your branch and add a topic and a brief description what this branch is about – a bugfix, hotfix, feature, release (e.g. feature/prj-145-lvm).
- Checkout the newly created feature branch to your local machine and start building your code and directory structure
  
- Create a directory and name it playbooks – it will be used to store all your playbook files.
  
- Create a directory and name it inventory – it will be used to keep your hosts organised.
  
- Within the playbooks folder, create your first playbook, and name it common.yml
  
- Within the inventory folder, create an inventory file (.yml) for each environment (Development, Staging Testing and Production) dev, staging, uat, and prod respectively.
  ![](https://github.com/BigTesty8/project-11/assets/137091610/a16f9f50-5b51-42c8-ae87-e9845e116b50)

####   Step 4 – Set up an Ansible Inventory
An Ansible inventory file defines the hosts and groups of hosts upon which commands, modules, and tasks in a playbook operate. Since our intention is to execute Linux commands on remote hosts, and ensure that it is the intended configuration on a particular server that occurs. It is important to have a way to organize our hosts in such an Inventory.

- Save below inventory structure in the inventory/dev file to start configuring your development servers. Ensure to replace the IP addresses according to your own setup.
  ##### Update your inventory/dev.yml file with this snippet of code:
  ![](https://github.com/BigTesty8/project-11/assets/137091610/14f18b05-12a6-47c7-bd6d-e3ee915ba807)

 ##   CREATE A COMMON PLAYBOOK
#### Step 5 – Create a Common Playbook
It is time to start giving Ansible the instructions on what you needs to be performed on all servers listed in inventory/dev.
In common.yml playbook you will write configuration for repeatable, re-usable, and multi-machine tasks that is common to systems within the infrastructure.
#### Update your playbooks/common.yml file with following code:
![](https://github.com/BigTesty8/project-11/assets/137091610/8aedb080-5f8e-4eec-9349-17d979b4f354)

#### Step 6 – Update GIT with the latest code
Now all of your directories and files live on your machine and you need to push changes made locally to GitHub.
- Commit your code into GitHub:
  
- use git commands to add, commit and push your branch to GitHub, using the commands in the following diagram :
  ![](https://github.com/BigTesty8/project-11/assets/137091610/24be394e-a984-4e51-8850-62489f2a2039)
  
- Create a Pull request (PR)
  
 ![](https://github.com/BigTesty8/project-11/assets/137091610/1cfd7ef3-1929-4099-af1f-f1b8a05b7016)

- If the reviewer is happy with your new feature development, merge the code to the master branch.

![](https://github.com/BigTesty8/project-11/assets/137091610/d1a6bc83-0031-435a-bfa5-0398f7f6ac08)


Head back on your terminal, checkout from the feature branch into the master, and pull down the latest changes.
Once your code changes appear in master branch – Jenkins will do its job and save all the files (build artifacts) to /var/lib/jenkins/jobs/ansible/builds/<build_number>/archive/ directory on Jenkins-Ansible server.

## RUN FIRST ANSIBLE TEST
#### Step 7 – Run first Ansible test
Now, it is time to execute ansible-playbook command and verify if your playbook actually works:
- Using the following command "ansible-playbook -i inventory/dev.yml playbooks/common.yml"
![](https://github.com/BigTesty8/project-11/assets/137091610/b82d49da-e02d-4d87-b9d3-cc3ccd9c270b)

![](https://github.com/BigTesty8/project-11/assets/137091610/a09eaae7-6147-4767-99eb-0a2dd561bec3)




  




  


