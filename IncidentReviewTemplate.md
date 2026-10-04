# Incident Review Template

Every incident is an expensive lesson about the gap between how work is imagined and how it is actually done. This template helps teams extract maximum learning value from that cost by understanding not just what broke, but what the breakage reveals about gaps in understanding how systems actually work.

This is about learning, not blame. Incident analysis helps teams discover why their mental models were incomplete and how to build better adaptive capacity.

## How to Use This Template

This is not THE template. It is A template. Treat it as a starting point for developing your organization's approach to learning from incidents. Make it yours. Adapt the questions to your context, add your own insights, and modify sections to fit your culture and needs.

The template provides structure while allowing flexibility to explore the unique aspects of each incident. Not every question will be relevant to every situation. Select those that help you understand what happened and why.

**Getting started**

- Start early. Begin the process immediately after an incident while details are fresh.
- Include diverse perspectives. Everyone involved should participate in the analysis.
- Evolve gradually. You don't need to transform your entire process overnight. Introduce new questions alongside existing practices.
- Share widely. Analyses should be shared across teams to spread learning.
- Follow through. Track action items and ensure lessons influence future decisions.

## Moving Beyond Root Cause Analysis

Complex systems never have single root causes. Instead, they have multiple contributing factors that accumulate over time and combine to create incidents. Traditional "5 Whys" approaches can lead to oversimplified conclusions and missed opportunities for systemic improvement.

This template uses a systems thinking approach that explores multiple contributing factors instead of seeking one root cause, uses open-ended questions that promote understanding rather than defensiveness, examines the context, pressures, and constraints that shaped decisions, and focuses on learning and adaptation.

**Key principles**

**Multiple contributing factors.** Look for the accumulation of contributing factors that combined to create the incident.

**Blameless and open.** Focus on the systemic conditions and decision-making contexts behind individual actions. Use language that promotes learning over blame.

**Second stories over first stories.** The first story is "someone made a mistake." The second story asks why the action made sense given the person's knowledge, time pressure, and available information. Second stories reveal learning opportunities that first stories obscure.

**Learning-focused.** Emphasize what surprised you, what assumptions proved wrong, and how your mental models need updating.

**Single-loop versus double-loop.** Single-loop analysis fixes the specific problem. Double-loop analysis questions the assumptions and mental models that made the problem possible. Push toward double-loop.

**The WAI-WAD gap.** Work-as-Imagined and Work-as-Done always differ, and most days the gap goes unnoticed. An incident shows where it mattered: the gap grew, or conditions changed in ways the system had never experienced. Analysis should discover where that gap existed and what it reveals about broader patterns.

**Where these ideas come from.** Blameless postmortems: John Allspaw. Second stories: Richard Cook, David Woods, and Sidney Dekker. Single- and double-loop learning: Chris Argyris and Donald Schön. Work-as-Imagined and Work-as-Done: Erik Hollnagel.

## Language That Promotes Learning

- Use "contributing factors" instead of "root cause"
- Say "systemic conditions" rather than "human error"
- Frame issues as "unexpected behavior" or "surprises"
- Focus on "learning" rather than defaulting to new preventive measures. Learning means understanding the conditions that enabled the problem. Adding controls after every incident ends in controls over controls.
- Ask "what about the system made this outcome likely?" rather than "who made the mistake?"

## Developing Precise Vocabulary

Teams benefit from developing precise vocabulary for failure modes, propagation patterns, and incident characteristics. Vague descriptions like "database performance problem caused outage" don't enable pattern recognition or deep learning. Precise descriptions like "table lock contention from maintenance operation blocked application queries, causing timeouts that tripped circuit breakers and spread failures to dependent services" describe specific mechanisms that can be reasoned about and compared to other incidents.

When multiple incidents share specific characteristics despite different immediate causes, that pattern suggests systemic issues. The pattern becomes visible only when there's vocabulary to describe it.

## Interview Approach

- Adopt a learning mindset. Emphasize that the goal is understanding and improvement, not assigning blame.
- Seek the second story. When someone describes what happened, ask what made their actions reasonable at the time. What did they know? What didn't they know? What pressures existed?
- Listen actively. Pay attention to hesitations, uncertainties, or emotional responses that may indicate areas to explore further.
- Encourage storytelling. Allow people to narrate their experience rather than just answering discrete questions.
- Probe with care. When a response reveals a potential area for deeper understanding, follow up while maintaining psychological safety.
- Consider multiple perspectives. Interview different stakeholders to build a comprehensive picture.
- Document context, not just answers. Capture the conditions, constraints, and considerations that influenced decisions.

---

## Template Structure

1. Title
2. Incident Details
3. Owner & Review Committee
4. Classification
5. Executive Summary
6. Supporting Data
7. Customer Impact
8. Incident Response Analysis
9. Post-Incident Analysis
10. Timeline
11. Contributing Factors Analysis
12. Surprises & Learning
13. Action Items
14. Learning Loops & Knowledge Sharing

*The template ends with a quality checklist to run before you publish.*

---

## 1 - Title

Descriptive title that captures the essence of the event.

*Example: "Service XYZ degradation affecting EU customers due to database connection exhaustion"*

---

## 2 - Incident Details

- Incident date. Date and time of the event (include timezone).
- Duration. Total time from start to full resolution.
- Severity. High/Medium/Low based on customer impact.
- Detection method. How was the incident first detected? (monitoring, customer report, etc.)

---

## 3 - Owner & Review Committee

- Owner. Name of the person leading the analysis process.
- Peer-review committee. List of people who will verify the quality of the analysis before publishing.
- Team members involved. Everyone who participated in the incident response.

---

## 4 - Classification

- Tags. Keywords to classify the event for future search and analysis. Examples: Configuration, Database, Dependency, Latent-defect, Capacity, Deployment.
- Incident type. Outage, Degradation, Near-miss, Surprising-behavior.
- Systems involved. List of all services/components that played a role.

---

## 5 - Executive Summary

- What happened. Brief description of the event in plain language.
- Why it mattered. Impact on customers and business.
- What we learned. Key insights in 2-3 bullet points.
- What we're doing. Top 3 action items to address what we learned.

---

## 6 - Supporting Data

Include metric graphs, tables, logs, or other data that best illustrate:

- The impact and progression of the incident
- System behavior before, during, and after the event
- Evidence supporting your analysis and conclusions

---

## 7 - Customer Impact

- Customers affected. Specific number or percentage of impacted customers.
- Geographic impact. Which regions/locations were affected.
- Functionality impact. What features or capabilities were degraded/unavailable.
- Duration of impact. How long customers experienced issues.
- Business impact. Revenue loss, SLA breaches, reputation impact.

---

## 8 - Incident Response Analysis

Analyze how well your incident response process worked.

**Detection & Notification**

- Was the event detected within the expected time?
- How was it detected? What worked well or poorly about detection?
- How could time to detection be improved?
- Did notifications and escalations work appropriately?

**Response & Mitigation**

- How did responders know what actions to take?
- Who coordinated the response? How were roles assigned?
- What runbooks or procedures were used? How well did they work?
- How could time to mitigation be improved?
- What communication challenges occurred during response?
- How and when were customers told what was happening?
- How did you confirm the event was fully resolved?

---

## 9 - Post-Incident Analysis

Examine the technical and process aspects.

**Diagnosis & Understanding**

- How were the contributing factors diagnosed?
- What made diagnosis difficult or easy?
- How could time to diagnosis be improved?

**Change Management**

- Did a change trigger this event? How was it deployed?
- What safeguards did the deployment have? How did they behave?
- How was this change tested? What would make testing catch this type of issue?
- If manual, was there a runbook? When was it last practiced?

**Systemic Questions**

- Did you have backlog items related to this? What were they competing with?
- What programmatic verification would catch this type of issue?
- When was the last operational readiness review conducted on this system?

---

## 10 - Timeline

Detailed timeline of major events with timestamps (include timezone).

Format: Time - Description - Supporting evidence

*Example:*
- 09:19 EEST - Database connection pool exhausted, new requests failing - database metrics
- 09:21 EEST - First customer reports received - support tickets
- 09:23 EEST - Alert fired: DB_CONNECTION_POOL_HIGH - alerting history
- 09:25 EEST - On-call engineer paged - pager log

---

## 11 - Contributing Factors Analysis

Move beyond "5 Whys" to understand the complex interactions that created conditions for this incident. Instead of seeking a single root cause, explore multiple contributing factors across different dimensions. Use open-ended questions that promote understanding rather than defensiveness.

### Discovery & Context

- How did you first become aware of the issue?
- What were you working on when you noticed it?
- What were the operational conditions when the incident happened?
- How would you describe the normal functioning of this system?
- What was the state of the system before the incident occurred?
- Were there any recent changes to processes, systems, or personnel?

### Decision-Making Under Uncertainty (The Second Story)

Understanding why actions made sense at the time reveals learning opportunities that blame obscures.

- What options did you consider at various points?
- How did you decide which action to take?
- What constraints (time, resources, access) influenced your decisions?
- What information would have been helpful but wasn't available?
- How confident were you in your assessment of the situation?
- How did this make sense to everyone involved at the time?

### Organizational Context & Pressures

- What trade-offs do you regularly navigate in your work?
- Were there organizational pressures (deadlines, resource constraints) that influenced decisions?
- What competing priorities existed during this time period?
- How are priorities typically communicated during incidents?
- What unstated expectations exist about handling such situations?
- What were we afraid to talk about before this problem happened?

### Human Factors & Working Conditions

- Were there signs of fatigue, stress, or high workload?
- How long had you been working prior to the incident?
- Were there distractions or interruptions that affected your work?
- What was the emotional climate during the incident response?
- How prepared did you feel for this specific situation?

### Communication & Coordination

- How was critical information shared among team members?
- Were there any misunderstandings or communication gaps?
- How clear were instructions and procedures?
- Who knew things that others didn't?
- Were there barriers to speaking up about concerns?
- How did handoffs between teams work?

### Technical Systems & Environment

- Was all equipment and tooling functioning as expected?
- How did the tools you were using affect your ability to respond?
- Were monitoring systems providing the right information?
- What assumptions about system behavior proved incorrect?
- How did different parts of the system interact during the incident?

### Propagation & Cascades

Understanding how the incident spread reveals interaction patterns and dependencies that might not be well understood.

- Why did a localized problem cause broader impact?
- What coupling or dependencies allowed the failure to propagate?
- Why didn't isolation mechanisms contain the failure?
- What resilience mechanisms (circuit breakers, timeouts, retries) were involved? How did they behave?
- What about this propagation pattern was surprising?

### Warning Signs & Missed Signals

- Were there warning signs or precursors to this incident?
- What near-misses have occurred that might relate to this incident?
- Were relevant concerns raised before but not addressed?
- What barriers or safeguards didn't work as expected?
- What signals were available but not recognized as important at the time?
- What would monitoring have needed to catch this earlier?

### Knowledge & Preparedness

- What knowledge and training did this situation call for?
- Were procedures and documentation accessible and accurate?
- What type of practice or rehearsal had been done for this scenario?
- What knowledge gaps became apparent during the incident?
- Where was critical knowledge concentrated rather than distributed?

**Remember.** Never stop at "human error" or "process failure." These are symptoms, not explanations. Dig deeper into the systemic conditions that made errors likely and processes ineffective.

---

## 12 - Surprises & Learning

Focus on what challenged your understanding and expectations. The goal is not just to fix what broke, but to understand why your mental models of the system were incomplete. These surprises are opportunities to build better adaptive capacity.

**WAI-WAD Gap Discovery**

- Where did Work-as-Imagined diverge from Work-as-Done?
- What assumptions about how the system works proved incorrect?
- What assumptions about how operations work proved incorrect?
- What assumptions about where knowledge lives proved incorrect?

**Surprises & Updated Mental Models**

- What surprised you most during this incident?
- Where did your understanding of the system prove incorrect?
- What mental models need updating based on this event?
- How did the system fail differently than you anticipated?
- What "normal" behaviors during the incident might indicate deeper issues?

**What Worked Well**

- What worked better than expected that you should do more of?
- What adaptations did people make that prevented worse outcomes?
- What knowledge or skills proved valuable during response?

**Systemic Patterns**

- Have you seen incidents with similar characteristics before?
- What patterns across incidents suggest systemic issues rather than isolated failures?
- What does this incident reveal about how the organization thinks, designs, or operates?

---

## 13 - Action Items

Address multiple contributing factors, not just immediate technical issues. List specific, actionable items that address the various systemic conditions that contributed to this incident.

**Format for each action item**

- Title. Clear description of the action.
- Owner. Person responsible for completion.
- Due date. Realistic timeline for completion.
- Priority. High/Medium/Low based on impact and effort.
- Contributing factor addressed. Which systemic issue this addresses.
- Success criteria. How you'll know it's done correctly.
- Backlog link. Link to tracking system item.

**Categorize action items by type**

**Technical improvements**

- System design changes to reduce coupling
- Better monitoring and observability
- Tool improvements to reduce error-prone manual work
- Infrastructure changes to improve resilience

**Process improvements**

- Guardrails for high-risk changes
- Better escalation and communication protocols
- Improved documentation and knowledge sharing
- More effective testing and validation processes

**Organizational improvements**

- Training and skill development
- Workload and priority management
- Cultural changes to improve psychological safety
- Better support for decision-making under uncertainty

**Learning investments**

- Regular practice and simulation exercises
- Cross-team knowledge sharing sessions
- Documentation of mental models and assumptions
- Mechanisms to capture and act on weak signals

*Example: "Implement gradual deployment tooling to catch configuration issues before full rollout - Sarah - July 15th - High priority - Addresses deployment process contributing factor - Can deploy to 5% of fleet and validate before proceeding - [JIRA-123]"*

Ensure action items address contributing factors from multiple categories, not just the immediate technical fix.

---

## 14 - Learning Loops & Knowledge Sharing

Insights from incident analysis should inform other resilience practices. If practices don't reference each other, learning stays siloed.

**Chaos Engineering**

- What chaos experiments should we design based on what this incident revealed?
- What assumptions about system behavior should we test?
- Which of the failure modes we discovered should we deliberately inject?

**Load Testing**

- What load testing scenarios does this incident suggest?
- What monitoring gaps did we discover that load testing could help validate?
- What performance thresholds need verification?

**Operational Readiness Reviews**

- What operational knowledge should future ORRs examine based on this incident?
- What documentation gaps did this incident reveal?
- What questions should we add to our ORR template?

**GameDays**

- What coordination scenarios should we practice based on this incident?
- What response challenges emerged that warrant rehearsal?
- What communication patterns need improvement?

**Knowledge Sharing**

- Internal sharing. How will you share findings with related teams?
- Documentation updates. What runbooks, guides, or procedures need updating?
- Training needs. What training or education should result from this incident?
- Cross-team applicability. Which other teams might benefit from these insights?
- Follow-up timeline. When will you check that action items are completed and effective?

---

## Quality Checklist

Before publishing your incident analysis, ensure the following.

- [ ] Analysis is blameless and focuses on systems, not individuals.
- [ ] Second stories are captured. We understand why actions made sense at the time.
- [ ] Contributing factors go beyond immediate technical causes.
- [ ] Timeline is complete with supporting evidence.
- [ ] Action items address contributing factors, not just symptoms.
- [ ] Surprises and learning insights are captured.
- [ ] What worked well is captured. We know what kept this from being worse.
- [ ] WAI-WAD gaps are identified. We know where imagined diverged from actual.
- [ ] Learning loops are documented. Insights will inform other practices.
- [ ] Knowledge sharing plan ensures lessons spread.
- [ ] All action items have owners and realistic timelines.
- [ ] Customer impact is clearly quantified.
- [ ] Supporting data validates your conclusions.
- [ ] Patterns across incidents are considered. We looked for systemic issues.
