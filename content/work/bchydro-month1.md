---
title: "BC Hydro Month 1: A hands-on journey from onboarding to a full Redis migration"
date: 2025-06-08T00:03:09-07:00
draft: false
tags: ["Internship", "Monthly Reflection", "Redis", "PostgreSQL", "Distributed Systems"]
---

🗓 Week 1: May 5 – June 6, 2025

📌 Highlights
- Wrapped up onboarding, set up VPN access, and joined daily standups
- Got familiar with internal tools and the overall project structure
- Migrated the wildfire risk rating API from PostgreSQL to Redis
- Learned how to work with Redis data structures, perform location-based lookups, and use locks to prevent conflicts
- Removed the old database code and built out a Redis-only system
- Updated the Docker environment and local development setup
- Gave a live walkthrough to the team explaining how the Redis migration works

✅ Things I Worked On
- Replaced all SQL queries with Redis operations
- Added Redis locks to prevent multiple servers from running imports at the same time
- Wrote Redis setup scripts to load initial data (instead of using DB migrations)
- Added support for location-based search of nearby weather stations
- Built a simple status page to track running import jobs
- Updated existing API endpoints to work with Redis
- Improved error handling and added logging around Redis connections
- Wrote documentation to help others understand and use the new system

🧠 Reflections
- This month was a deep dive into backend infrastructure. Switching from a relational database to Redis meant changing how I think about data — from tables and joins to keys and hashes. Redis locks were new to me, but super helpful for making sure everything runs safely when multiple processes are involved. Giving a demo to the team was a great way to reflect on the work and explain it in simple terms. I’m really proud of how much I learned in just a few weeks, and I’m excited to keep building on this foundation in Month 2.