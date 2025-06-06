# Unit 6 Worksheet

## Instructions

---

Fill out the worksheet as you progress through the lab and discussions.
Hold your worksheets until the end to turn them in as a final submission packet.

### Resources / Important Links

- [Official Firewalld Documentation](https://firewalld.org/documentation/)
- [RedHat Firewalld Documentation](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/configuring_firewalls_and_packet_filters/using-and-configuring-firewalld_firewall-packet-filters)
- [Official UFW Documentation](https://help.ubuntu.com/community/UFW)
- [Wikipedia entry for Next-Gen Firewalls](https://en.wikipedia.org/wiki/Next-generation_firewall)

#### Discussion Post #1

Scenario:
> A ticket has come in from an application team. Some of the servers your team built for them last week
> have not been reporting up to enterprise monitoring and they need it to be able to troubleshoot a current
> issue, but they have no data. You jump on the new servers and find that your engineer built everything
> correctly and the agents for node_exporter, ceph_exporter and logstash exporter that your teams use. But,
> they also have adhered to the new company standard of firewalld must be running. No one has documented the
> ports that need to be open, so you're stuck between the new standards and fixing this problem on live systems.

Next, answer these questions here:

1. As you're looking this up, what terms and concepts are new to you?
- Collectors
- High Cardinality
- Ceph Cluster
- Helm
- Grok

2. What are the ports that you need to expose? How did you find the answer?

Used google and got the following:
- node_exporter: 9100
- ceph_exporter: 9128
- logstash_exporter: 9198


3. What are you going to do to fix this on your firewall?

I would allow the ports through running the commands below and document
the changes (if there's a specific zone I'd add the `--zone <name>`):

```bash
firewall-cmd --add-port=9100/tcp
firewall-cmd --add-port=9128/tcp
firewall-cmd --add-port=9198/tcp
firewall-cmd --runtime-to-permanent
```

On a separate note, I also found these options for the service names versus the port:

```bash
firewall-cmd --add-service=prometheus-node-exporter
firewall-cmd --add-service=ceph-exporter
```


#### Discussion Post #2

Scenario:
> A manager heard you were the one that saved the new application by fixing the firewall. They get your manager
> to approach you with a request to review some documentation from a vendor that is pushing them hard to run a
> WAF in front of their web application. You are “the firewall” guy now, and they're asking you to give them a
> review of the differences between the firewalls you set up (which they think should be enough to protect them)
> and what a WAF is doing.

1. What do you know about the differences now?

To my understanding, firewalld and others like it work at layer 3 of the OSI model (network layer) filtering IP Addresses and Ports while WAFs work at layer 7 which allows you to filter at that level (although I'm not sure what that data is or would look like).

2. What are you going to do to figure out more?

For now I'll read up on articles like [Layer 3 vs. Layer 7 Firewalls](https://www.paloaltonetworks.com/cyberpedia/layer-3-vs-layer-7-firewall) to understand the differences. Also, I'll look into how I can set one of these up myself to test and get more of a practical usage and understanding.  I see that `OpenAppSec` can be installed with nginx may be something to look into as a homelab project [OpenAppSec](https://docs.openappsec.io/what-is-open-appsec).

3. Prepare a report for them comparing it to the firewall you did in the first discussion.

**Firewalld**  
It's a host-based firewall that filter's traffic originating from the server or destined for the server. It can filter traffic by IP Address, Port, Services, and interfaces but can't filter based on the specific layer 7 application data.

**WAF (Web Application Firewall)**  
Firewall that filters based on the data at the application layer. This would give us futher control to what we allow access to our hosted web applications. Typically we install this either on our web application servers or in front of them. We would want to implement one of these to better secure our web based applications that are being hosted.


## Definitions

---

Firewall  
 - A security system that monitors and controls incoming and outgoing traffic on a network/system based on configurable security rules.

Zone  
 - The trust level for a connection, interface or source address binding

Service  
 - An application running in the background that serves some type of functionality.

DMZ  
 - A subnetwork that separates an orgs internal network from untrusted external networks but provides access to certain services to users on the external network.

Proxy  
 - A server that sends traffic on behalf of another which provides some security benefits.

Stateful packet filtering  
 - Analysis of the state of a process/connection as well as it's context.

Stateless packet filtering  
 - Opposite of stateful, analysing the packet headers but doesn't keep track of the state or the history of the connection (context).

WAF  
 - Web Application Firewall that can monitor/filter http traffic between web applications and the internet.

NGFW  
 - Next-Generation Firewall are newer firewalls that do the functions of traditional firewalls but perform deeper inspection by doing things like checking packet payloads and matching signatures for harmful attacks/malware. NGFW include IPS and Application control which typical firewalls do not.

PKI  
 - Public Key Infrastructure.  It's a system that manages digital certificates and public-key encryption to secure and authenticate communications digitally. 

Zero Trust  
 - A security model that requires strict identity verification for every user and device attempting to access a resource regardless of whether they're inside or outside the network. "Never Trust, Always Verify".



## Digging Deeper

---

1. Read <https://docs.rockylinux.org/zh/guides/security/firewalld-beginners/>  
   What new things did you learn that you didn't learn in the lab?  
   What functionality of firewalld are you likely to use in your professional work?

## Reflection Questions

---

1. What questions do you still have about this week?
- Nothing at the moment.  Still processing a lot of the information.

2. How are you going to use what you've learned in your current role?
- Nothing at the moment, most of the systems I work with currently are windows systems. I do intend to setup a WAF in the homelab once I have more time to test how it works in application (instead of in theory).
