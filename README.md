#  File Permissions in Linux

##  Project Description

The research team at my organization needed to update file permissions for specific files and directories within the `projects` directory. The existing permissions did not reflect the appropriate level of authorization. Verifying and updating these permissions was important to help secure the system.

To complete this task, I performed the following steps:

---

##  Check File and Directory Details

I used the following Linux command to inspect the current permissions set for the `projects` directory:

<img src="https://github.com/user-attachments/assets/da3f961c-cfd2-4323-8b26-2a5219b4213d" alt="capturea" style="width: 100%;" />


The first line of the screenshot displays the command I entered, and the other lines display the output. The code lists all the contents of the `projects` directory. I used the `ls` command with the `-la` option to display a detailed listing of the file contents that also returned hidden files. The output of my command indicates that there is one directory named `drafts`, one hidden file named `.project_x.txt`, and five other project files. The 10-character string in the first column represents the permissions set on each file or directory.

---

##  Describe the Permissions String

Each file or directory has a 10-character permission string. Here's how to interpret it:

| Position | Description                                      |
|----------|--------------------------------------------------|
| 1st      | File type: `d` (directory) or `-` (regular file) |
| 2-4      | User (owner) permissions: read (`r`), write (`w`), execute (`x`) |
| 5-7      | Group permissions: read (`r`), write (`w`), execute (`x`) |
| 8-10     | Others' permissions: read (`r`), write (`w`), execute (`x`) |

**Example:**  
Permissions for `project_t.txt`:  
`-rw-rw-r--`

- `-` → Regular file  
- `rw-` → User can read and write  
- `rw-` → Group can read and write  
- `r--` → Others can only read

---

##  Change File Permissions

The organization determined that other shouldn't have write access to any of their files. To comply with this, I referred to the file permissions that I previously returned. I determined `project_k.txt` must have the write access removed for other.

The following code demonstrates how I used Linux commands to do this:

<img width="359" height="129" alt="captureb" src="https://github.com/user-attachments/assets/075883ed-2b68-437a-9bf4-a2e659f389ba" />

The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. The `chmod` command changes the permissions on files and directories. The first argument indicates what permissions should be changed, and the second argument specifies the file or directory. In this example, I removed write permissions from other for the `project_k.txt` file. After this, I used `ls -la` to review the updates I made.

---

##  Change Permissions on a Hidden File

The research team at my organization recently archived `project_x.txt`. They do not want anyone to have write access to this project, but the user and group should have read access.
The following code demonstrates how I used Linux commands to change the permissions:

<img width="362" height="128" alt="capturec" src="https://github.com/user-attachments/assets/5e77ba10-11eb-46fe-a27e-2fd00759d845" />

The first two lines of the screenshot display the commands I entered, and the other lines
display the output of the second command. I know `.project_x.txt` is a hidden file because
it starts with a period (`.`). In this example, I removed write permissions from the user and group,
and added read permissions to the group. I removed write permissions from the user with `u-w`.
Then, I removed write permissions from the group with `g-w`, and added read permissions to
the group with `g+r`.

---

##  Change Directory Permissions

My organization only wants the `researcher2` user to have access to the `drafts` directory and its contents. This means that no one other than `researcher2` should have execute permissions.

The following code demonstrates how I used Linux commands to change the permissions:

<img width="370" height="128" alt="captured" src="https://github.com/user-attachments/assets/9746432a-898f-4765-8839-64d3bf14d298" />

The output here displays the permission listing for several files and directories. Line 1 indicates the current directory (projects), and line 2 indicates the parent directory (home). Line 3 indicates a regular file titled `.project_x.txt`. Line 4 is the directory (drafts) with restricted permissions. Here you can see that only researcher2 has execute permissions. It was previously determined that the group had execute permissions, so I used the `chmod` command to remove them. The `researcher2` user already had execute permissions, so they did not need to be added.

---

##  Summary

I changed multiple permissions to match the level of authorization my organization wanted for files and directories in the `projects` directory. The first step in this was using `ls -la` to check the permissions for the directory. This informed my decisions in the following steps. I then used the `chmod` command multiple times to change the permissions on files and directories.
