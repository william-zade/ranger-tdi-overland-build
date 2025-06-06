Resetting Arch Linux Password via GRUB

This guide walks you through resetting a forgotten Arch Linux user password by booting directly into a root shell. Useful for recovery situations when you have physical access to the machine.

🧰 Prerequisites

Arch Linux installation with GRUB bootloader

Physical access to the machine

A keyboard :)

🧯 Step-by-Step Instructions

1. Reboot and Open GRUB Menu

Restart your laptop.

When the GRUB menu appears, use the arrow keys to highlight your usual boot entry.

Press e to edit boot parameters.

2. Edit Kernel Boot Parameters

Find the line starting with linux (this contains the kernel path and parameters).

Navigate to the end of that line.

Add a space and append:

init=/bin/bash

3. Boot into Shell

Press Ctrl+X or F10 to boot with this temporary change.

The system will boot into a minimal root shell without a password prompt.

4. Remount Root Filesystem Read-Write

By default, the filesystem is mounted read-only. Remount it:

mount -o remount,rw /

5. Identify Your Username (Optional)

If you forgot your username, list home directories:

ls /home

6. Reset the Password

Replace your_username with your actual username:

passwd your_username

Enter your new password twice when prompted.

7. Reboot Normally

Once done:

exec /sbin/init

Or just force a reboot:

reboot -f

✅ Done

You can now log in with your new password. Make sure to update any saved credentials or keyrings if needed.