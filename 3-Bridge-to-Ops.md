# Part 3: Bridge to Operations

Now that I've set the stage with broad, sweeping, and up to now rather esoteric definitions, let me change things up and present a more step-by-step approach. In this part I'll talk about the actions you should take to use this framework, building mitigations that allow you to:

1. Remove high-priority threats; and 
2. Reduce the impact of the threats that remain

Generally, the process looks like this: 

![alt text](https://github.com/TITO-Threat-Intel/TITO-Framework/blob/master/TITO-Framework.jpg "TITO Framework")

First things first, we need to evaluate the threat. How do we do this, when it seems *everything* can target us? One gap, one new 0-day, and we're owned. Right? Yes, but... let's focus first on what we can manage. The idea here is to prioritize based on potential impact to our mission or business and broaden down from there. There's a saying you've probably heard: "You can't boil the ocean." In this first phase we're casting a net for the most dangerous fish, pulling them into a tidepool, and we'll boil those waters first. Really, what we're trying to do is focus, because not everything is a threat. Consider this:

![alt text](https://github.com/TITO-Threat-Intel/TITO-Framework/blob/master/IMG_034BDA4D50D3-1.JPG "Threats we care about")

## Evaluating and Reducing the Threat (The "T")

In this phase, we determine, "threat or not." It's not as simple as tracking a threat group. I've created this graphic to demonstrate why it's not really possible to track a threat actor group alone:

![alt text](https://github.com/TITO-Threat-Intel/TITO-Framework/blob/master/TrackThreatsHalf.jpg "Categories for tracking")

Do we need to track threat groups? Yes, we do. First though, it's important to narrow things down. Many threat intel providers tell you what to track: Threat Actor A, IOCs related to Malware B. It's all important, yes, but you *MUST* start with PIRs. Without PIRs, you don't know where your gaps are. You can't set signposts and indicators of change. You can't really apply any analyst tradecraft. I'm my view, It's probably best to do something like this when you track threats:

![alt text](https://github.com/TITO-Threat-Intel/TITO-Framework/blob/master/Threat%20Tiers%20Half.jpg "Tracking heirarchy")

Let me break it all into steps.

### Step 1: Active Techniques

* Know (or write!) your PIRs 
    * Identify systems and data critical to enabling the business or mission
    * Consider what the Information Ecosystem looks like that makes it all work
    * List what are the critical elements, mapped to the CIA Triad 
* Considering the list of data and assets above, identify which threat actors or individuals target this currently. You can accomplish this by:
    * Tasking an external partner to do research
    * Researching current threats to systems yourself
    * Looking at malware which has already targeted your critical Information Ecosystem elements and look at which external threat actors frequently use these techniques
* Take the above set of Threat Actors, decide on a naming convention or framework for how to track, and map their techniques and tools to a framework of choice

If you've spent a day on the above with the business and your teams collectively, you can come up with a solid list of TTPs that are most relevant to your business case. They must have a common naming convention that describes the technique adequately, yet is standard enough to use across threat actor families. If you use the Kill Chain, you'll probably need to add sub-categories. If you use the MITRE ATT&CK framework, you may need to add custom techniques for Mac, Linux, mobile systems, etc. This is something to discuss with your leadership.

Congratulations! You've just accomplished **Step 1** of Threat Evaluation. You've identified **Active Techniques**. All threat groups, threat actors, and malware campaigns that use these techniques you've identified will get **one point added to their base threat score**.

### Step 2: Threat Actor has Intent

Now that you've identified active techniques, you should understand which threat actors, malware, or individuals use these techniques.

* Search for similar techniques, processes exploited, or tools used in the wild
* List threat groups, threat actors, and malware campaigns involved; map their TTPs
* Determine if you are being targeted directly
    * Are there indications the groups in this list are directly interested in compromising (or have previously compromised) elements of your Information Ecosystem, or similar infrastructure at other companies; or are targeting your company/organization by name? 
    * Have they targeted data of others, unique to the industry vertical, suggesting a pattern?
    * If you answered *yes* to either of the questions above, there is INTENT. **Add 1 point to the base threat score for these entities.**

* Expand your research out to understand which threat actors or groups have compromised those running the same infrastructure, the same security tools, who have very similar data, exist in the same industry vertical; or who have specifically stated an intent to target the company or organization by name. *These threats should also get **one point**, and their TTPs should be evaluated, even if they don't seem to be a threat to your business or organization at this time.*

If you've done the above, you can now say you have identified what threat groups have intent. Time to move to step 3.

### Step 3: Visibility in Logs

Link up with your incident response team lead, Blue Team lead, SOC Director, or Sr. Analysts as applicable. They can help you determine the following:

* What incidents have you seen active in your organization in the last 6 months that have:
    * Been persistent or repetitive
    * Progressed beyond defense mechanisms
    * Been detected at a late stage (e.g. command and control, data exfiltration, execution of destructive process)
* Red Team activities that have gone undetected or penetrated the organization's defenses

Map these techniques to threat actor groups, individuals, or malware campaigns in the wild and **add 1 point to the base threat score** for these groups. If there's an intersection with one of the threat actors on the list you created in Step 1 and/or Step 2, it goes without saying those groups' base threat scores have increased either to 2 or 3 at this point. Remember our scoring convention from earlier:

Threat Score | Threat Level | Action to Take | Message to Leadership
------------ | ------------ | -------------- | ---------------------
0 | No Threat | Ignore | Business as Usual
1 | Emerging Threat | Monitor for Change | Be Vigilant
2 | Present Threat | Implement Mitigations | Be Wary
3 | Critical Threat | Proactive Tracking | Breach is Likely
4 | Crisis | All Hands on Deck | Breach Imminent

Congratulations! If you've gotten this far, you've done the groundwork to get **Visibility in Logs**, a catch-all term for seeing evidence from internal data sources of threat actors and their tools in your environment. In case you were wondering, I do consider all Red Team activity as threat actor behavior!

### Step 4: Critical & Vulnerable

This stage is all about the operating environment... the *Critical and Vulnerable*. This is where we consider everything that keeps your CISO up at night. Your job here is to create a final list of threat actor TTPs and tools that are:

* All over the news, which will likely lead the CISO to ask, "are we protected from this"?
* New 0-days
* Newly weaponized and commoditized (e.g., new Metasploit module available, or POC released on a researcher blog)
* Likely to be successful because patching hasn't occurred in a timely fashion
* New and targeting legacy infrastructure that can't be immediately replaced
* May impact areas where there is no visibility, or no defense in depth
* Likely to weaken defenses (security stack vulnerabilities)
* Expensive and/or impossible to mitigate (e.g. National Infrastructure attacks)

If there's a unique, internal issue that makes a threat actor technique, tool, or malware campaign particularly dangerous to your company or organization, **add 1 point to the base threat score**. Again, if these intersect with something already on the list, increase that score by 1. 

Great! You've reached the end of the first step to operationalizing threat intelligence - *identifying the threat*. So far you've:

* Listed expected threats to your data, infra, and people, per your PIRs
* Pivoted to look for the external groups, TTPs, tools associated with these threats
* Looked in your logs and internal sources for past or active threats
* Considered newsworthy events and unique internal challenges

You've also grouped and started tracking everything by:

* PIR First
* Then, by named threat group, actor or campaign; tool; TTP per a framework
* Finally, by IOC (+ IOC pivoting)

**NOTE:** Tracking all this in a spreadsheet, blog, etc. is a terrible idea. Make sure you use a system where you can use *tags*. Knowlege management is outside the scope of this framework, but it needs to be considered at the start of any asset tracking endeavor. 

**Reducing the Threat** is critical to threat prioritization, and this is *Step 5*. Once you've added a point, what do we do to *remove* that point?

### Step 5: Removing Points

* Run **Micro Red Teaming** exercises to test all *Active Techniques*. Micro Red Teaming, in a nutshell, is the testing of a single adversary TTP at a time across an entire organization to find defensive gaps.
    * Look at all TTPs on a heat map using your framework of choice
    * Develop scripts, tests; or deploy tools that emulate or execute these TTPs to test whether a technique would be successful against your organization
    * If you can eliminate enough TTPs in an attack chain, you can **remove the point** from that threat actor for **Active Techniques**
* Track threat actor intent decay to target your organization per Step 2, above
    * Look at how active a threat actor or tool TTP is in targeting your organization 
    * If the tool or technique hasn't been seen, or no similar data or company in a similar vertical has been targeted by this threat actor in 6 months or more (or longer, if the retool and attack cycle by this threat is long) **remove the point** from that threat actor for **Intent to Target** 
* For past attacks, assume your threat actor has established persistence mechanisms, command and control channels, and is still exfiltrating data or abusing your resources
    * Create Hunt hypotheses and conduct retrospective hunting across your entire organization
    * If no trace of the threat actor is found after doing this for some time, **remove the point** you gave for **Visibility in Logs**
* Finally, you should build in effective mitigations for *Critical and Vulnerable* items as they appear in the wild or become apparent based on your infrastructure or team composition. If you can significantly remove the impact of a current event or an internal vulnerability/weakness, **remove the point** from **Critical and Vulnerable**. 

Alright! Now you know how to add points to a threat, and how to remove points. I know in most organizations, Threat Intelligence won't be running Threat Hunting or a leading a Red Team. They likely won't be developing mitigating controls to threats, or be involved in patching systems as a Vulnerability Management team might. However, if your company or organization wants to **reduce** the threats from these threat actors or groups based on the TITO Framework, Threat Intel will provide feedback to assist stakeholders executing these efforts. We can even use the scoring to automate ticket generation, point removal when the tickets are closed, and an automatic reprioritization of threats to the org based on the actions taken. 

If Threat Intelligence identifies an elevated risk based on TITO elements, provides the evidence, and gives the organization real levers to reduce this score, you'll have a direct and measurable impact to security. Or, if there's resistance, you can wait it out and let natural decay reduce the score for you. Not ideal, but it's a method and you'll certainly have done your job providing the appropriate threat warning. 

Threats with points are *Ongoing Threats* and to mitigate these, there are a few things to do in parallel to the above. Those are covered in the next section below. 

## Mitigations for Ongoing Threats (The "ITO")

So far, I've talked about how to scope threats and how to deprioritize or remove threats. While you do this, you should work on countering the effectiveness of threat actors by introducing as much friction as possible to them. This will look different for every organization or business -- mainly because organizations come in all sizes, levels of maturity, and complexity. Also, the threats will differ depending on your own internal IT investments as well as the data and resources that are critical, so you'll need to identify defense gaps every time you add or remove a threat actor from your *ongoing threats* list. 

### Step 1: Infrastructure

You can slow most threat actors and commodity threats by identifying and de-fanging infrastructure used to target your information ecosystem. As a threat intelligence analyst, identifying bad infrastructure and pivoting to find associated attack vectors should be part of your normal routine. Are you looking for fast flux DNS, DGAs, known proxies and TOR exit notes? Are you looking at passive DNS? Do you have a handle on bulletproof hosting providers? Have you looked at web or proxy logs for badness? Start with what you can do, and work to fill in visibility gaps. So you should: 

* Mitigate malicious infrastructure:
    * Using technical solutions such as email gateways, WAFs, anti-phishing tools, DNS monitoring/blocking, zero trust/software defined perimeter tools, IPS, MFA, etc. (Match solution with attacker methods!)
    * Rate limiting
    * Blacklisting/Blocking -- **use caution** doing this: There may be unforeseen consequences to operations!
    * Sinkholing
    * Proxying to a honeypot/honeynet
    * Reporting/Initiating account takedowns
    * Etc. (your case will determine actions!)
* Continue to monitor threat actor for changes in infrastructure used (find data gaps) or attempts to circumvent your mitigations (both inbound and outbound)

If you can block or mitigate the adversary's infrastructure, you will greatly reduce the impact of the threat.

### Step 2: Target

In the adversary's chain of attack or attack scheme, there will be a logical target. Is the attacker going after individuals in your finance department? Does the attacker target unpatched Windows servers with a specific exploit? Does the attacker attempt to disable a specific security tool? There are many more questions you can ask, but you get the point. Your goal here should be to identify the systems targeted by the attacker internally. If you you've already mapped attacker TTPs to a standard framework you can simply map **ATTACKER TTP** --> **SYSTEM/PERSON/DATA IMPACTED BY TTP**. The latter is the *target* of the attack, and you can do this for each phase of the attacker scheme as it pertains to your information ecosystem.

Again, this will look different for every organization or business. Build a list of your resources targeted by your threat actors, campaigns, etc.

* Identify what data you have that indicates the attacker is manipulating or accessing your resource 
    * If you don't have visibility, work to fill the gap
    * If you already have visibility, make sure the severity of alerts for that asset are raised 
* Harden the targeted assets
    * Add additional threat detection and prevention resources, if possible
    * Limit privileges, admins, accessibility from the targeted resource
    * Patch and modernize!
    * Backup the data and build in redundancies for this asset
* Initiate threat hunts, assuming the actor is already in your environment (if found unexpectedly, you may need to up the threat score!)

If you've done a thorough assessment of what resources or systems are being targeted and take these steps, your SOC/Blue Team will be in a better position to respond to and defend these assets.

### Step 3: Outcomes

Every attacker has a motivation, but this may be hard to know or discover. Even if we could, it would be very hard to influence this. Every attacker does have a *scheme* in mind however, and by examining attacker behavior, targets, and origins we can build logical stories or use cases for what the attacker might be trying to accomplish -- their desired *outcomes*. If we understand this, it helps us disrupt attackers' chances for success at many levels.

#### Map the Scheme

* Considering past actions, targets, and stated motivations; make a list of every possible hypothesis for *what a threat actor hopes to achieve* by targeting your data, people, or resources. Some are easy to imagine: for example, a ransomware attack. Other may be more difficult. Use historical examples, your own experience, and notional scenarios based on logic. 

* Build alternative stories
    * What are the known or attempted targets of the threat actor or group you're following?
    * What exactly has the threat actor **done** to access or misuse the target? This is the *Action*.
    * What, in your estimation, is the attacker **trying to achieve** by taking above action? This is the *Objective*. 
    * How does the above objective help the attacker **further** the scheme? This is the *Result*.
* Build the attack chain, or *scheme*, end to end, by filling in the following blanks:

![alt text](https://github.com/TITO-Threat-Intel/TITO-Framework/blob/master/AttackScheme.jpg "Schemes")

Build as many hypotheses on the attack scheme as possible, looking for intersections across *actions* and *outcomes* in multiple stories. By doing this, you'll find quick wins; that is, things you can influence by your own actions or defenses that will have the biggest impact to the attacker.

#### Defeat the Scheme

Now that you know what the attacker is doing, and have estimated the probable next step, you can build defenses against possible future actions. This is how we build a *predictive* threat intelligence capability. These things will be **highly** specialized to the business or organization. 

* **De-incentivize**: List what provides value to the attacker in the scheme, and remove the value. For example, if your attacker targets credentials you can use salted hashes, enable MFA globally, etc.
    * In the sentence, The attacker does ________(action) in order to ________(outcome), allowing him/her to ________(result); your action should keep the attacker from doing bridging the outcome and result.
    * Even if the attacker manages to accomplish the *outcome* then, the *result* will not be what the attacker expects
* **Remove Feedback Loop**: Look at what the attacker is trying to accomplish, the *outcome*, and determine how the attacker knows if he/she is successful. Are they expecting a certain server response? A particular banner message? A specific http status code? Can you delay the drop in a connection? If you can determine your traffic is not legitimate, provide random or confusing results that keep the attacker from being able to retool or know where their attack failed. Immediate feedback is the worst! 
* **"Booby trap"** the attacker's process flow. If you can identify attacker infrastructure or targets, even retrospectively, blocking and forgetting may not be the best answer. Use *honeytokens*, fake portals, fake leaked credentials, fake documents... use your imagination. The idea is to create high fidelity signals that alert you to badness without damaging the user experience of legitimate users. You want to increase the friction here to attackers. 

For the above three steps, remember to first build the stories, and then look for the actions you can take that have the biggest impact across intersections in your hypotheses. This way you can have the biggest impact to attacker behavior. You're not looking for the most *diagnostic* data to prove your hypothesis, you're trying to cause the most possible friction to the attacker. In an *Analysis of Competing Hypotheses* exercise you'd typically throw out common observations as non-diagnostic. We don't want to do that here. We WANT to see those commonalities, the "choke points," in adversarial behavior. This is where we draw in the attacker; detect, deceive, and defeat them. 

## In Summary (aka, "Keeping it Simple")

In summary, the framework has two key phases: 

1) Identify what is a threat, and take actions to remove this threat (The "T"). The -**T**- is finding and cutting the head off the beast.
2) Prioritize what threats remain or are active, and mitigate them (The "ITO") 
    * The -**I**- helps by working against external attacker infrastructure
    * The -**T**- helps by defending and hardening internal information nodes and links (e.g., servers and ports)
    * The -**O**- helps by defending against data attacks

Key elements that enable the framework:
* Start with PIRs (your link to impact-to-business), track responsiveness to PIRs, and group threats in context of ability to compromise the information ecosystem in context of PIRs
* Track named threat groups, campaigns; and collect IOCs in context of PIRs
* The analyst's job is to "think about thinking," identifying data gaps and hidden relationships. If you're not doing this, you can (and should) be replaced by a robot. =)
* Proactively grow your internal stakeholders: Threat Intel should be a service to all Defenders.

Finally, these are just my thoughts, **a** way but not **the** way, to operationalize threat intelligence to have a real impact on security. They reflect my personal opinions; and in no way reflect the opinions or methods of operations of any of my employers, current or past.

Take what is useful, throw out the rest; and at the very least, let's have meaningful discussions that lift us all. 

## Sample Threat Intelligence Metrics 

Here's a small sample of metrics you can use to determine if your efforts are having an impact on security to your business or organization, based on this framework:

* Threat: How many threat actor groups have a score of 2 or greater? *Work to reduce % of threat actors with a score 2 or greater*.
* Threat: How long does a threat actor sit at score 4/3/2 without a reduction? *Work to reduce the time it takes to reduce the threat score*.
* Infrastructure: What percentage of active attack vectors have mitigations built in? *Strive for 100%*.
* Targets: On what percentage of Targets have you developed or increased visibility? Defense in depth? *Strive for 100%*.
* Outcomes: How often are fake data, randomized responses, or deceptions triggered? What is the FP rate? *Work to drive FP rate to zero*.
