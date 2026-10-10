---
title: "What is first principle thinking"
description: ""
pubDate: 2026-10-09
tags: ["Thinking", "Engineering", "Databases"]
draft: false
---

## Thinking from the Groud Up: Why First Principles Still Matter in Engineering

More than two thousand years ago, Aristotle came up with a simple idea that still shapes how the best engineering gets done: **first-principles thinking**.

Strip away the buzzwords, and it's straightforward: break a problem down to the few things you know are 100% true, throw out all assumptions, and build your solution from there.

It's how scientists work. They don't just accept things because "that's how everyone does it." They ask: *What are the bare facts here? What can we actually prove?*

With AI now writing code and spitting out architectures in seconds, our real value as engineers isn't copying what's trendy - it's knowing how to look at a messy problem, strip away the hype, and find what actually makes sense.

### A Familiar Trap: Picking Databases by Habit

Take database choice. A lot of team discussions start like this:

*"Should we go with Postgres or Mongo? I saw a great post about how Company XYZ uses it.*

That's reasoning by analogy - copying someone else's homework without knowing if their problem matches yours.

First-principles thinking asks you to look only at what your app really does. Suppose the bare facts of your system are:

- **Write vs. Read:** You write data 99 times for every single time someone reads it.
- **Data nature:** Records are just event logs. Once written, they never change.
- **Queries:** You never need to join tables together.

### Letting the Facts Pick the Tool

Once you have just those thruths, the decision almost makes itself:

- You don't need complex relational locks or full ACID transactions for data that is never updated.
- Standard relational databases often write to disk in random locations to keep tables organized, which slows down heavy write workloads.
- What you really need is an append-only, sequential log (like an LSM-tree system - think Kafka or Cassandra). Writing data sequentially to disk is fast, simple, and matches your access pattern perfectly.

When you think from the hardware and data patterns up, database design stops being a debate over favorites. It just becomes good, honest problem-solving.






Coined by the ancient Greek philosopher almost 2000 years ago, this term still holds importance over everything else, in every field.
Being an engineer, I think of ways to implement it in my work.
You can find the definition online with a single click search, but still, just to make this blog post complete, let me define it here as well.
To my understanding, first principle thinking is about breaking down a complex task or problem into smaller fundamental chunks, that are undeniable truths and not assumptions, and building the solution from there.
Even if you do your research about what is one of the most important skills employers look for in a candidate, it comes down to problem solving and critical thinking. 

In todays day and age when AI is doing most of the work, the responsiblity of an engineer is to break down the complicated task into chunks, use first principle thinking, and think of a better solution from there.

Is it not thinking like a scientist? As scientists don't assume anything, they question everything, go to the basics of the problem, and try to think of ways other than the obvious ones.

A good question to ask is - "What are we absolutely sure of? What has been already proven?".

Because we intend to talk about databases here, let's take an example of a database problem and apply first principle thinking there.

Instead of asking "Should we use PostgreSQL or MongoDB because tech blogs say so?", let's try to strip the problem into the fundamental truths.

Fundamental truths about the application - Read to write ratio is 99:1, records are strictly append only event logs, and we never perform complex multi-table joins.

Derived decision based on fundamentals - Relational ACID gaurantees and secondary indexing overhead are unnecessary constraints for this workload; an append-only log or LSM-tree engine (like Cassandra/Kafka) directly maps to our data's physical reality.

When you start thinking from the metal up, when you start thinking about disk I/O, access patterns, data structures involved in storing the data, it all comes down to problem solving using just the fundamentals.