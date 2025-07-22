#  File Permissions in Linux

##  Project Description

The research team at my organization needed to update file permissions for specific files and directories within the `projects` directory. The existing permissions did not reflect the appropriate level of authorization. Verifying and updating these permissions was important to help secure the system.

To complete this task, I performed the following steps:
<img width="372" height="141" alt="capturea" src="https://github.com/user-attachments/assets/da3f961c-cfd2-4323-8b26-2a5219b4213d" />

The first line of the screenshot displays the command I entered, and the other lines display the output. The code lists all the contents of the `projects` directory. I used the `ls` command with the `-la` option to display a detailed listing of the file contents that also returned hidden files. The output of my command indicates that there is one directory named `drafts`, one hidden file named `.project_x.txt`, and five other project files. The 10-character string in the first column represents the permissions set on each file or directory. 
---

##  Check File and Directory Details

I used the following Linux command to inspect the current permissions set for the `projects` directory:



---

## 🧾 Describe the Permissions String

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

## 🔧 Change File Permissions

### Remove Write Access from "Other" for `project_k.txt`

```bash
chmod o-w project_k.txt
ls -la project_k.txt
```

- `chmod` modifies file permissions
- `o-w` removes write access from "others"

---

## 🕶 Change Permissions on a Hidden File

The archived file `.project_x.txt` required stricter permissions:

```bash
chmod u-w .project_x.txt
chmod g-w .project_x.txt
chmod g+r .project_x.txt
ls -la .project_x.txt
```

- Hidden files begin with a `.`  
- Removed write access from user and group  
- Added read access to the group

---

## 📁 Change Directory Permissions

Only the `researcher2` user should have access to the `drafts` directory. Others should not be able to execute into it.

```bash
chmod g-x drafts
ls -la
```

- `chmod g-x` removes execute permission from the group  
- Execute permission on a directory allows accessing its contents

---

## ✅ Summary

I adjusted file and directory permissions based on my organization's security needs:

- Used `ls -la` to inspect permissions
- Interpreted the permission string
- Used `chmod` to:
  - Remove write access for "other"
  - Adjust permissions on a hidden file
  - Restrict access to a sensitive directory

These actions improved system security by aligning file access with required authorization levels.
