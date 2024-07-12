# File Permissions in Linux

## Objective
[Brief Objective - Remove this afterwards]

The Detection Lab project aimed to establish a controlled environment for simulating and detecting cyber attacks. The primary focus was to ingest and analyze logs within a Security Information and Event Management (SIEM) system, generating test telemetry to mimic real-world attack scenarios. This hands-on experience was designed to deepen understanding of network security, attack patterns, and defensive strategies.

### Skills Learned


- Advanced understanding of SIEM concepts and practical application.
- Proficiency in analyzing and interpreting network logs.
- Ability to generate and recognize attack signatures and patterns.
- Enhanced knowledge of network protocols and security vulnerabilities.
- Development of critical thinking and problem-solving skills in cybersecurity.



## Procedure

### Checking File and Directory Details
The project's scope took place entirely within the <b>/home/researcher2/projects</b> directory. Once in the directory, I used <b>ls -la</b> to view the permissions on every file within <b>projects</b>. The <b>-la</b> ensured that hidden files and directories were also included. I found five files and one directory named <b>drafts</b> inside the parent <b>projects</b> directory. Below is a screenshot of my initial permissions check.

![image](https://github.com/user-attachments/assets/f7b8daa0-1b51-4609-ad75-90aa8e10b1ee)



### Describing Permission Strings

The following is an example of a permissions string: <b>drwxrwxrwx</b>. The string's first character represents the type of file, which can be defined as <b>d</b> for directories or a hyphen character, <b>-</b>, for files.  Characters 2-4 represent the permissions for user. The first of these is <b>r</b> for read permissions, the second is <b>w</b> for write permissions, and the final character <b>x</b> represents executable permissions. Any absence/restriction of these permissions will replace the letter character with a hyphen, <b>-</b>. Characters 5-7 represent the permissions for group and follow the same order as the permissions for user. The same restriction rules apply. The final three characters represent the permissions for “other” and follow the same ordering of rules and also use the same restriction rules. An example of a permissions string with restrictions in place for both the group and other may look like this: <b>-rwxr—-r—-</b>.


### Changing File Permissions



# Changing File Permissions on a Hidden File


## Changing Directory Permissions


