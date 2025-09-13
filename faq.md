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

```C
ss -tulnp | grep “port numner”
```
    
and then use `kill` command to kill or stop the process.

- **Answer 4.2:**

```C
netstat -tulnp | grep “port number”
```

and then use `kill` command to kill or stop the process.


**Question 5: How to identify the top 5 process names with high memory usage in a single command?**

- **Answer 5:**

```C
top -o %MEM | head -n 12
```

[Please don’t show 5 with head, because head -n 5 will only display top 5, which has usual information.](https://unix.stackexchange.com/questions/128953/how-to-display-top-results-sorted-by-memory-usage-in-real-time)


**Question 6: What is the difference between bare metal and hypervisor?**

- **Answer 6:** A bare metal server is a dedicated physical server owned and managed by a single user or entity, while a hypervisor is software that allows multiple virtual machines (VMs) to run on a single physical server.


**Question 7: What is the command to know the routing information in linux?**

- **Answer 7:**

```C
route
```

```C
netstat -r
```


**Question 8: A file is there and changes its output from new line to comma separated.**

```C
$ cat pass.txt
ubuntu
hello
buddy
world!!
two
three
four
```

- **Answer 8.1:**

```C
sed -z 's/\n/,/g' pass.txt
```

- **Answer 8.2:**

```C
echo pass.txt | tr “\n” “,”
```


**Question 9: What will be the output of this command?**

```C
$ iostat -x 5 10
```

- **Answer 9:**

```C
iostat -x 5 10
```

**What is iostat?**

[iostat is a Linux/Unix command-line utility](https://www.linkedin.com/pulse/interview-question-how-analyze-iostat-output-akshay-siwal-1pbtc/) that provides detailed statistics about CPU usage and input/output (I/O) performance of storage devices (disks, partitions, or logical volumes). It is part of the sysstat package and is widely used by system administrators and SREs to diagnose performance bottlenecks related to disk I/O and CPU utilization.

Let’s go through the full output of iostat step by step, explaining each section and metric in detail.
 
- x: Displays extended statistics for devices.
- 5: Interval in seconds between reports.
- 10: Number of reports (including the first one).


**Question 10: Your file system is corrupted, how will you check and recover it?**

- **Answer 10:** With the [`fsck`](https://phoenixnap.com/kb/fsck-command-linux) command, I will check and recover the file system.


**Question 11: How can I update the changes made in grub?**

- **Answer 11.1: For Debian OS**

```C
update-grub
```

- **Answer 11.2: For RHEL OS**

Or [update-grub](https://unix.stackexchange.com/questions/712643/how-can-i-make-grub-changes-permanent) is a Debianism and might not exist in Manjaro. Try `sudo grub-mkconfig -o /boot/grub/grub.cfg` or `sudo grub2-mkconfig -o /boot/grub/grub.cfg`


**Question 12: What is the difference between YUM and RPM?**

- **Answer 12:** RPM is a package format and management system for Linux, while YUM is a higher-level package manager built on top of RPM that simplifies package installation and updates. RPM handles the underlying packaging and verification, while YUM provides features like dependency resolution and repository management.


**Question 13: Use `for` loop to check if a list of servers is alive and print its uptime in the terminal?**

- **Answer 13:** Please find the below code with `for` loop in `bash`.

```C
#!/usr/bin/env bash
        
for ip in `cat iplist`;
do
ssh -i path_of_ssh_key "user@$ip" 'hostname; uptime'
echo "done"
done
```


**Question 14: Use `while` loop to check if a list of servers is alive and print its uptime in the terminal?**

- **Answer 14:** Please find the below code with `while` loop in `bash`.

```C
#!/usr/bin/env bash
        
while read ip
do
ssh -i path_of_ssh_key "user@$ip" 'hostname; uptime'
echo "done"
done < iplist
```


**Question 15: What is the difference bw sudo su and sudo su - or sudo -i**

- **Answer 15:** The primary difference between sudo su and sudo su - lies in how they handle the user's environment after switching to the root user. sudo su keeps you in your current directory and retains your environment variables, while sudo su - switches to the root user's home directory and sets the environment to the root user's default setup. In essence, sudo su - is equivalent to sudo -i


**Question 16: What is the default file system in RHEL 7?**

- **Answer 16:** The default file system in RHEL 7 is `xfs`.


**Question 17: What is the difference between init vs systemd service?**

- **Answer 17:** .


**Question 18: How to idedntify or found out the hard disk serial number from linux command**

- **Answer 18:** .


**Question 19: How to identify the `NIC` serial number from linux command?**

- **Answer 19:** .


**Question 20: What is the difference between problem management and incident management?**

- **Answer 20:** Incident management focuses on addressing immediate disruptions to IT services, aiming for quick resolution and service restoration within agreed-upon SLAs. Problem management, on the other hand, focuses on preventing future incidents by identifying and resolving the root causes of recurring issues, leading to long-term service improvements.


**Question 21: Write a bash program to know about the OS information.**

- **Answer 21:**

```C
#!/usr/bin/env bash

echo -e $(cat /etc/issue)
```


**Question 22: Write a `for` loop program to write down the number from 1 to 100.**

- **Answer 22:** Please find the below `bash` code.

```C
#!/usr/bin/env bash

for i in {1..100}
do
echo $i
done
```


**Question 23: #Write a Bash script that does the following:
    Accepts a directory path as an argument.
    Lists all files in that directory (not subdirectories) that are larger than 100 MB.
    For each such file, prints:
    The filename
    Its size in a human-readable format
    The output should be sorted by size in descending order.
    Bonus: Make sure the script gracefully handles the case where the directory doesn't exist.**

- **Answer 23:** Please find the below `bash` code.

```C
directory_name=$1

#find $1 -type f -size +100M -exec du -sh {} \; | sort -hr

#echo "$#"
if [ "$#" -eq 0 ]
then
        echo -e "\n\tPlease provide directory name as argument. Please see below line on how to use this command"
        echo -e "\tUsage: $0 Directory_Name\n"
else
#       find $1 -type f -size +100M -exec du -sh {} \; | sort -hr | awk BEGIN { print "File Size \t File Name \n -----------\t----------" }; '{print $1,$2}'
        find $1 -maxdepth 1 -type f -size +100M -exec du -sh {} \; | sort -hr | awk 'BEGIN {print "\nFile Name \t\t File Name\n------------\t\t------------";} {print $1"\t\t"$2} END {print "------------\t\t------------\n"}'
fi
```


**Question 24: What is hard link and soft link in Linux**

- **Answer 24:** In Linux, hard links and soft links (also known as symbolic links or symlinks) are two distinct ways to create references to files or directories within the file system.

- Hard Link:
  * A hard link is a direct pointer to the data on the disk, essentially another name for an existing file's inode. An inode is a data structure that stores information about a file, such as its permissions, ownership, and location of its data blocks.
  * Hard links share the same inode number as the original file.
  * Deleting the original file does not remove the data as long as at least one hard link to that inode still exists. The data is only freed when all hard links pointing to that inode are removed.
  * Hard links can only be created within the same file system.
  * They cannot be created for directories.

- Soft Link (Symbolic Link / Symlink):
  * A soft link is a special file that contains the path to another file or directory. It acts like a shortcut.
  * Soft links have their own unique inode number, distinct from the target file or directory.
  * If the original file or directory to which a soft link points is deleted or moved, the soft link will become "broken" or "dangling" as it no longer points to a valid target.
  * Soft links can span across different file systems.
  * They can be created for both files and directories.

Key Differences Summarized:

|Feature | Hard Link | Soft Link (Symbolic Link) |
| ------------------- | ------------------- | ------------------- |
|Reference | Direct to inode/data | Path to another file/directory |
|Inode | Same as original file | Unique inode |
|Deletion | Data persists until all links removed | Becomes broken if target removed |
|Filesystem | Cannot cross file systems | Can cross file systems |
|Target | Files only | Files and directories |


**Question 25: What is stateful and stateless?**

- **Answer 25:** 


**Question 26: What is `Security Group` in AWS**

- **Answer 26:** 


**Question 27: What is `NACL` in AWS**

- **Answer 27:** 


**Question 28: What is the difference between `NACL` and `Security Group`?**

- **Answer 28:** Security Group works on Instance level where NACL works on Subnet level.


**Question 29: What is stateful and stateless?**

- **Answer 29:** In AWS, stateful and stateless refer to how applications handle data between user sessions or requests. Stateful applications retain data from previous interactions, while stateless applications treat each interaction as independent, without retaining context from prior interactions.


----------------------------------------------------------
                                    Terraform Interview Questions 
----------------------------------------------------------


Having conducted many DevOps interviews, let me share what really matters when it comes to Terraform questions.

👉1) What happens if your state file is accidentally deleted?

- ✅Answer: Terraform loses track of managed infrastructure. On next apply, it attempts to recreate everything, causing duplicates or failures. Recovery requires manual imports or restoring backups. Always enable versioning on S3 state storage.

👉2) How do you handle large-scale refactoring without downtime?

- ✅Answer: Use "terraform state mv" to rename resources without destroying them. Control changes with targeted applies. Split refactoring into multiple non-destructive PRs and verify plans carefully to prevent resource destruction.

👉3) What happens if a resource fails halfway through a terraform apply?

- ✅Answer: Terraform creates a partial deployment with successful resources running but failed ones marked as tainted. Use targeted applies and "-refresh-only" to recover systematically.

👉4) How do you manage secrets in Terraform?

- ✅Answer: Use external secret stores (Vault, AWS Secrets Manager), ensure state encryption, mark outputs as sensitive, and integrate securely with CI/CD. For highly sensitive values, consider managing them outside Terraform completely.

👉5) What happens if terraform plan shows no changes but infrastructure was modified outside Terraform?

- ✅Answer: Terraform remains unaware until "terraform refresh" is run. Implement regular drift detection in your CI/CD process to catch unauthorized changes.

👉6) What happens if you delete a resource definition from your configuration?

- ✅Answer: Terraform destroys the corresponding infrastructure. Either use "terraform state rm" first or implement "lifecycle { prevent_destroy = true }" for critical resources.

👉 7) What happens if Terraform provider APIs change between versions?

- ✅Answer: Compatibility issues may arise. Always read release notes, use version constraints, test upgrades in lower environments, and consider targeted updates for gradual migration.

👉 8) How do you implement zero-downtime infrastructure updates?

- ✅Answer: Use "create_before_destroy" lifecycle blocks, blue-green deployments, health checks, and state manipulation for complex scenarios. For databases, use replicas or managed services with failover capabilities.

👉 9) What happens if you have circular dependencies in your Terraform modules?

- ✅Answer: Terraform fails with "dependency cycle" errors. Refactor module structure using data sources, outputs, or restructuring resources to establish clear dependency hierarchy.

👉 10) What happens if you rename a resource in your Terraform code?

- ✅Answer: Terraform sees this as destroying and recreating the resource. Use "terraform state mv" to update state while preserving infrastructure, avoiding rebuilds and downtime.


----------------------------------------------------------
                                    Cloud DevOps Interview Questions 
----------------------------------------------------------


PWC Interview experience for Senior DevOps Engineer role

Round 1: Screening Round (30 minutes)

- Walk me through your current project architecture and your role in it.
- Which DevOps tools have you worked with in the last 2 years?
- What AWS services have you used in production?
- Explain the difference between EC2 and ECS.
- How do you expose a Kubernetes application to external traffic?
- What is the purpose of a NAT Gateway?
- How do you check running processes in Linux?
- What command would you use to find files larger than 100MB?
- What is the difference between Deployment and StatefulSet in Kubernetes?
- How do you provide access to an S3 bucket from an EC2 instance?
- What is a ConfigMap and how is it different from a Secret?
- How do you check network connectivity between two servers?
- Describe your experience with CI/CD pipelines.
- What containerization technologies have you worked with?

Round 2: Technical Round (60 minutes)

- You have an application in Account A that needs to access an S3 bucket in Account B. How would you configure this?
- Write a Dockerfile for a Node.js application with multi-stage builds.
- How do you handle Terraform state file corruption?
- Your EC2 instance in a private subnet needs to download packages without NAT Gateway. What alternatives exist?
- How do you debug a container that has exited?
- You need to import an existing AWS VPC into Terraform. What are the steps?
- How would you implement blue-green deployment in Kubernetes?
- Write a shell script to check if a service is running and restart it if down.
- How do you manage secrets in Terraform without hardcoding them?
- What's the difference between COPY and ADD commands in Dockerfile?
- How would you implement cross-account resource provisioning using Terraform?
- How do you implement parallel job execution in Jenkins?
- How would you handle secrets in a Docker container for a PHP application connecting to MySQL?
- An S3 bucket was created via Terraform but someone manually added a policy. How do you handle this drift?
- How do you secure a Jenkins server in production?
Your application is hosted in S3 and users globally are experiencing high latency. How would you optimize this?
- How do you implement network policies to restrict pod-to-pod communication in Kubernetes?
- Write a Python script to backup all files older than 30 days from a directory.
- Your company's cloud costs are increasing rapidly. - How would you approach cost optimization without impacting performance?
- How would you set up geolocation-based routing using AWS services?
- What strategies do you use to manage Jenkins server space issues?

Deep Grilling Scenario: A critical production Kubernetes cluster is experiencing multiple issues. Pods are stuck in ImagePullBackOff, some pods are being evicted, and users are reporting 503 errors from the application.

- What would be your immediate first step to assess the situation?
- How would you troubleshoot the ImagePullBackOff issue?
- What commands would you run to investigate the pod evictions?
- How would you identify which pods are causing the 503 errors?
- What long-term measures would you implement to prevent this situation?

Round 3: Behavioral Round

- Describe a time when you had to troubleshoot a critical production issue. What was your approach?
- Tell me about a situation where you disagreed with a fellow engineer on a technical decision.
- How do you handle a situation where you're asked to work on a technology you have no experience with?
- Describe a time when you had to work with tight deadlines and limited resources.
- Tell me about a mistake you made in production and how you handled it.
- How do you ensure smooth collaboration when working with development teams?
- Describe the most challenging technical problem you've solved in your career.
- How would you convince stakeholders to adopt a new technology or process?
- Tell me about a time when you had to learn a new tool quickly to solve a business problem.
