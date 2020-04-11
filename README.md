     _________  ___  _________  ________     
    |\___   ___\\  \|\___   ___\\   __  \    
    \|___ \  \_\ \  \|___ \  \_\ \  \|\  \   
         \ \  \ \ \  \   \ \  \ \ \  \\\  \  
          \ \  \ \ \  \   \ \  \ \ \  \\\  \ 
           \ \__\ \ \__\   \ \__\ \ \_______\
            \|__|  \|__|    \|__|  \|_______|

# TITO-Framework

## TITO is a light framework for operationalizing threat intelligence that is platform and data agnostic.

What does this mean? Let's examine the parts of this objective statement. "Light" means TITO is not heavily prescriptive. It's not intended to be a how-to guide for threat intelligence, but more of a *how-about* guide. "Operationalizing threat intelligence" means TITO helps bridge the gap between threat identification and concrete actions to reduce the threat in a measurable way. "Data agnostic" means there's no prescribed data feed, subscription, vendor, or InfoSec solution here that is offered: TITO is a framework, not a tool. 

## Background: Whither Threat Intelligence 

There are many versions of threat intelligence operationalized out in the wild. For most, and especially for those who graduated into the world of threat intelligence with a primarily dev or IR background, it seems threat intel means we do the following:

### Workstream Sample 1: 
* Identify an InfoSec threat
* Gather Indicators of Compromise (IOCs)
* Create detection logic
* BONUS: Decay or "age out" indicators

This work is important, and has a place in any IR and threat detection program. But, for those who think this is **all** there is to threat intelligence, you probably won't find this repo valuable. For those if us who grew up in intelligence analysis and pivoted into cyber threat intelligence or cyber intelligence, there's another missing piece. For us, the process looks a little more like this:

### Workstream Sample 2:
* Identify stakeholders and understand stakeholders' information needs
* Develop plan to fill information needs
* Collect relevant information
* Process information, correlate data; assess suitability, reliability, relevance
* Identify diagnostic information, consider key assumptions; build hypotheses, test
* Uncover data gaps and hidden relationships
* Craft finished products that answer stakeholder questions; and deliver on time, in a useable format
* Fight for feedback, and incorporate this into future assessments

As you can see, the second path doesn't care so much about WHAT to do. It's more of a process guide for the Threat Intel Analyst to follow, if he/she wants to provide unbiased information that is relevant. I see threat intelligence slowly moving in this direction. I have a lot of thoughts about *why* this is happening slowly, but I'll spare you and keep them to myself. Bottom line: The analysts job isn't to be a data collection monkey. Routine, structured data can be automated and in fact is, by many out there. The true analyst is paid to *think about thinking*, not about the problem. The problem is provided by the stakeholder codefied into intelligence requirements, and managed by the threat intelligence program manager. Is some cases, in small organizations, these may all be the same person even if they're different roles. 

If you're talking about support to operations (I'll acknowledge but skip over support to strategic decision making here), you have really two things going on: First is the **tactical support** to front-line network defenders. These are your IR analysts or third-party support analysts, your tooling that generates alerts. These are the help desks, the employees that notice something "just isn't right," and the auditors who discover anomalies after the fact as well. Second is **operational intelligence support**, which aims to merge new data in light of old to paint a better or more complete picture of the overall threat. In **Workstream Sample 1**, there are good things happening; however, let's examine Workstream Sample 1 in context of Sample 2:

* Identify an InfoSec Threat
    * Who determines what is a threat? (Identify Stakeholders) 
    * Who wants to know the answer? (Fill Information Needs)
    * How do we prioritize threats if I'm really busy? (Collect Relevant Information)
* Gather IOCs
    * What do we gather? (Collect Relevant Information)
    * Have we collected this before? (Process Information)
    * What does it tell us about a threat? (Uncover Gaps and Hidden Relationships)
* Create detection login
    * Will this create false positives? (Craft Finished Products, Fight for Feedback)
    * Will this negatively impact operations? (Craft Finished Products, Fight for Feedback)
    * How will I know it works? How do I know when it stops working? (Craft Finished Products, Fight for Feedback)
* BONUS: Decay or "age-out" indicators 
    * How much of my giant blacklist is still relevant? (Fight for Feedback)
    * How can I make my list more relevant in the future? (Fight for Feedback)

You can see how, in the above context, **Workstream Sample 1** is still good work. But, we have a lot of thinking to do about what the impact of this effort is on the big picture, and thinking like **Workstream 2** allows us to do this. **Workstream 2** also opens up a whole other world of assessments we can do, based on the deep and rich history of analyst tradecraft, to support the business or the mission, operations, tactics; and the full spectrum of decision-makers in between.

## In Summary

I realize my examples here are oversimplified and incomplete -- but, they're for illustration purposes only and not meant to belittle the work anyone is doing. There are many wonderful threat intelligence analysts our there, and many are intuitively achieving great wins for their organizations. But, I think we can all do better - from the most junior to the most elite professionals. 

In my opinion, the way we do better is by all getting *on the same page*. I always say, you can't solve any problem alone, and a group can't solve any problem without first agreeing on what the problem is. The best way to reach *agreement* on the problem here is to build a taxonomy or framework, and the best way to evaluate a framework is to build in a scoring mechanism based on as empirical of data as we can collect. I'd like to do this in a way that is super easy for InfoSec professionals to adopt, and this is why I'm sharing **TITO** with you all. 

Thanks for reading!
