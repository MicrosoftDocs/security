---
title: The immutable laws of security
description: Busting myths, biases, and uncertainty with the 10 laws of cybersecurity.

ms.service: security
ms.subservice: zero-trust
ms.topic: conceptual
ms.date: 05/23/2024
ms.author: kenwith
author: kenwith

ms.reviewer: mas
---
# The immutable laws of security

The [original immutable laws of security](#immutable-laws-of-security-v2) identified key technical truths that busted prevalent security myths of those times. In that spirit, we're publishing a new complementary set of laws focused on busting prevalent myths in today's world of ubiquitous cybersecurity risk.

Since the original immutable laws, information security has grown from a technical discipline into a cybersecurity risk management discipline that includes cloud, IoT, and OT devices. Now, security is part of the fabric of our daily lives, business risk discussions, and elections.

As many of us in the industry followed this journey to a higher level of abstraction, we saw patterns of common myths, biases, and uncertainty emerge at the risk management layer. We decided to create a new list of laws for cybersecurity risk while retaining the original laws (v2) as is (with a single slight change of "bad guy" to "bad actor" to be fully correct and inclusive).

Each set of laws deals with different aspects of cybersecurity, designing sound technical solutions vs. managing a risk profile of complex organizations in an ever-changing threat environment. The difference in the nature of these laws also illustrates the difficult nature of navigating cybersecurity in general. Technical elements tend toward the absolute, while risk is measured in likelihood and certainty.

Because it's difficult to make predictions, especially about the future, we suspect these laws might evolve with our understanding of cybersecurity risk.

## Ten Laws of Cybersecurity Risk

1. **Security success is ruining the attacker's ROI** – Security can't achieve a perfect secure state, so deter them by disrupting and degrading their Return on Investment (ROI). Increase the attacker's cost and decrease the attacker's return for your most important assets.
1. **Not keeping up is falling behind** – Security is a continuous journey. You must keep moving forward because it will continually get cheaper for attackers to successfully take control of your assets. You must continually update your security patches, strategies, threat awareness, inventory, tooling,  monitoring, permission models, platform coverage, and anything else that changes over time.
1. **Productivity always wins** – If security isn't easy for users, they work around it to get their job done. Always make sure solutions are secure **and** usable.
1. **Attackers don't care** – Attackers use any available method to get into your environment and access your assets, including networked printers, fish tank thermometers, cloud services, PCs, servers, Macs, or mobile devices. They influence or trick users, exploit configuration mistakes or insecure operational processes, or just ask for passwords in a phishing email. Your job is to understand and take away the easiest, cheapest, and most useful options, like anything that leads to administrative privileges across systems.
1. **Ruthless prioritization is a survival skill** – Nobody has enough time and resources to eliminate all risks to all resources. Always start with what is most important to your organization or most interesting to attackers, and continuously update this prioritization.
1. **Cybersecurity is a team sport** – Nobody can do it all, so always focus on the things that only you (or your organization) can do to protect your organization's mission. If security vendors, cloud providers, or the community can do better or cheaper, have them do it.
1. **Your network isn't as trustworthy as you think it is** – A security strategy that relies on passwords and trusting any intranet device is only marginally better than lack of security strategy. Attackers easily evade these defenses, so the trust level of each device, user, and application must be proven and validated continuously, starting with a level of zero trust.
1. **Isolated networks aren't automatically secure** – While air-gapped networks can offer strong security when maintained correctly, successful examples are extremely rare because each node must be isolated from outside risk. If security is critical enough to place resources on an isolated network, you should invest in mitigations to address potential connectivity via methods such as USB media (for example, required for patches), bridges between the intranet network and external devices (for example, vendor laptops on a production line), and insider threats that could circumvent all technical controls.
1. **Encryption alone isn't a data protection solution** – Encryption protects against out-of-band attacks (for example, network packets, files, and storage), but data is only as secure as the decryption key (key strength + protections from theft/copying), and other authorized means of access.
1. **Technology doesn't solve people and process problems** – While machine learning, artificial intelligence, and other technologies offer amazing leaps forward in security (when applied correctly), cybersecurity is a human challenge, and will never be solved by technology alone.

## Reference

### Immutable Laws of Security v2

- **Law #1:** If a bad actor can persuade you to run their program on your computer, it's not solely your computer anymore.
- **Law #2:** If a bad actor can alter the operating system on your computer, it's not your computer anymore.
- **Law #3:** If a bad actor has unrestricted physical access to your computer, it's not your computer anymore.
- **Law #4:** If you allow a bad actor to run active content in your website, it's not your website anymore.
- **Law #5:** Weak passwords trump strong security.
- **Law #6:** A computer is only as secure as the administrator is trustworthy.
- **Law #7:** Encrypted data is only as secure as its decryption key.
- **Law #8:** An out-of-date antimalware scanner is only marginally better than no scanner at all.
- **Law #9:** Absolute anonymity isn't practically achievable, either online or offline.
- **Law #10:** Technology isn't a panacea.
