# The Linux File System

It is helpful to have an idea of the Linux file system structure to navigate the terminal effectively. The Linux file system is a hierarchical structure that starts from the root directory `/`. Here are some key directories in the Linux file system:

- `/`: The root directory of the file system.
- `/bin`: Contains essential binaries (programs) that are required for the system to boot and run.
- `/boot`: Contains the Linux kernel and boot loader configuration files.
- `/dev`: Contains device files that represent hardware devices connected to the system.
- `/etc`: Contains system-wide configuration files.
- `/home`: Contains user home directories.
- `/lib`: Contains shared libraries that are required for programs to run.
- `/media`: Contains mount points for removable media such as USB drives.
- `/mnt`: Contains mount points for temporary file systems.
- `/opt`: Contains optional software packages.
- `/proc`: Contains information about system processes.
- `/root`: The home directory for the root user.
- `/run`: Contains system runtime data.
- `/sbin`: Contains essential system binaries.
- `/srv`: Contains data for services provided by the system.
- `/sys`: Contains information about the system hardware.
- `/tmp`: Contains temporary files.
- `/usr`: Contains user binaries, libraries, and documentation.
- `/var`: Contains variable data such as logs and spool files.

The most commonly used directories are `/home`, `/usr`, and `/var`.

When building containers, it is common to use the `/app` directory to store application code and assets. This directory is not a standard Linux directory but is often used in containerized applications for consistency.
