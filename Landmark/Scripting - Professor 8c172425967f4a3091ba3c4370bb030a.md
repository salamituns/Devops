# Scripting - Professor

Created: October 28, 2023 1:05 PM
Class: Dev
Type: Study Group

After this course, you would be able to function as:

DevOp/Cloud/SRE/DevSecOps/Application Engineering

Platform/Kubernetes/Infrastructure Engineering

================================================

Automating IT Processes/workloads with CLI /GUI and Scripting

=========================================

Automating IT:
Processes
Workloads
Jobs
Tasks

Hardware components: 
RAM - memory
CPU
ROM 
Mouse
Keyboard
Screen

Software component: OS
Windows OS
MacOS
Solaris
Linux OS: Redhat, Ubuntu, CentOS, Debian, Amazon Linux
Other softwares:  shell, sublime, VScode, gitbash. 
-----
All of the above is used perfrom workloads; examples of workloads:
fileMgt, UserMgt, PackageMgt, SecurityMgt, SystemMgt, etc.

================================================

Scripts : a shell-script is a collection of one or more commands in a file
            a script is a file containing commands

Shell: is an interpreter that interprets commands to the OS.

Ticket 001: write a simple welcome script that welcome engineers to work 
execute
```bash
    #!/bin/bash
    echo "Good Morning"
    whoami
    echo "Welcome to Landmark Technologies"
    echo "Today is "
    date
```

Assigning executable permission:

chmod + x fileName
chmod + x [script1.sh](http://script1.sh) 
chmod 775 fileName
chmod 700 fileName
-----------
Shell command interpreters:
sh 
bash
csh / ksh / tsh / zsh
cat /etc/shells : list all shells in your system
sh fileName, sh [script.sh](http://script.sh) (hence you can run the script by using the interpretable script)
===================================================

Bash shell scripting:

Naming convention best practices:
bash shell-scripts = [script.sh] or hello.sc
shell-scripts has ‘.sc’ or ‘.sh’ extensions
[scriptname.sh] or [scriptname.sc] or *.sh or *.sc
[deploy.sh] = shell-script  [*.sh] 
test.txt = text file  [*.txt]
[app.sc] = shell script  [*.sc]
[app.java]= java code  [*.java]
[monitor.py] = python code  [*.py]
app.yaml = playbook or manifest file   [*.yml]
[main.tf] = terraform script/codes [*.tf]

===================================================

Scripting or automation languages: 

1. Bash shell scripting
2. python
3. Groovy (jenkins)
4. Ruby
5. Yaml (k8, ansible, cloudformation)
6. json / java
7. HCL -Terraform
8. xml
9. html
10. go/golang
11. powershell

Task- Ticket 002: write a shell simple script to deploy applications

solution:

1. create a deployment directory
    1. mkdir deployment
2. create a deployment [app.java] file
    1. touch deployment/app.java
3. assign read permission to [app.java] file
    1. chmod 744 deployment/app.java
4. changing ownership of [app.java] file
    1. sudo chown obi: amaka deployment/app.java
5. copy the file to the app directory
    1. mkdir app
    2. cp deployment/app.java app

vim deploy.sh

    ```bash
    #!/bin/bash
    echo "Tesla project1 is ready for the market"
    echo "Deployment started"
    mkdir deployment
    touch deployment/app.java
    chmod 744 deployment/app.java
    sudo chown obi:amaka deployment/app.java
    mkdir app
    cp deployment/app.java app
    echo "Deployment successful"
    whoami
    echo "Congratulations `whoami`, you are fully deployed"
    echo "You are blessed in Jesus name." 
    ```

save file as: deploy.sh
display script = cat -n [deploy.sh]
deploy the script = sh [deploy.sh]

======How to make your code easily readable/understandable=====

- by adding note/comments/explanations.
    - use ‘#’ to add comments to a script- for single line comment
    - use ‘<<startword ….. comments……. startword’ - for multiline comment.
        
        multi comment line starts
        
        - <<boy
        - comments 1
        - comment 2
        - boy
        
        multi comment line ends
        
- it makes your script/code to be understood by you and other over time
- it makes your script/code to be easily reusable in the future
- facilitate/ease troubleshooting and debugging
- comments are good for teams to have a better understanding of script deployment.

====================================================

Making your script portable by:

- Hard coding
- Soft coding

Soft coding by using variables in scripting:

===============================

name=SimonLegah
cpy=LandmarkTechnology

how to call variables in bash shell scripting:

$variableName
${variableName}

open the file var1.sh
vim var1.sh 

```bash
#!/bin/bash
name = SimonLegah
cpy = Landmark Technology
echo “Good morning $name”
echo “Good morning ${name}”
echo Welcome to $cpy
echo Good morning ${name}, welcome to $cpy
```

variables: 
Variables are defined by either the user or the system. we can refer/call a variable with $variable
User defined variables = UDV: are defined/created by some admins, are generally written in lowercase.

vim udv.sh
name = simonlegah
cpy = landmark technology
city = Toronto
country = Canada
echo $name works for $cpy located in $city, $country
export  class = DevOpsMasterClass 
#(We can change variables and assign variables with the help of the export command)
echo class

System defined variable = SDV
SDV are variable that comes with the OS; such as variables generally in uppercase

SHELL = bin/bash
echo $SHELL = /bin/bash
env = list all system defined variables
echo $HISTSIZE
echo $PATH
echo $HOME
echo $USER
echo $LOGNAME

====================================================

Dynamic script; this is a universal script that can be run over and over, at anytime, anywhere and by different individuals.

Task: ticket 003-  write a script to authenticate bank users:

vim read.sh

```bash
#!/bin/bash
echo ’Please enter your name’
read name
#read command is used to clooect dynamic variable
echo “$name, welcome to TD Bank”
echo ‘Please enter your card’
echo ‘Please enter your pin’
read pin
echo “$pin is the correct pin, $name, how may we help you today?”
```

Task: ticket 004 - Write a script to dynamically create users.

userMGT commands: adduser / usermod / userdel/ groupadd / groupdel

vim createuser.sh

```bash
#!/bin/bash
echo “Please enter the name of the new User”
read newuser
echo "Now ready to create $newuser"
sudo adduser $newuser
#this script requires root or sudo access
echo "$newuser account is created successfully"

#to validate or verify that new user is indeed created
grep $newuser /etc/passwd 

#NB user details are saved in 'etc/passwd'
```

Ticket 005: Create a dynamic script to add new users to a management account

vim userMGT.sh

```bash
echo "creating a newuser account"
echo "enter the new username' name"
read name
sudo adduser $name
sudo usermod -aG manager $name
id $name
```

<aside>
💡 IQ: Explain your experience in shell scripting?

1. Using bash shell scripting for userMGT
2. In my environment/company, I use scripting for userMGT for over 5 years
</aside>

Ticket- 006: Create a dynamic script to grant access for a bank account user

vim bank.sh

```bash
#!/bin/bash
echo "Please enter your name"
read name
echo "$name, welcome to TD Bank"
echo "Please enter your pin"
read -s pin # -s pass a secret variable
echo "$name you entered an invalid pin"
```

Run code with: sh bank.sh

========= Command Line Arguments =====================

Ticket 007: write a script to backup databases in our environment

#!/bin/bash
echo "The 1st argument is  $1"
echo "The 2nd argument is  $2"
echo "The 3rd argument is  $3"
echo "The 6th argument is  $6"
echo "The scriptName is  $0"
echo "The 10th argument is  ${10}"
echo The number argument is $#
echo The list of argument are $@
echo The list of argument are $*
echo The status of the last run command is $?
echo The process ID is $$

> IQ: what is the significance of the $? in scripting
> It is used to get the status of your last run command, whether it runs successfully or not.
> 
> The value can be = 0 [its okay] or
> 
> The value can be = 1 - 127 [It is not okay]
> 
> ============================================

> IQ: what is the significance of $$ in scripting
> It is used to get the process ID of the script

> ============================================
> 
> IQ how do you troubleshoot a script?
> 
>   by running the script in debugging mode
>   sh -x scriptName
> 

========Redirecting Standard output and Standard error========

Standard output redirect:

sh scriptName > log

sh [debug.sh] > log or sh debug.sh 1> log

Standard errors:

sh scriptName 2> fileName

sh [debug.sh](http://debug.sh) 2> error.log

redirect both standard output and error

sh scriptName > fileName 2>&1

sh [debug.sh](http://debug.sh) > all.log 2>&1

tail -1 /etc/passwd > new-user.txt = This will replace existing contents in the new location

tail -1 /etc/passwd | tee new-user.txt = gives the same result.

tail -1 /etc/passwd >> new-user.txt = This will add to the existing contents in the new file location

===================================================

=========== Package Management ======================

We can install, remove, update and upgrade packages in our servers.

examples of packages:

nano, tree, vim, jenkins, httpd, java, maven, tomcat, kubernetes, kublet, docker, etc.

we can download and install packages using package managers like:

yum/dnf ————- ————centos, redhat

apt/apt-get ——— ———-ubuntu , debian

chocolately/choco ——— windows OS

brew —— ————————mac

helm —————————— kubernetes

pip ——————————- python

---

Ticket 001: create a package management script. - on a centos/redhat/amazon linux system.

vim packages.sh

```bash
#!/bin/bash
#run the script with sudo access
#run this script on redhat/centos system
#run this script on amazon linux system
sudo yum install nano -y
sudo yum install vim -y
sudo yum install tree -y
sudo yum install python nginx -y

sh packages.sh #to run the script
```

---

Ticket: Install and start the apache webserver

vim apachepackage.sh

```bash
#!/bin/bash
#this script will install ans start the apache httpd
sudo yum install httpd -y
sudo systemctl start httpd - y
sudo systemctl enable httpd
ps -ef | grep httpd #check that httpd is installed
systemctl status httpd #check the status of httpd

sh apachepackage.sh # to run the script
```

---

---

setting up your httpd browser page

1. Use the vim editor to open the index html file in the var directory
    
    vim /var/www/html/index.html
    
2. Add contents to the index.html file
    
    **<**h1**>**Welcome to my webpage**</**h1**>**
    
    **<**h2**>**The pride of Africa**</**h2**>**
    

3. Press the Esc key, and enter :wq to save and close the file.

1. run curl command to load the index.html file in the browser
    
    curl [localhost](http://localhost) 
    

---

====== File Management =============

How to Add a user to the sudoers file

1. Log in as **root** user.
2. Enter the following command to open the sudoers file for editing:
    
    visudo -f /etc/sudoers
    

At the end of the file, add the following line for your user

*username* ALL=(ALL) ALL

3. Press the Esc key, and enter :wq to save and close the file.

---

======== Control commands = conditions: ============

if statements: 

Syntax:

```bash
if [ conditions ]
then 
commands
else 
commands 
fi
```

```bash
if (( conditions ))
then 
commands
else 
commands 
fi
```

Ticket:002 create a dynamic conditional statement for a betting firm

vim if1.sh

```bash
echo "Please enter your ticket prediction"
read ticket
if [ "$ticket" = "4008" ]
then 
  echo "You are the winner"
else
  echo "Please try again"
fi

sh if1.sh #command to run the code
```

Ticket: 003 create a dynamic script to determine 1st class student

vim if2.sh

```bash
#This script determines 1st class students
echo 'Enter your GPA'
read gpa
if [ $gpa -ge 4 ]
then 
echo "Congratulations,"
echo "You are a 1st class student"
elif [ $gpa -ge 3 ]
then
echo "Congratulations,"
echo "You are a 2nd class student"
else 
echo "You can do better"
fi 

sh if2.sh #command to run the code
```

Ticket: 004 create a dynamic script for a real estate company

vim realestate.sh

```bash
#!/bin/bash
#realtor selling a property
echo "How much is customer1 offereing?"
read offer1
echo "How much is customer2 offering?"
read offer2
if [ $offer1 -gt $offer2 ]
then 
echo "Customer1 has a better offer"
echo "Sell to customer1."

elif [ $offer1 -lt $offer2] #ekif is case if multiple conditions
then 
echo "Customer2 offer is better"
echo "Sell to customer2."
else
echo "We have a tie of $offer!"
echo "Request for an increase and choose the best possible offer."
fi 

sh realestate.sh #command to run the code
```

Ticket: 005 create a dynamic script to grant permission to new user

vim filemgt.sh

```bash
echo "enter username"
read p
echo "Your username is $p"

echo "creating a new user"
if (( uid == 0 )) 
then 
echo "you have permission to add users to the server"
echo "enter the name of the new user"
read name
adduser $name
else
echo "sorry only the root can run this script"
fi 
```

```bash
echo "creating a new user"
if [ uid == 0 ] 
then 
echo "read username"
read username
echo "Creating $username user account"
useradd $username
else
echo "sorry only the root can run this script"
fi 
```

Case for multiple elif:

```bash
if [ condition ]
then 
command1
command2
elif [ condition ]
then 
command1
command2
else
command1
command2
fi
```

---

===== For loop ======

Loops = conditions with multiple iterations

x < 200 could mean x = 1 or 2 or 3 or 4, etc.

### Syntax: for loop

```bash
for (( condition ))
do
commands
commands 
#execute all command/scripts until the condition is no longer met/satisfied.
#and repeat all statement between do and done
done 
```

example:

vim f1.sh

```bash
for (( a=1; a<= 5; a++ ))
do 
echo $a
done

sh fi.sh #command to run the script
```

---

write a shell script to print numbers from 100 -90

using for loop [100, 99, 98, —-,90] 

```bash
for (( a=100; a>=90; a-- ))
do 
echo $a
done

sh fi.sh #command to run the script
```

---

### syntax: while loop

```bash
initiation
while [ condition ]
do 
commands/statements
done
```

Example:  vim y1.sh

```bash
#!/bin/bash
echo "while loop starts"
echo "performing load testing for tesla"
l=10000
while [ $l -le 90000 ]
do
  echo "performing load testing"
  echo $l
  l=`expr $l + 10000`
done
echo "while loop ends"

sh y1.sh #to run the script
```

use cases for loop:

used to run load testing, get ranges of values, etc.

---

### Functions

A function is a piece of code that performs a specific task and avoids repetition/duplication  

Ticket 001: write a dynamic script with numerous functions:

```bash
#!/bin/bash

# Function to create a new user
usermgt() {
    echo "Enter the username of the new user: "
    read name

    # Use sudo to add the new user
    sudo adduser "$name"

    # Check if the new user was added successfully
    if grep -q "$name" /etc/passwd; then
        echo "User $name added successfully."
    else
        echo "Failed to add user $name."
    fi
}

# Function to manage files
filemgt() {
    # Check if the /etc/passwd file exists
    if [[ -f /etc/passwd ]]; then
        echo "File management"
        echo "The file exists. Please proceed."

        # Grep for the syntuns user in the /etc/passwd file
        grep syntuns /etc/passwd

        # Create a test.java file in the syntuns home directory
        touch /home/syntuns/test.java
    else
        echo "The /etc/passwd file does not exist."
    fi
}

# Function to install packages
packagemgt() {
    # Use sudo to install the tree, nano, vim, and unzip packages
    sudo yum install -y tree nano vim unzip
}

# Function to back up the database
db_backup() {
    # Copy all files and directories recursively to the /tmp/backup directory
    cp -r * /tmp/backup
}

# Function to monitor the system
monitoring() {
    # Show disk usage
    df -h

    # Show free memory
    free -m

    # Show the top 10 processes by CPU usage
    top
}

# Invoke the usermgt and filemgt functions
usermgt
filemgt
```

<aside>
💡 Examples of automated tasks:

Explain your experience in bash shell scripting??

Answer:

In my environment, I have written, maintained/ modifed shell scripts to:

monitor_servers.sh

dataBase_backup.sh

deploy_app.sh

access_account.sh

user_management.sh

file_management.sh

</aside>

---

### SCP command - Secure Copy

It is used to transfer files from one server to another and vice-vera

It is good for data migration, application deployment, etc.

scp transfer files and directory securely using the ssh protocol

- Through password authentication
    - scp fileName userName@ipaddress : destination — transfer files
    - scp -r direname userName@ipaddress : destination —  directory transfer
- Through ssh key authentication
    - scp -i key.pem fileName ubuntu@ipaddress : destination —- transfer file
    - scp -i key.pem -r direName userName@ipaddress : destination —- directory

---

Change password authentication

<aside>
💡 file for password authentication

sudo vi /etc/ssh/sshd_config 

change password authentication from No to Yes

</aside>

---

CronJobs: Scheduling Tasks/Workloads for automation.

===========

Scheduling Tasks/Workloads for automation.

Assignment/Ticket:

1. Write a script that monitors servers very minutes.
    
    This script should alert management of anormalies
    
2. Write a script that backups dbservers every midnight

Execution:

1. We shall use cronJobs and create cron tables to achieve this Automation and Schedule the tasks to run as expected.
    
    cron table = contains schedules tasks
    
    crontab -e = To edit the cron table
    
    crontab -l = List the cron table
    
2. Access to the crontab should be restricted because 
    1. Processes/workloads consumes systems resources [cpu, memory]
    2. some tasks can affect processes and shutdown the system

How to restrict crontab access:

sudo touch /etc/cron.allow [ username ] = allow

or 

sudo touch /etc/cron.deny [ username] = restrict

Scheduling Tasks/Workloads for automation.

Assignment/Ticket:

1. Write a script that monitors servers very minutes.
    
    This script should alert management of anormalies
    

vim monitor_server.sh

```bash
echo "server monitoring activated"
date 
df -h 
free -m
whoami
```

create and schedule a task to be executed every minute

/home/syntuns/monitor_server.sh = absolute path

monitor_server.sh = relative path

<aside>
💡 Always run crontab using absolute path

</aside>

- visit: http://crontab-generator.org
- select the duration options;
- crontab -e = To open and edit the cron table
    
    ```bash
    *** * * * * /home/syntuns/monitor_server.sh >/tmp/log 2>&1
    #every min, hour, day, week, month
    #append to the log file in the temp directory**
    ```
    

Project 1: 

- Create AWS account
- create a redhat8 linux server
- connect to the redhat server using ssh-client
- program or configure the server for password authentication
- create a user called Dominion and assign a password
- connect to the server using dominion user
- run commands in the server as dominion user