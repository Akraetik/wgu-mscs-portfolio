# D780 — Software Architecture and Design

**Course 9 of 10** · Jul 2 – 21, 2026 · 2 performance tasks · 3 textbooks · 23 Gang of Four patterns

**Time:** 20 calendar days · ~28 hours on WGU work · ~4 hours of outside courses *(from my study journal; see [Time per course](../README.md#time-per-course))*

**How it went:** Before starting the tasks I spent a week on 100 Days of Python, then took four days off. I turned the course textbooks into audio to listen to on drives. Task 1 was one 8-hour night, and Task 2 took three sessions.

This course requires some Flask knowledge so I'd study that before to get prepared. It also claims to need Docker but I didn't. 

## In one line

I spotted and replaced poorly fitting design patterns in a grocery-store codebase. Then I split a monolithic retail app into four Flask microservices that talk over REST.

## What the course covers

Designing, analyzing, and managing large software systems: architecture styles, choosing and applying design patterns, and building software that is well structured, reliable, and secure.

## What I did

**Task 1: design patterns**
- **Identified three patterns from the code alone** and named the evidence for each:
  - *Singleton* — a class-level `_instance` plus an overridden `__new__`
  - *Factory* — a static creation method choosing between concrete processors
  - *Strategy* — an injected behavior object used through composition
- **Argued why each was the wrong fit:**
  - A Singleton cart means every shopper shares one cart.
  - A simple factory must be edited for every new payment type, which breaks the Open/Closed Principle.
  - "Add stock" and "remove stock" aren't interchangeable algorithms, so Strategy was over-engineering.
- **Refactored each one:**
  - Singleton → **Decorator** (per-customer carts; tax and discount wrappers on items at runtime)
  - Factory → **Strategy** (a `PaymentStrategy` abstract base class plus a `CheckoutContext` with dependency injection)
  - Strategy → **Observer** (one inventory subject; low-stock alerts and reorder services subscribe)
- Drew UML class diagrams for the before and after in draw.io.

**Task 2: architecture**
- **Picked an architecture for three business cases:** microservices for a seasonal retailer, microservices for a high-traffic ticketing site, and event-driven pub/sub for an order pipeline. I also made the cloud-vs-on-premises call for each, with evidence.
- **Refactored a monolith into four Flask services:**

| Service | Port | Endpoint |
|---|---|---|
| Inventory | 5001 | `PUT` / `GET /inventory/<item>` |
| Cart | 5002 | `POST /cart/add` |
| Payment | 5003 | `POST /payment/process` |
| Orchestrator | 5000 | `POST /checkout` — calls the other three |

- Added a `run_all.py` launcher, a README with Windows-specific `curl` notes, and test cases. I showed it working in a recorded demo.
- Committed each step separately to Git with clear messages.

## Skills used

`Python` `Flask` `requests` `REST APIs` `GoF design patterns` `SOLID / Open-Closed` `abc.ABC` `dependency injection` `UML` `microservices` `event-driven architecture` `Git`

## What I'd do differently

The architecture is right for a teaching exercise. In production it would break. Here's where:

- **No rollback.** If payment fails, the stock is already deducted. Real systems use a *saga*: compensating actions or a reservation step.
- **Race condition.** "Check stock" and "deduct stock" are two separate calls. Two shoppers can buy the last laptop. Do it as one atomic "reserve" call.
- **The client sends the price.** Anyone could POST `amount: 1`. The server should look up the price.
- **No timeouts.** `requests.get()` without `timeout=` can hang forever. Add timeouts and retries.
- **In-memory state and `debug=True`.** Fine for a demo. Production needs a database per service and debug off.
- **Task 1 bugs I'd fix:** the tax decorator's comment says 10.4% but the code multiplies by 1.14. The base decorator never calls `super().__init__()`. Prices use floats instead of `Decimal`. A discount can push a price below zero.

## Key ideas worth knowing

- The 23 GoF patterns in three groups: **creational** (Singleton, Factory Method, Abstract Factory, Builder, Prototype), **structural** (Adapter, Decorator, Facade, Proxy, Composite, Bridge, Flyweight), **behavioral** (Strategy, Observer, Command, State, Template Method, Iterator, and more)
- SOLID principles
- Monolith vs. microservices vs. event-driven vs. layered vs. client-server
- API gateway / orchestration vs. choreography
- The saga pattern; idempotency; eventual consistency
- UML class diagrams and ER diagrams; Attribute-Driven Design (ADD)

## Books and reading

### *Hands-On Design Patterns with Java*
**Dr. Edward Lavieri** · 2019 · Packt

**What's in it:** the GoF patterns (creational, structural, behavioral) plus functional, reactive, and architectural patterns, with Java examples.

**Thoughts:** I stuck with Python so this was not extremely useful for me. Mostly the prompt of Gang of Four patterns and looking them up myself. 

### *Mastering Python Design Patterns* (3rd ed.)
**Kamon Ayeva, Sakis Kasampalis** · 2024 · Packt

**What's in it:** SOLID principles, then creational, structural, and behavioral patterns in idiomatic Python, plus architectural, concurrency, and testing patterns and anti-patterns.

**Thoughts:** Useful book but again, I skimmed it and used it for prompts to look online for learning through AI, pre made videos, and interactive prompting. 

### *Learning Systems Thinking*
**Diana Montalion** · 2024 · O'Reilly

**What's in it:** software as systems of relationships: feedback loops, leverage points, mental models, and how teams reason about large designs.

**Thoughts:** I was experimenting with AI as a learning aide at this point and took this book and made it into AI Audio designed like a podcast to be listened to while driving. I listened to an AI Parsed version of this book over many hours of driving. I then later skimmed the book. It has useful information. The topics are great prompts for deeper research on your own. 

**The classic behind all three:** Gamma, Helm, Johnson & Vlissides, *Design Patterns: Elements of Reusable Object-Oriented Software* (1994, Addison-Wesley).

## Outside courses I took for this one

About 4 hours of assigned outside courses, plus a lot of Python practice on my own.

| Course | Platform | Length |
|---|---|---|
| [100 Days of Code: The Complete Python Pro Bootcamp](#100-days-of-code-the-complete-python-pro-bootcamp) | Udemy | about 30 days done during this course |
| [Software Design: Modeling with UML](#software-design-modeling-with-uml) | LinkedIn Learning | 1h 45m |
| [Software Architecture Foundations](#software-architecture-foundations) | LinkedIn Learning | 1h 37m |
| [Top 10 Skills for AI Systems Designers](#top-10-skills-for-ai-systems-designers) | LinkedIn Learning | 45m |
| [Domain-Driven Design Fundamentals](#domain-driven-design-fundamentals) | Pluralsight | 6h (partly done) |
| [From Java to Python OOP](#from-java-to-python-oop) | LinkedIn Learning | 1h 7m (partly done) |

### 100 Days of Code: The Complete Python Pro Bootcamp
[Udemy](https://www.udemy.com/course/100-days-of-code/) · about 30 days done during this course

**Thoughts:** I love this course for learning Python. Not necessarily for this program, although it does go into API's and Flask which was useful for this course. 

### Software Design: Modeling with UML
[LinkedIn Learning](https://www.linkedin.com/learning/software-design-modeling-with-uml) · 1h 45m

**Thoughts:** I don't value UML as a method. It's just a very rigidly complex way to create trees and graphs to explain things. 

### Software Architecture Foundations
[LinkedIn Learning](https://www.linkedin.com/learning/software-architecture-foundations) · 1h 37m

**Thoughts:** Very generic course on the basics. 

### Top 10 Skills for AI Systems Designers
[LinkedIn Learning](https://www.linkedin.com/learning/search?keywords=Top+10+Skills+for+AI+Systems+Designers) · 45m

**Thoughts:** Useless.

### Domain-Driven Design Fundamentals
[Pluralsight](https://www.pluralsight.com/search?q=Domain-Driven+Design+Fundamentals) · 6h (partly done)

**Thoughts:** It felt more like naming conventions and overly generalized theory. It didn't help me at all.

### From Java to Python OOP
[LinkedIn Learning](https://www.linkedin.com/learning/search?keywords=From+Java+to+Python+OOP) · 1h 7m (partly done)

**Thoughts:** I was not coming to Python from Java. This basically is along the lines of learning the design patterns better learned elsewhere. Not great course.

## Public rebuild (planned)

Part 1: a small catalog of GoF patterns in Python, each with a pytest file. Part 2: my own checkout service with the production fixes above, running in Docker Compose. It will go in `rebuilds/` when it's done.

The skill built here is choosing and working with the Gang of Four design patterns, implementing them in a language of choice, and then the testing of them with PyTest. Getting familiar with API's and Docker are useful reps too.
