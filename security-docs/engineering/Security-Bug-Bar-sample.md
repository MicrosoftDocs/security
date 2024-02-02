---
layout: Conceptual
title: SDL Security Bug Bar (Sample)
description: This document outlines the basic criteria to consider when creating security processes, and serves as an example of a security bug bar as recommended within the SDL practices information found at https://microsoft.com/sdl.
ms.date: 12/03/2018
ms.service: security
ms.author: bcowper
author: BruceCowper
ms.topic: conceptual
---

# SDL Security Bug Bar (Sample)

**Note:** This sample document is for illustration purposes only. The content presented below outlines basic criteria to consider when creating security processes. It is not an exhaustive list of activities or criteria and should not be treated as such.

Please refer to the [definitions of terms](#Definition_of_Terms) in this section.

## Server

<table>
<thead>
<tr class="header" colspan="2">
<th><p><span id="Server" class="anchor"></span>Server<br /></th>
<p>Please refer to the <a href="#denial-of-service-server-matrix">Denial of Service Matrix</a> for a complete matrix of server DoS scenarios.</p>
<p>The server bar is usually not appropriate when user interaction is part of the exploitation process. If a Critical vulnerability exists only on server products, and is exploited in a way that requires user interaction and results in the compromise of the server, the severity may be reduced from Critical to Important in accordance with the NEAT/data definition of extensive user interaction presented at the start of the client severity pivot.</p>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Critical</td>
<td><p>Server summary: Network worms or <em>unavoidable</em> cases where the server is “owned.”</p>
<ul>
<li><p>Elevation of privilege: The ability to either execute arbitrary code <em>or</em> obtain more privilege than authorized</p>
<ul>
<li><p>Remote anonymous user</p>
<ul>
<li><p>Examples:</p>
<ul>
<li><p>Unauthorized file system access: arbitrary writing to the file system</p></li>
<li><p>Execution of arbitrary code</p></li>
<li><p>SQL injection (that allows code execution)</p></li>
</ul></li>
</ul></li>
<li><p>All write access violations (AV), exploitable read AVs, or integer overflows in remote anonymously callable code</p></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td>Important</td>
<td><p>Server summary: Non-default critical scenarios or cases where mitigations exist that can help <em>prevent</em> critical scenarios.</p>
<ul>
<li><p>Denial of service: Must be &quot;easy to exploit&quot; by sending a small amount of data or be otherwise quickly induced</p>
<ul>
<li><p> Anonymous</p>
<ul>
<li><p>Persistent DoS</p>
<ul>
<li><p>Examples:</p>
<ul>
<li><p>Sending a single malicious TCP packet results in a Blue Screen of Death (BSoD)</p></li>
<li><p>Sending a small number of packets that causes a service failure</p></li>
</ul></li>
</ul></li>
<li><p>Temporary DoS with amplification</p>
<ul>
<li><p>Examples:</p>
<ul>
<li><p>Sending a small number of packets that causes the system to be unusable for a period of time</p></li>
<li><p>A web server (like IIS) being down for a minute or longer</p></li>
<li><p>A <em>single remote client</em> consuming all available resources (sessions, memory) on a server by establishing sessions and keeping them open</p></li>
</ul></li>
</ul></li>
</ul></li>
<li><p>Authenticated</p>
<ul>
<li><p>Persistent DoS <em><strong>against a high value asset</strong></em></p>
<ul>
<li><p>Example:</p>
<ul>
<li><p>Sending a small number of packets that causes a service failure for a <em><strong>high value asset</strong></em> in server roles (certificate server, Kerberos server, domain controller), such as when a domain-authenticated user can perform a DoS on a domain controller</p></li>
</ul></li>
</ul></li>
</ul></li>
</ul></li>
</ul>
<ul>
<li><p>Elevation of privilege: The ability to either execute arbitrary code <em>or</em> to obtain more privilege than intended</p>
<ul>
<li><p>Remote authenticated user</p></li>
<li><p>Local authenticated user (Terminal Server)</p>
<ul>
<li><p>Examples:</p>
<ul>
<li><p>Unauthorized file system access: arbitrary writing to the file system</p></li>
<li><p>Execution of arbitrary code</p></li>
</ul></li>
</ul></li>
<li><p>All write AVs, exploitable read AVs, or integer overflows in code that can be accessed by remote or local authenticated users that are not administrators (Administrator scenarios do not have security concerns by definition, but are still reliability issues.)</p></li>
</ul></li>
<li><p>Information disclosure (targeted)</p>
<ul>
<li><p>Cases where the attacker can locate and read information <em>from anywhere</em> on the system, including system information that was not intended or designed to be exposed</p>
<ul>
<li><p>Examples:</p>
<ul>
<li><p>Personally identifiable information (PII) disclosure</p>
<ul>
<li><p>Disclosure of PII (email addresses, phone numbers, credit card information)</p></li>
<li><p>Attacker can collect PII without user consent or in a covert fashion</p></li>
</ul></li>
</ul></li>
</ul></li>
</ul></li>
<li><p>Spoofing</p>
<ul>
<li><p>An entity (computer, server, user, process) is able to masquerade <em><strong>as a</strong></em> <strong>specific entity</strong> (user or computer) of his/her choice.</p>
<ul>
<li><p>Examples:</p>
<ul>
<li><p>Web server uses client certificate authentication (SSL) improperly to allow an attacker to be identified as any user of his/her choice</p></li>
<li><p>New protocol is designed to provide remote client authentication, but flaw exists in the protocol that allows a malicious remote user to be seen as a different user of his or her choice</p></li>
</ul></li>
</ul></li>
</ul></li>
<li><p>Tampering</p>
<ul>
<li><p>Modification of any <em><strong>“high value asset”</strong></em> data in <em><strong>a common or default scenario</strong></em> where the modification persists after restarting the affected software</p></li>
<li><p>Permanent or persistent modification of any user or system data used <em><strong>in a common or default scenario</strong></em></p>
<ul>
<li><p>Examples:</p>
<ul>
<li><p>Modification of application data files or databases in a common or default scenario, such as authenticated SQL injection</p></li>
<li><p>Proxy cache poisoning in a common or default scenario</p></li>
<li><p>Modification of OS or application settings without user consent in a common or default scenario</p></li>
</ul></li>
</ul></li>
</ul></li>
<li><p>Security features: Breaking or bypassing any security feature provided.<br />
Note that a vulnerability in a security feature is rated “Important” by default, but the rating may be adjusted based on other considerations as documented in the SDL bug bar.</p>
<ul>
<li><p>Examples:</p>
<ul>
<li><p>Disabling or bypassing a firewall without informing users or gaining consent</p></li>
<li><p>Reconfiguring a firewall and allowing connections to other processes</p></li>
</ul></li>
</ul></li>
</ul></td>
</tr>
<tr class="odd">
<td>Moderate</td>
<td><ul>
<li><p>Denial of service</p>
<ul>
<li><p>Anonymous</p>
<ul>
<li><p>Temporary DoS without amplification in a default/common install.</p>
<ul>
<li><p>Example:</p>
<ul>
<li><p><em><strong>Multiple remote clients</strong></em> consuming all available resources (sessions, memory) on a server by establishing sessions and keeping them open</p></li>
</ul></li>
</ul></li>
</ul></li>
<li><p>Authenticated</p>
<ul>
<li><p>Persistent DoS</p>
<ul>
<li><p>Example:</p>
<ul>
<li><p>Logged in Exchange user can send a specific mail message and crash the Exchange Server, and the crash is <strong>not</strong> due to a write AV, exploitable read AV, or integer overflow</p></li>
</ul></li>
</ul></li>
<li><p>Temporary DoS with amplification in a default/common install</p>
<ul>
<li><p>Example:</p>
<ul>
<li><p>Ordinary SQL Server user executes a stored procedure installed by some product and consumes 100% of the CPU for a few minutes</p></li>
</ul></li>
</ul></li>
</ul></li>
</ul></li>
<li><p>Information disclosure (targeted)</p>
<ul>
<li><p>Cases where the attacker can easily read information on the system <em>from <strong>specific locations</strong></em>, including system information, which was not intended/ designed to be exposed.</p>
<ul>
<li><p>Example:</p>
<ul>
<li><p>Targeted disclosure of anonymous data</p></li>
<li><p>Targeted disclosure of the existence of a file</p></li>
<li><p>Targeted disclosure of a file version number</p></li>
</ul></li>
</ul></li>
</ul></li>
<li><p>Spoofing</p>
<ul>
<li><p>An entity (computer, server, user, process) is able to masquerade as a different, random entity that cannot be specifically selected.</p>
<ul>
<li><p>Example:</p>
<ul>
<li><p>Client properly authenticates to server, but server hands back a session from another random user who happens to be connected to the server at the same time</p></li>
</ul></li>
</ul></li>
</ul></li>
<li><p>Tampering</p>
<ul>
<li><p>Permanent or persistent modification of any user or system data <em><strong>in a specific scenario</strong></em></p>
<ul>
<li><p>Examples:</p>
<ul>
<li><p>Modification of application data files or databases <em><strong>in a specific scenario</strong></em></p></li>
<li><p>Proxy cache poisoning <em><strong>in a specific scenario</strong></em></p></li>
<li><p>Modification of OS/application settings without user consent <em><strong>in a specific scenario</strong></em></p></li>
</ul></li>
</ul></li>
<li><p>Temporary modification of data in a common or default scenario that does not persist after restarting the OS/application-/session</p></li>
</ul></li>
<li><p>Security assurances:</p>
<ul>
<li><p>A security assurance is either a security feature or another product feature/function that customers expect to offer security protection. Communications have messaged (explicitly or implicitly) that customers can rely on the integrity of the feature, and that’s what makes it a security assurance. Security bulletins will be released for a shortcoming in a security assurance that undermines the customer’s reliance or trust.</p>
<ul>
<li><p>Examples:</p>
<ul>
<li><p>Processes running with normal “user” privileges cannot gain “admin” privileges unless admin password/credentials have been provided via intentionally authorized methods.</p></li>
<li><p>Internet-based JavaScript running in Internet Explorer cannot control anything the host operating system unless the user has explicitly changed the default security settings.</p></li>
</ul></li>
</ul></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td>Low</td>
<td><ul>
<li><p>Information disclosure (untargeted)</p>
<ul>
<li><p>Runtime information</p>
<ul>
<li><p>Example:</p>
<ul>
<li><p>Leak of random heap memory</p></li>
</ul></li>
</ul></li>
</ul></li>
<li><p>Tampering</p>
<ul>
<li><p>Temporary modification of data <em>in a specific scenario</em> that does not persist after restarting the OS/application</p></li>
</ul></li>
</ul></td>
</tr>
</tbody>
</table>

## Client

<table>
<thead>
<tr class="header" colspan="2">
<th><p><span id="Client" class="anchor"></span>Client<br /></th>
Extensive user action is defined as:</p>
<ul>
<li><p>&quot;User interaction&quot; can only happen in client-driven scenario.</p></li>
<li><p>Normal, simple user actions, like previewing mail, viewing local folders, or file shares, are not extensive user interaction.</p></li>
<li><p>&quot;Extensive&quot; includes users manually navigating to a particular website (for example, typing in a URL) or by clicking through a yes/no decision.</p></li>
<li><p>&quot;Not extensive&quot; includes users clicking through e-mail links.</p></li>
<li><p><strong>NEAT</strong> qualifier (<em>applies to warnings only</em>). Demonstrably, the UX is:</p>
<ul>
<li><p><strong>N</strong>ecessary (Does the user really need to be presented with the decision?)</p></li>
<li><p><strong>E</strong>xplained (Does the UX present all the information the user needs to make this decision?)</p></li>
<li><p><strong>A</strong>ctionable (Is there a set of steps users can take to make good decisions in both benign and malicious scenarios?)</p></li>
<li><p><strong>T</strong>ested (Has the warning been reviewed by multiple people, to make sure people understand how to respond to the warning?)</p></li>
</ul></li>
<li><p><strong>Clarification:</strong> Note that the effect of extensive user interaction is not one level reduction in severity, but is and has been a reduction in severity in certain circumstances where the phrase extensive user interaction appears in the bug bar. The intent is to help customers differentiate fast-spreading and wormable attacks from those, where because the user interacts, the attack is slowed down. This bug bar does not allow you to reduce the Elevation of Privilege below Important because of user interaction.</p></li>
</ul>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Critical</td>
<td><p>Client summary:</p>
<ul>
<li><p>Network Worms or <em>unavoidable</em> common browsing/use scenarios where the client is “owned” <strong>without</strong> warnings or prompts.</p></li>
<li><p>Elevation of privilege (remote): The ability to either execute arbitrary code <em>or</em> to obtain more privilege than intended</p>
<ul>
<li><p>Examples:</p>
<ul>
<li><p>Unauthorized file system access: writing to the file system</p></li>
<li><p>Execution of arbitrary code without extensive user action</p></li>
<li><p>All write AVs, exploitable read AVs, stack overflows, or integer overflows in remotely callable code (<em><strong>without</strong></em> extensive user action)</p></li>
</ul></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td>Important</td>
<td><p>Client summary:</p>
<ul>
<li><p>Common browsing/use scenarios where client is “owned” <strong>with</strong> warnings or prompts, or via extensive actions without prompts. Note that this does not discriminate over the quality/usability of a prompt and likelihood a user might click through the prompt, but just that a prompt of some form exists.</p></li>
<li><p>Elevation of privilege (remote)</p>
<ul>
<li><p>Execution of arbitrary code <em>with</em> extensive user action</p>
<ul>
<li><p>All write AVs, exploitable read AVs, or integer overflows in <em><strong>remote</strong></em> callable code (<em><strong>with</strong></em> extensive user action)</p></li>
</ul></li>
</ul></li>
<li><p>Elevation of privilege (local)</p>
<ul>
<li><p>Local low privilege user can elevate themselves to another user, administrator, or local system.</p>
<ul>
<li><p>All write AVs, exploitable read AVs, or integer overflows in <strong>local</strong> callable code</p></li>
</ul></li>
</ul></li>
<li><p>Information disclosure (targeted)</p>
<ul>
<li><p>Cases where the attacker can locate and read information on the system, including system information that was not intended or designed to be exposed.</p></li>
<li><p>Example:</p>
<ul>
<li><p>Unauthorized file system access: reading from the file system</p></li>
<li><p>Disclosure of PII</p>
<ul>
<li><p>Disclosure of PII (email addresses, phone numbers)</p></li>
</ul></li>
<li><p>Phone home scenarios</p></li>
</ul></li>
</ul></li>
<li><p>Denial of service</p>
<ul>
<li><p>System corruption DoS requires re-installation of system and/or components.</p>
<ul>
<li><p>Example:</p>
<ul>
<li><p>Visiting a web page causes registry corruption that makes the machine unbootable</p></li>
</ul></li>
</ul></li>
<li><p>Drive-by DoS</p>
<ul>
<li><p>Criteria:</p>
<ul>
<li><p>Un-authenticated System DoS</p></li>
<li><p>Default exposure</p></li>
<li><p>No default security features or boundary mitigations (firewalls)</p></li>
<li><p>No user interaction</p></li>
<li><p>No audit and punish trail</p></li>
<li><p>Example:</p>
<ul>
<li><p>Drive-by Bluetooth system DoS or SMS in a mobile phone</p></li>
</ul></li>
</ul></li>
</ul></li>
</ul></li>
<li><p>Spoofing</p>
<ul>
<li><p>Ability for attacker to present a UI that is different from but visually identical to the UI that users <em>must rely on to make valid trust decisions</em> in a <em>default/common scenario</em>. A trust decision is defined as any time the user takes an action believing some information is being presented by a particular entity—either the system or some specific local or remote source.</p>
<ul>
<li><p>Examples:</p>
<ul>
<li><p>Displaying a different URL in the browser’s address bar from the URL of the site that the browser is actually displaying in a <em><strong>default/common scenario</strong></em></p></li>
<li><p>Displaying a window over the browser’s address bar that looks identical to an address bar but displays bogus data in a <em><strong>default/common scenario</strong></em></p></li>
<li><p>Displaying a different file name in a “Do you want to run this program?” dialog box than that of the file that will actually be loaded in a <em><strong>default/common scenario</strong></em></p></li>
<li><p>Display a “fake” login prompt to gather user or account credentials</p></li>
</ul></li>
</ul></li>
</ul></li>
<li><p>Tampering</p>
<ul>
<li><p>Permanent modification of any user data or data used to make trust decisions in a common or default scenario that persists after restarting the OS/application.</p>
<ul>
<li><p>Examples:</p>
<ul>
<li><p>Web browser cache poisoning</p></li>
<li><p>Modification of significant OS/application settings without user consent</p></li>
<li><p>Modification of user data</p></li>
</ul></li>
</ul></li>
</ul></li>
<li><p>Security features: Breaking or bypassing any security feature provided</p>
<ul>
<li><p>Examples:</p>
<ul>
<li><p>Disabling or bypassing a firewall with informing user or gaining consent</p></li>
<li><p>Reconfiguring a firewall and allowing connection to other processes</p></li>
<li><p>Using weak encryption or keeping the keys stored in plain text</p></li>
<li><p>AccessCheck bypass</p></li>
<li><p>Bitlocker bypass; for example not encrypting part of the drive</p></li>
<li><p>Syskey bypass, a way to decode the syskey without the password</p></li>
</ul></li>
</ul></li>
</ul></td>
</tr>
<tr class="odd">
<td>Moderate</td>
<td><ul>
<li><p>Denial of service</p>
<ul>
<li><p>Permanent DoS requires cold reboot or causes Blue Screen/Bug Check.</p>
<ul>
<li><p>Example:</p>
<ul>
<li><p>Opening a Word document causes the machine to Blue Screen/Bug Check.</p></li>
</ul></li>
</ul></li>
</ul></li>
<li><p>Information disclosure (targeted)</p>
<ul>
<li><p>Cases where the attacker can read information on the system <em>from known locations</em>, including system information that was not intended or designed to be exposed.</p>
<ul>
<li><p>Examples:</p>
<ul>
<li><p>Targeted existence of file</p></li>
<li><p>Targeted file version number</p></li>
</ul></li>
</ul></li>
</ul></li>
<li><p>Spoofing</p>
<ul>
<li><p>Ability for attacker to present a UI that is different from but visually identical to the UI that users <em>are accustomed to trust</em> in <em>a specific scenario</em>. &quot;Accustomed to trust&quot; is defined as anything a user is commonly familiar with based on normal interaction with the operating system or application but does not typically think of as a &quot;trust decision.&quot;</p>
<ul>
<li><p>Examples:</p>
<ul>
<li><p>Web browser cache poisoning</p></li>
<li><p>Modification of significant OS/application settings without user consent</p></li>
<li><p>Modification of user data</p></li>
</ul></li>
</ul></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td>Low</td>
<td><ul>
<li><p>Denial of service</p>
<ul>
<li><p>Temporary DoS requires restart of application.</p>
<ul>
<li><p>Example:</p>
<ul>
<li><p>Opening a HTML document causes Internet Explorer to crash</p></li>
</ul></li>
</ul></li>
</ul></li>
<li><p>Spoofing</p>
<ul>
<li><p>Ability for attacker to present a UI that is different from but visually identical to the UI <em>that is a single part of a bigger attack scenario</em>.</p>
<ul>
<li><p>Example:</p>
<ul>
<li><p>User has to go a “malicious” web site, click on a button in spoofed dialog box, and is then susceptible to a vulnerability based on a different browser bug</p></li>
</ul></li>
</ul></li>
</ul></li>
<li><p>Tampering</p>
<ul>
<li><p>Temporary modification of any data that does not persist after restarting the OS/application.</p></li>
<li><p>Information disclosure (untargeted)</p>
<ul>
<li><p>Example:</p>
<ul>
<li><p>Leak of random heap memory</p></li>
</ul></li>
</ul></li>
</ul></li>
</ul></td>
</tr>
</tbody>
</table>


## Definition of Terms  

**authenticated**  
Any attack which has to include authenticating by the network. This
implies that logging of some type must be able to occur so that the
attacker can be identified.  

**anonymous**  
Any attack which does not need to authenticate to complete.  

**client**  
Either software that runs locally on a single computer or software that
accesses shared resources provided by a server over a network.  

**default/common**  
Any features that are active out of the box or that reach more than 10
percent of users.  

**scenario**  
Any features that require special customization or use cases to enable,
reaching less than 10 percent of users.  

**server**  
Computer that is configured to run software that awaits and fulfills
requests from client processes that run on other computers.  

**Critical**  
A security vulnerability that would be rated as
having the highest potential for damage.

**Important**  
A security vulnerability that would be rated as
having significant potential for damage, but less than Critical.

**Moderate**  
A security vulnerability that would be rated as
having moderate potential for damage, but less than Important.

**Low**  
A security vulnerability that would be rated as having
low potential for damage.

**targeted information disclosure**  
Ability to intentionally select (target) desired information.  

**temporary DoS**  
A temporary DoS is a situation where the following criteria are met:

  - The target cannot perform normal operations due to an attack.

  - The response to an attack is roughly the same magnitude as the size
    of the attack.

  - The target returns to the normal level of functionality shortly
    after the attack is finished. The exact definition of "shortly"
    should be evaluated for each product.

For example, a server is unresponsive while an attacker is constantly
sending a stream of packets across a network, and the server returns to
normal a few seconds after the packet stream stops.

**temporary DoS with amplification**

A temporary DoS with amplification is a situation where the following
criteria are met:

  - The target cannot perform normal operations due to an attack.

  - The response to an attack is magnitudes beyond the size of the
    attack.

  - The target returns to the normal level of functionality after the
    attack is finished, but it takes some time (perhaps a few minutes).

For example, if you can send a malicious 10-byte packet and cause a
2048k response on the network, you are DoSing the bandwidth by
amplifying our attack effort.

**permanent DoS**

A permanent DoS is one that requires an administrator to start, restart,
or reinstall all or parts of the system. Any vulnerability that
automatically restarts the system is also a permanent
DoS.

## Denial of Service (Server) Matrix

| **Authenticated vs. Anonymous attack** | **Default/Common vs. Scenario** | **Temporary DoS vs. Permanent**  | **Rating** |
| -------------------------------------- | ------------------------------- | -------------------------------- | ---------- |
| Authenticated                          | Default/Common                  | Permanent                        | Moderate   |
| Authenticated                          | Default/Common                  | Temporary DoS with amplification | Moderate   |
| Authenticated                          | Default/Common                  | Temporary DoS                    | Low        |
| Authenticated                          | Scenario                        | Permanent                        | Moderate   |
| Authenticated                          | Scenario                        | Temporary DoS with amplification | Low        |
| Authenticated                          | Scenario                        | Temporary DoS                    | Low        |
| Anonymous                              | Default/Common                  | Permanent                        | Important  |
| Anonymous                              | Default/Common                  | Temporary DoS with amplification | Important  |
| Anonymous                              | Default/Common                  | Temporary DoS                    | Moderate   |
| Anonymous                              | Scenario                        | Permanent                        | Important  |
| Anonymous                              | Scenario                        | Temporary DoS with amplification | Important  |
| Anonymous                              | Scenario                        | Temporary DoS                    | Low        |

**Content Disclaimer**

<table>
<tbody>
<tr class="odd">
<td><p><em>This documentation is not an exhaustive reference on the SDL practices at Microsoft. Additional assurance work may be performed by product teams (but not necessarily documented) at their discretion. As a result, this example should not be considered as the exact process that Microsoft follows to secure all products. </em></p>
<p><em>This documentation is provided “as-is.” Information and views expressed in this document, including URL and other Internet website references, may change without notice. You bear the risk of using it. </em></p>
<p><em>This documentation does not provide you with any legal rights to any intellectual property in any Microsoft product. You may copy and use this document for your internal, reference purposes. </em></p>
<p><em>© 2018 Microsoft Corporation. All rights reserved.</em></p>
<p><em>Licensed under</em> <a href="https://creativecommons.org/licenses/by-nc-sa/3.0/">Creative Commons Attribution-NonCommercial-ShareAlike 3.0 Unported</a></p></td>
</tr>
</tbody>
</table>
