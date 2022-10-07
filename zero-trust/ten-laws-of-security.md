---
title: The immutable laws of security
description: Learn how to assign Azure roles to the local administrators group of a Windows device.


ms.service: security

ms.topic: conceptual
ms.date: 10/07/2022

ms.author: joflore
author: MicrosoftGuyJFlo
manager: amycolannino
ms.reviewer: mas
---
# The immutable laws of security

The original immutable laws of security (v2 below) identified key technical truths that busted prevalent security myths of those times. In that spirit, we're publishing a new set of laws focused on busting prevalent myths in today’s world. Since the time of the original immutable laws, the domain of information security has grown into a cybersecurity risk management discipline that includes cloud, IoT and OT devices, while simultaneously being woven into the fabric of our daily lives, business risk discussions, elections, and more.

As we followed this journey to a higher level of abstraction, patterns of common myths, biases, and blind spots emerged like before. We decided to create a new list of laws for cybersecurity risk while retaining the original laws (v2) as is. While there was some debate on the precision of the ‘immutable’ title for risks, we ultimately decided to keep it because these new observations are patterns that result from nearly universal human behavior patterns and organizational incentive structures. 

## Immutable Laws of Cybersecurity Risk

1. **Security success is ruining the attacker ROI** - Security can’t achieve an absolutely secure state so deter them by disrupting and degrading their ability to realize Return on Investment (ROI). Increase the attacker’s cost and decreasing the attacker’s return for your most important assets.
1. **Not keeping up is falling behind** – If you aren't staying current with security and the environment you're protecting, it will continually get cheaper and cheaper for attackers to successfully take control of your assets.  You must continually update your security patches, security strategies, threat awareness, asset inventory, security tooling, security hygiene, permission models, trust relationship inventory, and anything else that changes over time.
1. **Productivity always wins** – If security isn’t easy for users, they'll work around it to get their job done. Solutions must be secure and productive to be successful.
1. **Attackers don't care** - whether they use a networked printer, a fish tank thermometer, a cloud service, a PC, a Server, a Mac, a mobile device, a malicious insider, or a configuration mistake to get in your environment and increase control over it. Technology is available to make every device highly secure (expensive to attack), so security should make it expensive to get and increase access (especially administrative privileges).
1. **Ruthless Prioritization is a survival skill** – Nobody has enough time and resources to eliminate all risks to all resources. Always start with what is most important to the organization, most interesting to attackers, and continuously update this prioritization.
1. **Cybersecurity is a team sport** – nobody can do it all, so always focus on the things that only you (or your organization) can do to protect the organization's mission. For things that others can do better or cheaper, have them do it (security vendors, cloud providers, community)
1. **Trust must be earned (and verified)** - A security strategy that relies on passwords and trusting any device on an intranet is only marginally better than no security strategy at all. The trust level of each device, user, and application must be proven and validated continuously starting with a level of zero trust
1. **Air-gapped networks don't stay isolated** – While some individual systems can be isolated with rigorous discipline, network systems almost always communicate and interact with outside environments, it just may take days or weeks.
1. **Encryption alone isn’t a data protection solution** - Encryption protects against out of band attacks (on network packets, files, storage, etc.), but data is only as secure as the decryption key (key strength + protections from theft/copying) and other authorized means of access.
1. **Technology doesn't solve human problems** - While machine learning, artificial intelligence, and other technologies offer amazing leaps forward in security (if applied correctly), cybersecurity is a human challenge and will never be solved by technology alone.

## Reference

### Immutable Laws of Security v2

- **Law #1:** If a bad guy can persuade you to run their program on your computer, it's not solely your computer anymore.
- **Law #2:** If a bad guy can alter the operating system on your computer, it's not your computer anymore.
- **Law #3:** If a bad guy has unrestricted physical access to your computer, it's not your computer anymore.
- **Law #4:** If you allow a bad guy to run active content in your website, it's not your website anymore.
- **Law #5:** Weak passwords trump strong security.
- **Law #6:** A computer is only as secure as the administrator is trustworthy.
- **Law #7:** Encrypted data is only as secure as its decryption key.
- **Law #8:** An out-of-date antimalware scanner is only marginally better than no scanner at all.
- **Law #9:** Absolute anonymity isn't practically achievable, online or offline.
- **Law #10:** Technology is not a panacea.
