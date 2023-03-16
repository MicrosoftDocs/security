Rules

Another set of out-of-the-box rules enabled by default are Anomaly Rules in Sentinel. These are based on Machine Learning models and UEBA that train on the data in your workspace to flag anomalous behavior across users, hosts, etc. Often a phishing attack will lead to an execution step such as local or cloud account manipulation/control or malicious script execution. Anomaly Rules look exactly for those types of activities: 

-   [<u>Anomalous Account Access Removal</u>](https://learn.microsoft.com/en-us/azure/sentinel/anomalies-reference#anomalous-account-access-removal) 

-   [<u>Anomalous Account Creation</u>](https://learn.microsoft.com/en-us/azure/sentinel/anomalies-reference#anomalous-account-creation) 

-   [<u>Anomalous Account Deletion</u>](https://learn.microsoft.com/en-us/azure/sentinel/anomalies-reference#anomalous-account-deletion) 

<!-- -->

-   [<u>Anomalous Account Manipulation</u>](https://learn.microsoft.com/en-us/azure/sentinel/anomalies-reference#anomalous-account-manipulation) 

-   [<u>Anomalous Code Execution (UEBA)</u>](https://learn.microsoft.com/en-us/azure/sentinel/anomalies-reference#anomalous-code-execution-ueba) 

-   [<u>Anomalous Data Destruction</u>](https://learn.microsoft.com/en-us/azure/sentinel/anomalies-reference#anomalous-data-destruction) 

-   [<u>Anomalous Defensive Mechanism Modification</u>](https://learn.microsoft.com/en-us/azure/sentinel/anomalies-reference#anomalous-defensive-mechanism-modification) 

-   [<u>Anomalous Failed Sign-in</u>](https://learn.microsoft.com/en-us/azure/sentinel/anomalies-reference#anomalous-failed-sign-in) 

<!-- -->

-   [<u>Anomalous Password Reset</u>](https://learn.microsoft.com/en-us/azure/sentinel/anomalies-reference#anomalous-password-reset) 

-   [<u>Anomalous Privilege Granted</u>](https://learn.microsoft.com/en-us/azure/sentinel/anomalies-reference#anomalous-privilege-granted) 

-   [<u>Anomalous Sign-in</u>](https://learn.microsoft.com/en-us/azure/sentinel/anomalies-reference#anomalous-sign-in) 

Review the Anomaly Rules and Anomaly Score Threshold for each one; if you are observing false positives for example, consider duplicating the rule and modifying the threshold by following the steps outlined [<u>here</u>](https://learn.microsoft.com/en-us/Azure/sentinel/work-with-anomaly-rules#tune-anomaly-rules).  

After reviewing and modifying Fusion and Anomaly rules, enable the out-of-the-box Microsoft Threat Intelligence Analytics Rule. [<u>This rule matches your log data with Microsoft-generated threat intelligence</u>](https://learn.microsoft.com/en-us/azure/sentinel/understand-threat-intelligence#detect-threats-with-threat-indicator-analytics). Microsoft has a vast repository of threat intelligence data, and this Analytic Rule uses a subset of it to generate high fidelity alerts and incidents for SOC (security operations centers) teams to triage. 

 

With Fusion, Anomaly, and Threat Intelligence Analytic Rules enabled, you should conduct a [<u>MITRE Att&ck crosswalk</u>](https://learn.microsoft.com/en-us/azure/sentinel/mitre-coverage) to help you decide which remaining Analytic Rules to enable and to finish implementing a mature XDR (extended detection and response) process. This will empower you to detect and respond throughout the lifecycle of an attack.  

 The [<u>MITRE Att&ck research department</u>](https://attack.mitre.org/matrices/enterprise/) created the MITRE method, and it is provided as part of Microsoft Sentinel to ease your implementation. You should ensure you have Analytic rules that stretch the length and breadth of the attack vectors approach. Start by reviewing the MITRE techniques that are covered by your existing ‘Active’ Analytic Rules, and then select ‘**Analytic rule templates**’ and ‘**Anomaly Rules**’ in the **Simulated** dropdown. Now, it will show you where you have the adversary tactic and/or technique covered and where there are available Analytic Rules you should consider enabling to improve your coverage. For example, to detect potential phishing attacks, review the **Analytic rule templates** for the Phishing technique, and prioritize enabling the rules that specifically query the data sources you have onboarded to Sentinel.  

> <img src="c:\security-pr-branches\operations/media/image1.png" style="width:6.5in;height:3.16458in" alt="Graphical user interface, application, Teams Description automatically generated" /> 
>
>  

In summary, when turning on Analytic rules for Sentinel, prioritize enabling by connected data sources, organizational risk, and MITRE tactic.  

 
