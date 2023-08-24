---
title: "Command Line Arguments in Bash Shell"
datePublished: Thu Aug 03 2023 07:16:30 GMT+0000 (Coordinated Universal Time)
cuid: clkutpsc7001609jqfi2285ou
slug: command-line-arguments-in-bash-shell
tags: linux, linux-for-beginners, bash-script, 90daysofdevops, bash-shell-script

---

In Bash, command-line arguments are accessed using special variables: `$0`, `$1`, `$2`, and so on. Let's explore these command-line arguments with easy-to-understand examples:

1. `$0`: The value of `$0` represents the name of the script or program being executed.
    

Example: If we have a script called "[myscript.sh](http://myscript.sh)" with the following content:

```bash
#!/bin/bash

echo "This script is named: $0"
```

Usage:

```bash
./myscript.sh
```

Output:

```bash
This script is named: ./myscript.sh
```

1. `$1`, `$2`, `$3`, ...: These variables represent the first, second, third, and so on, command-line arguments provided when executing the script.
    

Example: Let's create a script called "[greet.sh](http://greet.sh)" that takes two arguments: the first argument is the name of a person, and the second argument is their age.

[greet.sh](http://greet.sh):

```bash
#!/bin/bash

name=$1
age=$2

echo "Hello, $name! You are $age years old."
```

Usage:

```bash
./greet.sh John 30
```

Output:

```bash
Hello, John! You are 30 years old.
```

1. `$#`: Represents the total number of command-line arguments passed to the script.
    

Example: Create a script called "[countargs.sh](http://countargs.sh)" to display the number of arguments passed.

[countargs.sh](http://countargs.sh):

```bash
#!/bin/bash

echo "The number of arguments provided is: $#"
```

Usage:

```bash
./countargs.sh arg1 arg2 arg3
```

Output:

```bash
The number of arguments provided is: 3
```

1. `$*` and `$@`: These variables represent all command-line arguments as a single string and as an array, respectively.
    

Example: Let's create a script called "[printargs.sh](http://printargs.sh)" to print all command-line arguments.

[printargs.sh](http://printargs.sh):

```bash
#!/bin/bash

echo "All arguments as a single string: $*"
echo "All arguments as an array: $@"
```

Usage:

```bash
./printargs.sh arg1 arg2 arg3
```

Output:

```bash
All arguments as a single string: arg1 arg2 arg3
All arguments as an array: arg1 arg2 arg3
```

1. `$?`: This variable holds the exit status of the last executed command. Typically, a value of `0` indicates success and a non-zero value indicates an error.
    

Example: Create a script called "[exitstatus.sh](http://exitstatus.sh)" that runs the `ls` command and then display the exit status.

[exitstatus.sh](http://exitstatus.sh):

```bash
#!/bin/bash

ls
echo "Exit status of the 'ls' command: $?"
```

Usage:

```bash
./exitstatus.sh
```

Output:

```bash
file1.txt file2.txt
Exit status of the 'ls' command: 0
```

1. `$$`: This variable contains the process ID (PID) of the current script.
    

Example: Create a script called "[showpid.sh](http://showpid.sh)" to display its own process ID.

[showpid.sh](http://showpid.sh):

```bash
#!/bin/bash

echo "The process ID of this script: $$"
```

Usage:

```bash
./showpid.sh
```

Output:

```bash
The process ID of this script: 12345 (an actual process ID number)
```

Now let us talk about scenarios of these command line arguments in the bash shell.

**Scenario 1: Lost Files - Recovering from a Backup**

Problem: Imagine you have important documents and photos stored on your computer. One day, you accidentally delete some of these files, and they are no longer in the "Trash" folder. You realize that you should have made a backup of your data earlier, but you didn't. Now, you are worried about losing those files permanently.

Solution: To prevent such data loss, you can create a simple backup script that runs daily and copies your critical data to an external hard drive. The script could be named "backup\_data.sh" and would take the source data directory and backup destination directory as command-line arguments.

backup\_data.sh:

```bash
bashCopy code#!/bin/bash

# Check if the correct number of arguments is provided
if [ $# -ne 2 ]; then
  echo "Usage: $0 <source_directory> <backup_destination>"
  exit 1
fi

# Store the arguments in meaningful variables
source_dir=$1
backup_dir=$2

# Check if the source directory exists
if [ ! -d "$source_dir" ]; then
  echo "Error: Source directory '$source_dir' does not exist."
  exit 1
fi

# Check if the backup directory exists, if not, create it
if [ ! -d "$backup_dir" ]; then
  mkdir -p "$backup_dir"
fi

# Perform the backup using rsync
rsync -av "$source_dir" "$backup_dir"

# Check if the backup was successful
if [ $? -eq 0 ]; then
  echo "Backup completed successfully!"
else
  echo "Backup failed. Please check for errors."
fi
```

Usage:

```bash
./backup_data.sh /path/to/source_directory /path/to/backup_destination
```

Example:

```bash
./backup_data.sh /home/user/documents /media/external_drive/backup
```

Now, you have a backup solution that can be scheduled to run daily using cron or any other scheduling tool. This way, even if you accidentally delete important files, you can recover them from the backup destination.

**Scenario 2: Checking Server Health - Alert System**

Problem: Suppose you run a small business website hosted on a remote server. You want to be alerted if the server's CPU usage goes above a certain threshold, indicating potential performance issues.

Solution: You can create a script named "server\_health\_check.sh" that takes the CPU threshold as a command-line argument. The script will periodically check the CPU usage, and if it exceeds the threshold, it will send an email notification.

server\_health\_check.sh:

```bash
#!/bin/bash

# Check if the correct number of arguments is provided
if [ $# -ne 1 ]; then
  echo "Usage: $0 <cpu_threshold>"
  exit 1
fi

cpu_threshold=$1

# Function to get CPU usage percentage
function get_cpu_usage() {
  top -bn1 | grep "Cpu(s)" | awk '{print $2 + $4}'
}

# Infinite loop for continuous monitoring
while true; do
  cpu_usage=$(get_cpu_usage)
  
  if (( $(echo "$cpu_usage > $cpu_threshold" | bc -l) )); then
    # Send email notification using 'mail' command (mail server setup required)
    echo "Alert: High CPU usage detected! Current CPU usage: $cpu_usage%" | mail -s "CPU Alert" admin@example.com
  fi

  # Wait for 1 minute before checking again
  sleep 60
done
```

Usage:

```bash
./server_health_check.sh 80
```

Example:

```bash
./server_health_check.sh 90
```

With this script, you can monitor the server's CPU usage in real-time. If the CPU usage goes above the specified threshold (e.g., 80% or 90%), an email notification will be sent to the admin, alerting them about the issue. This way, you can take necessary actions to address the performance problems and ensure the smooth running of your website.