---
title: "BC Hydro Term 1: Building a Strong DevOps Foundation"
date: 2025-08-30T11:01:58-07:00
draft: false
tags: ["Internship", "DevOps", "Kubernetes", "CI/CD", "Testing"]
---

![DevOps Term 1 Reflection](/images/devops_term1.jpeg)

🗓 Term 1: May 5 – Aug 29, 2025

Four months went by fast. Here's a quick look back at what I worked on this term.

The biggest project was the **Wildfire Risk Rating API migration** — moving the data layer from PostgreSQL to Redis. I wrote about the technical details in an earlier post, but the short version is: we needed faster lookups, and Redis made sense for the data structure we had. A lot of the work was making sure the new outputs matched the legacy system exactly, which meant building automated tests to compare results across environments. Tedious, but worth it — saved a lot of debugging time later.

I also spent time improving our dev and deployment setup: updating local and containerized environments, cleaning up the CI/CD pipelines, and tightening up how we handle credentials. Not the most glamorous work, but the kind of thing that makes everyone's life easier down the line.

One side project I enjoyed was a **proof of concept for HTML-to-PDF generation**. Sounds simple until you start dealing with images, links, and weird formatting edge cases. Got it working in a container eventually, which was satisfying.

Throughout the term, I gave a few demos and wrote documentation to help the team adopt the new workflows. Presenting in English still feels a bit nerve-wracking: I'd sometimes stumble over words or say things awkwardly, but everyone was patient and encouraging. My manager and teammates made it easy to ask questions and learn. The weekly team lunches helped too; small thing, but it made me feel like I actually belonged here rather than just being "the co-op student."

**Next term**, I want to expand the automated testing to cover more edge cases and get it integrated into the CI pipeline properly. There's also some production-level work coming up for the Wildfire and Dam Safety systems, which I'm looking forward to digging into.