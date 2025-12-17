---
title: "BC Hydro Month 1: A hands-on journey from onboarding to a full Redis migration"
date: 2025-06-08T00:03:09-07:00
draft: false
tags: ["Internship", "Monthly Reflection", "Redis", "PostgreSQL", "Distributed Systems"]
---

🗓 Week 1: May 5 – June 6, 2025

First month done. The main thing I worked on was migrating the wildfire risk rating API from PostgreSQL to Redis — which sounds straightforward, but it ended up touching pretty much everything.

The biggest shift was changing how I think about data. With Postgres, it's all tables, rows, joins. With Redis, it's keys and hashes, and you have to be a lot more intentional about how you structure things because there's no schema to fall back on. Took me a bit to get used to, but once it clicked, I started to see why Redis makes sense for this use case — we needed fast lookups, and the data structure is simple enough that we don't really need relational queries.

A few specific things I had to figure out along the way: Redis locks (to prevent multiple servers from running imports at the same time), location-based lookups for nearby weather stations, and writing setup scripts to load initial data since we couldn't rely on DB migrations anymore. I also built a simple status page to track running import jobs, which turned out to be more useful than I expected.

Toward the end of the month, I gave a live walkthrough to the team explaining how the new system works. Honestly, preparing for that was almost as valuable as doing the actual work — it forced me to think through the "why" behind each decision and figure out how to explain it without getting lost in the weeds.

Also updated the Docker environment and local dev setup, wrote some documentation, and cleaned up error handling around Redis connections. The usual stuff that doesn't sound exciting but makes everything else easier.