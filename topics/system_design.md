## System Design


| Table of Contents |
| ----------------- |
| [Intro](#intro) |
| [Interview Structure](#structure) |
| [SQL vs NoSQL](#sql_vs_nosql) |


# <a id="intro"></a> Intro - Why is System Design Important?

**What is system design?** A system design interview assesses a candidate's ability to build scalable and efficient software systems by using the right tools to meet requirements.

Think of it like constructing a building. The building is the system.

Consider the most simple web setup:

<img src="../img/web_traffic.png" width="600"><br>

1. User requests from Domain Name System (DNS) via domain name (e.g. `www.mysite.com`)
2. DNS returns server IP
3. User requests webpage/data via HTTP
4. Server returns HTML webpage or (typically JSON) data

As the number of users grow, a single computer server is not enough to handle all incoming traffic. This is where system design becomes important.

# <a id="structure"></a> Interview Structure

Below is a outline of how the logic a system design interview usually flows:

### 1. Understanding Requirements

Clients -- Who will use this system?

Features -- What can the system do?

Scope & Scale -- Where is the system at in the development lifecycle? How much traffic is going through the system? Will traffic be increasing in the near future?

Performance -- Do we need low latency when writing data? Reading data?

Cost -- Do we need to minimize cost of development? Of maintenance?

### 2. Define Functional & Non-Functional Requirements

Functional Requirements -- system behavior, APIs

Non-Functional Requirements -- system qualities (*e.g.*, fast, fault-tolerant, secure)

### 3. High-Level Architecture

Critical Components -- Identify key parts of the system and how they interact (*e.g.*, databases, application servers, load balancers)

API Design -- What program calls are exposed to accomplish functional requirements?

Database Structure -- What data will be stored? In what format?

### 4. Situational Optimizations

Selecting Tools -- Based off non-func requirements, choose tools and designs that reflect target qualities

Tradeoffs -- Justify your choices and bring up challenges that could arise

### 5. Overview & Discussion

Interviewer may ask you any question about any part of your design!

Bottlenecks -- Where the system potentially be slowed down by?

Alternative Options -- Could 'X' tool or 'Y' architecture be another potential choice for our system? Why or why not?

Future Roadmap -- How can the system be modified to support new features or increased load?

## Summary

Systems Design:

1. Understand requirements
    - Clients
    - Features
    - Scale
    - Performance
2. Define features & qualities
3. High-level architecture
    - Key components
    - API
    - Database
4. Optimizations
    - Scalability, performance, availability, security, etc.
    - Tradeoffs
5. Overview & discussion
    - Bottlenecks
    - Alternative options
    - Future roadmap

# <a id="sql_vs_nosql"></a> SQL vs NoSQL Databases

- SQL
    - atomicity, consistency, isolation, durability (ACID)
        - transaction support
    - data integrity
    - easier vertical scaling (sharding needed for horizontal scaling)

- NoSQL
    - performance, flexibility, availability
    - eventual consistency
    - easier horizontal scaling

# tradeoffs

event driven vs client server?

stream vs batch data processing

availability vs consistency
