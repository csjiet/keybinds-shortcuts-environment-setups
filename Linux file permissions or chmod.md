``` bash
# Owners, Groups, Others
drwx rwx rwx
```
### User types
1. **Owners**:
    - The "owners" are also referred to as the "user" or "file owner." They are the users who created the file or directory. Owners have the most control over the file's permissions and can perform actions like changing the permissions, modifying the file's contents, and deleting the file.
2. **Groups**:
    - The "groups" refer to the user groups to which the file or directory is associated. Files and directories can be assigned to specific groups, and group members share certain permissions. Group permissions are useful for collaborative work because they allow multiple users to work on the same set of files with shared access.
3. **Others**:
    - "Others" refers to all users who are not the owner of the file or part of the associated group. These users have the most limited permissions on the file or directory.
### Permissions, for each user type
1. **r, w, x**:
    - "r" stands for "read" permission.
    - "w" stands for "write" permission.
    - "x" stands for "execute" permission.

# How to chmod?
Commands:
```
chmod xyz filename
```
- x: "Owners" permission - (specified using numerical codes/ character codes)
- y: "Groups" permission - (specified using numerical codes/ character codes) 
- z: "Others" permission - (specified using numerical codes/ character codes)
#### Numerical codes
- 7: Read, write, and execute permission (rwx)
- 6: Read and write permission (rw)
- 5: Read and execute permission (rx)
- 4: Read permission (r)
- 3: Write and execute permission (wx)
- 2: Write permission (w)
- 1: Execute permission (x)
- 0: No permission (-)

#### Character codes
- `u`: Stands for "user" or "owner."
- `g`: Stands for "group."
- `o`: Stands for "others" or "world."
- `a`: Stands for "all" and represents all users (equivalent to ugo).

> You can use these character commands along with `+` to add permissions, `-` to remove permissions, and `=` to set permissions.

Common character command examples:
- `u+r`: Add read permission for the owner.
- `g-w`: Remove write permission for the group.
- `o+x`: Add execute permission for others.
- `a=rwx`: Set read, write, and execute permissions for all users.


