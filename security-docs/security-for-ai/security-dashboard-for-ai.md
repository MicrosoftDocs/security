---
title: Assess your organization's AI risk with Microsoft Security Dashboard for AI (Preview)
description: Use the Microsoft Security Dashboard for AI dashboard to discover, assess, and mitigate AI risks across your organization.
ms.date: 12/05/2025
ms.update-cycle: 90-days
ms.service: security
ms.subservice: security-for-ai
author: guywi-ms
ms.author: guywild
ms.topic: concept-article
ms.collection: 
  - msftsolution-security-for-ai
  - msftsolution-overview
  - zerotrust-solution
  - msec-ai-copilot
---

# Assess your organization's AI risk with Microsoft Security Dashboard for AI (Preview)

[Microsoft Security Dashboard for AI](https://ai.security.microsoft.com) is a unified security dashboard that helps security leaders understand and address the AI risk in their organization. The dashboard equips leadership with a governance tool that provides clear and comprehensive AI security insights and answers the most pressing questions about AI risk, including:

- Which AI assets exist in our environment?
- What’s their current security posture?
- Where must we take action?

This article explains the core capabilities of the Security Dashboard for A and how to use the dashboard effectively to manage AI security across your enterprise.

## End-to-end AI security visibility and management

Security Dashboard for AI provides a real-time view of AI security posture and risk across Microsoft Security solutions - including Microsoft Entra, Microsoft Purview, and Microsoft Defender - enabling proactive governance and reactive threat protection. This lets security teams keep using the tools they trust while empowering security leaders to govern and collaborate seamlessly.

The dashboard provides:

- **Real-time visibility of AI risk**: Aggregated insights across Microsoft Entra, Defender, and Purview.
- **Comprehensive inventory of AI assets**: The dashboard covers Microsoft AI solutions - including Microsoft 365 Copilot, Microsoft Copilot Studio agents, and Microsoft Foundry apps and agents - as well as third-party AI models, applications, and agents such as Google Gemini, OpenAI ChatGPT, and MCP servers.
- **Recommendations and remediation paths**: Direct integration with Microsoft productivity tools and practitioner portals.
- **AI-powered insights**: Leverages Security Copilot for intelligent risk assessment and recommendations.  
- **Executive reporting**: Board-ready analytics and compliance insights.

:::image type="content" source="media/security-dashboard-for-ai/security-for-ai-dashboard-overview.png" alt-text="A screenshot showing the Overview page of the Security Dashboard for AI." lightbox="media/security-dashboard-for-ai/security-for-ai-dashboard-overview.png":::

## How Security Dashboard for AI works

Security Dashboard for AI requires no additional licensing beyond the underlying Microsoft Security products. It's available to all customers to support secure, governed AI deployments.

Microsoft Security and partner products provide the sensors and signals the dashboard uses. If a required service isn’t deployed, the dashboard guides security leaders on which capabilities are missing and how to strengthen AI security.

**Supported products:**


| **Product**      | **Key capabilities**                                                                 |
|----------------------------|--------------------------------------------------------------------------------------|
| **Microsoft Entra**        | <ul><li>**Identity management**: Centralized user and application identity governance</li><li>**Conditional access**: Risk-based access controls for AI applications</li><li>**Privileged identity management**: Elevated access monitoring and control</li></ul> |
| **Microsoft Defender**     | <ul><li>**Threat protection**: Real-time monitoring of AI workloads and endpoints</li><li>**Cloud security posture**: Infrastructure vulnerability assessment</li><li>**App security**: SaaS AI application risk evaluation</li></ul> |
| **Microsoft Purview**      | <ul><li>**Data classification**: Automated labeling and protection of AI-accessible data</li><li>**Data loss prevention**: Prevent sensitive information exposure through AI</li><li>**Insider risk management**: Detect anomalous AI usage patterns</li></ul> |
| **Microsoft Security Copilot**| <ul><li>**Prompt-based exploration**: Explore AI risks, agent activity, and security recommendations via prompts</li><li>**Enhanced AI risk insights**: Aggregates signals across Microsoft and partner security solutions for deeper analysis</li><li>**Enhanced agent discovery and categorization**: Improves identification of managed, unmanaged, and shadow AI agents to strengthen your AI security posture</li></ul> |


## Permissions

You must be granted explicit access to the dashboard to view AI security data. By default, only Global Administrators and Security Administrators have access.

## Delegate security recommendations

The **Overview** page of the dashboard lists actionable recommendations to help reduce AI risk. To delegate these recommendations to specific teams or individuals for remediation:

1. Select a recommendation on the **Overview** page.

   :::image type="content" source="media/security-dashboard-for-ai/security-dashboard-for-ai-delegate-recommendation.png" alt-text="A screenshot showing the Overview page with one of the security recommendations highlighted." lightbox="media/security-dashboard-for-ai/security-dashboard-for-ai-delegate-recommendation.png":::

1. On the recommendation details page, select **Delegate**.

   :::image type="content" source="media/security-dashboard-for-ai/security-dashboard-for-ai-recommendation-details.png"  alt-text="A screenshot showing the recommendation details page with the Delegate button highlighted." lightbox="media/security-dashboard-for-ai/security-dashboard-for-ai-recommendation-details.png":::" 

1. On the **Delegate to** page, select a user or group to assign the recommendation to.
Access comprehensive visibility into all AI applications and agents across your environment.

**Discovery Capabilities:**
- **Managed AI Applications** - Microsoft-native AI solutions with full governance
- **Unmanaged AI Applications** - Shadow AI and unapproved applications  
- **Third-party AI Solutions** - External AI services and platforms
- **Agent Classification** - Automated categorization by function and risk level

**Asset Details:**
- **Application Profiles** - Detailed information about each AI asset
- **Usage Patterns** - User behavior and access analytics
- **Data Access** - Information about data sources and permissions
- **Security Configuration** - Current protection status and gaps

## Risk Assessment and Prioritization

Understand and prioritize AI-related security risks across your organization.

**Risk Categories:**
- **Identity and Access Risks** - Authentication and authorization vulnerabilities
- **Data Security Risks** - Information exposure and oversharing threats
- **Cloud Security Risks** - Infrastructure and configuration vulnerabilities
- **Compliance Risks** - Regulatory and policy violations

**Prioritization Features:**
- **Risk Scoring** - AI-powered assessment of threat severity
- **Business Impact Analysis** - Evaluation based on organizational priorities
- **Remediation Recommendations** - Specific actions to reduce risk
- **Timeline Tracking** - Progress monitoring for risk mitigation efforts

## Security Copilot Integration

Leverage AI-powered insights for enhanced security intelligence and decision-making.

**Natural Language Queries:**
- Ask questions about AI risks using conversational prompts
- Explore agent activity and security recommendations
- Generate insights by aggregating signals across security solutions

**Guided Prompts:**
- **Risk Exploration** - "What are the highest priority AI risks in my environment?"
- **Agent Discovery** - "Show me all unmanaged AI agents accessing sensitive data"
- **Remediation Guidance** - "What steps should I take to reduce data leakage risks?"
- **Compliance Assessment** - "Are there any AI applications violating our data policies?"

**AI-Generated Insights:**
- **Risk Summaries** - Automated analysis of complex security data
- **Trend Identification** - Pattern recognition across multiple data sources
- **Recommendation Prioritization** - Intelligent ranking of security actions

## Detailed Operational Workflows

### Discovering AI Assets

1. **Navigate to AI Inventory**
   - Access the inventory section from the main dashboard
   - Review the complete list of discovered AI applications and agents

2. **Apply Filters and Search**
   - Use filters to focus on specific asset types or risk levels
   - Search for particular applications or business units
   - Sort by discovery date, risk score, or usage frequency

3. **Investigate Asset Details**
   - Click on any AI asset to view detailed information
   - Review security configuration and compliance status
   - Analyze user access patterns and data interactions

4. **Export Inventory Data**
   - Generate comprehensive reports for stakeholder review
   - Export filtered views for targeted analysis
   - Schedule regular inventory updates

### Assessing and Managing Risks

1. **Risk Dashboard Analysis**
   - Review risk summary cards for immediate priorities
   - Examine trend charts to identify emerging threats
   - Use Security Copilot to explore complex risk scenarios

2. **Individual Risk Investigation**
   - Click on specific risks for detailed analysis
   - Review affected assets and potential business impact
   - Understand the root cause and attack vectors

3. **Remediation Planning**
   - Follow recommended remediation steps
   - Assign responsibilities to appropriate teams
   - Set timelines and track progress

4. **Validation and Monitoring**
   - Verify that remediation actions are effective
   - Monitor for similar risks across other assets
   - Update security policies based on lessons learned

### Executive Reporting and Governance

1. **Board-Ready Reports**
   - Access pre-configured executive dashboards
   - Generate compliance reports for regulatory requirements
   - Create custom views for specific stakeholder needs

2. **Trend Analysis**
   - Review historical data to identify patterns
   - Compare current posture against previous periods
   - Forecast future risks based on adoption trends

3. **Compliance Monitoring**
   - Track adherence to internal policies and external regulations
   - Monitor AI governance committee requirements
   - Generate audit trails for regulatory review

## Advanced Configuration and Administration

### User Access Management

1. **Role-Based Access Control**
   - Configure appropriate permissions for different user types
   - Implement least-privilege access principles
   - Regular review and update of access permissions

2. **Dashboard Customization**
   - Personalize views based on role and responsibilities
   - Configure notification preferences and alerting
   - Set up automated reporting schedules

### Integration Configuration

1. **Data Source Management**
   - Verify connections to all Microsoft Security products
   - Configure data retention and processing policies
   - Monitor integration health and performance

2. **API Access and Automation**
   - Set up API access for custom integrations
   - Configure automated workflows with other security tools
   - Implement PowerBI integration for advanced analytics

### Performance Optimization

1. **Dashboard Performance**
   - Optimize query performance for large environments
   - Configure caching and refresh schedules
   - Monitor resource usage and scaling requirements

2. **Data Management**
   - Implement data archival policies
   - Optimize storage for historical analysis
   - Configure backup and disaster recovery

## Best Practices and Recommendations

### Operational Excellence

1. **Regular Review Cycles**
   - Establish weekly risk assessment meetings
   - Monthly executive briefings on AI security posture
   - Quarterly strategic reviews and policy updates

2. **Team Collaboration**
   - Create cross-functional AI security teams
   - Establish clear escalation procedures
   - Implement knowledge sharing and training programs

3. **Continuous Improvement**
   - Regularly review and update security policies
   - Incorporate lessons learned from security incidents
   - Stay current with emerging AI threats and regulations

### Security Hygiene

1. **Asset Management**
   - Maintain accurate and up-to-date AI inventory
   - Regularly validate asset ownership and classification
   - Implement automated discovery and monitoring

2. **Risk Management**
   - Prioritize risks based on business impact and likelihood
   - Implement defense-in-depth strategies
   - Regular testing and validation of security controls

3. **Compliance Management**
   - Stay current with evolving AI regulations
   - Implement proactive compliance monitoring
   - Maintain comprehensive audit trails

## Troubleshooting and Support

### Common Issues and Solutions

**Dashboard Access Problems:**
- Verify user permissions and licensing
- Check network connectivity and firewall settings
- Contact Microsoft Support for authentication issues

**Data Integration Issues:**
- Validate Microsoft Security product configurations
- Review data source connection status
- Monitor integration logs for error messages

**Performance Issues:**
- Optimize query filters and date ranges
- Check system resource availability
- Consider data archival for improved performance

### Support Resources

- **Microsoft Learn Documentation** - Comprehensive product documentation
- **Microsoft Security Community** - Peer support and best practices sharing
- **Microsoft Support** - Professional technical support services
- **Training and Certification** - Skill development resources

## Frequently Asked Questions

**Q: Does Security Dashboard for AI replace existing security tools?**
A: No, the dashboard complements existing Microsoft Security tools by providing unified visibility. Security teams continue using familiar tools like Defender, Purview, Entra, and Intune for detailed operations.

**Q: What AI applications are covered by the dashboard?**
A: The dashboard covers Microsoft AI solutions (Microsoft 365 Copilot, Copilot Studio agents, Foundry apps, Agent 365) and third-party AI applications like Google Gemini, OpenAI ChatGPT, and MCP servers.

**Q: How does Security Copilot enhance the dashboard experience?**
A: Security Copilot provides natural language queries, guided prompts for risk exploration, and AI-generated insights that help security leaders quickly surface risks and understand remediation priorities.

**Q: What licensing is required for the dashboard?**
A: Security Dashboard for AI requires no additional licensing beyond underlying Microsoft Security products. All customers with Microsoft Security deployments can access the dashboard.

**Q: How does the dashboard support regulatory compliance?**
A: The dashboard provides compliance assessments, audit trails, and governance capabilities to help organizations meet regulatory requirements including emerging AI regulations.

## Conclusion

Microsoft Security Dashboard for AI empowers security leaders to confidently manage AI adoption while maintaining strong security posture. By providing unified visibility, AI-powered insights, and actionable remediation guidance, the dashboard enables organizations to realize the benefits of AI while effectively managing associated risks.

For the most current information and updates, visit the official Microsoft Security Dashboard for AI documentation at [Microsoft Learn](https://learn.microsoft.com/security).

## Related Resources

- [Build a strong security posture for AI](posture.md)
- [Prepare for AI security](prepare.md)
- [Discover AI apps and data](discover.md)
- [Protect AI apps and data](protect.md)
- [Govern AI for compliance](govern.md)
- [Zero Trust adoption framework](../zero-trust/adopt/zero-trust-adoption-overview.md)
- [Cloud Adoption Framework for AI](/azure/cloud-adoption-framework/scenarios/ai/)
