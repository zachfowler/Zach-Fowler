## 2.3: Governance Frameworks, Compliance, and BCP/DR

### Overview

In the final lesson of the GRC unit, we will cover policy, compliance, and business continuity planning / disaster recovery.

### Class Objectives

By the end of this lesson, we will be able to: 

- Explain how organizations use policy and procedure to formalize standards of "right" and "wrong".

- Use governance frameworks to determine which policies an organization must develop.

- Explain how audits are used to ensure compliance.

- Explain how business continuity planning and disaster recovery ensure business and mission critical functions in the event of a disruption.

### Slideshow

- The lesson slides are available on Google Drive here: [2.3 Slides](https://docs.google.com/presentation/d/1yaOq2tUOw2cR0h-IVPV1n_S_Zex5uAswKReo_L4Y-iE) 

- **Note:** Editing access is not available for this document. If you wish to modify the slides, please create a copy by navigating to File > "Make a copy...".

---

### 01. Welcome and Overview 

Today's lesson will introduce you to **governance**, **compliance**, and **business continuity planning** and **disaster recovery**. 

  - **Governance** is concerned with codifying and enforcing proper behavior and operations. In other words, governance is the field concerned with establishing standards of "right" and "wrong", and enforcing those standards.

  - **Compliance** focuses on enforcing the policies in order to meet those standards.

Knowledge of governance, compliance, and BCP/DR is crucial context for all security professionals, because most of what security professionals do is mandated by governance policies and subjection to compliance audits.


Class will proceed as follows:

- Codifying Rules with Policy and Procedures
- Using Governance Frameworks to Guide Policy Decisions
- Understanding Audit and Compliance
- Business Continuity Planning and Disaster Recovery
- Describing BCP/DR Recommendations for an Organization


### 02. Codifying and Enforcing Behavior with Policies and Procedures 

Remember the week began by developing a training plan to improve GeldCorp's security culture. This training plan was meant to protect the organization by changing employee behavior.

- The training exercise defined what employees _should_ do when faced with suspicious links. In other words, it defined the "right" behavior. 

A rule that defines the "right" behavior is called a **policy**. Organizations use policies to define standards for behavior and operations. 

- Each individual policy is just one rule amongst many. In practice, organizations will have many policies to support a given goal. 
- For example, a company must have many security policies in place to protect its data.

Guidelines for which kinds of policies an organization should have in place are called **governance frameworks**. Governance frameworks describe which guarantees a company must provide to remain compliant with federal regulations and industry standards.

Today, we'll explore these concepts by:
- Defining formal policies for GeldCorp.
- Assessing what user data collected by GeldCorp is subject to GDPR and PCI.
- Determining whether GeldCorp's data collection practices are GDPR and PCI compliant.


#### Using Organizational Goals to Define Policies

Remember: we developed our training plan by setting a goal and determining the necessary steps to achieve it.

- The training plan prescribed a specific rule that employees should follow. For example: "Do _not_ click on links to domains outside of the corporate intranet."

- This rule is an example of a **policy**, which is _a course or principle of action proposed by a business_. In this case, the rule specifies a **download policy**.

- The goal of defining and implementing a new download policy was to reduce employee _click-through rate_ to less than 5%. In other words, the business implemented _policy_ as a means of achieving this _goal_.

Such business goals often drive the development of policies. Broadly speaking, there are two categories of "business goals":

- **Internal/Volitional**: Targets that the business sets in its own interest. For example, an organization might aim to reduce long-term security expenses to less than $400,000.

- **External/Imposed**: These are targets that the business must hit because they will suffer consequences if they do not. Examples include the requirement that e-merchants handle all credit card transactions securely, under penalty of law in the event of a breach of customer PII.

This section will focus on _volitional_ objectives. We will look into Imposed Objectives in the next section and discuss **governance frameworks**.

#### Internal Objectives and Policies

Consider the following objective example: 

Suppose we want to reduce unauthorized root-level login incidents on Domain Controllers to 0:

- An organization that adopts such a policy would hand it off the IT team, who would be responsible for determining how best to implement it.

- One possible implementation is to require all Domain Administrators to use strong passwords and force them to create a new password every month.

- A _password policy_ might require that Administrators create passwords with:
  - At least 16 characters.
  - At least 1 letter and 1 number.
  - At least 1 special character (`'`, `(`, `]`, etc.).

- Additionally, the password policy could dictate that passwords contain no portion of the administrator's username, and that they create a new strong password every month.

This policy defines clear standards of behavior: Administrators are expected to follow very specific rules with regard to their passwords, which their computers will enforce. Moreover, these rules are specifically designed to achieve the goal of reducing the incidence of unauthorized root-level logins on Domain Controllers to 0.

- Here is an example of a completed password policy:

  ```md
  DATE: 5/17/2017
  AUTHOR: Jane Author

  DOMAIN ADMINISTRATOR PASSWORD POLICY
  This document lays out a password policy for Domain Administrators.

  PURPOSE
  The purpose of implementing a Domain Administrator password policy is to reduce the incidence of unauthorized root-level logins on Domain Controllers. 

  The organization has prioritized this objective in the interest of protecting the integrity and confidentiality of data on the corporate intranet.

  POLICY DESCRIPTION
  Domain Administrators will be required to create a new strong password every month. This password MUST NOT include any substring of the Domain Administrator's username.

  In addition, the password must include:
  - At least 16 characters.
  - At least 1 letter and 1 number.
  - At least 1 special character (`'`, `(`, `]`, etc.)

  For example, the following passwords are legal for the user guest:

  - CloGyPTioNEntEDist
  - CloGyPTioNEntEDist
  - n0tparticularly!strong

  The following password is illegal:
  - `gue1st12345678901342`
  

  ENFORCEMENT
  All workstations on the corporate domain have been configured to force Administrators to adhere to the above password complexity constraints and refresh intervals. 
  
  Non-compliant passwords will be rejected by the operating system.

  MONITORING
  All attempts to log in as a Domain Administrator, both remote and local, will be monitored.
  ```

- This policy still does not guarantee strong passwords: 

  - For example, `n0tparticularly!strong` is legal, but easy to crack. It is up to policy developers to determine whether such a policy is adequately secure.


### 03. Partner/Group Do: Documenting Company Policies

### 04. Instructor Review: Review Policies Exercise  

### 05. Instructor Do: Using Frameworks to Guide Policy Development 

Internal policies often support business goals, such as backing up a guarantee of 99% uptime.

Businesses often have to follow rules in addition to those they set for themselves. These rules don't directly benefit the business, but they might be mandated by the law or industry standards.

- For example, merchants that process financial transactions are legally required to guarantee that their customers' data remains confidential. If a company suffers a breach that results in the disclosure of customer PII, they may be subject to fines and other legal penalties.

These rules that everyone should follow are often called **governance frameworks**. Frameworks can be either internal (developed by the company) or external (developed by standards bodies or governments). The focus will be on the latter, as it is more important for understanding audit and compliance.

#### Securities and Exchange Commission

Governance frameworks codify standards that all businesses should follow. Within the US, these frameworks have their origins in statutes adopted by the **Securities and Exchange Commission (SEC)**, the regulatory body in charge of enforcing and proposing laws regarding financial instruments (stocks, bonds, options, etc.), and protecting consumers from fraud.

- In the 1990s, the Internet grew explosively, leading to the emergence of cybercrime. During the 90s, the SEC worked with Congress to pass anti-fraud statutes to discourage many incidents of cybercrime.
  - **Note**: A _statute_ is a law passed by Congress. An _anti-fraud statute_, in our context, is simply a law criminalizing the use of technology to commit fraud.

- In 2000, the SEC moved past simple anti-fraud laws by adopting a **regulatory statute** called **Regulation S-P**. This regulation did not focus entirely on security, but **Rule 30** of Regulation S-P mandated that organizations establish written policies and procedures that are designed to " **(a)** insure the security and confidentiality of customer records and information; **(b)** protect against any anticipated threats or hazards to the security or integrity of customer records and information; and **(c)** protect against unauthorized access to or use of customer records or information that could result in substantial harm or inconvenience to any customer".

  - **Note**: A _regulatory statute_ is a rule or order issued by an executive-branch department (Governor's or President's Office), _or_ an administrative agency such as the SEC. Though not passed by Congress, regulatory statutes have the force of law—i.e., those found to be in violation of regulations might be subject to criminal penalties.

  - Rule 30 of Regulation S-P is also known as the _Safeguard Rule_.

Additional regulatory statutes and administrative milestones followed in subsequent years. Amongst the more important are:

- **Regulation S-AM** (August 2009)
  
  - Regulation S-AM placed limits on when corporations could share consumers' private information for advertising and marketing purposes.
  
- **Disclosure Guidance** (October 2011)

  - On October 13 2011, the SEC issued guidelines for when and how organizations should disclose breaches of cybersecurity. While not formal regulatory statutes with the force of law, these guidelines mark an important step towards cyber regulation. 

  - When the guidelines were released, the federal government still had no formal regulations around cybersecurity or cyber incidents, but the disclosure guidance specified that businesses were still obligated to disclose cybersecurity breaches under then-current SEC rules, if the breach resulted in the disclosure of information that a "reasonable investor would consider important to an investment decision".

  - Read the full guidelines at the following link: [SEC Disclosure Guidelines](https://www.wilmerhale.com/en/insights/publications/sec-issues-new-guidance-on-disclosing-cybersecurity-risks-and-incidents-october-27-2011).
  
- **Regulation S-ID** (April 2013)
  
  - Also known as the _Identity Theft Red Flags Rule_, Regulation S-ID laid forth "final rules and guidelines to require certain regulated entities to establish programs to address risks of identity theft." This was the first regulation to formally require corporations to protect consumers' **Non-Public Information (NPI)**.
  
  - Regulation S-ID obligates firms to do two things: Protect against identity theft, and verify that requests to change an account holder's registered address indeed come from the account holder themselves.
  
    -   First, the rules require financial institutions and creditors to develop and implement a written identity theft prevention program designed to detect, prevent, and mitigate identity theft in connection with certain existing accounts or the opening of new accounts.

    -  Second, the rules establish special requirements for any credit and debit card issuers that are subject to the Commissions’ respective enforcement authorities, to assess the validity of notifications of changes of address under certain circumstances.

  - The full text of the regulation is available here: [Regulation S-ID](https://www.govinfo.gov/content/pkg/FR-2013-04-19/pdf/2013-08830.pdf)

- **SEC Releases Cybersecurity Regulation Blueprint** (April 15 2014): In April 2014, the SEC officially recognized cybersecurity as an exam priority, meaning that they would consider a firm's security posture as a routine part of their evaluations and audit standards. The blueprint provides examples of the kinds of questions the SEC would ask brokerages and asset managers during audits.

While these statues, regulations, and guidelines were developed for financial institutions, they apply to all publicly traded organizations, regardless of industry.

- While these guidelines explain what kinds of protections companies are obligated to provide their customers, they do not specify how they should meet those obligations.

- Since businesses in different industries manage different kinds of data, organizations must meet these obligations in different ways. Therefore, there are different frameworks for different industries. 

A business's internal policies often document how they choose to implement these mandates, in addition to "private" business goals.

There are many industry frameworks. The importance of each framework depends on the specific industry. However,all security professionals must be familiar with the following, at minimum:

- **GDPR** (2016): The **General Data Protection Regulation** protects the private data of all citizens of the EU and European Economic Area (EEA). It requires that organizations that process data belonging to EU citizens protect the data sufficiently. GDPR regulations apply to organizations based in the EU, as well as those based elsewhere that process data belonging to EU citizens.

- **HIPAA**: HIPAA is a law that mandates the protection of medical information. HIPAA has five sections, called _titles_, but "HIPAA compliance" typically refers to abiding by **Title II: HIPAA Administrative Specification**. Title II is the section that establishes privacy standards around electronic access to healthcare data. Organizations must uphold the following standards to remain HIPAA compliant:
  
  - **National Provider Identifier Standard**: All healthcare entities (people, healthcare providers, health plans, and employers) must have an ID, called the National Provider Identifier (NID).
  
  - **Transactions and Code Set Standard**: This standardizes health insurance claims.
  
  - **HIPAA Privacy Rule**: Establishes standards protecting _individually identifiable health information_, such as prescription information and lab results. This defines _what_ data to protect.
  
  - **HIPAA Security Rule**: Sets standards for patient data security. This defines _how well_ data should be protected.
  
  - **HIPAA Enforcement Rule**: Establishes guidelines for investigations of non-compliant providers.

- **PCI**: The Payment Card Industry Data Security Standard (PCI DSS) establishes guidelines that all companies that handle credit card transactions do so securely. 

  - It is an organizational standard and applies to both public and private organizations that accept, transmit, or store credit card data. 

  - PCI defines different compliance "levels". Each level has more requirements than the last. Companies that handle many transactions must have a stricter level of compliance than smaller ones.

  - The most important data protected by PCI includes:

    - Cardholder Name, Expiry Date, and 3-Digit Service (CVV) Code

    - Magnetic Strip Data

    - PIN Numbers

### 06. Partner/ Group Do: GDPR Compliance 


### 07. Instructor Review: Review GDPR Compliance


### 08. Break

### 09. Instructor Do: Compliance and Audit

Businesses must enforce their policies in order to guarantee **compliance** with legal mandates. An **audit** is the process of checking how well an organization is adhering to its policies.

- Audits are typically conducted to ensure that an organization does indeed uphold the statutes required of it by government frameworks. 

To perform an audit, auditors refer to each rule in the framework, and check that the business is following it. If they find that the organization is in violation of a given mandate, they notify the Compliance/Legal and Executive teams in a final report.

- In the event a business is found to be non-compliant in any way, the organization will typically respond by:

  - Acknowledging that they are aware of the non-compliance.
  - Determining a timeline to remediate the issue.
  - Develop a plan to bring the organization back into compliance.

- Audits are typically performed periodically by third parties, to eliminate conflicts of interest. However, an organization's Compliance and/or Legal team is responsible for ensuring the company is compliant between audits.

The details of conducting audits are out of scope for this course, but that the next exercise will give them an opportunity to review _GeldCorp's_ data processing practices for non-compliance.

### 10. Partner/Group Do: Audit Procedures

### 11. Review: Compliance and Audit

### 12. Contingency Planning for Business Continuity and Disaster Recovery

Even all the machinery of governance and compliance can't guarantee that an organization will not experience a breach. This is why business engage in _contingency planning_ to "plan for the worst".

Organizations need to be ready for any disturbances that can lead to interruptions or full suspension of their operations. 

- We’ve discussed controls as a way to mitigate threats, vulnerabilities, and risks but organizations also simultaneously need to think bigger picture in terms of building an infrastructure that can minimize the impact on mission critical functions.

- Contingency planning therefore not only takes into consideration technology and information systems but also the larger business processes, employees, and facility requirements.

A breach can have one of two results:
 
  - **Mild/Moderate Breach**: The business has been impacted, but can still handle day-to-day operations at greater cost.
 
  - **Serious/Catastrophic Breach**: The business has been impacted so severely they cannot operate. Instead, they must use their resources to contain the incident, recover from the disaster, and eventually return to operation.

Business continuity planning (BCP) and disaster recovery (DR) planning focus on contingency plans in the event of a disruption or disaster, and ensure that the business can get back on their feet and remain operational 

- Can you think of examples of disruptions or disasters. Possible answers include: cyber attacks, human errors, and environmental disasters such as earthquakes and fires. 

- As it relates to the CIA triad, contingency planning is focused primarily on ensuring the availability of information, including timely and reliable access to it.

It is important to note the differences between BCP and DR: 

- Business continuity planning focus on processes and procedure that an organization needs to consider in order to ensure that these mission critical functions continue both during and after a disaster. Since this takes into consideration business processes, business continuity involves much more comprehensive and thorough planning to ensure an organization’s long-term success.

- Disaster Recovery is more focused on the specific steps that a organization needs to take to resume work after a disaster. It is concerned more with the technology and information infrastructure and related complexities.

  - For example, some of the concerns for DR are how information systems and their operations can be moved to another location following an incident, how information is backed up, and what are the costs associated with equipment replacement.

#### Contingency Planning

Both BCP and DR begin with a contingency planning policy and business impact analysis.

- Refer to this description taken from from the  [NIST Contingency Planning Guide for Federal Information Systems](<https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-34r1.pdf>): 

  - Contingency planning considerations and strategies address the impact level of the availability security objective of information systems. 

  - Strategies for high-impact information systems should consider high availability and redundancy options in their design. Options may include fully redundant load balanced systems at alternate sites, data mirroring, and offsite database replication. 
  
  - High-availability options are normally expensive to set up, operate, and maintain and should be considered only for those high-impact information systems categorized with a high-availability security objective. 
  
  - Lower-impact information systems may be able to use less expensive contingency options and tolerate longer downtimes for recovery or restoration of data.

Refer to the below information regarding impact levels taken directly from the [NIST Contingency Planning Guide for Federal Information System](<https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-34r1.pdf>)  when it comes to impact levels.

- If the potential impact is LOW, the loss of confidentiality, integrity, or availability could be expected to have a limited adverse effect on organizational operations, organizational assets, or individuals.

- If the potential impact is MODERATE, the loss of confidentiality, integrity, or availability could be expected to have a serious adverse effect on organizational operations, organizational assets, or individuals. 

- If the potential impact is HIGH,  the loss of confidentiality, integrity, or availability could be expected to have a severe or catastrophic adverse effect on organizational operations, organizational assets, or individuals.

Contingency planning should result in a **contingency policy statement**, which establishes the larger organization framework and responsibilities revolving around maintaining confidentiality, integrity, and availability of data and the impact level to those objectives in the event of a disruption 

- Additionally a policy statement also considers roles and responsibilities of an emergency response team, resource requirements, training requirements such as exercise and testing schedules, and schedules for maintaining the plan. 

#### Business Impact Analysis

The first step in BCP and DR planning is to conduct a **Business Impact Analysis** and Risk Assessment. We’ve covered many aspects of Risk Analysis in the previous lesson. 

- Conducting a BIA is a lengthy process and outside the scope of this lesson. Typically, it is a multi-phase process that involves gathering and evaluating information, and then preparing a report that is presented to senior management. 

- The goals of the BIA overall are to: 

  - Identify key processes and functions of the business.
  - Establish a detailed list of requirements for business recovery.
  - Determine what the resource interdependencies are.
  - Figure out the impact on daily operations.
  - Develop priorities and classification of business processes and functions.
  - Develop recovery time requirements.
  - Determine financial, operational, and legal impact of disruption.

The results of the BIA will impact how the DR plan develops. In particular, there are two specific metrics from a BIA that will impact the parameters of a Disaster Recovery plan. 

- **Recovery Point Objective (RPO**) represents the amount of data that a  mission/business process data can afford to loose (given the most recent backup copy of the data) following a disruption or system outage. 

  - For example, if your company performs weekly backups, then they have determined that they can tolerate / recover from a week’s loss of data. 

- **Maximum Tolerable Downtime (MTD)** is the total amount of downtime that a system can be unavailable for users and the business. Within the time span of MTD, there are two other metrics.

  - **Recovery Time Objective (RTO)**  is  the the maximum tolerable amount of time needed to bring all critical systems back online after a disaster has occurred. 

  - **Work Recovery Time (WRT)** is the remaining segment that makes up MTD. For example, if the MTD is 4 days and the RTO is 1 day, then the work recovery time needed to get everything up and running again is 3 days. The longer the MTD, the more costly it can be to the business. On the other hand, the shorter the RTO, the more costs that will need to be allotted to recovery efforts 

Disaster recovery plans will vary by organization. Recovery priorities are dependent on the above metrics as well as outage impacts, resource availability, and costs.

One last major consideration for disaster recovery is alternate sites to house critical data and technology functions. While rare, disasters may require that these operations be moved to one of these alternate sites and the facility needs to support the operations set forth in the contingency plan. 

- There are three common types of alternate sites: hot sites, cold sites, and warm sites.

  - A hot site is essentially one that is ready to go and running 24/7 and can accommodate immediate continuation of operations. It will have equipment set up with current available data. While costly, hot sites are important to have for mission-critical data.
  
  - A cold site on the other hand is a space that has very little set up. They’re typically not used until a disaster occurs, and there should be a strategy in place for rapid set-up. While the costs of maintaining a cold site are less expensive, it is not ideal for mission-critical data

  - A warm site is an in-between. For example, servers, hardware, software, and other equipment might be set up but the latest data is not available, and so there must be a plan for getting that in place.


### 13. Partner/Group Do: Disaster Recovery Planning for *Geldcorp* 

### 14. Review: Disaster Recovery Planning for *GeldCorp* (0:10)


---

&copy; 2019 Trilogy Education Services
