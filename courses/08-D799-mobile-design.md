# D799 — Mobile and Ubiquitous Design

**Course 8 of 10** · Jun 22 – Jul 1, 2026 · 2 performance tasks

**Time:** 10 calendar days · ~29 hours on WGU work · ~14 hours of outside courses *(from my study journal; see [Time per course](../README.md#time-per-course))*

**How it went:** I'd over-prepared in D800, so this one felt doable from day one. Most of the work was four sessions of 3–8 hours. I drew the wireframes on paper at a coffee shop first, then rebuilt them in Visio.

This course was hyped up for me from a mentor in that it would have me making a complete app and deploying it. This course was good, but it was not in depth and I did not create a finished product in this course. Instead it was almost like a supplemental course to D800 which I previously did. Because I did so much for the previous one I could have finished this in probably a long weekend. 

## In one line

I planned a campus-life mobile app ("Studience") end to end, from architecture to personas, sensors, security, and ethics. Then I mapped every screen and flow as a wireframe in Microsoft Visio.

## What the course covers

The technical side of mobile and connected devices (sensors, processors, embedded systems, communication protocols, connectivity) combined with user-centered design. It covers personas, usability testing, privacy, and designing apps that work across several devices.

## What I did

**Task 1: the app creation plan** (before drawing a single screen)
- **Scope and scale:** features grouped into *Access, Viewing, Connection*; phased rollout; AWS Auto Scaling for start-of-semester spikes.
- **Architecture:** cloud microservices on AWS behind a REST API. It reads from the university's Student Information System instead of copying records.
- **Two personas:** a 19-year-old full-time undergrad who is very comfortable with tech, and a 46-year-old working parent in grad school with moderate tech comfort. Each has needs, goals, challenges, and how the app meets them.
- **Sensors and comms:** GPS for campus wayfinding, camera for uploads, Firebase Cloud Messaging for push, Wi-Fi/cellular handoff, Bluetooth.
- **Offline-first:** local caching of schedules, grades, and announcements, with a background sync on reconnect.
- **Security and privacy:** TLS, OAuth 2.0 single sign-on through university credentials, RBAC, end-to-end encrypted messaging, data minimization, FERPA.
- **Built for mid-range devices:** Android 10+ / iOS 15+, a low-battery mode, server-side media compression.
- **UX:** WCAG accessibility and a usability testing plan.

**Task 2: the wireframe**
- Sketched on paper first, then built in **Microsoft Visio**.
- Home, current courses → course detail, schedule, messaging ("Student-Connect"), resources, and a persistent menu and bottom nav bar. Every screen is connected by flow lines.

## Skills used

`mobile app planning` `personas` `REST APIs` `AWS Auto Scaling` `OAuth 2.0` `offline-first / caching` `push notifications (FCM)` `FERPA` `WCAG` `Microsoft Visio` `wireframing`

## What I'd do differently

- **Check the design against the policy.** End-to-end encrypted student-faculty messaging may clash with a university's record-keeping duties. I'd flag that trade-off explicitly.
- **Define the MVP.** The plan lists many features. I'd name the three that ship first and the KPI each one moves.
- **Click-through prototype.** A static Visio map shows structure. A Figma prototype lets someone actually test it.

## Key ideas worth knowing

- Sensing, computing, communication: the three layers of ubiquitous computing
- User personas; pain points; jobs to be done
- MVP; KPIs; NPS (Net Promoter Score); product roadmap
- Touch heatmaps; eye tracking; usability testing
- Native vs. cross-platform vs. web apps
- Color theory and typography basics for mobile

## Books and reading

### *Mobile App Development for Businesses: Create a Product Roadmap and Digitize Your Operations*
**Maja Dakić** · 2023 · Apress

**What's in it:** eight chapters. Why a business needs an app, choosing a platform, building a product roadmap, balancing features, why users matter, promoting the app, working with a technical partner, and technology use cases.

**Thoughts:** I enjoyed this book. I read this book as a textbook with references to other things and looking up relevant information online as I went through it slowly. At this point I'm convinced that textbooks will become extinct soon and our idea of textbooks will just be bullet points and prompts of what we have AI/SI look into and build us a personalized plan. The information was good. The ROADMAP of information in it was more useful. What to study and in what order. What to do for completing an app and why.

## Outside courses I took for this one

About 14 hours finished.

| Course | Platform | Length |
|---|---|---|
| [The Complete App Design Course: UX, UI and Design Thinking](#the-complete-app-design-course-ux-ui-and-design-thinking) | Udemy | 3h |
| [Principles and Practices for Great UI/UX Design](#principles-and-practices-for-great-uiux-design) | Udemy | 3h 30m |
| [UX Strategy Fundamentals](#ux-strategy-fundamentals) | Udemy | 2h 30m |
| [Microsoft Visio Masterclass](#microsoft-visio-masterclass) | Udemy | 4h (partly done) |
| [Sketching for UX Designers](#sketching-for-ux-designers) | Udemy | 4h 30m |

### The Complete App Design Course: UX, UI and Design Thinking
[Udemy](https://www.udemy.com/course/the-complete-app-design-course-ux-and-ui-design/) · 3h

**Thoughts:** Useful covering of the fundamentals of app design like Color Theory and Typography. 

### Principles and Practices for Great UI/UX Design
[Udemy](https://www.udemy.com/course/principles-and-practices-for-great-ui-ux-design/) · 3h 30m

**Thoughts:** Same as previous one. I like to hit the same information from slightly different angles to solidify it. This was about 10-20% better than the previous one in my opinion.

### UX Strategy Fundamentals
[Udemy](https://www.udemy.com/course/ux-strategy-fundamentals/) · 2h 30m

**Thoughts:** Same topic. But the fundamentals for the business and strategic side of creating an app. Also useful. 

### Microsoft Visio Masterclass
[Udemy](https://www.udemy.com/course/microsoft-visio-masterclass/) · 4h (partly done)

**Thoughts:** Not great. It seems every course I find for enterprise and old world things like Visio or Microsoft products or Java are not great. Not engaging. Not dynamic. Not useful. Boring. I couldn't finish this one. I learned more about Visio with youtube videos and experimenting with it myself making the deliverables for this class than any boring video I saw available could do. 

### Sketching for UX Designers
[Udemy](https://www.udemy.com/course/sketching-for-ux-designers/) · 4h 30m

**Thoughts:** The instructor was very passionate about this. It was nice. Useful? I don't know if it is. I did sketch out my entire UX for this course in a coffee shop so I guess it was inspirational but not necessary. 

**Final Note:** This course had a lot of Percipio videos offered. I skimmed them. I was not a huge fan of Percipio or of the material. 

## Public rebuild (planned)

A different app concept of my own, taken from persona to MVP to a clickable Figma prototype, with a short usability test. It will go in `rebuilds/` when it's done.

Using the software is how I learn. Visio I learned from doing. I used Draw.io a lot as well for this program. Figma was superior but not used for this. With how AI is eating the industry I don't know what I can recommend going forward. I like Figma. It works for now. 
