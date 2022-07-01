---
title: Secure AWS resources using Security Groups
date: 2022-06-21 22:10:00 -400
categories: [aws, security]
tags: [aws,security]      # TAG names should always be lowercase
---

<iframe width="686" height="386" src="https://www.youtube.com/embed/Gm8fgVqzdM8" title="Secure AWS resources using Security Groups" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

To quote AWS documentation:

<b>A security group acts as a virtual firewall, controlling the traffic that is allowed to reach and leave the resources that it is associated with. For example, after you associate a security group with an EC2 instance, it controls the inbound and outbound traffic for the instance.</b>

   
   <a href="https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html">Reference to the security groups documentation</a>

   Part of deploying AWS resources is understanding how to secure various applications and services. I believe at the base layer, security groups play a big part in providing a layer of security to the applications. It is very important that we don’t forget to restrict access to the resources that are deployed in AWS, and ensuring only authorized communication can occur between these resources.