# Unit 4 Worksheet

## Instructions

---

Fill out the worksheet as you progress through the lab and discussions.
Hold your worksheets until the end to turn them in as a final submission packet.

### Resources / Important Links

- [Operations Bridge](https://cio-wiki.org/wiki/Operations_Bridge)
- [Security Incident Cheatsheet](https://zeltser.com/media/docs/security-incident-survey-cheat-sheet.pdf?msc=Cheat+Sheet+Blog)
- [Battle Drills](https://en.wikipedia.org/wiki/Battle_drill)

#### Discussion Post #1

Read this article: <https://cio-wiki.org/wiki/Operations_Bridge>

1. What terms and concepts are new to you?
- I've never heard of the term operations bridge until now although I think I've seen/heard of tools that can help create your own like Grafana, Cloudwatch, etc.

2. Which pro seems the most important to you? Why?
- The pro that I find most important is the proactive monitoring and incident detection. In my head, this is similar to keeping up with routine maintenance on your vehicle like oil changes. If you do it, the less headaches and disasters you have down the road. Proactively monitoring your systems and detecting incidents will help you keep your systems up and running like clockwork.

3. Which con seems the most costly, or difficult to overcome to you? Why?
- At the moment, I think the initial setup and configuration would be the most difficult to overcome. I haven't setup one of these systems myself so I'd imagine there being a learning curve.

#### Discussion Post #2

Scenario:
> Your team has no documentation around how to check out a server during an incident.
> Write out a procedure of what you think an operations person should be doing on the
> system they suspect is not working properly.

```text
Generally I would start with documenting the incident itself with as
much detail as possible, asking myself questions like:

* What exactly happened or what was noticed about the incident? Any 
  specific error messages? What time/date was the specific incident 
  noticed?

From there I would start checking for anything I can related to the
incident itself starting with the system logs and work my way through
checking system specific things by running relevant commands. For
example, if a specific service was hosted on a windows server is no
longer accessible I would:

1. Check that the service is running by running the command
   "task list /svc | findstr <NameOfService>".

2. Copy and paste the command with the output in the documentation.

3. Check EventViewer for any logs related to the service and note the
   error message if any as well as the date/time stopped. 

4. Right-Click and Copy the event details as text and copy it to the
   documentation for reference.

5. Continue with the investigation following the same format of checking
   system settings and documenting your findings.

6. If needed escalate the issue. If it's a security incident, notify
   your manager or team lead in person, if possible, or through a medium 
   that wouldn't be compromised if in person is not possible.
```


This may help, to get you started <https://zeltser.com/media/docs/security-incident-survey-cheat-sheet.pdf?msc=Cheat+Sheet+Blog>
You may use AI for this, but let us know if you do.

## Definitions

---

Detection  
- The process of identifying potential unauthorized or malicious activity occurring on a fleet of systems or network.

Response  
- Actions taken after a security incident (or percieved incident) has been detected. 

Mitigation  
- Actions taken to minimize the risk or impact of a security incident.

Reporting  
- The process of documenting and relaying information about a security incident.

Recovery  
- Restoring systems to their original state.

Remediation  
- Fixing the root cause of the problem so that the incident or issue doesn't happen again.

Lessons Learned  
- The information you've learned during and after an incident.

After Action Review  
- Structured process to analyze and learn from a security incident.

Operations Bridge  
- A system/software that actively monitors system information in real time.

## Digging Deeper

---

1. Read about battle drills here <https://en.wikipedia.org/wiki/Battle_drill>

2. Why might it be important to practice incident handling before an incident occurs?

3. Why might it be important to understand your tools before an incident occurs?

## Reflection Questions

---

1. What questions do you still have about this week?
- What does an actual plan look like? I'm curious to see an org that not only has an incident response plan but actually has a normal routine for practicing it.

2. How much better has your note taken gotten since you started?
   What do you still need to work on? Have you started using a different tool?
   Have you taken more notes?
- It's going pretty well. I keep notes on keywords that I don't know about in the live sessions and then I look them up after when I have time. I have taken more notes.
