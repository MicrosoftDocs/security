# Microsoft Cybersecurity Defense Operations Center

![](/security/media/FY18CDOC_StrategyBrief_1.png")
Cybersecurity is a shared responsibility, which impacts us all. Today, a single breach, physical or virtual, can cause millions of dollars of damage to an organization and potentially billions in financial losses to the global economy. Every day, we see reports of cybercriminals targeting businesses and individuals for financial gain or socially-motivated purposes. Add to these threats those by nation-state actors seeking to disrupt operations, conduct espionage, or generally undermine trust.

In this brief, we share the state of online security, threat actors and the sophisticated tactics they employ to advance their goals, and how Microsoft’s Cyber Defense Operations Center combats these threats and helps customers protect their sensitive applications and data.

<table>
<tbody>
<tr>
<td><img src="/security/media/FY18CDOC_StrategyBrief_2.png"></td>
<td valign="top">
<h2>The Microsoft Cyber Defense Operations Center</h2>
Microsoft is deeply committed to making the online world safer for everyone. Our company’s cybersecurity strategies have evolved from the unique visibility we have into the rapidly evolving cyberthreat landscape.
<p>Innovation in the attack space across people, places, and processes is a necessary and continual investment we all need to make, as adversaries continue to evolve in both determination and sophistication. In response to increased investments in defense strategies by many organizations, attackers are adapting and improving tactics at breakneck speed.
Fortunately, cyberdefenders like Microsoft’s global information security teams are also innovating and disrupting long-reliable attack methods with ongoing, advanced training and modern security technologies, tools, and processes.</p>
<p>The Microsoft Cyber Defense Operations Center (CDOC) is one example of the more than $1 billion we invest each year on security, data protection, and risk management. The CDOC brings together cybersecurity specialists and data scientists in a 24x7 facility to combat threats in real-time.  We are connected to more than 3,500 security professionals globally across our product development teams, information security groups, and legal teams to protect our cloud infrastructure and services, products and devices, and internal resources.</p>
<p>Microsoft has invested more than $15 billion in our cloud infrastructure, with over 90 percent of Fortune 500 companies using the Microsoft cloud. Today, we own and operate one of the world’s largest cloud footprints with more than 100 geo-distributed datacenters, 200 cloud services, millions of devices, and a billion customers around the globe.</p>
<h2>Cybersecurity threat actors and motivations</h2>
The first step to protecting people, devices, data, and critical infrastructure is to understand the different types of threat actors and their motivations.
<ul>
<li><b>Cybercriminals</b> span several subcategories though they often share common motivations—financial, intelligence, and/or social or political gain. Their approach is usually direct—by infiltrating a financial-data system, skimming micro-amounts too small to detect and exiting before being discovered. Maintaining a persistent, clandestine presence is critical to meeting their objective.<br><br>Their approach may be an intrusion that diverts a large financial payout through a labyrinth of accounts to evade tracking and intervention. At times, the goal is to steal intellectual property that the target possesses so the cybercriminal acts as an intermediary to deliver a product design, software source code, or other proprietary information that has value to a specific entity. More than half of these activities are perpetrated by organized criminal groups.</li>
<li><b>Nation-state actors</b> work for a government to disrupt or compromise targeted governments, organizations, or individuals to gain access to valuable data or intelligence. They are engaged in international affairs to influence and drive an outcome that may benefit a country or countries. A nation-state actor’s objective is to disrupt operations, conduct espionage against corporations, steal secrets from other governments, or otherwise undermine trust in institutions. They work with large resources at their disposal and without fear of legal retribution, with a toolkit that spans from simple to highly complex.<br><br>Nation-state actors can attract some of the most sophisticated cyberhacking talent and may advance their tools to the point of weaponization. Their intrusion approach often involves an advanced persistent threat using supercomputing power to brute-force break credentials through millions of attempts at arriving at the correct password. They may also use hyper-targeted phishing attacks to attract an insider into revealing their credentials.</li>
<li><b>Insider</b> threats are particularly challenging due to the unpredictability of human behavior. The motivation for an insider maybe opportunistic and for financial gain. However, there are multiple causes for potential insider threats, spanning from simple carelessness to sophisticated schemes. Many data breaches resulting from insider threats are completely unintentional due to accidental or negligent activity that puts an organization at risk without being aware of the vulnerability.</li>
<li><b>Hacktivists</b> focus on political and/or socially-motivated attacks. They strive to be visible and recognized in the news to draw attention to themselves and their cause. Their tactics include distributed denial-of-service (DDoS) attacks, vulnerability exploits or defacing an online presence. A connection to a social or political issue can make any company or organization a target. Social media enables hacktivists to quickly evangelize their cause and recruit others to participate.</li>
</ul>
</td>
</tr>
</tbody>
</table>

![](/security/media/FY18CDOC_StrategyBrief_3.png)
### Threat actor techniques 
Adversaries are skilled at finding ways to penetrate an organization’s network despite the protections in place using various sophisticated techniques. Several tactics have been around since the early days of the Internet, though others reflect the creativity and increasing sophistication of today’s adversaries.

  - **Social engineering** is a broad term for an attack that tricks users into acting or divulging information they would otherwise not do. Social engineering plays on the good intentions of most people and their willingness to be helpful, to avoid problems, to trust familiar sources, or to potentially gain a reward. Other attack vectors can fall under the umbrella of social engineering, but the following are some of the attributes that make social engineering tactics easier to recognize and defend against:

      - **Phishing emails** are an effective tool because they play against the weakest link in the security chain—everyday users who don’t think about network security as top-of-mind. A phishing campaign may invite or frighten a user to inadvertently share their credentials by tricking them into clicking a link they believe is a legitimate site or downloading a file that contains malicious code. Phishing emails used to be poorly written and easy to recognize. Today, adversaries have become adept at mimicking legitimate emails and landing sites that are difficult to identify as fraudulent.

      - **Identity spoofing** involves an adversary masquerading as another legitimate user by falsifying the information presented to an application or network resource. An example is an email that arrives seemingly bearing the address of a colleague requesting action, but the address is hiding the real source of the email sender. Similarly, a URL can be spoofed to appear as a legitimate site, but the actual IP address is actually pointing to a cybercriminal’s site.

  - Malware has been with us since the dawn of computing. Today, we’re seeing a strong up-tick in ransomware and malicious code specifically intended to encrypt devices and data. Cybercriminals then demand payment in cryptocurrency for the keys to unlock and return control to the victim. This can happen at an individual level to your computer and data files, or now more frequently, to an entire enterprise. The use of ransomware is particularly pronounced in the healthcare field, as the life-or-death consequences these organizations face make them highly sensitive to network downtime.

  - **Supply chain insertion** is an example of a creative approach to injecting malware into a network. For example, by hijacking an application update process, an adversary circumvents anti-malware tools and protections. We are seeing this technique become more common and this threat will continue to grow until more comprehensive security protections are infused into software by application developers.

  - **Man-in-the-middle** attacks involve an adversary inserting themselves between a user and a resource they are accessing, thereby intercepting critical information such as a user’s login credentials. For example, a cybercriminal in a coffee shop may employ key-logging software to capture a users’ domain credentials as they join the wifi network. The threat actor can then gain access to the user’s sensitive information, such as banking and personal information that they can use or sell on the dark web.

  - **Distributed Denial of Service (DDoS)** attacks have been around more than a decade and are massive attacks are becoming more common with the rapid growth of the Internet of Things (IoT). When using this technique, an adversary overwhelms a site by bombarding it with malicious traffic that displaces legitimate queries. Previously planted malware is often used to hijack an IoT device such as a webcam or smart thermostat. In a DDoS attack, incoming traffic from different sources flood a network with numerous requests. This overwhelms servers and denies access from legitimate requests. Many attacks involve forging of IP sender addresses (IP address spoofing) also, so that the location of the attacking machines cannot easily be identified and defeated.
   
  Often a denial of service attack is used to cover or distract from a more deceptive effort to penetrate an organization. In most cases, the objective of the adversary is to gain access to a network using compromised credentials, then move laterally across the network to gain access to more “powerful” credentials that are the keys to the most sensitive and valuable information within the organization.

![](/security/media/FY18CDOC_StrategyBrief_4.png)
### The militarization of cyberspace 
The growing possibility of cyberwarfare is one of the leading concerns among governments and citizens today. It involves nation-states using and targeting computers and networks in warfare. 

Both offensive and defensive operations are used to conduct cyberattacks, espionage and sabotage. Nation-states have been developing their capabilities and engaged in cyberwarfare either as aggressors, defendants, or both for many years. 

New threat tools and tactics developed through advanced military investments may also be breached and cyberthreats can be shared online and weaponized by cybercriminals for further use.

### The Microsoft cybersecurity posture
While security has always been a priority for Microsoft, we recognize that the digital world requires continuous advances in our commitment in how we protect, detect, and respond to cybersecurity threats. These three commitments define our approach to cyber defense and serve as a useful framework for our discussion of Microsoft’s cyber defense strategies and capabilities.

## PROTECT
![](/security/media/FY18CDOC_StrategyBrief_5.png)

### Protect
Microsoft’s first commitment is to protect the computing environment used by our customers and employees to ensure the resiliency of our cloud infrastructure and services, products, devices, and the company’s internal corporate resources from determined adversaries.

The CDOC teams’ protection measures span across all endpoints, from sensors and datacenters to identities and software-as-a-service (SaaS) applications. Defense-indepth—applying controls at multiple layers with overlapping safeguards and risk mitigation strategies—is a best-practice across the industry and it’s the approach we take to protect our valuable customer and corporate assets.

Microsoft’s protection tactics include:

  - Extensive monitoring and controls over the physical environment of our global datacenters including cameras, personnel screening, fences and barriers, and multiple identification methods for physical access.

  - Software-defined networks that protect our cloud infrastructure from intrusions and DDoS attacks.

  - Multi-factor authentication is employed across our infrastructure to control identity and access management. It ensures that critical resources and data are protected by at least two of the following:

    - Something you know (password or PIN)
    - Something you are (biometrics)
    - Something you have (smartphone)

  - Non-persistent administration employs just-in-time (JIT) and just-enough administrator (JEA) privileges to engineering staff who manage infrastructure and services. This provides a unique set of credentials for elevated access that automatically expires after a pre-designated duration.

  - Proper hygiene is rigorously maintained through up-to-date, anti-malware software and adherence to strict patching and configuration management.
  
  - Microsoft Malware Protection Center’s team of researchers identify, reverse engineer, and develop malware signatures and then deploy them across our infrastructure for advanced detection and defense. These signatures are distributed to our responders, customers and the industry through Windows Updates and notifications to protect their devices.
  
  - Microsoft Security Development Lifecycle (SDL) is a software development process that helps developers build more secure software and address security compliance requirements while reducing development cost. The SDL is used to harden all applications, online services and products, and to routinely validate its effectiveness through penetration testing and vulnerability scanning.
  
  - Threat modeling and attack surface analysis ensures that potential threats are assessed, exposed aspects of the service are evaluated, and the attack surface is minimized by restricting services or eliminating unnecessary functions.

  - Classifying data according to its sensitivity and taking the appropriate measures to protect it, including encryption in transit and at rest, and enforcing the principle of least-privilege access provides additional protection. • Awareness training that fosters a trust relationship between the user and the security team to develop an environment where users will report incidents and anomalies without fear of repercussion.

Having a rich set of controls and a defense-in-depth strategy helps ensure that should any one area fail, there are compensating controls in other areas to help maintain the security and privacy of our customers, cloud services, and our own infrastructure. However, no environment is truly impenetrable, as people will make errors and determined adversaries will continue to look for vulnerabilities and exploit them. The significant investments we continue to make in these protection layers and baseline analysis enables us to rapidly detect when abnormal activity is present.

## DETECT
![](/security/media/FY18CDOC_StrategyBrief_6.png)

### Detect
The CDOC teams employ automated software, machine learning, behavioral analysis, and forensic techniques to create an intelligent security graph of our environment. This signal is enriched with contextual metadata and behavioral models generated from sources such as Active Directory, asset and configuration management systems, and event logs.

Our extensive investments in security analytics build rich behavioral profiles and predictive models that allow us to “connect the dots” and identify advanced threats that might otherwise have gone undetected, then counter with strong containment and coordinated remediation activities.

Microsoft also employs custom-developed security software, along with industryleading tools and machine learning. Our threat intelligence is continually evolving, with automated data-enrichment to more rapidly detect malicious activity and report with high fidelity. Vulnerability scans are performed regularly to test and refine the effectiveness of protective measures. The breadth of Microsoft’s investment in its security ecosystem and the variety of signals monitored by the CDOC teams provide a more comprehensive threat view than can be achieved by most service providers.

Microsoft’s detection tactics include:

  - Monitoring network and physical environments 24x7x365 for potential cybersecurity events. Behavior profiling is based on usage patterns and an understanding of unique threats to our services.
  
  - Identity and behavioral analytics are developed to highlight abnormal activity.
  
  - Machine learning software tools and techniques are routinely used to discover and flag irregularities.
  
  - Advanced analytical tools and processes are deployed to further identify anomalous activity and innovative correlation capabilities. This enables highlycontextualized detections to be created from the enormous volumes of data in near real-time.

  - Automated software-based processes that are continuously audited and evolved for increased effectiveness.
  
  - Data scientists and security experts routinely work side-by-side to address escalated events that exhibit unusual characteristics requiring further analysis of targets. They can then determine potential response and remediation efforts.

## RESPOND
![](/security/media/FY18CDOC_StrategyBrief_7.png)

### Respond
When Microsoft detects abnormal activity in our systems, it triggers our response teams to engage and quickly respond with precise force. Notifications from software-based detection systems flow through our automated response systems using risk-based algorithms to flag events requiring intervention from our response team. Mean-Time-to-Mitigate is paramount and our automation system provides responders with relevant, actionable information that accelerates triage, mitigation, and recovery.

To manage security incidents at such a massive scale, we deploy a tiered system to efficiently assign response tasks to the right resource and facilitate a rational escalation path. 

Microsoft’s response tactics include:

  - Automated response systems use risk-based algorithms to flag events requiring human intervention.
  
  - Well-defined, documented, and scalable incident response processes within a continuous improvement model helps to keep us ahead of adversaries by making these available to all responders.
  
  - Subject matter expertise across our teams, in multiple security areas, provides a diverse skill set for addressing incidents. Security expertise in incident response, forensics, and intrusion analysis; and a deep understanding of the platforms, services, and applications operating in our cloud datacenters.
  
  - Wide enterprise searching across cloud, hybrid and on-premises data and systems to determine the scope of an incident.
  
  - Deep forensic analysis for major threats are performed by specialists to understand incidents and to aid in their containment and eradication. • Microsoft’s security software tools, automation and hyper-scale cloud infrastructure enable our security experts to reduce the time to detect, investigate, analyze, respond, and recover from cyberattacks.
  
  - Penetration testing is employed across all Microsoft products and services through ongoing Red Team/Blue Team exercises to unearth vulnerabilities before a real adversary can leverage those weak points for an attack.

### Cyberdefense for our customers
We are often asked what tools and processes our customers can adopt for their own environment and how Microsoft might help in their implementation. Microsoft has consolidated many of the cyberdefense products and services we use in the CDOC into a range of products and services. The Microsoft Enterprise Cybersecurity Group and Microsoft Consulting Services teams engage with our customers to deliver the solutions most appropriate for their specific needs and requirements. 

One of the first steps that Microsoft highly recommends is to establish a security foundation. Our foundation services provide critical attack defenses and core identity-enablement services that help you to ensure assets are protected. The foundation helps you to accelerate your digital transformation journey to move towards a more secure modern enterprise. 

Building on this foundation, customers can then leverage solutions proven successful with other Microsoft customers and deployed in Microsoft’s own IT and cloud services environments. For more information on our enterprise cybersecurity tools, capabilities and service offerings, please visit Microsoft.com/security and contact our teams at cyberservices@microsoft.com.

### Best practices to protect your environment
| Invest in your platform | Invest in your instrumentation | Invest in your people |
| ----------------------- | :-----------------------------:| ---------------------:|
| _Agility and scalability require planning and building enabling platforms_ | _Ensure you are exhaustively measuring the elements in your platform_ | _Skilled analysts and data scientists are the foundation of defense, while users are the new security perimeter_ |
| Maintain a welldocumented inventory of your assets | Acquire and/or build the tools needed to fully monitor your network, hosts, and logs | Establsih relationships and lines of communication between the incident response team and other groups |
| Have a well-defined security policy with clear standards and guidance for your organization | Proactively maintain controls and measures, and regularly test them for accuracy and effectiveness | Adopt least privilege administrator principles; eliminate persistent administrator rights |
| Maintain proper hygiene—most attacks could be prevented with timely patches and antivirus | Maintain tight control over change management policies | Use the lessons-learned process to gain value from every major incident |
| Employ multi-factor authentication to strengthen protection of accounts and device | Monitor for abnormal account and credential activity to detect abuse | Enlist, educate, and empower users to recognize likely threats and their own role in protecting business data |

#### The following individuals contributed to this strategy brief: Alex Harmon, Bryan Casper, Cory Gehr, John Dellinger, Monica Drake, Brian Hooper, Kristina Laidler, Cory Marchand, Steven Meyers, Phillip Misner, Ben Ridgway, Joanna Sharpe, Darrell West, and Hannah West.

##### © 2018 Microsoft Corporation. All rights reserved. This document is for informational purposes only. MICROSOFT MAKES NO WARRANTIES, EXPRESS OR IMPLIED, IN THIS SUMMARY. 