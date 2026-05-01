---
title: "BC Hydro Term 3: Security, Logs, and Learning to Rest"
date: 2026-04-30T23:39:27-07:00
draft: false
tags: ["DevOps", "DevSecOps", "Kubernetes", "CI/CD", "GitHub Actions", "Contractor"]
---

![DevOps Term 3 Reflection](/images/devops_pt1.JPG)

🗓 Term 3: Feb 2 – Apr 30, 2026

Coming back after the holidays felt different this time. Same team, same Rancher UI, same daily standups — but I wasn't a co-op anymore. I was a contractor. On paper it's just a title change, but it didn't quite feel that way.

There's something subtle that shifts when you're not "the intern." You get pulled into incidents. People ping you directly when something breaks. You're expected to figure things out, not just complete tasks. I haven't graduated yet, but somewhere in the last few months I stopped thinking of myself as a student who happens to be working, and started thinking of myself as someone who works and also happens to still be finishing school.

---

**The main project: a security scanning report pipeline**

The idea started simple enough: run CodeQL and Trivy across our repos, generate a report, send it out. Sounds like an afternoon project. It wasn't.

The first thing I hit was a permissions issue — `GITHUB_TOKEN` doesn't have access to the security alerts API. You need a PAT configured as a secret in each repo. The kind of thing you only find out by hitting a 403 and digging through docs.

But the bigger lesson wasn't about tokens. It was about what "security reporting" actually means.

I started with the mindset of: run the scan → have results → done. Scanning is the easy part. The hard part is making the output useful. A report that lists every CVE and every low-severity flag is a report no one reads. Too much information is the same as no information.

So the real work became: what goes at the top? How often do you send this without creating noise? We landed on a weekly Teams channel report instead of a distribution list — easier to see, less likely to get buried. We also built in a manual trigger so you can run it without sending an email when you're just testing changes.

One thing I didn't expect to think about: not all vulnerabilities are fixable. Some CVEs live at the OS level, baked into the base image. You wait for upstream to patch, or you document the risk and move on.

---

**The other thread: SEN backup observability**

I added centralized logging to the backup CronJob system using Fluent Bit sidecar + VictoriaLogs. Not full Grafana dashboards — the Rancher-Prometheus integration on our end was temporarily unavailable, which was frustrating. But having structured, searchable logs is already a step up from digging through pod logs manually.

Toward the end of the term, the SAP EnableNow migration was put on hold, so the backup system is sitting in the backlog for now. That's just how projects go sometimes — the infrastructure is ready when the business needs it.

---

**What I'm looking forward to**

The team has been talking about moving to Azure and leaning more into Terraform — and honestly, I'm curious how AI tooling starts fitting into that picture too. That's the direction I want to go. And after a term of juggling work, school, and everything in between — I'm very much looking forward to actually resting for a bit. Maybe even some travelling before graduation. ✈️ 🥳

The team's been great. Still a few more months of part-time before I wrap up school and sort out the next steps — looking forward to seeing where things go from here.