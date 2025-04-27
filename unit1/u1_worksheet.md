# Unit 1 Worksheet

## Instructions

---

Fill out the worksheet as you progress through the lab and discussions.
Hold your worksheets until the end to turn them in as a final submission packet.

### Resources / Important Links

- [What is Vim?](https://github.com/vim/vim)
- [The Linux Foundation](https://www.linux.org/pages/download/)
- [Linux CLI Cheatsheets](https://www.digitalocean.com/community/tutorials/linux-commands)

#### Discussion Post #1

Using a 0-10 system, rate yourself on how well you think you know each topic in the table below. (You do not have to post this rating).

|   Skill    | High (8-10) | Mid (4-7) | Low (0-3) | Total |
| :--------: | :---------: | :-------: | :-------: | :---: |
|   Linux    |             |           |     3     |   3   |
|  Storage   |             |           |     3     |   3   |
|  Security  |             |           |     3     |   3   |
| Networking |             |     4     |           |   4   |
|    Git     |             |           |     3     |   3   |
| Automation |             |           |     2     |   2   |
| Monitoring |             |           |     2     |   2   |
|  Database  |             |     4     |           |   4   |
|   Cloud    |             |     4     |           |   4   |
| Kubernetes |             |           |     0     |   0   |
|   Total    |             |           |           |   28  |


Next, answer these questions here:

1. What do you hope to learn in this course?
 - I hope to learn enough fundamental skills that would help me get a job in the field. I also hope to learn some of the other fields that exists out there that I may not be aware of.

2. What type of career path are you shooting for?
 - Platform Engineer because Scott said I can watch netflix while doing the job (joking). On a serious note, getting good at building systems that others use sounds rewarding and it seems like in that position you get to learn/know about how many things work at the foundational level.

#### Discussion Post #2

1. Post a job that you are interested in from a local job website. (link or image)
 - https://www.indeed.com/jobs?q=platform+engineer&latLong=28.30468%2C-81.41667&locString=Kissimmee%2C+FL%2C+34744&radius=25&start=10&vjk=bd3f58e78acd124a

2. What do you know how to do in the posting?
 - Nothing.  But I see I'm actively working on some of the items listed.

3. What don't you know how to do in the posting?

    - Kubernetes & Rancher
    - VMWare
    - DevSecOps & Automation
    - Programming (Powershell, Python, Ruby)
    - Git
    - CI/CD (Azure DevOps, Jenkins, Harness)
    - Cloud (AWS)
    - SQL & Oracle Technologies
    - Redhat Openshift
    - Terraform/Atlantis
    - AWS Cloud (Fargate, ECS, Lambdas, ApiGateways, EC2, S3, ALB/ELB, Elasticache, EKS, KMS-Secret Manager, VPCs, IAM)
    - Logging/Monitoring/Alerting (Cloudwatch/Splunk/AppDynamics/Elasticache/Grafana)
    - Rundeck, Chef, Ansible, Vault, AWX, Azure DevOps
    - MessageQueueing: RabbitMQ, PubSub
    - OpenShift, Kubernetes
    - Load balancers, Akamai
    - Languages: Go/Python/ Node.js (Angular.js framework)/Java (Spring MVC)

4. What are you doing to close the gap? What can you do to remedy the difference?

To close the gap, I'm currently:
* Taking this linux administration course.
* Taking the security engineering course.
* Started learning some python and git to upload scripts to github

### Start thinking about your project ideas (more to come in future weeks):

Topics:

1. System Stability
2. System Performance
3. System Security
4. System monitoring
5. Kubernetes
6. Programming/Automation

You will research, design, deploy, and document a system that improves your administration of Linux systems in some way.

## Definitions

---

Kernel:
 - The program on a computer that has complete control over the system.  It's the middleman between applications/software you run on the system and the hardware resources like memory, cpu, and peripherals.

Kernel Args:
 - Parameters that you can pass to modify kernel behavior.

OS Version:
 - Version of the installed system software.  Each OS has it's own way of releasing updates and naming convention that can be looked up.

Modules:
 - Kernel Modules are pieces of code that can be loaded and used that extend the functionality of the kernel.  Typically modules that are created revolve around device drivers, file system drivers, and system calls.

Mount Points:
 - A directory in linux that storage devices and file systems get attached.

Text Editor:
 - Program that can edit plan text files.


## Digging Deeper

---

1. Use vimtutor and see how far you get. What did you learn that you did not know about vi/vim?

I finished Lesson 7.  
- I did not know that I can press "A" to start modifying at the end of a line.  I only knew about "i" and "a".  
- I did not know that I can delete a character using "x".  I only knew about pressing "d" and then a direction.  
- I did not think to use "d$" to delete to end of line.  
- I did not think to use "dw" to delete an entire word.  
- "e" means to the end of the current word including the last character.  
- I knew I can use "u" to undo but I didn't know about "U" or "ctrl-r"  
- There's a difference between yanking with "y" and pasting with "p" than to use "dd" and then type "p" to paste.  For one it's called "put" and it inserts what you deleted in the vim register and when you use it puts the line below where the cursor is currently at.  
- I can use "ce" to edit to the end of a word.  "cc" change entire line.  
- "ctrl-G" gives me line number and file name, then I can type "number-G" to go back to that line number  
- In normal mode I can type ":help [command]" and it'll open the help file where the command is referenced.  
- Use "?" instead of "/" to search in reverse  
- "ctrl-o" goes back to where your cursor was previosly while "ctrl-i" goes forward  
- Substitute Command:  
  - `":s/old/new"` - changes the first instance of "new" to "old"  
  - `":s/old/new/g"` - changes all instances of "new" to "old" on the current line  
  - `":1,4s/old/new/g"` - changes all instances of "new" to "old" on line number 1-4  
  - `":%s/old/new/g"` - changes all instances of "new" to "old" in the entire file  
  - `":%s/old/new/gc"` - changes all instances of "new to "old" in the entire file but asks you first for each instance  

2. Go to <https://vim-adventures.com/> and see how far you get. What did you learn that you did not already know about vi/vim?

I got to level 3.  But I got bored.  I prefer actually just typing and editing files.

3. Go to <https://www.youtube.com/watch?v=d8XtNXutVto> and see how far you get with vim. What did you learn that you did not already know about vi/vim?

## Reflection Questions

---

1. What questions do you still have about this week?
 - I have a lot to learn.  How long would it take me to be decent at all the different technologies?

2. How are you going to use what you’ve learned in your current role?
 - I will practice using vim to write documentation and notes. 
