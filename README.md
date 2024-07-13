# File Permissions and User Management in Linux

## Project Description


This project focuses on evaluating and configuring file and directory permissions within a hypothetical company's environment. The initial step involved auditing current permissions to identify discrepancies. After that, I configured permissions to comply with the organization's security policies. The project also includes adding new employees, assigning project ownership, and updating user group memberships to reflect changes in their roles.

### Skills Learned


- Proficiency in managing and configuring file and directory permissions using Linux commands like chmod
- Expertise in user account management, including adding new users, assigning group memberships, and deleting users
- Ability to audit and secure file permissions to meet organizational security requirements



## Procedure

### Checking File and Directory Details
The first part of the project took place entirely within the <b>/home/researcher2/projects</b> directory. Once in the directory, I used <b>ls -la</b> to view the permissions on every file within <b>projects</b>. The <b>-la</b> ensured that hidden files and directories were included. I found four files and one directory named <b>drafts</b> inside the parent <b>projects</b> directory. I also noted a hidden file named <b>.project_x.txt</b> inside the directory. Below is a screenshot of my initial permissions check.

![image](https://github.com/user-attachments/assets/f7b8daa0-1b51-4609-ad75-90aa8e10b1ee)



### Describing Permission Strings

The 10-character permission string can be analyzed to understand who can access a file and their respective permissions. Each character in the string represents a specific aspect of the file's permissions. Any hyphen <b>(-)</b> from the second character onward indicates a lack of permission.
- 1st character: This character represents the type of item in the directory. It can either be a <b>d</b> for directory or a hyphen <b>-</b> for file
- 2nd-4th characters: These characters indicate the read (r), write (w), and execute (x) permissions for the user in that order (rwx)
- 5th-7th characters: These characters indicate the read (r), write (w), and execute (x) permissions for the group
- 8th-10th characters: These characters indicate the read (r), write (w), and execute (x) permissions for other. This type consists of all other users on the system other than the user and the group





### Changing File Permissions

According to company policy, no employee may have write permissions for archived files, and no employees belonging to "other" may write to any files. By running <b>ls -la</b> again, I found that employees belonging to other had write permissions on a file named <b>project_k.txt</b>. To solve this, I used <b>chmod o-w project_k.txt</b> with <b>o-w</b> to indicate that I wanted to remove write permissions from other. I used <b>ls -l</b> to verify the change, as seen below.

![image](https://github.com/user-attachments/assets/546f57e7-3892-417b-b3da-f799fc3efdc3)

I also found user and group had write permissions on the archived file <b>.project_x.txt</b>. I used <b>chmod u=r,g=r .project_x.txt</b> to apply proper permissions on the file. Using <b>u=r,g=r</b> ensured that the only permissions for both would be set to read-only. 

![image](https://github.com/user-attachments/assets/140ea69d-386a-4bff-b440-4f9b92041f91)




### Changing Directory Permissions

Company policy mandated that the subdirectory <b>drafts</b> only be accessed by user. I used <b>ls -l</b> to check the permissions on the subdirectory. I found that employees belonging to group had executable permissions set. The screenshot below depicts the permissions check, and the second one demonstrates the command I used to fix this issue. 
![image](https://github.com/user-attachments/assets/8c5ba782-0f12-4c4a-b0d9-a915b7cef0ce)


![image](https://github.com/user-attachments/assets/b8ab30bc-96f2-4e2e-aeec-db46c2921367)



### Adding a New Employee

The next task was to add a new employee to the system. This new employee joined the company research department and was designated "researcher9" on the system. I began by creating their user by writing the command seen below: 

![image](https://github.com/user-attachments/assets/432f06dc-912d-47bd-8aa5-4303710d1286)

Now that <b>researcher9</b> was added to the system, it was time to add them to their appropriate group. I used the command <b>sudo usermod -g research_team researcher9</b> to add researecher9 to the group research_team. The screenshot below demonstrates this.


![image](https://github.com/user-attachments/assets/ee770aa9-8a10-4dab-8957-dadd455845b5)



### Assigning the New Employee a Project


The new employee was to be in charge of a project titled <b>project_r</b>. This project was owned by user <b>researcher2</b> before the new employee's arrival. I used the command <b> cd /home/researcher2/projects</b> to navigate to the <b>projects</b> directory of user <b>researcher9</b>. Once I located <b>project_r</b>, I used the <b>chown</b> command to make <b>researcher9</b> the new owner of the project. This command is shown below.

![image](https://github.com/user-attachments/assets/05537256-f57e-4917-9de4-129a57fa6dcc)

### Adding the User to a Secondary Group


A few months after hiring, the employee's role at the company changed, as they were now part of both the research and sales departments. My new task was to add <b>researcher9</b> to their secondary group <b>sales_team</b>. I used <b>usermod</b> with the <b>-a</b> and <b>-G</b> attributes to add <b>researcher9</b> to the group <b>sales_team</b> as their secondary group. This command is shown below. 

![image](https://github.com/user-attachments/assets/b3664dcc-4b57-47ae-a080-415a91a1b8f6)


## Removing the User from the System

A year after hiring, <b>researcher9</b> decided to leave the company. My new task was to delete them from the system. When creating a new user in Linux, a group of the same name is automatically created. The user is then made the only member of that group. Attempting to erase the user from the system using <b>userdel</b> would print the following error: 

![image](https://github.com/user-attachments/assets/dc0d587e-468e-4564-9112-74d0881af22c)

To avoid this, I used <b>groupdel</b> to remove the user and its associated empty groups. The command is shown below.

![image](https://github.com/user-attachments/assets/bbfc9a30-4703-4cfe-8c78-592e1323590e)


## Summary

In this project, I audited and reconfigured file and directory permissions in the <b>/home/researcher2/projects</b> directory to match company security requirements. Using commands like <b>chmod</b> and <b>chown</b>, I ensured appropriate controls. I also managed user accounts by adding new employees, assigning project ownership, and modifying group memberships, properly establishing and maintaining a secure file system environment.
