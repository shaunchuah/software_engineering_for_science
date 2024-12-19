# Basic Commands

Let's get going. Open a terminal window. In MacOS you can hit `Cmd + Space` and type `Terminal` to open it. In Windows you can hit `Win + R` and type `cmd` to open the command prompt.

## Navigating the terminal

### List all files in the current directory

=== "MacOS/Linux"
    ```bash
    ls
    ls -al # -a shows hidden files, -l shows long format with permissions
    ```
=== "Windows"
    ```bash
    dir
    ```

### Change directories

=== "MacOS/Linux"
    ```bash
    cd path/to/directory
    cd .. # Move up one directory
    cd ~ # Move to home directory
    ```
=== "Windows"
    ```bash
    cd path\to\directory
    cd .. # Move up one directory
    cd %HOMEPATH% # Move to home directory
    ```

!!! note "What is the home directory and where is it located?"

    The home directory is represented by `~` in MacOS and Linux.
    For example, `/Users/username` in MacOS and `/home/username` in Linux.
    In Linux, if you are using the root user, the home directory is `/root`.

## File and Directory Operations

### Create a new directory

=== "MacOS/Linux"
    ```bash
    mkdir new_directory
    ```
=== "Windows"
    ```bash
    mkdir new_directory
    ```

### Deleting files and directories

=== "MacOS/Linux"
    ```bash
    rm file.txt # Delete a file
    rm -r directory # Delete a directory and its contents
    ```
=== "Windows"
    ```bash
    del file.txt # Delete a file
    rmdir /s directory # Delete a directory and its contents
    ```

### Copying files and directories

=== "MacOS/Linux"
    ```bash
    cp file.txt new_file.txt # Copy a file
    cp -r directory new_directory # Copy a directory and its contents
    ```
=== "Windows"
    ```bash
    copy file.txt new_file.txt # Copy a file
    xcopy /s directory new_directory # Copy a directory and its contents
    ```

### Moving files and directories

=== "MacOS/Linux"
    ```bash
    mv file.txt new_directory # Move a file
    mv directory new_directory # Move a directory
    ```
=== "Windows"
    ```bash
    move file.txt new_directory # Move a file
    move directory new_directory # Move a directory
    ```

### Viewing file contents

=== "MacOS/Linux"
    ```bash
    cat file.txt # View the contents of a file
    ```
=== "Windows"
    ```bash
    type file.txt # View the contents of a file
    ```

### Editing text files

=== "MacOS/Linux"
    ```bash
    nano file.txt # Edit a file in the terminal
    ```
=== "Windows"
    ```bash
    notepad file.txt # Edit a file in Notepad
    ```

## Tips

### Autocomplete file names

Press `Tab` to autocomplete file names in the terminal.

### Clear the terminal

=== "MacOS/Linux"
    ```bash
    clear
    ```
=== "Windows"
    ```bash
    cls
    ```
You can also use `Ctrl + L` to clear the terminal.

### Previous commands

Use the up and down arrow keys to navigate through previous commands.

### Manual pages

Use the `man` command to view the manual pages for a command.

=== "MacOS/Linux"
    ```bash
    man ls # View the manual page for the ls command
    ```
=== "Windows"
    Windows does not have a built-in manual page viewer. You can use the `/?` option with commands to view help.

    ```bash
    dir /? # View help for the dir command
    ```
