# MINIX Installation and Login Update

This repository provides a guide for installing the MINIX operating system and customizing the login prompt by modifying the `getty.c` file. MINIX is a Unix-like, microkernel-based OS known for its educational value in operating system concepts.

## Project Overview
This guide explains the process of installing MINIX on a virtual machine and updating the login prompt text. The modification involves locating the `getty.c` file and changing the default "login:" prompt to a custom text, which can be useful for localizing or customizing login messages.

## Requirements
- **Virtual Machine Software**: VirtualBox or VMware
- **MINIX ISO**: Available from the [MINIX official website](https://www.minix3.org/).
- **Basic Unix Knowledge**: Familiarity with terminal commands and basic text editing in Unix.

## Installation Steps

1. **Download MINIX ISO**: Download the MINIX ISO from the [official website](https://www.minix3.org/).
2. **Create a New Virtual Machine**:
   - Open your virtual machine software (e.g., VirtualBox or VMware).
   - Create a new virtual machine with the following settings:
     - **Operating System**: Linux
     - **Version**: Other Linux (64-bit)
     - **Memory**: At least 512 MB
     - **Hard Disk**: Minimum 2 GB
3. **Attach the ISO and Boot**:
   - Attach the MINIX ISO as a virtual CD/DVD drive in the VM settings.
   - Boot the VM and follow the installation prompts.
4. **Partition and Install**:
   - Partition the disk as prompted.
   - Install the OS and reboot when complete, removing the ISO.

## Login Prompt Update

### Steps to Modify the Login Prompt
This section explains how to update the login prompt from "login:" to "Giris:" by modifying the `getty.c` file.

1. **Locate the Getty File**:
   - Use the command below to find any files named `getty`:
     ```bash
     find . -name getty*
     ```
   - The target file, `getty.c`, was found under `usr/src/commands/simple`.

2. **Navigate to the File Directory**:
   - Move to the directory containing the file:
     ```bash
     cd usr/src/commands/simple
     ```

3. **Edit `getty.c`**:
   - Open the `getty.c` file in the `vi` editor:
     ```bash
     vi getty.c
     ```
   - Search for "login:" in the file to locate the prompt text:
     ```bash
     /login:
     ```

4. **Modify the Login Prompt**:
   - Replace "login:" with "Giris:" by using the following command in `vi`:
     ```bash
     :%s/login:/Giris:/g
     ```

5. **Save and Exit**:
   - Save the file and exit `vi`:
     ```bash
     :wq
     ```

6. **Compile and Apply Changes**:
   - Go back to the `usr/src` directory and compile the source code:
     ```bash
     cd /
     cd usr/src
     make clean install
     ```
   - Reboot the system to apply the changes:
     ```bash
     reboot
     ```

## Result
After following these steps, the login prompt text will display "Giris:" instead of "login:" when accessing the system. This change is now permanently applied across system reboots.

## Troubleshooting
- **Compilation Errors**: Ensure all dependencies are correctly installed and that there are no syntax errors in `getty.c` before compiling.
- **Revert Changes**: If needed, edit the `getty.c` file again to restore the original text, recompile, and reboot.

## Acknowledgments
This guide leverages the educational potential of MINIX, illustrating how to make core modifications to OS functionality.
