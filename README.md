# K8s-Runtime-Security


Learning Objectives 

🔎 Understand Kubernetes Auditing and how it can be used to trace and troubleshoot security events

🔎 Understand the various problems and solutions surrounding runtime security in Kubernetes

🔎 Understand Falco, how it works and how it can be used in a Kubernetes cluster for real-time threat detection

🔎 Understand the importance of end-to-end monitoring and how other tools can work along with Falco to achieve this


<h3>1.Kubernetes Auditing</h3>

Task 1:In which request stage will the response headers have been sent out but not the response body?
ResponseStarted: This is when the response headers have been sent out, but the response body hasn't. This stage will only be present for long-running requests such as “wait” (a Kubernetes command you can use to wait for a condition to be met, such as the running status of a resource).

Task 2:Which level will capture the most data?
RequestResponse - This tells Kubernetes to log the request metadata, request body and response body.

Task 3:What field must be contained in an audit policy for it to be valid?
rule field must be contained in an audit policy for it to be valid

Task 4:At what level is it recommended to log sensitive resources (like secrets)? 
For sensitive resources (anything containing security-sensitive information, such as secrets or config maps), log only at the Metadata level; otherwise, the sensitive information will be included in the audit log.


<h3>2.Runtime Security & K8s</h3>

Task 1:What percentage of containers live less than 5 minutes in 2024 according to the annual report provided in this task?
When check by annual report below, the answer will be: 70

![image](https://github.com/user-attachments/assets/cfa2fb76-c362-4470-a402-188f1c9f5e62)

Task 2:What security concept, covered in this task, is a communication that takes place between a running process and the kernel?
System calls are an important security concept to understand, especially in the context of runtime security. System calls (or syscalls) are communication that takes place between a running process (in the user space) and the kernel (in the OS).

Task 3:Which security runtime enforcement tool works by filtering system calls, only allowing processed to perform certain calls to already open file descriptors?
eccomp (standing for secure computing mode) is an enforcement tool that operates at the kernel level. It works by filtering system calls, only allowing processed to perform certain calls (exit(), sigreturn(), read() and write()) to already open file descriptors (a process unique identifier for a file or other input/output resource)


<h3>3.Falco</h3>

Task 1:Falco can gain deep visibility into a Kubernetes runtime environment by analysing events from various sources. Which source (covered in a previous task) is available in Kubernetes?
It offers us audit logs via Kubernetes Auditing, which allows us to track resource requests in our cluster. However, it does nothing with this information. No analysis is done, and no alerting is in place.

Task 2:What allows user programs to run securely in a protected environment within the kernel space?
eBPF is yet another hero coming to the rescue of engineers in pursuit of securing their environments. It solves this problem by allowing programs to run in a protected environment within the kernel space, which ensures the code is safe to run before being executed

Task 3:Enriched events are compared against _____, which can either be included by default or user-defined. 
The answer will be a rules.


<h3>4.Falco in Action</h3>

Task 1:When defining a Falco rule condition, what snippet could be used to match bash processes?
```
condition: >
    spawned_process and 
    container and 
    proc.name = bash 
``` 
The answewr is: proc.name = bash 

Task 2:What can be used to reference a collection of items in a condition?


Task 3:What can be used to abbreviate conditions which are frequently used? 
Macros are used in Falco rule definition as a way to abbreviate conditions that are used frequently across multiple rules; this saves time, meaning a condition that is used repeatedly doesn't have to be typed out every single time. 


<h3>5.Event Monitoring</h3>

Task 1:Which tool covered in this task can be used as a visualisation layer and allows collected data to be visualised as charts and graphs?
Grafana is an interactive data visualisation platform which was developed by Grafana Labs

Task 2:Which tool covered in this task collects and stores time series data?
Prometheus is an open-source systems monitoring and alerting tool, it was first built in 2012 at SoundCloud. It is now a stand-alone, open-source project attached to no company and is also part of CNCF

Task 3:Which tool covered in this task is a companion project that can act as a forwarder for Falco?
Falcosidekick isn't another tool entirely but a companion project to Falco that can be enabled during/after configuration. Its primary function addresses an issue users were running into when using Falco.


<h3>6.Practical</h3>
