---
title: The immutable laws of security
description: Learn how to assign Azure roles to the local administrators group of a Windows device.

ms.service: security

ms.topic: conceptual
ms.date: 10/17/2022

ms.author: joflore
author: MicrosoftGuyJFlo
manager: amycolannino
ms.reviewer: mas
---
# The immutable laws of security

The original immutable laws of security (v2 updated below) identified key technical truths that busted prevalent security myths of those times. In that spirit, we're publishing a new complementary set of laws focused on busting prevalent myths in today’s world of ubiquitous cybersecurity risk.

Since the time of the original immutable laws, the technical discipline of information security has grown up into a cybersecurity risk management discipline that includes cloud, IoT and OT devices, while simultaneously being weaved into the fabric of our daily lives, business risk discussions, elections, and more.

As many of us in the industry followed this journey to a higher level of abstraction, we saw patterns of common myths, biases, and blind spots emerge at the risk management layer. We decided to create a new list of laws for cybersecurity risk while retaining the original laws (v2) as is (with a single slight change of “bad guy” to “bad actor” to be fully correct and inclusive).

Each set of laws deals with different aspects of cybersecurity – designing sound technical solutions vs. managing a risk profile of complex organizations in an ever-changing threat environment. The difference in the nature of these laws (technical elements tend toward the absolute while risk is measured in fractions/percentages of certainty) also illustrates the difficult nature of navigating this evolution and cybersecurity in general.

Because it's difficult to make predictions (especially about the future), we suspect these laws may evolve with our understanding of cybersecurity risk.

## 10 Laws of Cybersecurity Risk

1. **Security success is ruining the attacker ROI** - Security can’t achieve an absolutely secure state so deter them by disrupting and degrading their ability to realize Return on Investment (ROI). Increase the attacker’s cost and decreasing the attacker’s return for your most important assets.
1. **Not keeping up is falling behind** – Security is a continuous journey and if you aren't staying current, it will continually get cheaper and cheaper for attackers to successfully take control of your assets. You must continually update your security patches, security strategies, threat awareness, inventory, security tooling, security hygiene, security monitoring, permission models, and anything else that changes over time.
1. **Productivity always wins** – If security isn’t easy for users, they'll work around it to get their job done. Always make sure solutions are secure and usable.
1. **Attackers don't care** - Attackers are willing to use any available method to get into your environment and increase control over it including compromising a networked printer, a fish tank thermometer, a cloud service, a PC, a Server, a Mac, a mobile device, use of a malicious insider, use of a configuration mistake, or just asking for passwords in a phishing email. Your job is to understand and take away the easiest and cheapest options as well as the most useful ones (for example, anything that leads to administrative privileges across many systems).
1. **Ruthless Prioritization is a survival skill** – Nobody can do it all, so always focus on the things that only you (or your organization) can do to protect the organization's mission. For things that others can do better or cheaper, have them do it (security vendors, cloud providers, community)
1. **Cybersecurity is a team sport** – nobody can do it all, so always focus on the things that only you (or your organization) can do to protect the organization's mission. For things that others can do better or cheaper, have them do it (security vendors, cloud providers, community)
1. **Your network isn’t a trustworthy as you think it is** - A security strategy that relies on passwords and trusting any intranet device is only marginally better than no security strategy at all. Attackers easily evade these defenses so the trust level of each device, user, and application must be proven and validated continuously starting with a level of zero trust
1. **Isolated networks aren’t automatically secure** - While air-gapped networks can offer strong security when maintained correctly, successful examples are extremely rare because each node must be completely isolated from outside risk. If security is critical enough to place resources on an isolated network, you should invest in mitigations to address potential connectivity via methods such as USB media (for example, required for patches), bridges to intranet network, and external devices (for example, vendor laptops on a production line), and insider threats that could circumvent all technical controls.
1. **Encryption alone isn’t a data protection solution** - Encryption protects against out of band attacks (on network packets, files, storage, etc.), but data is only as secure as the decryption key (key strength + protections from theft/copying) and other authorized means of access.
1. **Technology doesn't solve people and process problems** - Encryption protects against out of band attacks (on network packets, files, storage, etc.), but data is only as secure as the decryption key (key strength + protections from theft/copying) and other authorized means of access.

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
- **Law #10:** Technology isn't a panacea.
