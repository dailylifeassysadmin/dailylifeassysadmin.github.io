# Interview Question - Linux Administrator and Cloud Engineer

**Question 1: Tell me about your day to day activity?**

- **Answer 1:** My day to day activity involves managing Linux systems, ensuring stability, security, and optimal performance. This includes tasks like user management, software installation and updates, system monitoring, security audits, and troubleshooting.


**Question 2: Write a shell script which will show 1 to 9 numbers except 6.**

- **Answer 2:**
```C
for i in {1..9}; do if (($i != 6)); then echo $i; fi; done;
```


**Question 3: Name of the DNS package?**

- **Answer 3:** The name of the DNS package is called bind-utils in debian OS and bind9 in RHEL.


**Question 4: Tell me how can I identify the process name from port number and then kill that process?**

- **Answer 4.1:**

    ss -tulnp | grep “port numner”
    
and then use `kill` command to kill or stop the process.

- **Answer 4.2:**

    netstat -tulnp | grep “port number”

and then use `kill` command to kill or stop the process.


**Question 5: How to identify the top 5 process names with high memory usage in a single command?**

- **Answer 5:**

    top -o %MEM | head -n 12

[Please don’t show 5 with head, because head -n 5 will only display top 5, which has usual information.](https://unix.stackexchange.com/questions/128953/how-to-display-top-results-sorted-by-memory-usage-in-real-time)


**Question 6: What is the difference between bare metal and hypervisor?**

- **Answer 6:** A bare metal server is a dedicated physical server owned and managed by a single user or entity, while a hypervisor is software that allows multiple virtual machines (VMs) to run on a single physical server.


**Question 7: What is the command to know the routing information in linux?**

- **Answer 7:**

    route
    netstat -r


**Question 8: A file is there and changes its output from new line to comma separated.**

    $ cat pass.txt
    ubuntu
    hello
    buddy
    world!!
    two
    three
    four

- **Answer 8.1:**

      sed -z 's/\n/,/g' pass.txt

- **Answer 8.2:**

      echo pass.txt | tr “\n” “,”


**Question 9: What will be the output of this command?**

    $ iostat -x 5 10

**Answer 9:**

    iostat -x 5 10

**What is iostat?**

[iostat is a Linux/Unix command-line utility](https://www.linkedin.com/pulse/interview-question-how-analyze-iostat-output-akshay-siwal-1pbtc/) that provides detailed statistics about CPU usage and input/output (I/O) performance of storage devices (disks, partitions, or logical volumes). It is part of the sysstat package and is widely used by system administrators and SREs to diagnose performance bottlenecks related to disk I/O and CPU utilization.

Let’s go through the full output of iostat step by step, explaining each section and metric in detail.
 
- x: Displays extended statistics for devices.
- 5: Interval in seconds between reports.
- 10: Number of reports (including the first one).


**Question 10: Your file system is corrupted, how will you check and recover it?**

**Answer 10:** With the [`fsck`](https://phoenixnap.com/kb/fsck-command-linux) command, I will check and recover the file system.


**Question 11: How can I update the changes made in grub?**

**Answer 11.1: For Debian OS**

    update-grub

**Answer 11.2: For RHEL OS**

Or [update-grub](https://unix.stackexchange.com/questions/712643/how-can-i-make-grub-changes-permanent) is a Debianism and might not exist in Manjaro. Try `sudo grub-mkconfig -o /boot/grub/grub.cfg` or `sudo grub2-mkconfig -o /boot/grub/grub.cfg`


**Question 12: What is the difference between YUM and RPM?**

**Answer 12:**RPM is a package format and management system for Linux, while YUM is a higher-level package manager built on top of RPM that simplifies package installation and updates. RPM handles the underlying packaging and verification, while YUM provides features like dependency resolution and repository management.


**Question 12: What is the difference between YUM and RPM?**

**Answer 12:**RPM is a package format and management system for Linux, while YUM is a higher-level package manager built on top of RPM that simplifies package installation and updates. RPM handles the underlying packaging and verification, while YUM provides features like dependency resolution and repository management.


**Question 12: What is the difference between YUM and RPM?**

**Answer 12:**RPM is a package format and management system for Linux, while YUM is a higher-level package manager built on top of RPM that simplifies package installation and updates. RPM handles the underlying packaging and verification, while YUM provides features like dependency resolution and repository management.


**Question 12: What is the difference between YUM and RPM?**

**Answer 12:**RPM is a package format and management system for Linux, while YUM is a higher-level package manager built on top of RPM that simplifies package installation and updates. RPM handles the underlying packaging and verification, while YUM provides features like dependency resolution and repository management.


**Question 12: What is the difference between YUM and RPM?**

**Answer 12:**RPM is a package format and management system for Linux, while YUM is a higher-level package manager built on top of RPM that simplifies package installation and updates. RPM handles the underlying packaging and verification, while YUM provides features like dependency resolution and repository management.
