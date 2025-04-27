# Unit 2 Worksheet

## Instructions

---

Fill out the worksheet as you progress through the lab and discussions.
Hold your worksheets until the end to turn them in as a final submission packet.

### Resources / Important Links

- [Bash Reference Manual](https://www.gnu.org/software/bash/manual/bash.html)
- [Security Enhanced Linux](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/using_selinux/getting-started-with-selinux_using-selinux#getting-started-with-selinux_using-selinux)

#### Unit 2 Discussion Post #1

Think about how week 1 went for you.

1. Do you understand everything that needs to be done?
- Not in time, no. But I'm working on catching up. I'm a bit of a slow learner and have greatly underestimated the time it takes me to try and process the information.

2. Do you need to allocate more time to the course, and if so, how do you plan to do it?
- I've been running behind on the course already, so I definitely need to allocate more time.  I plan on allocating 1-2hrs a day after work with the main goal being finishing the course work and then diving deeper if I accomplish the tasks before the end of the week.  My biggest problem is spending hours in a rabbit hole and not finishing or focusing on the course work in time.

3. How well did you take notes during the lecture? Do you need to improve this?
- When in any live lecture I tend to struggle with taking notes. I don't know what's important enough to write down and what to leave out so I end up trying to write every little thing down. I consider this to be a problem because this leads me to lose the forest for the trees. I think what I'm going to do moving forward is just take notes on key phrases that I've never heard before that I can look up later this way I'm not too bogged down and can listen/process the information in real time better.

#### Unit 2 Discussion Post #2

Read a blog, check a search engine, or ask an AI about SELinux.  
What is the significance of contexts? What are the significance of labels?
- SELinux checks the context of a subject (process or application) or object (file) and determines whether or not something has permissions to access.
- SELinux uses a labeling system. All files, processes, ports in a system will have an SELinux label associated with them. The label contains the user, role, type, and level. It uses this info when making decisions to allow/deny access to objects. I specifically read about the "type" portion of the label where it enforces policies based on type (aka Type Enforcement).


Scenario:

> You follow your company instructions to add a new user to a set of 10 Linux
> servers. They cannot access just one of the servers.
> 
> When you review the differences in the servers you see that the server they
> cannot access is running SELINUX. On checking other users have no problem
> getting into the system.
> 
> You find nothing in the documentation (typical) about this different system or
> how these users are accessing it.


What do you do? Where do you check?  
```text
1. Check to see if/how selinux is configured by running command:

grep -i ^selinux /etc/selinux/config

2. If SELinux is running in "enforced" mode, I would then check the logs
   to see if I can see a "deny" message when attempting to login:

grep -i avc /var/log/messages
grep -i avc /var/log/audit/audit.log

3. I would check user mappings too and compare the settings for the
   users that do work against the user that does not.

semanage login -l

4. If everything is fine regarding selinux, I'd check to make sure the 
   user itself was created properly.
```


You may use any online resources to help you answer this. This is not a trick
and it is not a “one answer solution”. This is for you to think through.

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

Uptime  
- A measurement of a systems reliability. Defines the period of time a machine has been working and available.

Standard input (stdin)  
- Stdin is the data that comes into the command.

Standard output (stdout)  
- Stdout is the output of the command.

Standard error (stderr)  
- Stderr is any errors that come out from the command.

Mandatory Access Control (MAC)  
- Security policy where access to objects are restricted based on the identity of the subject and it's defined attributes.

Discretionary Access Control (DAC)  
- Security policy where access to objects are restricted based on the subject's identity or group. This is more flexible then MACs.

Security contexts (SELinux)  
- Users, files, processes, and applications have additional information that allow SELinux to make access control decisions. These are known as Security Contexts. The information are user, role, type, and level.

SELinux operating modes  
- SELinux has to modes when enabled: permissive, enforcing. When in permissive mode the policies won't be enforced and will only log avc messages. When set to enforcing, it will both enforce the policies and log the messages.

## Digging Deeper

---

1. How does troubleshooting differ between system administration and system
   engineering? To clarify, how might you troubleshoot differently if you know a
   system was previously running correctly. If you’re building a new system out?

2. Investigate a troubleshooting methodology, by either Google or AI search.
   Does the methodology fit for you in an IT sense, why or why not?

[Troubleshooting Methods](https://www.learnleansigma.com/problem-solving/5-problem-solving-methods/)

## Reflection Questions

---

1. What questions do you still have about this week?
- I'm still wrapping my head around SELinux and labels and contexts. I want to make/do a lab where I play around with setting permissions for a user and trigger deny's to see the messages in logs.

2. How are you going to use what you’ve learned in your current role?
- I've never really had a structured way of trying to troubleshoot something. I just intuitively try to solve a problem based on what I know and trying to figure out what I don't know. But I'm going to actively try to apply one of the methodologies for troubleshooting over time and see which one works best for me. I like the idea of having an outlined repeatable method of doing things, especially troubleshooting.
