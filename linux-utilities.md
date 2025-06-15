# Basic Linux Utility Commands

This is a quick reference for some commonly used Linux utility commands.

## 💾 Disk Usage

*   `df -h`
    *   Displays disk space usage for all mounted filesystems in a human-readable format (e.g., KB, MB, GB).
*   `du -sh <directory_path>`
    *   Shows the total disk space used by a specific directory in a human-readable summary.
    *   Example: `du -sh /var/log`
*   `du -h --max-depth=1 <directory_path>`
    *   Shows disk space used by a directory and its immediate subdirectories in human-readable format.
    *   Example: `du -h --max-depth=1 /home/user`
*   `lsblk`
    *   Lists block devices (hard drives, partitions, USB drives) in a tree-like format.
*   `fdisk -l` (requires root/sudo)
    *   Lists disk partitions.

## ⚙️ CPU & Memory Checks

*   `top`
    *   Displays an interactive, real-time view of system processes, CPU usage, memory usage, and more. Press `q` to quit.
*   `htop`
    *   An interactive process viewer (often more user-friendly than `top`). May need to be installed (`sudo apt install htop` or `sudo yum install htop`).
*   `vmstat`
    *   Reports virtual memory statistics, including processes, memory, paging, block IO, traps, and cpu activity.
*   `free -h`
    *   Displays the amount of free and used memory in the system in human-readable format.
*   `lscpu`
    *   Displays information about the CPU architecture.
*   `uptime`
    *   Shows how long the system has been running, current time, number of users, and load averages.

## 🌐 Networking

*   `ip addr` or `ifconfig` (older, may not be installed by default on newer systems)
    *   Displays network interface configuration (IP addresses, MAC addresses, etc.).
*   `ping <hostname_or_ip>`
    *   Sends ICMP ECHO_REQUEST packets to network hosts to test connectivity.
    *   Example: `ping google.com`
*   `nslookup <hostname_or_ip>`
    *   Queries Internet domain name servers (DNS).
    *   Example: `nslookup www.github.com`
*   `dig <hostname>` (more advanced DNS lookup utility)
    *   Provides detailed DNS lookup information.
    *   Example: `dig example.com MX` (to find mail exchange servers)
*   `netstat -tulnp` (requires root/sudo for `-p` to show PIDs)
    *   Shows network connections (TCP, UDP), listening ports, and the programs using them.
    *   `-t`: TCP, `-u`: UDP, `-l`: listening sockets, `-n`: numeric addresses/ports, `-p`: show PID/program name.
*   `ss -tulnp` (modern replacement for `netstat`)
    *   Similar to `netstat`, used to investigate sockets.
*   `traceroute <hostname_or_ip>` or `tracepath <hostname_or_ip>`
    *   Traces the path packets take to a network host.
    *   Example: `traceroute google.com`
*   `route -n` or `ip route show`
    *   Displays the IP routing table.

## 📁 File & Directory Management

*   `pwd`
    *   Prints the current working directory.
*   `ls -lha`
    *   Lists directory contents in long format (`-l`), including hidden files (`-a`), with human-readable sizes (`-h`).
*   `cd <directory_path>`
    *   Changes the current directory.
    *   Example: `cd /var/www`
*   `mkdir <directory_name>`
    *   Creates a new directory.
*   `rm <file_name>`
    *   Removes (deletes) a file. Use with caution.
*   `rm -r <directory_name>`
    *   Removes a directory and its contents recursively. Use with extreme caution.
*   `cp <source_file> <destination_file_or_directory>`
    *   Copies files or directories.
    *   Example: `cp myfile.txt /backup/`
*   `mv <source> <destination>`
    *   Moves or renames files or directories.
    *   Example (rename): `mv oldname.txt newname.txt`
    *   Example (move): `mv myfile.txt /tmp/`
*   `find <path> -name "<filename_pattern>"`
    *   Searches for files in a directory hierarchy.
    *   Example: `find /home/user -name "*.log"`
    *   Example (find files modified in the last 7 days): `find . -type f -mtime -7`
    *   Example (find directories named 'backup'): `find / -type d -name "backup"`
*   `grep "<pattern>" <file_name>`
    *   Searches for a pattern within a file.
    *   Example: `grep "error" /var/log/syslog`
    *   Example (recursive, case-insensitive, line numbers): `grep -rni "mytext" /some/path`
*   `chmod <permissions> <file_or_directory>`
    *   Changes the permissions of a file or directory.
    *   Example (add execute permission for owner): `chmod u+x script.sh`
    *   Example (set read-write for owner, read-only for group and others): `chmod 644 data.txt`
*   `chown <user>:<group> <file_or_directory>`
    *   Changes the owner and group of a file or directory (often requires root/sudo).
    *   Example: `sudo chown www-data:www-data /var/www/html/index.html`
*   `which <command_name>`
    *   Shows the full path of a command.
    *   Example: `which python`
*   `ln -s <target_path> <link_name>`
    *   Creates a symbolic link (soft link).
    *   Example: `ln -s /var/log/app.log ./app_log_link`
*   `cat <file_name>`
    *   Concatenates and displays the content of files.
    *   Example: `cat /etc/hosts`
*   `less <file_name>` or `more <file_name>`
    *   Allows backward and forward movement through file content (pager). Press `q` to quit.
    *   Example: `less /var/log/syslog`
*   `head -n <number> <file_name>`
    *   Displays the first N lines of a file (default is 10).
    *   Example: `head -n 20 access.log`
*   `tail -n <number> <file_name>`
    *   Displays the last N lines of a file (default is 10).
    *   Example: `tail -n 50 error.log`
*   `tail -f <file_name>`
    *   Follows the content of a file in real-time (outputs appended data as the file grows).
    *   Example: `tail -f /var/log/syslog`

## 🖥️ System Information

    *   Displays or sets the system date and time.
*   `history`
    *   Displays the command history.
*   `echo $PATH`
    *   Displays the current system PATH environment variable, showing directories searched for executables.
*   `dmesg`
    *   Prints or controls the kernel ring buffer. Useful for diagnosing hardware or driver issues.
*   `lsmod`
    *   Shows the status of modules in the Linux Kernel.

## ⚙️ Process Management

*   `pgrep <process_name>`
    *   Finds process IDs by name.
    *   Example: `pgrep nginx`
*   `pkill <process_name>`
    *   Sends a signal to processes based on name (similar to `kill` but uses name instead of PID).
    *   Example: `pkill firefox`
*   `jobs`
    *   Lists active jobs (processes running in the background or stopped).
*   `fg %<job_number>`
    *   Brings a background job to the foreground.
    *   Example: `fg %1`
*   `bg %<job_number>`
    *   Resumes a stopped background job in the background.
    *   Example: `bg %2`
*   `nohup <command> &`
    *   Runs a command immune to hangups, with output to a `nohup.out` file, in the background (`&`).
    *   Example: `nohup ./my_long_script.sh &`

## 🗜️ Archives & Compression

*   `tar -czvf <archive_name.tar.gz> <directory_or_files_to_archive>`
    *   Creates a gzipped tar archive. (`c`reate, `z`ip, `v`erbose, `f`ile)
    *   Example: `tar -czvf backup.tar.gz /home/user/documents`
*   `tar -cjvf <archive_name.tar.bz2> <directory_or_files_to_archive>`
    *   Creates a bzip2 compressed tar archive. (`c`reate, `j` (bzip2), `v`erbose, `f`ile)
*   `tar -xzvf <archive_name.tar.gz> -C <destination_directory>`
    *   Extracts a gzipped tar archive. (`x`tract, `z`ip, `v`erbose, `f`ile, `-C` change to directory)
    *   Example: `tar -xzvf backup.tar.gz -C /tmp/restore`
*   `tar -xjvf <archive_name.tar.bz2> -C <destination_directory>`
    *   Extracts a bzip2 compressed tar archive. (`x`tract, `j` (bzip2), `v`erbose, `f`ile)
*   `gzip <file_name>`
    *   Compresses a file (replaces original with `<file_name>.gz`).
    *   Example: `gzip large_log_file.log`
*   `gunzip <file_name.gz>`
    *   Decompresses a gzipped file.
    *   Example: `gunzip large_log_file.log.gz`
*   `zip <archive_name.zip> <file1> <file2> <directory>`
    *   Creates a ZIP archive.
    *   Example: `zip my_archive.zip report.docx images/`
*   `unzip <archive_name.zip> -d <destination_directory>`
    *   Extracts files from a ZIP archive.
    *   Example: `unzip my_archive.zip -d ./extracted_files`

## 🚰 Input/Output Redirection & Piping

*   `command > file`
    *   Redirects standard output (stdout) of `command` to `file`, overwriting `file` if it exists.
*   `command >> file`
    *   Appends standard output (stdout) of `command` to `file`.
*   `command < file`
    *   Redirects standard input (stdin) for `command` from `file`.
*   `command1 | command2`
    *   Pipes the standard output (stdout) of `command1` to the standard input (stdin) of `command2`.
    *   Example: `ls -l | grep ".txt"`
*   `command 2> error_file`
    *   Redirects standard error (stderr) of `command` to `error_file`.
*   `command &> output_file` or `command > output_file 2>&1`
    *   Redirects both standard output (stdout) and standard error (stderr) of `command` to `output_file`.

---

Remember to replace placeholders like `<directory_path>`, `<hostname_or_ip>`, etc., with actual values.
Many commands offer extensive options; use `man <command_name>` (e.g., `man ls`) or `<command_name> --help` for detailed information.
Some commands may require `sudo` (superuser do) for elevated privileges.