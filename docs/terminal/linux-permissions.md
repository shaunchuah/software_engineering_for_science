# Linux Permissions

Linux file permissions are a way to control who can read, write, and execute files and directories on a Linux system. Understanding how permissions work is essential for managing files and ensuring the security of your system. It is common to encounter issues with running your code or accessing files due to incorrect permissions.

In this lesson, you will learn how to view and change file permissions using the `ls` and `chmod` commands. You will also learn about the different permission levels and how to interpret the output of the `ls` command.

## Viewing File Permissions

To view the permissions of a file or directory, you can use the `ls -l` command. This command displays detailed information about the files and directories in the current directory, including their permissions.

```bash
ls -l
```

The output of the `ls -l` command will look something like this:

```bash
-rw-r--r-- 1 user user 0 Jan 1 00:00 file.txt
drwxr-xr-x 2 user user 4096 Jan 1 00:00 directory
```

The first column represents the permissions of the file or directory. The permissions are divided into three groups: user, group, and others. Each group has three permission levels: read, write, and execute. The permissions are represented by a series of characters:

- `-`: Indicates that the permission is not granted.
- `r`: Indicates that the read permission is granted.
- `w`: Indicates that the write permission is granted.
- `x`: Indicates that the execute permission is granted.

For example, `rw-r--r--` means that the user has read and write permissions, while the group and others have read-only permissions. Side note: the `d` at the beginning of the line indicates that the entry is a directory.

## Changing File Permissions

To change the permissions of a file or directory, you can use the `chmod` command. The `chmod` command allows you to add or remove permissions for the user, group, and others.

The `chmod` command takes two arguments: the permissions you want to set and the file or directory you want to modify. The permissions are represented by a series of characters:

- `r`: Grants read permission.
- `w`: Grants write permission.
- `x`: Grants execute permission.

You can use the following syntax to set permissions with the `chmod` command:

```bash
chmod [permissions] [file]
```

For example, to give the user read and write permissions on a file, you can use the following command:

```bash
chmod u+rw file.txt
```

In this command:

- `u`: Represents the user.
- `+`: Adds the specified permissions.
- `rw`: Grants read and write permissions.

You can also use the following shorthand notation to set permissions:

- `u`: Represents the user.
- `g`: Represents the group.
- `o`: Represents others.
- `a`: Represents all (user, group, and others).

For example, to give read and write permissions to the user, read permissions to the group, and no permissions to others, you can use the following command:

```bash
chmod u+rw,g+r,o-r file.txt
```

In this command:

- `u+rw`: Grants read and write permissions to the user.
- `g+r`: Grants read permissions to the group.
- `o-r`: Removes read permissions from others.

## Using Permission Numbers

Another way to set permissions is to use numeric values. Each permission level (read, write, execute) is assigned a numeric value:

- `r` (read): 4
- `w` (write): 2
- `x` (execute): 1

You can calculate the permission value by adding the numeric values for each permission level. For example, to grant read and write permissions to the user, you can use the following command:

```bash
chmod 600 file.txt
```

In this command:

- `6`: Represents read and write permissions for the user.
- `0`: Represents no permissions for the group and others.

You can also use the following values to set permissions:

- `7`: Grants
- `6`: Grants read and write permissions.
- `5`: Grants read and execute permissions.
- `4`: Grants read permissions.
- `3`: Grants write and execute permissions.
- `2`: Grants write permissions.
- `1`: Grants execute permissions.

For example, to grant read, write, and execute permissions to the user, read and execute permissions to the group, and no permissions to others, you can use the following command:

```bash
chmod 750 file.txt
```

In this command:

- `7`: Represents
- `5`: Represents read and execute permissions for the group.
- `0`: Represents no permissions for others.

## Most Common Scenario

The most common scenario where you use permissions is when trying to execute a bash script file. This is because when you copy a script file into Linux, it does not have execute permissions by default. To give execute permissions to a script file, you can use the following command:

```bash
chmod +x script.sh
```
