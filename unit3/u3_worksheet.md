# Unit 3 Worksheet

## Instructions

---

Fill out the worksheet as you progress through the lab and discussions.
Hold your worksheets until the end to turn them in as a final submission packet.

### Resources / Important Links

- [Google SRE Book - Implementing SLOs](https://sre.google/workbook/implementing-slos/)
- [AWS High Availability Architecture Guide](https://docs.aws.amazon.com/pdfs/whitepapers/latest/real-time-communication-on-aws/real-time-communication-on-aws.pdf)
- [Red Hat High Availability Cluster Configuration](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html/configuring_and_managing_high_availability_clusters/index)

#### Discussion Post #1

Scan the chapter [here](https://google.github.io/building-secure-and-reliable-systems/raw/ch17.html) for keywords and pull out what you think will help you to better understand how to triage an incident.

Read the section called "Operation Security" in this same chapter: [Building Secure and Reliable Systems](https://google.github.io/building-secure-and-reliable-systems/raw/ch17.html)

1. What important concepts do you learn about how we behave during an
   operational response to an incident?

```text
Keywords:

* OODA Loop
* Playbook-Driven Approach
* Crisis Managemeent Approach
* Incident Commander (IC)
* Incident Response (IR)

I've learned the importance of having a predetermined plan/processes
that revolve around:

a.) Handling Data
      * Planning ahead for how to handle access to data and the machines
        without providing the attacker additional leverage.
      * Ensure that your machines have remote agents or key-based access
        methods configured which will allow you to collect evidence
        without revealing login secrets.

b.) Communication
      * Clearly communicate confidentiality rules to all relevant
        parties.
      * Conduct meetings and discussions in person where possible.

The breadth of information regarding things to think about both
before an incident occurs and when an incident occurs is helpful.
A lot to think about.
```


#### Discussion Post #2

Ask Google, find a blog, or ask an AI about high availability. (Here's one if you need it: [AWS Real-Time Communication Whitepaper](https://docs.aws.amazon.com/pdfs/whitepapers/latest/real-time-communication-on-aws/real-time-communication-on-aws.pdf#high-availability-and-scalability-on-aws)

1. What are some important terms you read about? Why do you think understanding
   HA will help you better in the context of triaging incidents?

```text
Important Terms:

* Redundancy
* Load Balancing
* Uptime
* Downtime
* Disaster Recovery
* Monitoring/Alerting
* Scalability


Defining and engineering processes in place, having HA in mind, will
better help not only in triaging/responding to incedents, but be
resilient when they occur as well. It just makes things easier to
handle.

The scenarios presented in the article "Building Secure and Reliable
Systems" put it into persepctive for me:

"Organization 1 has a mature security process and layered defenses, 
including a restriction that permits only cryptographically signed 
and approved software to execute. In this environment, it's highly 
unlikely that well-known ransomware can infect a machine or spread 
throughout the network. If it does, the detection system raises an 
alert, and someone investigates. Because of the mature processes 
and layered defenses, a single engineer can handle the issue: they 
can check to make sure no suspicious activity has occurred beyond 
the attempted malware execution, and resolve the issue using a 
standard process. This scenario doesn't require a crisis-style 
incident response effort."

vs

"Organization 3 has fewer layered defenses and limited visibility 
into whether its systems are compromised. The organization is at 
much greater risk of the ransomware spreading across its network and 
may not be able to respond quickly. In this case, a large number of 
business-critical systems may be affected if the worm spreads, and the 
organization will be severely impacted, requiring significant technical 
resources to rebuild the compromised networks and systems. This worm 
presents a serious risk for Organization 3."
```

## Definitions

---

Five 9's  
- 99.999% availability, around 5 minutes of downtime per year.

Single Point of Failure (SPOF)  
- A part of a system that would stop an entire system from working if it were to fail.

Key Performance Indicators (KPIs)  
- A collection of quantifiable measurments that assess the performance of a company, project, or activity.

Service Level Indicator (SLI)  
- A quantitative measure of some aspect of the level of service provided. Examples of SLI's are availability, error rate, system throughput, etc.

Service Level Objective (SLO)  
- A target value or range of values for the SLI. For example, you want the average latency for an https request to be handled in under 100 milliseconds.

Service Level Agreement (SLA)  
- An explicit or implicit contract with users that includes consequences of meeting/missing SLO's.

Active-Standby  
- Standby system only activates if the active system goes down. I think of the term "failover".

Active-Active  
- Systems process parallel to each other. I think of the term "load-balancing".

Mean Time to Detect (MTTD)  
- An example of a KPI that refers to the time it takes for an org to discover/detect an incident.

Mean Time to Recover/Restore (MTTR)  
- An example of a KPI that refers to the time it takes for an org to repair/restore a system once a failure is discovered.

Mean Time Between Failures (MTBF)  
- An example of a KPI that refers to the average time that happens between failures of something that can be repaired.

## Digging Deeper

---

1. If uptime is so important to us, why is it so important to us to also understand how our systems can fail? Why would we focus on the thing that does not drive uptime?
- If we understand how our systems can fail we can put systems in place to mitigate these failures and improve the availability of the services our systems provide.

2. Start reading about SLOs: [Implementing SLOs](https://sre.google/workbook/implementing-slos/)
   How does this help you operationally?
   Does it make sense that keeping systems within defined parameters will help keep
   them operating longer?
- Having SLO's gives an engineer a better idea of where to spend engineering their time. It does make sense that keeping systems within defined parameters will help keep the system operation because a failing system often times has indicators that it's failing before it fails. The more you monitor SLO's of a system the better/faster you can detect problems on the system.

## Reflection Questions

---

1. What questions do you still have about this week?
- None at the moment. It's more of processing the information that was provided in this weeks lesson.

2. How are you going to use what you've learned in your current role?
- I want to take the time and think about all the services that the current org I work at provides. Then I want to think about the SLI's and SLO's that I can make for each one of those services. Then I can possibly build systems to monitor and mitigate the failing of those systems (I may not have the power to actually implement, but I think it would be good practice to outline nonetheless).
