---
layout: post
title: How to transform your unused laptop into a server
---
I was reading this [tutorial](https://blog.mindorks.com/how-to-convert-your-laptop-desktop-into-a-server-and-host-internet-accessible-website-on-it-part-1-545940164ab9).
It shows how to run a server on your laptop and make it publicly accessible.
The critical problem is how to have a static IP for your laptop. And the answer is that your router has a static ip assigned by your 
ISP, and you can set up port forwarding on your router to redirect the traffic your laptop. 

It's quite fun to read and try it out.

Learnings:

1. If you have two computers both connected to one router, you can use their internal ip address to let them
communicate with each other. E.g., you can run a http server on one laptop (the simplest way: python -m SimpleHTTPServer 8000),
and use internal ip address to access it on the other.
1. The router has a static IP.
1. You can set up port forwarding on the router.
