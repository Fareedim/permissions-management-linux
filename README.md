# 📂 File Permissions in Linux

## 📌 Project Description

The research team at my organization needed to update file permissions for specific files and directories within the `projects` directory. The existing permissions did not reflect the appropriate level of authorization. Verifying and updating these permissions was important to help secure the system.

To complete this task, I performed the following steps:

---

## 🔍 Check File and Directory Details

I used the following Linux command to inspect the current permissions set for the `projects` directory:

```bash
ls -la /path/to/projects
```

This command:

- Lists all contents of the directory in detail
- Includes hidden files (those starting with a dot `.`)
- Displays a 10-character string representing the permissions for each item

### Example Output (Illustrative):
```
drwxr-xr--  2 researcher2 group   4096 Jul 21 09:00 drafts
-rw-rw-r--  1 researcher2 group   1200 Jul 21 09:00 project_a.txt
-rw-rw-r--  1 researcher2 group   800  Jul 21 09:00 project_b.txt
-rw-rw-r--  1 researcher2 group   950  Jul 21 09:00 project_k.txt
-rw-rw-r--  1 researcher2 group   1300 Jul 21 09:00 project_t.txt
-rw-rw-r--  1 researcher2 group   1000 Jul 21 09:00 project_z.txt
-rw-rw-r--  1 researcher2 group   1100 Jul 21 09:00 project_q.txt
-rw-rw-r--  1 researcher2 group   1150 Jul 21 09:00 .project_x.txt
```

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
