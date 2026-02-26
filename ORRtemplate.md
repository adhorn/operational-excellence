# Operational Readiness Review Template

## Introduction

An Operational Readiness Review (ORR) is a rigorous, evidence-based assessment that evaluates a particular service's operational state. While ORRs are often tailored to a specific company's culture and tools, they all share the same fundamental goal: **help you find blind spots in your operations**.

This template is based on two decades of experience writing application software, deploying servers, and managing large-scale architectures, refined over years of helping customers operate software systems in the cloud. It has been enhanced with resilience engineering principles to help teams build not just robust systems, but adaptive capacity to handle surprises.

### How to Use This Template

This is not THE template — it is A template. Treat it as a mechanism for regularly evaluating your workloads, identifying high-risk issues, and recording improvements. Most importantly, **make it yours**. Add your own experience, adapt it to your culture and needs.

The template focuses on launch readiness while building your team's ability to learn and adapt when assumptions prove incomplete.

### Can You Have the Right Answers to All Questions?

Very unlikely at first, but over time it should be your goal. Think of this as a learning path that supports continuous improvement. ORR reviews make it easy to capture point-in-time milestones and track operational improvements.

### Who Should Conduct an ORR?

ORRs work best with the entire service team: product owners, technical product managers, backend and frontend developers, designers, architects — everyone involved with the service. The more diversity, the better. We want to avoid confirmation bias and surface different perspectives on how the system might behave.

### When Should You Conduct an ORR?

**Start early and iterate continuously:**
- **At the beginning of service/feature design** - Start the ORR process early so teams understand operational requirements during development, not as a last-minute surprise before launch
- **Throughout development** - Conduct regular ORR workshops with Principal/Staff engineers meeting with the team as the product evolves. This creates ongoing learning opportunities and helps diffuse operational knowledge across the team
- **Before launch** (formal sign-off gate) - Complete the final ORR assessment before going to production
- **After significant changes** - Repeat when making major technological or architectural changes
- **Periodically** (approximately once per year) - Ensure operations haven't drifted but improved over time

The key is making ORR a **continuous exercise** rather than a one-time checklist. Regular ORR workshops during development help teams internalize operational thinking and build better systems from the ground up.

### How Does an ORR Differ from Architecture Reviews?

While architecture reviews focus on design principles and structural best practices, ORRs address the **operational aspects** of running a specific service in production. They complement each other but serve different purposes in the software development lifecycle.

---

## Template Structure

1. Service Definition and Goals
1. Architecture
1. Failures, Impact & Adaptive Capacity
1. Risk Assessment
1. Learning & Adaptation
1. Monitoring, Metrics & Alarms
1. Testing & Experimentation
1. Deployment
1. Operations & Adaptive Capacity
1. Disaster Recovery
1. Organizational Learning

_NOTE: Security must have its own, in-depth, review._

---

## 1 - Service Definition and Goals
* Describe what your service does from the customer's point of view.
* Describe your operational goals for the service.
* What is the SLA of the service?
* What are the business scaling drivers correlated with your services? (e.g. number of users, sales, marketing, ad-hoc, …)
* Describe the security review process for your service and what it covers.

---

## 2 - Architecture
* Describe the architecture of your service. Call out the critical functionalities. Identify the different components of the system and how they interact with one another.
* Describe each component of your system.
* Describe how your service scales and what triggers scaling.
* Walk me through what happens when traffic surges unexpectedly. Where does the system feel it first?
* What parts of your architectural design reduce the blast radius of failures? (discuss bulkheads, cells, shards, etc.)
* Where are your single-points of failure? For each, explain why it exists and what minimizes impact.
* Explain the different database and storage choices.
* List all customer-facing endpoints, explain what each does and what components and dependencies they have.
* List all dependencies that your service takes.
* What is the anticipated request volume for each component and dependencies of your system?

---

## 3 - Failures, Impact & Adaptive Capacity
* Explain how your service will be impacted based on the failure of each of your components and dependencies.
* What is the failure mode for each of the components? (fail-open vs. fail-closed)
* Explain the impact on customer experience for the failure of each component and each dependency.
* What are the limits imposed on your service by your dependencies? How are these limits tracked?
* How do you communicate scaling requirements to dependency owners? What happens when your needs change?
* What limits does your service impose on customer resources?
* Walk me through how limits get changed. What requires a deployment? What can be adjusted per-customer?
* Describe the resilience to failure of each of your components (discuss in particular multi-AZ, self-healing, retries, timeouts, back-off, throttles, and limits put in place).
* Walk me through what happens during an availability zone failure. Where does impact show up first? Can the service sustain production traffic with one AZ down? (ref. static stability)
* What is the retry/back-off strategy for each of your dependencies?
* What happens when your customers hit limits and get throttled? Can they raise them? How?
* What failure combinations have you never considered?
* What would happen if multiple "impossible" things occurred simultaneously?
* How does your service behave when it can only provide 80%, 50%, or 20% of normal functionality?
* When automated systems fail, what manual interventions can your team perform? Have these been practiced?
* What assumptions about your system have never been validated in production?

---

## 4 - Risk Assessment
* What are you worried about?
* What are you NOT worrying about?
* What are your operational risks?
* What features did you cut to meet your deadline?
* What are the top three things that you believe will catch fire first?
* How do you track dependencies and their criticality? When was the last time you reviewed them?
* Describe the cost and economics relationship of the service to scaling. What surprises you about it?

---

## 5 - Learning & Adaptation
* How does your team learn from near-misses and surprising behaviors?
* What mechanisms exist for sharing learnings across teams?
* When something surprising happens in production, how do you capture what you learned and share it with the team?
* How do you capture institutional knowledge about why certain design decisions were made?
* What's your process for revising your understanding of how the system works after an incident?

---

## 6 - Monitoring, Metrics & Alarms
* How do you measure and monitor the end-to-end customer experience?
* Walk me through how you detect when a single customer is having a bad experience versus a systemic problem. What's the difference in your alerting?
* How do you trace customer requests in your system?
* What are you alarming on? List all of your alarms, with period and threshold, and the severity of each.
* Show me your primary dashboard. What does it tell you and what doesn't it show?
* What metrics do you monitor that don't have alarms? Why not?
* What kind of health-checks does your system monitor? (discuss in particular if it is shallow or deep, if it uses cache, async vs. sync, etc., and the risks associated)
* Walk me through your monitoring coverage for external dependencies. How do you track usage against limits and remaining allowance?
* Describe your host-level monitoring: disk health, disk space, CPU, memory, log rotation. Where are the gaps and what concerns you?
* How do you track certificate expiration across your services?
* How do you monitor latency for synchronous and asynchronous calls? What thresholds trigger concern?
* Walk me through the path from alarm to action. What happens after an alarm fires? How does it become a ticket and reach the right person?
* How do you detect when expected signals are missing rather than just monitoring for bad signals?
* What early warning indicators help you detect problems before they become critical?
* What happens if your primary monitoring tools aren't available? Have you practiced flying blind?
* What processes help you detect when your assumptions about normal operation are wrong?
* What system behaviors have you started accepting as 'okay' that weren't happening 6 months ago?
* What error rates, timeouts, or performance patterns have become 'normal' for your team?
* What manual interventions does your team now do regularly that used to be rare?
* What processes help you identify when "normal" system behavior is actually drift toward danger?

---

## 7 - Testing & Experimentation
* Describe the overall test strategy you follow.
* When do you run tests? Do you have tests before and after conducting code review? Do they run automatically, or are developers running tests manually?
* How do you handle test data and test accounts? What are the risks?
* What's the percentage of public-facing APIs covered by tests?
* How do you test your dependencies? What assumptions do you make about their behavior?
* How do you verify that your service's monitoring and alarming function as expected?
* What is your GameDay plan?
* What controlled failure experiments have you run? What did you learn that surprised you?
* Where are the edges of your system's design parameters? What happens when you approach them?
* How do you verify that your system works the way you think it does under stress?
* What system behaviors only emerge under specific combinations of load, failure, and timing?
* How do you test for situations you haven't anticipated?

---

## 8 - Deployment
* How does your deployment procedure work? List actions and estimated time in the deployment pipeline.
* What are the manual touch-points in your system? Why aren't they automated? What are the risks associated with each of the touch-points?
* Walk me through how a change gets defined, approved, and deployed to production. Who reviews it and what are they looking for?
* How do you roll back a change?
* Walk me through your last rollback. What worked and what surprised you?
* How do you deploy the configuration to different stages?
* How do you validate configuration before deployment? Walk me through the last time a configuration issue was caught.
* What are the dependencies for deployment?
* Describe how deployments modify your infrastructure. What gets replaced versus updated in-place?
* What performance validation happens before production deployment? What does it cover and what doesn't it cover?

---

## 9 - Operations & Adaptive Capacity
* Describe what the on-call rotation for your service looks like.
* Show me how a new on-call engineer finds service documentation at 3am. Walk me through the path.
* What happens if your primary communication tools aren't available? Are you able to run incident operations through different channels?
* What happens if your runbooks aren't available? Do you have backups?
* When did you last execute each runbook end-to-end? Do you track execution dates for each runbook?
* When was the last time someone unfamiliar with a runbook executed it? What happened?
* Walk me through your recovery procedures for the most critical failure mode. Who wrote them and when were they last used?
* Describe the escalation path in the event of an outage (include timing expectations).
* How does your team maintain understanding of system state during novel situations?
* What processes help your team make good decisions when monitoring data is contradictory or incomplete?
* How does your team coordinate when incidents don't match any existing runbook?
* What authority do on-call engineers have to make system modifications during incidents?
* How do engineers share new understanding about system behavior discovered during incidents?

---

## 10 - Disaster Recovery
* Describe the access model for your on-call team. What can they do immediately, what requires escalation, and what safeguards prevent accidental damage during normal operations?
* Show me your escalation policies. How does someone find them during an incident? When were they last updated and what triggered the update?
* What mechanisms prevent routine tasks from interfering during an active disaster? Walk me through how they activate.
* Walk me through your last disaster recovery exercise. What was the scenario, who participated, and what surprised you?
* What are your measured RTO and RPO, and how do they compare to your targets?
* What are your DNS TTL values and what drove those choices?
* Walk me through how you measure customer impact during an incident. Show me the last time you used these tools.
* Describe your process for identifying the causes of outages. (e.g., postmortem, correction-of-error, etc.)
* Walk me through your backup and restoration process. When did you last restore from backup? When did you last fail over? What surprised you?
* What operational levers can your on-call team pull during emergencies? Walk me through throttles, limits, and other controls available to them.
* How do run-books stay current as the service changes? When was the last update and what triggered it?

---

## 11 - Organizational Learning
* How do you conduct blameless post-incident reviews that focus on learning?
* What mechanisms exist for questioning and updating operational procedures?
* How do you capture and share the reasoning behind design decisions for future teams?
* How do you measure your team's ability to handle novel situations?
* What forums exist for sharing near-miss stories and surprising system behaviors across teams?
* How do you distinguish between incidents that reveal system problems vs. those that reveal knowledge gaps?
* What mechanisms help you learn from other teams' incidents and apply those lessons to your service?
* How do you ensure that lessons learned from incidents actually influence future design and operational decisions?
