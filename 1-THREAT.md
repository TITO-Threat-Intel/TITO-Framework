# Step 1: Evaluating the Threat

The TITO Framework for Threat Intelligence always starts with an understanding and ranking of the **THREAT**. It's foundational in threat intelligence to define what it means to be a threat, and you can't outsource this. Aligning what you consider a threat based on on an industry vertical doesn't really work because attacks don't happen by vertical in the real world. Chasing blogs doesn't work either -- in fact, it's a clear sign of an immature threat intel program, or even worse: an inexperienced leadership team which pushes their InfoSec experts to focus only on the latest news stories and respond to crises. 

Most commercial Threat Intelligence companies can't define your threat for you either, because they don't have the data necessary to tailor intelligence in a way that's impactful. Enter, the TITO Framework 

The TITO Framework starts with the threat, but it also has a prerequisite: that you well understand the business, mission, or objective you're trying to perform in spite of your adversaries, and what you're trying to protect to accomplish this. The things you're trying to protect could be crown jewel IT or OT systems for example, or critical infrastructure; or anything else that, if compromised, would result in failure. *Compromise* here refers to the measurable impact from a breach in confidentiality, integrity, or availability, of course.

## The Four Elements in a Threat

There are many ways to describe a threat, but it's important to note that not *everything* that is present and dangerous is actually a threat! Sounds counterintuitive, I know, but consider this notional scenario: 

A threat actor develops a new exploit leveraging a previously unknown 0-day in the latest Windows Server version. The threat actor is interested in harvesting credit card information from databases, and collects the data for the purpose of buying goods through major retailer online shops and diverting the goods overseas through reshippers recruited through romance scams, fake job advertisements; and through shipping label fraud. This sounds serious! Now imagine your business uses only Linux servers, collects and stores no credit card data, and has encrypted data at rest and in motion at the database servers anyways. Is this still a threat? It's a threat to **someone**, sure. Just, not to you, right now. Leave these things for your tools to find and fix as they patch and update signatures; for your threat hunters to find as they search for C&C communications and data exfiltration. Understanding which threat actors are active and working is important, but it's more important to search for and fail to find badness with real potential impact, than to focus on the newest thing, even if present and active. What I'm saying is, unless you are drowning in threat intel analysts, opportunity costs apply.

In my view, *threat* is comprised of these four elements:

* Active Technique (or, Capability): Is a threat actor or exploit in the wild capable of targeting you? Are they actively using a technique sophisticated enough to compromise your network, hosts, applications, or people? If so, identify where this is possible and map to a framework of choice, explicitly. Be sure to document the references clearly, in case others need to validate your findings. Note that if the threat is social engineering or the threat actor routinely uses 0-days, this will almost definitely apply. **Score 1 point** for the bay guys. 

* Intent: Has the threat actor (or exploit) overtly stated or materially demonstrated they have a specific goal in mind? Do they tend to target one OS type, one company or group of companies (for example, financial institutions or insurance companies), or specific country assets? If you fall into this group, **Score 1 point** for the bad guys again. 

* Visibility in Logs (or, Past Actions): Have you actually had this threat actor or exploit compromise your protected environment, either in intelligence sources, breach notifications, security alerts, hunts, or infections? If so, you'll most likely see it again: Success breeds success when it comes to breaches, so **Score 1 point** for the adversary, once again.

* Critical & Vulnerable (or, Operating Environment): Think about your internal systems. I recognize internal means something different than in the past -- where we used to talk about hardware-defined perimeters, DMZs and bastion hosts; we now include protected enclaves, software-defined perimeters, and identity-as-perimeter. This means *internal* today might include protected data in the cloud accessed on a personal device. In any case, if you know where your crown jewels and critical assets are and where they are accessed, you should priortize them for patching, hardening and protection upgrades, defense in depth, monitoring and response, and auditing. These are elements of the operating environment. If you have a particularly large attack service, remote workers, legacy hardware challenges, a large OT environment, staff shortages... these things will factor in to the equasion, too. If there is a new 0-day in the wild and there is a working exploit for it in the wild, you better believe this factors into the operating environment. Bottom line, if the operating environment favors the attacker, **Score 1 point** for threat. 

## Scoring the Threat

As you can see, there is a ranking built here off binary, yes/no answers to the questions above. Capability and intent are external factors, while actions and the operating environment are much more of internal considerations (things we control or influence based on our decisions - past, present and future). All you have to do is add up where you gave points, based on the above criteria, to get a score of 0-4. 

Here's a chart for threat scoring you can use to evaluate what threats to baseline, track, hunt for, build detections for, etc.:

Threat Score | Threat Level | Action to Take | Message to Leadership
------------ | ------------ | -------------- | ---------------------
0 | No Threat | Ignore | Business as Usual
1 | Emerging Threat | Monitor for Change | Be Vigilant
2 | Present Threat | Implement Mitigations | Be Wary
3 | Critical Threat | Proactive Tracking | Breach is Likely
4 | Crisis | All Hands on Deck | Breach Imminent

As you can see, business or mission determines what is critical, targeting or the ability to exploit critical things drives the definition of threat, and threat drives our message. It also drives response actions, which will be outlined in Step 3. 

## Tying it All Together

Now that you know how to score (0-4), you know what a threat is and what threats to prioritize. But, there are literally countless *candidate* threats out there. Where do you start? 

It's simple, really. Attackers always have an **objective** in mind. Ask yourself (or even better, ask all your stakeholders):

* What data or capacity do you have, that an attacker would want to compromise or steal for their own purposes? 
* What networks, hosts, and people are critical to your business or mission? 

The intersection of these are where you should start. Remember our notional case, where the threat actor was looking to profit off stolen credit card data? Think about what **you** have that others might want to target, and whether it is critical to your business, operations, reputation, revenue generation, service offering, etc. What threat actors or groups overtly target these things? Which are most active today? What tactics, techniques, and procedures do these groups or individuals use to accomplish their objectives? You should be able to come up with a short list doing research. Examining malware that has impacted your organization already is also a great place to start. Learn everything you can about these groups, and track their TTP evolutions over time. Understand their favorite tools and exploits, who develops them, where they are bought and sold, and how these tools evolve over time. Learn how they like to deliver exploits. Become experts in your *present* and *critical* threats, and know who your *emerging* threats are. Above all, use a framework to describe threats in a common language! For example, if you're talking about a threat actor using RTLO (U+202E) text to make a filename look benign, or running a malicious rundll32.exe out of a temp file, you might want to call all of these types of attacks **Defense Evasion/Masquerading**. There's nothing worse than having a team working on a problem set, and finding months down the road that everyone was describing the same thing in a different way. Doing so makes threat actor TTP evolution tracking impossible.

Once you have your baseline of threats identified, and all are properly scored, you need to bridge this over to operations and work to *reduce* the threat score. I'll cover this in **Step 3: Bridge to Operations**. Next up though is **Step 2: Threat Tracking (the, "ITO")**.

Thanks for reading! -Tom S.