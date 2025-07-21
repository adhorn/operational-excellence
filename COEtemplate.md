### Investigation Guidelines

**Language that promotes learning**:
* Use "contributing factors" instead of "root cause"
* Say "systemic conditions" rather than "human error"  
* Frame issues as "unexpected behavior" or "surprises" rather than "failures"
* Focus on "learning" rather than "preventing"
* Describe "influences" instead of "causes"

**Interview approach**:
* **Adopt a learning mindset**: Emphasize that the goal is understanding and improvement, not assigning blame
* **Listen actively**: Pay attention to hesitations, uncertainties, or emotional responses that may indicate areas to explore further
* **Encourage storytelling**: Allow people to narrate their experience rather than just answering discrete questions
* **Probe with care**: When a response reveals a potential area for deeper understanding, follow up while maintaining psychological safety
* **Consider multiple perspectives**: Interview different stakeholders to build a comprehensive picture
* **Document context, not just answers**: Capture the conditions, constraints, and considerations that influenced decisions# Correction-of-Error (COE) Template

## Introduction

A Correction-of-Error (COE) is our mechanism to learn from incidents, near-misses, and surprising system behaviors. We use COEs to understand not just what went wrong, but **why our defenses didn't work as expected** and how we can build better adaptive capacity.

**This is about learning, not blame.** COEs help us celebrate the learning from our mistakes and the ownership that teams display when things don't go as planned. That's why we often call this the "Celebration-of-Error."

### Moving Beyond Traditional Root Cause Analysis

Complex systems never have single root causes. Instead, they have **multiple contributing factors** that accumulate over time and combine to create incidents. Traditional "5 whys" approaches can lead to oversimplified conclusions and missed opportunities for systemic improvement.

This template uses a **systems thinking approach** that:
- Explores multiple contributing factors instead of seeking one root cause  
- Uses open-ended questions that promote understanding rather than defensiveness
- Examines the context, pressures, and constraints that shaped decisions
- Focuses on learning and adaptation rather than blame and prevention

### Key Principles

**Multiple contributing factors**: Complex systems never have single root causes. Look for the accumulation of contributing factors that combined to create the incident.

**Blameless and open**: Focus on systemic conditions and decision-making contexts, not individual actions. Use language that promotes learning over blame.

**Learning-focused**: Emphasize what surprised you, what assumptions proved wrong, and how your mental models need updating.

**Context matters**: Understand the pressures, constraints, and environment that shaped decisions during the incident.

**Systems thinking**: Incidents emerge from interactions between people, technology, and organizational factors - not linear cause-and-effect chains.

### How to Use This Template

This is not THE template — it is A template. Treat it as a starting point for developing your organization's approach to learning from incidents. **Make it yours.** Adapt the questions to your context, add your own insights, and modify sections to fit your culture and needs.

The template provides structure while allowing flexibility to explore the unique aspects of each incident. Not every question will be relevant to every situation - select those that help you understand what happened and why.

**Getting started**:
- **Start early**: Begin the COE process immediately after an incident while details are fresh
- **Include diverse perspectives**: Everyone involved should participate in the analysis  
- **Evolve gradually**: You don't need to transform your entire process overnight - introduce new questions alongside existing practices
- **Share widely**: COEs should be shared across teams to spread learning
- **Follow through**: Track action items and ensure lessons influence future decisions

**Language that promotes learning**:
* Use "contributing factors" instead of "root cause"
* Say "systemic conditions" rather than "human error"  
* Frame issues as "unexpected behavior" or "surprises" rather than "failures"
* Focus on "learning" rather than "preventing"
* Describe "influences" instead of "causes"

**Interview approach**:
* **Adopt a learning mindset**: Emphasize that the goal is understanding and improvement, not assigning blame
* **Listen actively**: Pay attention to hesitations, uncertainties, or emotional responses that may indicate areas to explore further
* **Encourage storytelling**: Allow people to narrate their experience rather than just answering discrete questions
* **Probe with care**: When a response reveals a potential area for deeper understanding, follow up while maintaining psychological safety
* **Consider multiple perspectives**: Interview different stakeholders to build a comprehensive picture
* **Document context, not just answers**: Capture the conditions, constraints, and considerations that influenced decisions

---

## Template Structure

1. Title
1. Incident Details
1. Owner & Review Committee
1. Classification
1. Executive Summary
1. Supporting Data
1. Customer Impact
1. Incident Response Analysis
1. Post-Incident Analysis
1. Timeline
1. Contributing Factors Analysis
1. Surprises & Learning
1. Action Items
1. Knowledge Sharing Plan

---

## 1 - Title
Descriptive title that captures the essence of the event
*Example: "Service XYZ degradation affecting EU customers due to database connection exhaustion"*

## 2 - Incident Details
* **Incident date**: Date and time of the event (include timezone)
* **Duration**: Total time from start to full resolution
* **Severity**: High/Medium/Low based on customer impact
* **Detection method**: How was the incident first detected? (monitoring, customer report, etc.)

## 3 - Owner & Review Committee
* **Owner**: Name of the person leading the COE process
* **Peer-review committee**: List of people who will verify the quality of the COE before publishing
* **Team members involved**: Everyone who participated in the incident response

## 4 - Classification
* **Tags**: Keywords to classify the event for future search and analysis
  *Examples: Configuration, Database, Dependency, Latent-defect, Capacity, Deployment*
* **Incident type**: Outage, Degradation, Near-miss, Surprising-behavior
* **Systems involved**: List of all services/components that played a role

## 5 - Executive Summary
* **What happened**: Brief description of the event in plain language
* **Why it mattered**: Impact on customers and business
* **What we learned**: Key insights in 2-3 bullet points
* **What we're doing**: Top 3 action items to prevent recurrence

## 6 - Supporting Data
Include metric graphs, tables, logs, or other data that best illustrate:
* The impact and progression of the incident
* System behavior before, during, and after the event
* Evidence supporting your analysis and conclusions

## 7 - Customer Impact
* **Customers affected**: Specific number or percentage of impacted customers
* **Geographic impact**: Which regions/locations were affected
* **Functionality impact**: What features or capabilities were degraded/unavailable
* **Duration of impact**: How long customers experienced issues
* **Business impact**: Revenue loss, SLA breaches, reputation impact

## 8 - Incident Response Analysis
Analyze how well your incident response process worked:

**Detection & Notification**:
* Was the event detected within the expected time?
* How was it detected? What worked well or poorly about detection?
* How could time to detection be improved?
* Did notifications and escalations work appropriately?

**Response & Mitigation**:
* How did responders know what actions to take?
* What runbooks or procedures were used? How well did they work?
* How could time to mitigation be improved?
* What communication challenges occurred during response?
* How did you confirm the event was fully resolved?

## 9 - Post-Incident Analysis
Examine the technical and process aspects:

**Diagnosis & Understanding**:
* How were the contributing factors diagnosed?
* What made diagnosis difficult or easy?
* How could time to diagnosis be improved?

**Change Management**:
* Did a change trigger this event? How was it deployed?
* Could safeguards in deployment have prevented this?
* Was this change tested? Why didn't testing catch this issue?
* If manual, was there a playbook? When was it last practiced?

**Preventive Measures**:
* Did you have backlog items that could have prevented this? Why weren't they prioritized?
* Could programmatic verification have caught this?
* When was the last ORR conducted on this system?

## 10 - Timeline
Detailed timeline of major events with timestamps (include timezone):

*Format: Time - Description - Supporting evidence*

*Example:*
* *09:19 EEST - Database connection pool exhausted, new requests failing*
* *09:21 EEST - First customer reports received*
* *09:23 EEST - Alert fired: DB_CONNECTION_POOL_HIGH*
* *09:25 EEST - On-call engineer paged*

## 11 - Contributing Factors Analysis

**Move beyond "5 Whys" to understand the complex interactions that created conditions for this incident.**

Instead of seeking a single root cause, explore multiple contributing factors across different dimensions. Use open-ended questions that promote understanding rather than defensiveness.

### Discovery & Context
* How did you first become aware of the issue?
* What were you working on when you noticed it?
* What were the operational conditions when the incident happened?
* How would you describe the normal functioning of this system?
* What was the state of the system before the incident occurred?
* Were there any recent changes to processes, systems, or personnel?

### Decision-Making Under Uncertainty
* What options did you consider at various points?
* How did you decide which action to take?
* What constraints (time, resources, access) influenced your decisions?
* What information would have been helpful but wasn't available?
* How confident were you in your assessment of the situation?
* How did this make sense to everyone involved at the time?

### Organizational Context & Pressures
* What trade-offs do you regularly navigate in your work?
* Were there organizational pressures (deadlines, resource constraints) that influenced decisions?
* What competing priorities existed during this time period?
* How are priorities typically communicated during incidents?
* What unstated expectations exist about handling such situations?
* What were we afraid to talk about before this problem happened?

### Human Factors & Working Conditions
* Were there signs of fatigue, stress, or high workload?
* How long had you been working prior to the incident?
* Were there distractions or interruptions that affected your work?
* What was the emotional climate during the incident response?
* Did you feel adequately prepared for this specific situation?

### Communication & Coordination
* Was critical information shared effectively among team members?
* Were there any misunderstandings or communication gaps?
* How clear were instructions and procedures?
* Who knew things that others didn't?
* Were there barriers to speaking up about concerns?
* How did handoffs between teams work?

### Technical Systems & Environment
* Was all equipment and tooling functioning as expected?
* How did the tools you were using affect your ability to respond?
* Were monitoring systems providing the right information?
* What assumptions about system behavior proved incorrect?
* How did different parts of the system interact during the incident?

### Warning Signs & Risk Management
* Were there warning signs or precursors to this incident?
* What near-misses have occurred that might relate to this incident?
* Were relevant concerns raised before but not addressed?
* What barriers or safeguards should have prevented this but didn't work as expected?

### Knowledge & Preparedness
* Did you have the necessary knowledge and training for this situation?
* Were procedures and documentation accessible and accurate?
* What type of practice or rehearsal had been done for this scenario?
* What knowledge gaps became apparent during the incident?

**Remember**: Never stop at "human error" or "process failure." These are symptoms, not explanations. Dig deeper into the systemic conditions that made errors likely and processes ineffective.

## 12 - Surprises & Learning
**Focus on what challenged your understanding and expectations**:

* **What surprised you most** during this incident?
* **Where did your understanding** of the system prove incorrect?
* What assumptions about normal system behavior were challenged?
* What mental models need updating based on this event?
* What worked better than expected that you should do more of?
* What "normal" behaviors during the incident might indicate deeper issues?
* **What would have helped you** respond more effectively?
* What information or tools would be useful for future incidents?
* How did the system fail differently than you anticipated?
* What pressures and constraints shaped the environment where decisions were made?
* What did you learn about how teams coordinate during stressful situations?
* What patterns emerged that you hadn't noticed before?

**Key insight**: The goal is not just to fix what broke, but to understand why our mental models of the system were incomplete. These surprises are opportunities to build better adaptive capacity.

## 13 - Action Items

**Address multiple contributing factors, not just immediate technical issues**:

List specific, actionable items that address the various systemic conditions that contributed to this incident:

**Format for each action item**:
* **Title**: Clear description of the action
* **Owner**: Person responsible for completion
* **Due date**: Realistic timeline for completion
* **Priority**: High/Medium/Low based on impact and effort
* **Contributing factor addressed**: Which systemic issue this addresses
* **Success criteria**: How you'll know it's done correctly
* **Backlog link**: Link to tracking system item

**Categorize action items by type**:

**Technical improvements**:
* System design changes to reduce coupling
* Better monitoring and observability
* Tool improvements to reduce error-prone manual work
* Infrastructure changes to improve resilience

**Process improvements**:
* Enhanced review procedures for high-risk changes
* Better escalation and communication protocols
* Improved documentation and knowledge sharing
* More effective testing and validation processes

**Organizational improvements**:
* Training and skill development
* Workload and priority management
* Cultural changes to improve psychological safety
* Better support for decision-making under uncertainty

**Learning investments**:
* Regular practice and simulation exercises
* Cross-team knowledge sharing sessions
* Documentation of mental models and assumptions
* Mechanisms to capture and act on weak signals

*Example: "Implement gradual deployment tooling to catch configuration issues before full rollout - Sarah - July 15th - High priority - Addresses deployment process contributing factor - Can deploy to 5% of fleet and validate before proceeding - [JIRA-123]"*

**Important**: Ensure action items address contributing factors from multiple categories, not just the immediate technical fix.

## 14 - Knowledge Sharing Plan
**How will lessons from this COE spread beyond your team?**

* **Internal sharing**: How will you share findings with related teams?
* **Documentation updates**: What runbooks, guides, or procedures need updating?
* **ORR integration**: How will these lessons influence future ORRs?
* **Training needs**: What training or education should result from this incident?
* **Cross-team applicability**: Which other teams might benefit from these insights?
* **Follow-up timeline**: When will you check that action items are completed and effective?

---

## COE Quality Checklist

Before publishing your COE, ensure:

- [ ] Analysis is blameless and focuses on systems, not individuals
- [ ] Contributing factors go beyond immediate technical causes  
- [ ] Timeline is complete with supporting evidence
- [ ] Action items address root causes, not just symptoms
- [ ] Surprises and learning insights are captured
- [ ] Knowledge sharing plan ensures lessons spread
- [ ] All action items have owners and realistic timelines
- [ ] Customer impact is clearly quantified
- [ ] Supporting data validates your conclusions