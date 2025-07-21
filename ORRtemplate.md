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
1. Metrics and Alarms
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
* Are you conducting an in-depth security review of your service?

---

## 2 - Architecture
* Describe the architecture of your service. Call out the critical functionalities. Identify the different components of the system and how they interact with one another.
* Describe each component of your system.
* Does your service support auto-scaling? Describe the mechanisms and expectations.
* Does your architecture handle a sudden surge of traffic?
* What parts of your architectural design reduces the blast radius of failures? (discuss bulkheads, cells, shards, etc.)
* Do you have any single-points of failure? If you do, explain why and what is done to minimize the impact of failure.
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
* Do you communicate your scaling requirements to teams that own services you've taken dependencies on?
* Does your service impose limits on customer resources?
* Can you increase limits without making a deployment?
* Can you increase limits on a per-customer basis?
* Describe the resilience to failure of each of your components (discuss in particular multi-AZ, self-healing, retries, timeouts, back-off, throttles, and limits put in place)
* Can the service tolerate an availability zone (AZ) failure without impact?
* Can your service sustain production traffic with one AZ down? (ref. static stability)
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
* Do you keep track of your dependencies and their criticality? Do you review them regularly?
* Do you understand the cost/economics relationship of the service to scaling?

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
* Do you monitor for single-customer experience?
* Do you alarm on poor overall customer experience?
* Do you alarm on poor single-customer experience?
* How do you trace customer requests in your system?
* What are you alarming on? List all of your alarms, with period and threshold, and the severity of each.
* Are your dashboards clear? Does everyone know what to look at?
* Are there metrics you monitor that don't have alarms? Which? Why?
* What kind of health-checks does your system monitor? (discuss in particular if it is shallow or deep if it uses cache, async vs. sync, etc., and the risks associated)
* Do you monitor each external dependency and alarm on failure conditions?
* Do you monitor your dependency usage and remaining allowance?
* Do you monitor the hosts for disk failure?
* Do you monitor disk space utilization?
* Do you have log-rotation in place?
* Do you monitor for host CPU and memory utilization?
* Do you monitor for certificate expiration?
* Do you monitor the latency of synchronous and asynchronous calls?
* Do you auto-cut tickets on alarms?
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
* Do you test using "fake" accounts?
* What's the percentage of public-facing APIs covered by tests?
* Do you test your dependencies? What assumptions do you make on these?
* How do you verify that your service's monitoring and alarming function as expected?
* What is your GameDay plan?
* What controlled failure experiments have you run? What did you learn that surprised you?
* Have you tested your system at the edges of its design parameters?
* How do you verify that your system works the way you think it does under stress?
* What system behaviors only emerge under specific combinations of load, failure, and timing?
* How do you test for situations you haven't anticipated?

---

## 8 - Deployment
* How does your deployment procedure work? List actions and estimated time in the deployment pipeline.
* What are the manual touch-points in your system? Why aren't they automated? What are the risks associated with each of the touch-points?
* What is your procedure to define and approve a change in production? 
* Do you have a mandatory code review for each change? How do these changes get approved? Do you have several people approving changes?
* How do you roll back a change?
* Do you test the rollback procedures before deployment?
* How do you deploy the configuration to different stages?
* Do you error-and-syntax check your configuration before deployment?
* What are the dependencies for deployment?
* Does your deployment support immutability? Does your deployment update/upgrade software in-place?
* Do you perform load testing before deploying to production?

---

## 9 - Operations & Adaptive Capacity
* Describe how the on-call rotation for your service looks like.
* Do you have easily available and complete links to the documentation for the service?
* What happens if your primary communication tools aren't available? Are you able to run incident operations through different channels?
* What happens if your runbooks aren't available? Do you have backups?
* When did you last execute each runbook end-to-end? Do you track execution dates for each runbook?
* Have you tested runbooks with people who didn't write them?
* Do you have well defined, documented, and accessible recovery procedures? 
* Describe the escalation path in the event of an outage (include timing expectations).
* Does the trouble-ticketing system integrate with the monitoring system?
* Does the paging system integrate with the monitoring system?
* How does your team maintain understanding of system state during novel situations?
* What processes help your team make good decisions when monitoring data is contradictory or incomplete?
* How does your team coordinate when incidents don't match any existing runbook?
* What authority do on-call engineers have to make system modifications during incidents?
* How do engineers share new understanding about system behavior discovered during incidents?

---

## 10 - Disaster Recovery
* Do your on-calls have full access to connect to, debug, and configure the service?
* Are you preventing/discouraging your team from using full-admin access roles except when absolutely necessary?
* Do you have read-only roles for your team to use for non-critical situations?
* Do you have up-to-date escalation policies easily accessible by anyone in the company?
* How do you keep the escalation policies up-to-date?
* Do you have platform-wide locks that prevent or delay routine tasks in case of an active disaster?
* Do you have a well-defined process for DR situations? (e.g., war rooms, isolation, calls, internal & external communication)
* Are you practicing your disaster recovery procedure?
* Do you have measured and verified RTO and RPO?
* Are your DNS TTLs set to sane values?
* Do you have verified and tested tools deployed to query logs to measure the impact on customers?
* Do you have a process for identifying the causes of outages? (e.g., postmortem, correction-of-error, etc.)
* Do you back up critical data?
* Do you practice backup restoration regularly?
* Do you regularly practice fail-overs?
* Can your on-call team enable throttles to protect the service from user load?
* Can your on-call team increase limits in case of emergencies?
* Do you update run-books as the service changes?

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