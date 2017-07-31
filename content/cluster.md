---
title: "What is a cluster"
menu: main
weight: 2
---

The words "cloud", "cluster", and "high-performance computing" get thrown around a lot.
So what do they mean exactly?
And more importantly, how do we use them for our work?

The "cloud" is a generic term commonly used to refer to remote computing resources.
Cloud can refer to webservers, remote storage, API endpoints, and as well as more traditional "raw compute" resources. 
A cluster on the other hand, is a term used to describe a network of compters.
Machines in a cluster typically share a common purpose, 
and are used to accomplish tasks that might otherwise be too substantial for any one machine. 

![The cloud is made of Linux](../linux-cloud.jpg)

## High performance computing

A high-performance computing cluster is a set of machines that have been 
designed to handle tasks that normal computers can't handle.
This doesn't always mean simply having super fast processors. 
High-performance computing covers a lot of use cases.
Here are a couple of use cases where high-performance computing becomes extremely useful:

* You need access to large numbers of CPUs.
* You need to run a large number of jobs.
* Your jobs are running out of memory.
* Perhaps you need to store tons and tons of data.
* You require an exceptionally high-bandwidth internet connection for data transfer.
* You need a safe archival site for your data.
* Your compute jobs require specialized GPU or FPGA hardware.
* Maybe your jobs just take a long time to run.

Chances are, you've run into one of these situations before.
Fortunately, high-performance computing installations exist to solve these types of problems.

With all of this in mind, let's connect to a cluster (if you haven't done so already!). 
For these examples, we will connect to Frontenac - a high-performance cluster currently under construction.
Although it's unlikely that every system will be exactly like Frontenac, 
it's a very good example of what you can expect from a supercomputing installation.
To connect to our example computer, we will use SSH. 

## Logging onto the cluster

SSH allows us to connect to UNIX computers remotely, and use them as if they were our own.
The general syntax of the connection command follows the format `ssh yourUsername@some.computer.address`
Let's attempt to connect to the cluster now:
```
ssh yourUsername@login.cac.queensu.ca
```
```
The authenticity of host 'caclogin01.computecanada.ca (199.241.166.2)' can't be established.
ECDSA key fingerprint is SHA256:JRj286Pkqh6aeO5zx1QUkS8un5fpcapmezusceSGhok.
ECDSA key fingerprint is MD5:99:59:db:b1:3f:18:d0:2c:49:4e:c2:74:86:ac:f7:c6.
Are you sure you want to continue connecting (yes/no)?  # type "yes"!
Warning: Permanently added the ECDSA host key for IP address '199.241.166.2' to the list of known hosts.
yourUsername@login.cac.queensu.ca's password:  # no text appears as you enter your password
Last login: Wed Jun 28 16:16:20 2017 from s2.n59.queensu.ca
```

If you've connected successfully, you should see a prompt like the one below. 
This prompt is informative, and lets you grasp certain information at a glance:
in this case `[yourUsername@computerName workingDirectory]$`.

```{.output}
[yourUsername@caclogin01 ~]$
```

## Where are we? 

Very often, many users are tempted to think of a high-performance computing installation as one giant, magical machine.
Sometimes, people even assume that the machine they've logged onto is the entire computing cluster.
So what's really happening? What machine have we logged on to?
The name of the current computer we are logged onto can be checked with the `hostname` command.
(Clever users will notice that the current hostname is also part of our prompt!)

```
hostname
```
```
caclogin01
```

Clusters have different types of machines customized for different types of tasks.
In this case, we are on a login node.
A login node serves as a gateway to the cluster and serves as a single point of access.
As a gateway, it is well suited for uploading and downloading files, setting up software, and running quick tests.
It should never be used for doing actual work.

The real work on a cluster gets done by the "worker" nodes.
Worker nodes come in many shapes and sizes, but generally are dedicated to doing all of the heavy lifting that needs doing. 
All interaction with the worker nodes is handled by a specialized piece of software called a scheduler (called SLURM, in this case). 
We can view all of the worker nodes with the `sinfo` command.

```
sinfo
```
```
PARTITION AVAIL  TIMELIMIT  NODES  STATE NODELIST
standard*    up 14-00:00:0      1    mix cac101
standard*    up 14-00:00:0      5   idle cac[100,102-105]
```

There are also specialized machines used for managing disk storage, user authentication, 
and other infrastructure-related tasks. 
Although we do not interact with these directly, 
but these enable a number of key features like ensuring our user account and files are available throughout the cluster.
This is an important point to remember: 
files saved on one node (computer) are available everywhere on the cluster!

In this particular case, I've "hidden" several nodes specifically for use in our summer school.
You can view these with `sinfo -a`.

```
sinfo -a 
```
```
PARTITION     AVAIL  TIMELIMIT  NODES  STATE NODELIST
standard*        up 14-00:00:0      1    mix cac101
standard*        up 14-00:00:0      5   idle cac[100,102-105]
summer-school    up   infinite      6   idle cac[094-099]
```

## [Next section](../scheduler/)

