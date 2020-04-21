# Part 3: Bridge to Operations

Now that I've set the stage with broad, sweeping, and up to now rather esoteric definitions, let me change things up and present a more step-by-step approach. In this part I'll talk about the actions you should take to use this framework and the mitigations that allow you to:

* Remove high-priority threats
* Reduce the impact of the threats that remain

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

### Step 1: 

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

Congratulations! You've just accomplished **Step 1** of Threat Evaluation. You've identified **Active Techniques**. All threat groups, threat actors, and malware campaigns that use these techniques you've identitied will get **one point added to their base threat score**.

### Step 2:

Now that you've identified active techniques, you should understand which threat actors, malware, or individuals use these techniques.

* Search for similar techniques, processes exploited, or tools used in the wild
* List threat groups, threat actors, and malware campaigns involved; map their TTPs
* Determine if you are being targeted directly
    * Are there indications the groups in this list are directly interested in compromising (or have previously compromised) elements of your Information Ecosystem, or similar infrastructure at other companies; or are targeting your company/organization by name? 
    * Have they targeted data of others, unique to the industry vertical, suggesting a pattern?
    
**If so, they have INTENT. Add 1 point to the base threat score for these entities.**

* Expand your research out to understand which threat actors or groups have compromised those running the same infrastructure, the same security tools, who have very similar data, exist in the same industry vertical; or who have specifically stated an intent to target the company or organization by name. *These threats should also get one point, and their TTPs should be evaluated, even if they don't seem to be a threat to your business or organization at this time.

If you've done the above, you can now say you have identified what threat groups have intent. Time to move to step 3.

### Step 3: 

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

### Step 4:

This stage is all about the operating environment... the *Critical and Vulnerable*. This is where we consider everything that keeps your CISO up at night! Your job here is to create a final list of threat actor TTPs and tools that are:

* All over the news, which will likely lead the CISO to ask, "are we protected from this"?
* New 0-days
* Newly weaponized and commodotized (e.g., new Metasploit module available, or POC released on a researcher blog)
* Likely to be successful because patching hasn't occured in a timely fashion
* New and targeting legacy infrastructure that can't be immediately replaced
* May impact areas where there is no visibility, or no defense in depth
* Likely to weaken defenses (security stack vulnerabilities)
* Expensive and/or impossible to mitigate (e.g. National Infrastructure attacks)

If there's a unique, internal issue that makes a threat actor technique, tool, or malware campaign particularly dangerous to your company or organization, **add 1 point to the base threat score**. Again, if these intersect with something already on the list, increase that score by 1. 

Great! You've reached the end of the first step to operationalizing threat intelligence - *identifying the threat*. So far you've:

* Listed expected threats to your data, infra, and people, per your PIRs
* Pivoted to look for the external groups, TTPs, tools associated with these threats
* Looked in your logs and interal sources for past or active threats
* Considered newsworthy events and unique internal challenges

You've also grouped and started tracking everything by:

* PIR First
* Then, by named threat group, actor or campaign; tool; TTP per a framework
* Finally, by IOC (+ IOC pivoting)

**NOTE:** Tracking all this in a spreadsheet, blog, etc. is a terrible idea. Make sure you use a system where you can use *tags*. Knowlege management is outside the scope of this framework, but it needs to be considered at the start. of any asset tracking endeavor. 

**Reducing the Threat** is critical to threat prioritization, and this is *Step 5*. Once you've added a point, what do we do to *remove* that point?

### Step 5:

1. Run **Micro Red Teaming** exercises to test all *Active Techniques*. Micro Red Teaming, in a nutshell, is the testing of a single TTP across an entire organization.
    * Look at all TTPs on a heat map of your framework of choice
    * Develop scripts, tests; or deploy tools that do these things to test whether a technique would be successful against your organization
    * If you can eliminate enough TTPs in an attack chain, you can **remove the point** from that threat actor for **Active Techniques**.
2. Track threat actor intent decay to target your organization per Step 2, above.
    * Look at how active a threat actor or tool TTP is in targeting your organization. 
    * If the tool or technique hasn't been seen, or no similar data or company in a similar vertical has been targeted by this threat actor in 6 months or more (or longer, if the retool and attack cycle by this threat is long) **remove the point** from that threat actor for **Intent to Target**. 
3. For past attacks, assume your threat actor has established persistence mechanisms, command and control channels, and is still exfiltrating data or abusing your resources.
    * Create Hunt hypotheses and conduct retrospective hunting across your entire organization
    * If no trace of the threat actor is found after doing this for some time, **remove the point** you gave for **Visibility in Logs**. 
4. Finally, you should build in effective mitigations for *Critical and Vulnerable* items as they appear in the wild or become apparent based on your infrastructure or team composition. If you can significantly remove the impact of a current event or an internal vulnerability/weakness, **remove the point** from **Critical and Vulnerable**. 

Alright! Now you know how to add points to a threat, and how to remove points. I know in most organizations, Threat Intelligence won't be running Threat Hunting or a Red Team. They likely won't be developing mitigating controls to threats, patching systems as a Vulnerability Mangement team might. However, if your company or organization wants to **reduce** the threats from these threat actors or groups based on the TITO Framework, they will build in these steps. They can even use the scoring to automate ticket generation, point removal when the tickets are closed, and an automatic reprioritization of threats to the org based on the actions taken. If Threat Intelligence identifies the elevated risk based on TITO elements, provides the evidence, and gives the organization real levers to reduce this score, you'll have a real measurable impact to security. Or, if there's resistance, you can wait it out and let natural decay reduce the score for you. Not ideal, but it's a real method and you'll certainly have done your job providing the appropriate threat warning. 

Threats with points are *Ongoing Threats* and to mitigate these, there are a few things to do in parallel to the above. Those are covered in the next section below. 

## Mitigations for Ongoing Threats (The "ITO")

### Step 1: 

## TITO Maturity

## In Summary (aka, "Keeping it Simple")

## Metrics 


**Every actor, group, or campaign on this list gets 1 point added to their name for having active techniques.** Again, you should decide on a naming convention for all. This is your baseline for threat actor groups and at this point, 

* 
