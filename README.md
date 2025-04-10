# 🛡️ Managing File Permissions in Linux

## 📝 Project Description

In this project, I used Linux command-line tools to review and update file and directory permissions for a research team. The goal was to ensure users had appropriate levels of authorization, in line with the organization's security policies. I used the `ls` and `chmod` commands to analyze and modify access controls, removing unauthorized permissions and granting only those required for each user or group.

> *This lab was conducted in a simulated Linux environment using CLI commands.*

## 🧠 Skills Learned

- Managing file and directory permissions in Linux.  
- Interpreting Unix permission strings.  
- Using `ls -la` to audit access rights.  
- Applying `chmod` for granular permission control.  
- Differentiating user, group, and other access levels.  
- Working with hidden files and directories.  

## 🛠️ Tools Used

<img src="https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black" />

## ✅ Project Steps

| **Task** | **Description** |
|----------|-----------------|
| **Check file and directory details** | Used `ls -la` to list all files (including hidden ones) in the `/home/researcher2/projects` directory, along with their permission strings. |
| **Describe the permissions string** | Analyzed Unix-style permission strings (e.g., `-rw-rw-r--`) to understand access levels for user, group, and others. |
| **Change file permissions** | Used `chmod` to remove permissions. |
| **Change permissions on a hidden file** | Applied `chmod` to remove and grant access for a hidden file. |
| **Change directory permissions** | Changed directory permissions using `chmod`. |

## 📄 Project Report

### Description

The research team at my organization needs to update the file permissions for certain files and directories within the projects directory. The permissions do not currently reflect the level of authorization that should be given. Checking and updating these permissions will help keep their system secure. To complete this task, I performed the following tasks.

### Check file and directory details

The following code demonstrates how I used Linux commands to determine the existing permissions set for a specific directory in the file system.

<img width="817" alt="image" src="https://github.com/user-attachments/assets/0a1fb27f-4a3c-45b5-a520-469457d47161" />

The first line of the screenshot displays the command I entered, and the other lines display the output.

The command used to list the files, hidden files and directory permissions is: `ls -la`.

The output of the command indicates that in the `/home/researcher2/projects` directory, there is one hidden file (`.project_x.txt`), one directory named `drafts` and 4 other project files.

The 10-character string in the first column represents the permissions set on each file or directory.

### Describe the permissions string

The 10-character string can be deconstructed to determine who is authorized to access the file and their specific permissions. To describe the permissions string, I am going to use as an example the file named `project_r.txt`.

The first block of information that is shown is the directory/file permissions. In the example this is: `-rw-rw-r--`.

Each character means the following:

- The **1st** one indicates if it’s a directory or a file. In the example, since it’s (`-`) means that is a file. In case it was a directory it would be a `d`.
- The **2nd**, **3rd** and **4th** characters indicate the read (`r`), write (`w`) and execute (`x`) permissions for the user. When one of these characters is a hyphen (`-`) instead, it indicates that this permission is not granted to the user. In the example, the user has read and write permissions.
- The **5th**, **6th** and **7th** characters indicate the read (`r`), write (`w`) and execute (`x`) permissions for the group. When one of these characters is a hyphen (`-`) instead, it indicates that this permission is not granted to the group. In the example it is the same as the user, read and write.
- Lastly, the **8th**, **9th** and **10th** indicate the read (`r`), write (`w`) and execute (`x`) permissions for other. When one of these characters is a hyphen (`-`) instead, it indicates that this permission is not granted to the other. In the example, other has only read permissions.

### Change file permissions

The organization determined that other shouldn't have write access to any of their files. Referring to the file permissions I previously returned, I determined that `project_k.txt` must have the write access removed for other.

<img width="824" alt="image" src="https://github.com/user-attachments/assets/64493700-a9fa-4084-b4c1-7f18c77350db" />

The first two lines on the screenshot display the commands I entered and the other lines are the output for the second command.

The command I used was: `chmod o-w project_k.txt`. The `chmod` command changes the permissions on files and directories. The first argument indicates what permissions should be changed; `o-w` means that for other (`o`) I am removing the write (`w`) permission. The second argument specifies the file or directory; `project_k.txt`.

After this, I used `ls -l` to review the updates I made.

### Change file permissions on a hidden file

The research team at my organization recently archived `.project_x.txt`. They do not want anyone to have write access to this project, but the user and group should have read access.

I can see that for the hidden file `.project_x.txt`, user has read and write permissions; and group has write permissions.

<img width="827" alt="image" src="https://github.com/user-attachments/assets/2b263228-d24b-4652-9319-0a33d6f13e77" />

I need to remove write permissions for both and only leave read permissions.

The commands I used to change the permissions are the following:

<img width="828" alt="image" src="https://github.com/user-attachments/assets/7ae6b49e-2aff-4d90-8e1a-8f597026ebdb" />

The first 2 lines are the commands and the other lines display the output for the second command.

I know `.project_x.txt` is a hidden file because it starts with a period (`.`). In this example I removed write permissions from the user and assigned read permissions to the group: `chmod u-w,g=r .proyect_x.txt`.

In which:

- I removed write permissions from the user with `u-w`.
- I assigned read permissions to the group with `g=r`. This overwrites the existing permissions, so it removes the write permissions and assigns the read one.

### Change directory permissions

The drafts directory within projects should only be accessible for the user `researcher2`. Hence it is needed to remove the execute permissions that group has. 

<img width="822" alt="image" src="https://github.com/user-attachments/assets/f90b4b99-b746-4471-a810-e88227093e1b" />

The command used was: `chmod g-x drafts`.

Where `g-x` means that execute (`x`) permissions are being removed for the group (`g`). The user already had execute permissions, so they did not need to be added.

### Summary

I changed multiple permissions to match the level of authorization my organization wanted for files and directories in the projects directory. The first step in this was using `ls -la` to check the permissions for the directory. This informed my decisions in the following steps. I then used the `chmod` command multiple times to change the permissions on files and directories.

## 💡 Reflections

This lab reinforced my understanding of how critical proper permission management is in a Linux environment. I learned to confidently interpret and manipulate permission strings, and gained hands-on experience with real-world use cases involving access control. These skills are essential for maintaining system security and supporting secure collaboration among users.

