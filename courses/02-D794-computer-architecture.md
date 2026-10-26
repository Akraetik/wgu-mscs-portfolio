# D794 — Computer Architecture and Systems

**Course 2 of 10** · Apr 11 – 22, 2026 · 2 performance tasks · 3 textbooks

**Time:** 12 calendar days · ~43 hours on WGU work · ~5 hours of outside courses 

**How it went:** Most of the hours were the three textbooks. I listened to about 20 hours of the first one as audio during long drives across Washington, then reread the key chapters. Each paper was written in a single night. Paper 2 came back for one missed item, and the fix took 2 hours. 

I probably listened to a lot more than 20 hours of the books. They have a very poor audio reading of the textbooks built in. It was almost impossible to listen to. I used Claude later and created material from the reading that was more digestible. For me it was frustrating having to work through systems I did not like that owned the books digitally. I had to work around them to get the material into a format I could ingest properly. This class has a lot of reading though, if you have the time to sit down and read the books. 

The books and material for the class were informative but not required to complete the assignments. Each paper was done quickly with online research.

## In one line

I traced how one technology, passkeys, grew out of hardware, OS, and network design. Then I wrote a full system design plan for a cloud ML forecasting pilot.

## What the course covers

How computer systems evolved and fit together: hardware, systems software, networking. It also covers how to plan a solution that runs across platforms and integrates many devices. The training was mostly the chapters of three textbooks.

## What I did

**Paper 1: the evolution of a computing architecture (passkeys).**
- Traced authentication from passwords → MFA and hardware tokens → FIDO2 / WebAuthn passkeys.
- Explained the architecture: asymmetric key pairs, private keys held in secure hardware on the device, local biometric unlock, cloud sync of credentials.
- Weighed the trade-offs. Passkeys resist phishing and credential stuffing. They also bring endpoint risk, weaker account-recovery paths, and platform lock-in. (The biometric never leaves the device. It only unlocks the private key locally.)
- Looked ahead to post-quantum cryptography and AI-driven social engineering.

**Paper 2: a system design plan for an AI demand-forecasting pilot** (fictional 120-store retailer).
- Executive summary, budget, and an 8–10 week timeline.
- Functional requirements with measurable criteria: SKU-level daily and weekly forecasts, nightly data sync with a 99% pipeline success rate, dashboards under 3 seconds, anomaly alerts.
- Technical requirements: Python, PostgreSQL, scikit-learn / TensorFlow / PyTorch, Azure Databricks and Azure ML, Power BI, GPU VMs, RBAC, AES-256.
- Model choice: time-series forecasting (ARIMA hybrids, LSTM), with accuracy tracked by MAPE.
- Performance, security, and use-case test plans.

## Skills used

`systems design` `functional vs. non-functional requirements` `cloud architecture (Azure)` `FIDO2 / WebAuthn` `public-key cryptography` `ML pipeline design` `technical writing`

## What I'd do differently

- Paper 2 was 15 pages. A design plan should be as short as the decision allows. I'd lead with a one-page architecture diagram.
- I wrote the forecast target as "85–90% accuracy measured by MAPE." MAPE is an *error* metric, so the clean version is "MAPE at or below 10–15%." Small wording, but details matter.
- Paper 2 was sent back once for a single rubric item. I fixed it in two hours. Read the rubric line by line before you submit.

## Key ideas worth knowing

- Von Neumann architecture; the fetch–decode–execute cycle
- The Little Man Computer model (a teaching CPU)
- Memory hierarchy: registers → cache → RAM → storage
- Enterprise vs. solution vs. software architecture
- Gap analysis; stakeholder sign-off; the solution architecture life cycle

## Books

The course ran on three textbooks. WGU students get them free as e-books through the course pages. Their e-book access is not ideal with intermittent internet issues while driving.

### *The Architecture of Computer Hardware, Systems Software, and Networking: An Information Technology Approach* (6th ed.)
**Irv Englander, Wilson Wong** · 2021 · Wiley

**What's in it:** number systems and data formats, the Little Man Computer model, CPU and memory design, I/O, buses, networks, and operating systems.

**Thoughts:** I listened to chapters 1–15 as audio over about a week of long drives, then reread chapters 1–5 before the papers. The course doesn't require you to read every chapter. I did. It's a great general review of computer architecture and systems. It includes binary and numbers and how image files are formed. I enjoyed it as base information everyone should know. 

### *Solution Architecture Foundations*
**Mark Lovatt** · 2021 · BCS, The Chartered Institute for IT

**What's in it:** a life cycle for solution architecture. How it relates to enterprise, data, application, and security architecture. Gap analysis, stakeholder sign-off, and choosing the technology.

**Thoughts:** I skimmed this one. Far too often I read enterprise and I see a bunch of terms that explain things that should be common sense. A lot of this book was not new as I had a business degree and experience. 

### *Solutions Architect's Handbook* (3rd ed.)
**Saurabh Shrivastava, Neelanjali Srivastav** · 2024 · Packt

**What's in it:** design principles (scalability, resilience, security, cost), cloud migration, microservices and event-driven patterns, DevOps, data engineering, and generative AI architecture.

**Thoughts:** I did not really care for this book. It was not written by someone who understands education or how to explain things well. It tried to cover way too many things and ended up not being useful for me. I would rather find all of the topics in this book from other sources that are better explained and go more in depth individually.

## Outside courses I took for this one

All four were assigned in the course material. About 5 hours finished.

| Course | Platform | Length |
|---|---|---|
| [Networking Foundations: Networking Basics](#networking-foundations-networking-basics) | LinkedIn Learning | 2h |
| [CISA Cert Prep 4: IT Operations, Maintenance, and Service Delivery](#cisa-cert-prep-4-it-operations-maintenance-and-service-delivery) | LinkedIn Learning | 2h (partly done) |
| [Enterprise Architecture Foundations](#enterprise-architecture-foundations) | LinkedIn Learning | 1h |
| [Introduction to IT Architecture](#introduction-to-it-architecture) | LinkedIn Learning | 2h |

### Networking Foundations: Networking Basics
[LinkedIn Learning](https://www.linkedin.com/learning/networking-foundations-networking-basics) · 2h

**Thoughts:** This course had very useful information. But it crams all of Networking into two hours. It's a great refresher or basic coverage of Networking. 

### CISA Cert Prep 4: IT Operations, Maintenance, and Service Delivery
[LinkedIn Learning](https://www.linkedin.com/learning/cisa-cert-prep-4-it-operations-maintenance-and-service-delivery-for-is-auditors) · 2h

**Thoughts:** More basic Networking and hardware architecture material. Easy 2 hour listen.

### Enterprise Architecture Foundations
[LinkedIn Learning](https://www.linkedin.com/learning/enterprise-architecture-foundations) · 1h

**Thoughts:** One hour course on Enterprise Architecture. Not very useful. Very generic and shallow information. 

### Introduction to IT Architecture
[LinkedIn Learning](https://www.linkedin.com/learning/introduction-to-it-architecture) · 2h

**Thoughts:** Another extremely basic video. One hour. Good for people new to IT.

## Public rebuild (planned)

I will create a walk through on a home lab and how to create one at some point. I don't think building a Little Man computer simulator in Python is useful. It is very basic stuff. It will go in `rebuilds/` when it's done. If I find the time for this. Honestly not worth revisiting. The class was done to standard to move on to the next one. the important takeaway from this course was the basics of computer architecture. 
