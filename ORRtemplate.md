
# Operational Readiness Review Template


1. Service Definition and Goals
1. Architecture
1. Failures and Impact
1. Risk Assessment
1. Metrics and Alarms
1. Testing
1. Deployment
1. Operations
1. Disaster Recovery

_NOTE: Security must have it's own, in-depth, review._


---

## 1 - Service Definition and Goals
* Describe what your service does from the customer's point of view.
* Describe your operational goals for the service.
* What is the SLA of the service?
* What are the business scaling drivers correlated with your services? (e.g. number of users, sales, marketing, ad-hoc, …)
* Are you conducting an in-depth security review of your service?


---

## 2 - Architecture
* Describe the architecture of your service. Call out the critical functionalities. Identify the different components of the * system and how they interact with one another.
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

## 3 - Failures and Impact
* Explain how your service will be impacted based on the failure of each of your components and dependencies.
* What is the failure mode for each of the components? (fail-open vs. fail-closed)
* Explain the impact on customer experience for the failure of each component and each dependency.
* What are the limits imposed on your service by your dependencies? How are these limits tracked?
* Do you communicate your scaling requirements to teams that own services you've taken dependencies on?
* Does your service impose limits on customer resources?
* Can you increase limits without making a deployment?
* Can you increase limits on a per-customer basis?
* Describe the resilience to failure of each of your components (discuss in particular multi-AZ, self-healing, retries, timeouts, * back-off, throttles, and limits put in place)
* Can the service tolerate an availability zone (AZ) failure without impact?
* Can your service sustain production traffic with one AZ down? (ref. static stability)
* What is the retry/back-off strategy for each of your dependencies?
* What happens when your customers hit limits and get throttled? Can they raise them? How?


---

## 4 - Risk Assessment
* What are your operational risks?
* What scalability concerns are you worried about?
* What features did you cut to meet your deadline?
* What are the top three things that you believe will catch fire first?
* Do you keep track of your dependencies and their criticality? Do you review them regularly?
* Do you understand the cost/economics relationship of the service to scaling?


---

## 5 - Monitoring, Metrics & Alarms
* How do you measure and monitor the end-to-end customer experience?
* Do you monitor for single-customer experience?
* Do you alarm on poor overall customer experience?
* Do you alarm on poor single-customer experience?
* How do you trace customer requests in your system?
* What are you alarming on? List all of your alarms, with period and threshold, and the severity of each.
* Are you dashboard clear? Does everyone know what to look at?
* Are there metrics you monitor that don't have alarms? Which? Why?
* What kind of health-checks does your system monitor? (discuss in particular if it is shallow or deep if it uses cache, async * vs. sync, etc., and the risks associated)
* Do you monitor each external dependency and alarm on failure conditions?
* Do you monitor your dependency usage and remaining allowance?
* Do you monitor the hosts for disk failure?
* Do you monitor disk space utilization?
* Do you have log-rotation in place?
* Do you monitor for host CPU and memory utilization?
* Do you monitor for certificate expiration?
* Do you monitor the latency of synchronous and asynchronous calls?
* Do you auto-cut tickets on alarms?


---

## 6 - Testing
* Describe the overall test strategy should follow.
* When do you run tests? Do you have tests before and after conducting code review? Do they run automatically, or are developers * running tests manually?
* Do you test using "fake" accounts?
* What's the percentage of public-facing APIs covered by tests?
* Do you test your dependencies? What assumptions do you make on these?
* How do you verify that your service's monitoring and alarming function as expected?


---

## 7 - Deployment
* How does your deployment procedure work? Lists actions and estimated time in the deployment pipeline.
* What are the manual touch-points in your system? Why aren't they automated? What are the risks associate with each of the * touch-points?
* What is your procedure to define and approve a change in production? 
* Do you have a mandatory code review for each change? How do these changes get approved? Do you have several people approving * changes?
* How do you roll back a change?
* Do you test the rollback procedures before deployment?
* How do you deploy the configuration to different stages?
* Do you error-and-syntax check your configuration before deployment?
* What are the dependencies for deployment?
* Does your deployment support immutability? Does your deployment update/upgrade software in-place?
* Do you perform load testing before deploying to production?


---

## 8 - Operations
* Describe how the on-call rotation for your service looks like.
* Do you have easily available and complete links to the documentation for the service?
* Do you have well defined, documented, and accessible recovery procedures? 
* Describe the escalation path in the event of an outage (include timing expectations).
* Does the trouble-ticketing system integrates with the monitoring system?
* Does the paging system integrates with the monitoring system?


---

## 9 - Disaster Recovery
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