---
title: "Using resources effectively"
menu: main
weight: 6
---

We now know virtually everything we need to know about getting stuff on a cluster.
We can log on, submit different types of jobs, use preinstalled software, 
and install and use software of our own.
What we need to do now is use the systems effectively.

## Estimating required resources using the scheduler

Although we covered requesting resources from the scheduler earlier,
how do we know how much and what type of resources we will need in the first place?

Answer: we don't. 
Not until we've tried it ourselves at least once.
We'll need to benchmark our job and experiment with it before
we know how much it needs in the way of resources.

The most effective way of figuring out how much resources a job needs is to submit a test job,
and then ask the scheduler how many resources it used.
A good rule of thumb is to ask the scheduler for more time and memory than your job can use.
This value is typically two to three times what you think your job will need.

Using some of the data we downloaded from the last section.

## Playing nice



