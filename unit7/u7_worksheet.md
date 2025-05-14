# Unit 7 Worksheet

## Instructions

---

Fill out the worksheet as you progress through the lab and discussions.
Hold your worksheets until the end to turn them in as a final submission packet.

### Resources / Important Links

- [Semantic Versioning](https://semver.org/)
- [Rocky Documentation](https://docs.rockylinux.org/)
- [Rocky DNF Guidance](https://docs.rockylinux.org/guides/package_management/dnf_package_manager/)

#### Discussion Post #1

1. Why is software versioning so important to software security?

When vulnerabilities are found, it's one of the ways to specify what version of the software had it and what version patched the vulnerability.

2. Can you find 3 reasons, from the internet, AI, or your peers?
 * Allows vulnerability scanners to detect insecure versions.
 * Allows secure rollback to a known-good version before a vulnerability or flaw was introduced.
 * Allows specific versions to be tested or analyzed for forensic purposes.


#### Discussion Post #2

Scenario:
> You are new to a Linux team. A ticket has come in from an application team and has
> already been escalated to your manager.
> 
> They want software installed on one of their servers but you cannot find any
> documentation. Your security team is out to lunch and not responding.
> 
> You remember from some early documentation that you read that all the software in the
> internal repos you currently have are approved for deployment on servers.
> You want to also verify by checking other servers that this software exists.
> 
> This is an urgent task and your manager is hovering.

1. How can you check all the repos on your system to see which are active?
```bash
dnf reposlist enabled
```
2. How would you check another server to see if the software was installed there?
I would ssh into the server and then check if the software installed by running the following command:

```bash
rpm -qa <package name>
```

Example:
```bash
rpm -qa openssh
```

3. If you find the software, how might you figure out when it was installed? (Time/Date)
I would run the following command:

```bash
rpm -qi <package name>
```

Example:
```bash
rpm -qi openssh
```



#### Discussion Post #3

Scenario:
> Looking at the concept of group install from DNF or Yum.
> Why do you think an administrator may never want to use that in a running system?
> Why might an engineer want to or not want to use that?
> This is a thought exercise, so it’s not a “right or wrong” answer it’s for you to think about.

1. What is the concept of software bloat, and how do you think it relates?

I think of software bloat as software installed in a system that aren't used or don't need to be on a system that are. An engineer may forgo "group install" in order to be more meticulous and only install packages that absolutely need to exist on the system.

2. What is the concept of a security baseline, and how do you think it relates?

I think of security baseline as a template of standards that every server adhere's to. As part of the security baseline, you may have a set of packages on specific versions installed on all servers and avoid software bloat on principle.

3. How do you think something like this affects performance baselines?

It helps establish a consistent trend amongst the servers you administer. If something deviates, it's a lot easier to tell if all servers are running the same packages/software. 


## Definitions

---

Yum:

DNF:

Repo:

GPG Key:

Software dependency:

Software version:

Semantic Version:

## Digging Deeper

---

1.  What is semantic versioning? <https://semver.org/>

## Reflection Questions

---

1. What questions do you still have about this week?

2. How does security as a system administrator differ from what you expected?
