+++
title = "Thoughts on cloud providers"
date = 2024-07-03
draft = false

[taxonomies]
categories = ["thoughts"]

[extra]
lang = "en"
toc = true
comment = true
copy = true
math = false
mermaid = false
outdate_alert = true
outdate_alert_days = 120
display_tags = true
truncate_summary = false
featured = false
+++

Hello, people of the internet,

Today, I'll be talking about cloud providers and services. Are they magic? Are they a scam?

Well, not exactly. We must first understand how Azure, AWS, and GCP (the others aren't worth mentioning) work.

It all starts with a data center, a room full of servers.

So, what can servers do? They run virtual machines on top of the actual hardware.

Hardware must run an operating system, of course. This is where it splits into two families: hardware, then operating system, and finally, the software that manages your virtual machines. These are called Type 2 hypervisors.

Type 2 hypervisors are not ideal. An OS (Windows?) consumes resources and isn’t designed to handle thousands of VMs.

Therefore, people developed lightweight operating systems (most of them are BSD-based) designed specifically to run virtual machines and allow SSH access. Some also provide a web GUI for easier management. These are called Type 1 hypervisors.

Cloud providers use Type 1 hypervisors for obvious reasons.

Type 1 hypervisors, like Proxmox, can be run in clusters, allowing multiple servers to communicate as if they’re one giant server.

However, hardware is physical, and people are scattered around the globe, introducing latency and other issues.

So, to address this, multiple data centers are spread across "Earth" and synchronized.

This setup solves the latency issue.

Cloud providers also need to offer a user-friendly interface to abstract the complexities, so they’ve built web apps for that.

At its core, a simplified cloud provider is just a data center and a web app for creating VMs and managing network policies. You can even create a mini "cloud" at home.

Cloud providers don’t just offer VMs; they provide databases, queues, storage, and other services.

Once you have the "create VM" and "delete VM" functions in place, you can use open-source projects (like Postgres, RabbitMQ, OpenNAS, etc.) and write Ansible playbooks to provision these projects within the VMs. Provide users with a UI for basic tasks, and under the hood, you’re running shell scripts on those VMs.

Of course, you need to stay legal, so ensure you use licenses like MIT that grant you full rights. But you get the idea: these cloud services can be a huge SCAM.

At least, many of them are. For example, AWS has useful services like CDN, EC2 for running VMs, EKS for managing Kubernetes clusters (which is hell to manage on your own), and storage.

Storage is not something you can easily self-host on an EC2 instance or a Kubernetes service volume. You might need more storage or reliable backup solutions.

BUT THE MAIN IDEA IS: The better you are, the fewer services you need.

One other downside of having your cloud provider manage everything is vendor lock-in. Once your business grows, you’re stuck with huge bills, and migrating elsewhere can result in enormous egress fees.

So, should you build your own cloud?

No, that’s dumb.

Should you do it for fun?

Yes!

Should you go all in on cloud services?

Well, it’s your project and your money, do with it what you please. It could be a good idea if you have a team of developers with no self-hosting experience.

Thinking of that, the market is saturated with frontend developers who’ve switched to frameworks like Next.js and have no idea how to host things. Services like Vercel do what AWS does but on top of AWS, which is expensive and less flexible.

But hey, you do you, my friend.