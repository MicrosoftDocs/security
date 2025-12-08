---
title: Assess your organization's AI risk with Microsoft Security Dashboard for AI
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

# Assess your organization's AI risk with Microsoft Security Dashboard for AI

[Microsoft Security Dashboard for AI](https://ai.security.microsoft.com) is a unified security dashboard that helps security leaders understand and address the AI risk in their organization. As AI adoption accelerates, the dashboard equips leadership with a powerful governance tool that provides clear and comprehensive AI security insights - enabling informed decision-making and effective risk mitigation.

This article explains the core capabilities of the Security Dashboard for A and how to use the dashboard effectively to manage AI security across your enterprise.

## End-to-end AI risk management

The Security Dashboard for AI provides a real-time view of AI security posture and risk across Microsoft Security solutions - including Microsoft Entra, Microsoft Purview, and Microsoft Defender - enabling both proactive governance and reactive threat protection.

The dashboard provides:

- **Real-time visibility of AI risk**: Aggregated insights across Microsoft Entra, Defender, and Purview.
- **Comprehensive inventory of AI assets**: The dashboard covers Microsoft AI solutions — including Microsoft 365 Copilot, Microsoft Copilot Studio agents, and Microsoft Foundry apps and agents - as well as third-party AI applications and agents such as Google Gemini, OpenAI ChatGPT, and MCP servers.
- **Actionable remediation paths and recommendations**: Direct integration with Microsoft productivity tools and practitioner portals.
- **AI-powered insights**: Leverages Security Copilot for intelligent risk assessment and recommendations.  
- **Executive reporting**: Board-ready analytics and compliance insights.

:::image type="content" source="media/security-dashboard-for-ai/security-for-ai-dashboard-overview.png" alt-text="A screenshot showing the Overview page of the Security Dashboard for AI." lightbox="media/security-dashboard-for-ai/security-for-ai-dashboard-overview.png":::

## Prerequisites

Security Dashboard for AI requires no additional licensing beyond the underlying Microsoft Security products. It's available to all customers to support secure, governed AI deployments.

**Required products:**
- Microsoft Security suite components - Microsoft Entra, Microsoft Defender, and Microsoft Purview
- Microsoft Security Copilot for AI-powered insights

## Permissions

Users must be granted explicit access to the Security Dashboard for AI


## Executive Overview Dashboard

The main dashboard provides a strategic view of AI risk across your organization.

**Key Components:**
- **Risk Summary Cards** - High-level KPIs and critical metrics
- **Trend Analysis** - Historical risk patterns and emerging threats
- **Priority Risks** - Most critical issues requiring immediate attention
- **Coverage Metrics** - Visibility into AI asset discovery and protection status

**Navigation Elements:**
- **Global Search** - Find specific AI applications or agents
- **Filter Controls** - Refine views by risk level, asset type, or business unit
- **Time Range Selector** - Analyze trends over different periods
- **Export Options** - Generate reports for executive presentation

## AI Inventory and Asset Management

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

## Integration with Microsoft Security Ecosystem

### Microsoft Entra Integration

- **Identity Management** - Centralized user and application identity governance
- **Conditional Access** - Risk-based access controls for AI applications
- **Privileged Identity Management** - Elevated access monitoring and control

### Microsoft Defender Integration

- **Threat Protection** - Real-time monitoring of AI workloads and endpoints
- **Cloud Security Posture** - Infrastructure vulnerability assessment
- **App Security** - SaaS AI application risk evaluation

### Microsoft Purview Integration

- **Data Classification** - Automated labeling and protection of AI-accessible data
- **Data Loss Prevention** - Prevention of sensitive information exposure through AI
- **Insider Risk Management** - Detection of anomalous AI usage patterns

### Microsoft Intune Integration

- **Device Management** - Endpoint security for AI application access
- **App Protection** - Mobile application security for AI companions
- **Compliance Policies** - Device-level governance for AI access

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
