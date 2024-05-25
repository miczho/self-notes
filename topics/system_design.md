### System Design

# Table of Contents

| Section | Title |
| ------- | ----- |
| 01 | [Intro](#01) |

<a id="01"></a>
# Intro - Scaling From Zero to Millions

**What is system design?** A system design interview assesses a candidate's ability to build scalable and efficient software systems by selecting and utilizing the appropriate tools to meet requirements.

Think of it like constructing a building. The building is the system.

Consider the most simple web setup:

<img src="../img/web_traffic.png" width="600"><br>

1. User requests from Domain Name System (DNS) via domain name (e.g. `www.mysite.com`)
2. DNS returns server IP
3. User requests webpage/data via HTTP
4. Server returns HTML webpage or (typically JSON) data

As the number of users grow, a single computer server is not enough to handle all incoming traffic. This is where system design becomes important.


