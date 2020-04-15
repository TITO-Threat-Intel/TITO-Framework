# Step 2: Threat Tracking

Once you've identified the *threat* as defined in **Step 1**, it's time to track relevant and actionable information. This means moving on to the other three elements of the TITO Framework, namely, the "-ITO."

The TITO framework is grouped into two core phases, with four elements. In essence, identifying THREAT tells you **where** to apply the rest of the framework. If you successfully mitigate the threat by removing points, you no longer have to go through the -ITO elements for those threats. Think of TITO then as a living creature, and by eliminating the first *T*, you've cut the head off the beast: you no longer have to worry about the arms and legs.

As long as the threat still exists, you need to be doing the rest of these things:

## I: Infrastructure

While identifying and tracking infrastructure used by a threat actor in an incident (yours or someone else's) seems intuitive, it can be rather complex and challenging to do. If you've tracked your threat actors for a while and retrospectively examine attacks, you will develop a sense of where attacks originate. Some questions you may ask are:

* Do the threat actors I'm tracking use botnets, TOR exit nodes, or proxy lists?
* What ASNs do they prefer? Are they residential, commercial, corporate/private, cloud-based?
* What email patterns, DNS patterns, text patterns, and temporal patterns are used?
* What user agents are presented at entry points? Are they headless? Are they tool or test-kit based?
* How do they (or do they even try to) hide their origin?
* How often do they change infrastructure used?
* When they build and test exploits, do they use their own infrastructure?
* Where do they go to learn about, develop, test, and/or buy infrastructure?
* How do they identify themselves in forums, IRC, chats, etc.?
* Do they leverage mobile infrastructure or mobile emulators?
* How do they pay for services? Are they rented, or hijacked?
* How long does the infrastructure used typically last before it is burned, flagged, or blacklisted?

This is just a short list off the top of my head -- I'm sure I missed a lot but you get the point. Ask as many questions as you can, because the more you find patterns in and log, the better you'll be able to set a baseline for the threat and identify changes. This becomes super important later.

Notice I didn't offer any specific tools, vendors, or data sets here. There are *countless* numbers of sources, some great and some just OK. I've literally evaluated hundreds in the past couple years, and I can say honestly that the best solution is the one that best fits the threats you face and the resources -- people, money, and institutional support -- you have available. For the same reason, I've left the definition of infrastructure fairly loose, too. In my brainstormed list of questions above, I've called out both infrastructure and potential markers of the acquisition and development of new infrastructure. Both are important.

Also note, I didn't talk a lot about *attribution* either. I've had many conversations with CISOs, executives, and technical experts alike, and while all agree attribution is extremely hard, I tend to argue it's not super important in most cases. I feel attribution only matters in so much as you're willing (or able) to take action on this information. Law enforcement and government certainly care about this very much, and should. Businesses shouldn't care as much, for the most part. It's certainly case-by-case and may be necessary in yours, but attribution isn't for the faint of heart -- you'd better have the resources to do it; and a strong, experienced analytical team that understands how to mitigate the inevitable confirmation bias that will certainly be present. 

In nearly every case, tracking infrastructure (past, current, and potential future) is relevant. In almost every case, an adversary is going to HAVE to come in direct contact with your infrastructure, hosts, or people. Identifying the vehicle used to do this gives you insight into your attackers' sophistication level, plus possible evolutions. What you do with that information is covered in **Step 3**. More to come on this.

## T: Targets

*Target* in TITO refers to the systems targeted by attackers. **System** in this case refers not only to an endpoint, but to *all* the elements of your information ecosystem. This can certainly be endpoints, but is also much more: users (human and robotic), IAM systems, VPN portals, web-facing applications, individual hosts, active directory, cloud resources (IaaS, PaaS, SaaS, etc.) to name a few. This ecosystem will look different for every company, agency, organization. When assessing the target, you're looking for the collision of the attacker's tactics, techniques, proceedures, and tools on your information ecosystem. Forget about the objective for now.  

Here are some sample questions you may ask when assessing the target attackers may be trying to compromise. This is where chains, attack paths, etc. all come into play. Read: Diamond Model of Intrusion Analysis, Kill Chain, OODA loop, MITRE ATT&CK, etc. Take your attacker infrastructure apart from the lens of your favorite assessment framework and ask questions:

* How is malware, (or general "badness") delivered to the ecosystem? 
* Where does the threat first come in contact with your information ecosystem? Is it at the network? Email? WebApp?
* Which people are targeted for social engineering or phishing?
* Which internal systems need to be co-opted or leveraged? How does the attacker move laterally? How does this look compared to normal traffic or users? 
* What systems, scripts, or tools do they leverage, install, download, and/or execute? 
* How do they do they conduct C&C? How do they exfil data? What ports and protocols are favored?
* Do they use advanced encryption, XOR, or Base64 anywhere?
* How do attackers abuse or disable security features to cover their tracks and/or move invisibly?

Understanding the approach attackers use to touch your ecosystem, move through it, and action their objectives or desired outcomes helps you develop *signposts & indicators* of compromise. Once you develop these indicators, you can start becoming predictive, develop contingency plans, harden your critical information ecosystem nodes and links, build depth in alerting, prioritize backup and recovery capability deployment, prioritize patching and system upgrades; and generally do some other advanced things to cause as much friction to your adversaries as possible. While all these things may seem to be outside the scope of threat intelligence, I assure you they're not - you just haven't sold your craft and shown your value to the right internal stakeholder!

## O: Outcomes

Before we simplify, score, and and operationalize everything, let's talk about threat actors' desired outcomes, or simply *outcomes*. In my observation, most threat intel providers seem to create big buckets for understanding motivation, which has it's place but is a bit different from *outcomes*. Attackers can be called *nation state*, *criminal*, *activist*, or any other range of label; and all threat actor groups or individuals are dumped into these buckets. Generally speaking, threat intel providers do this for the sake of scaleability. In reality motivations are enigmatic -- sometimes attackers themselves don't understand their own motivations -- and so we should consider them purposefully using analytical tradecraft. In fact, the **analysis of competing hypotheses** technique works very well for assessing threat motivations. Doing this will help you identify the most diagnostic indicators of motivation and build in signpost and indicators of change. Understanding attacker categories and motivations then is useful but not implicitly actionably so, outside of the scope of TITO.

refers to the full chain of events an attacker undertakes to see the scheme through to the end. Each stage has an objective, and we need to map these schemes. Consider an simple example to illustrate what I mean by *outcomes* and *objectives*.:

Imagine a criminal would like make some extra cash. Through DNS brute forcing, this threat actor has found a large dump of user credentials in an open file share, and has decided to test these credentials using an automated tool on paid streaming video sites, subscription services, etc. About 4 percent of these credentials woreked on common paid sites, and the threat actor has listed these accounts for sale on a .onion page. Here's how this scheme would look: 

Action | Objective | Result
------ | --------- | ------
Access File Share | Find Credentials | Obtains Credentials to Test
Create Automated Tool Confiig | Weaponize Tool | Automate Attack on Subscription Sites
Scan Subscription Sites | Find Valid Credentials | Build List of Valid Credentials to Sell
Create .onion | Offer List for Sale | Host Safe Purchase Site
Post .onion on IRCs, Forums, Etc. | Market Subscription Accounts Sale | Generate Sales
Create Bitcoin Address | Facilitate Secure Payment | Monetize
Buy Gift Cards with Bitcoin | Launder Payments | Safely Access Money

Of course this is notional, very simple, but you get the point. In this table, **Action** is *what the attacker does*. The **Objective** is *what the attacker hopes will happen* by taking this action, and the **Result** is *how this helps further the scheme*. In summary, the attacker does an **action** to meet an **objective** that **results** in the scheme continuing to be successful. 

I want to point out that in most cases we won't be able to link this together in any complete way. We may only have visibility on one small part of the scheme! If you work for a large subscription service provider and you find your users' accounts are being taken over frequently, you may not know how it happened. You may have no way to see what attackers are doing to obtain leaked credentials. What we *can* see are the attacker coming in contact with our infrastructure. If we've identified where to start, developed a list of threats we need to track, and worked to identify the infrastructure these threat actors use, we can do something about it. "Doing something" probably isn't blocking based on atomic indicators, by the way. In fact, in this case, it's probably not even possible. I'll cover how to operationalize in **Step 3: Bridge to Operations**. We know then what we have of value, what threat actors might target this, with what tools; and what infrastructure they generally use. We know what assets in our information ecosystem they are targeting or are likely to target; and have a good idea, even if notional, of how they intend to meet their desired outcomes. These data points, for the threat actors we track, form the foundation of the actionable data we have. 

Threat intel analysts can do a ton of other things at the **tactical** level, to support a SOC as they deal with alerts and assess what is critical, interesting, or trivial. Threat intel analysts can spend a lot of time thinking **strategically**, assessing trends to help inform tool deployment solutions or infrastructure investments, or doing threat warning, for example. TITO is focused on *operations*, where 80% of the threat intelligence analyst's time should be spent.
