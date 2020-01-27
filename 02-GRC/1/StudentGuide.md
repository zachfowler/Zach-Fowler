## 2.1: Introduction to Security Within the Organization

### Overview

Today's class will introduce organizational security. You will get a holistic view of how the different security topics and fields that you will study connect to one another as well as to the larger business organization. 

### Class Objectives

By the end of this lesson, you will be able to:

- Identify at least three concrete benefits of a healthy security culture.

- Articulate the responsibilities of common C-Suite officers, including the CISO.

- Explain the responsibilities of the security department.

- Identify appropriate security controls for a given resource and situation.



#### Slideshow

- The lesson slides are available on Google Drive here: [GRC Day 1 Slides](https://docs.google.com/presentation/d/1YY1NISRoPy5sC5PsIGhidBDYyPQ4-4tOpPmJS1qXKJ4/edit#slide=id.g480f0dd0a7_0_1803)

- To add slides to the student-facing repository, download the slides as a PDF by navigating to File > "Download as" and choose "PDF document." Then, add the PDF file to your class repository along with other necessary files.

- **Note:** Editing access is not available for this document. If you or your students wish to modify the slides, please create a copy by navigating to File > "Make a copy...". 


### 01. How Security Aligns within an Organization (0:15)

Welcome students to the second week of class. 

- This week will explore how security teams integrate with their broader organizations. The lesson will introduce the foundational principles of governance, risk management, and compliance (GRC).

This course will focus on equipping you with the tools needed to perform common technical roles. The GRC unit will explain how teams that carry out these responsibilities interact with one another and the organization at large.

Let's begin by briefly covering some of the modules covered in this boot camp and their corresponding professional roles:

- **Linux and Windows**: The Linux and Windows units introduce students to the fundamentals of **systems administration**. 

  - You will learn how to manage users; control file permissions; schedule tasks with `cron`; manage installed software with `apt`; and configure system services. 

  - All of these tasks are common responsibilities of **system administrators**.

- **Networking**: The networking modules introduces students to the fundamentals of networks and network security. 

  - You will learn how to configure firewalls; port-scan remote hosts; use Wireshark to capture live traffic; and analyze network protocols that they find in their traffic captures. 

  - These skills are common requirements for **network administrators** and traffic analysis is required for **SOC Analysis**, **network forensics**, and **threat hunting** roles.

- **Web and Web Vulnerabilities**: The web and web vulnerabilities units introduce students to the network structure and protocols used on the modern web. They will become familiar with the most common vulnerabilities found on most live web servers. 

  - You will learn how to use use Burp Suite to hunt for vulnerabilities in web applications. 

  - These skills are important for **penetration testers** and **SOC Analysts**, as well as the **network administrators** who maintain web servers.

- **Offensive Security**: The offensive security units introduce students to the basics of assessing a network's security via penetration testing. 

  - These skills are relevant to **penetration testers**, but knowledge of attack methodologies is also useful for **SOC Analysts** and in **network forensics** roles.

- **Defensive Security**: The defensive security module introduces students to Splunk, incident response procedures, and forensics. 

  - These skills are most relevant to **SOC Analysts** and in **network forensics** roles.

#### Security Teams and the Aligning Organization

- None of these teams works in isolation from the others. 

  - **For example:** An organization's Incident Response team will need to work closely with its IT & Networking department in order to alert those teams of breaches and provide recommendations as to how to better secure their systems.

- These teams also do not work in isolation from the business they are a part of. 

  - **For example**: An organization's Marketing and Communications teams use the networks and accounts that IT & Networking manage.

- Furthermore, everything that the security team does will always be in relation to the broader needs of the business. 
  
  - **For example**: An organization's engineering team may propose an innovative but insecure new feature for their flagship product. The security team would probably advise against developing the feature due to its poor security. However, the business might decide to develop it under the assumption that the feature's profit potential is worth the insecurity.

  - In this example, the security team must adapt its operations to accommodate a product they know is insecure. 
  
  - The security team's reaction might include: implementing more aggressive monitoring on data servers that are likely to be exposed by the new feature; advising IT & Networking to implement more sophisticated access controls on important servers and proxies; etc.

- A security team's main goal is to protect the business's data. On the other hand, the business's main goal is to make a profit. 

  - The most profitable decision is not always the most secure. 
  
  - Therefore, the security team often finds itself in tension with the rest of the organization, because its goals are not always aligned with those of the business as a whole.

- Additionally, it costs money to run a security department. 

  - Therefore, "perfect" security is never the realistic goal for any organization. 

  - Instead, businesses seek to provide _adequate_ protection for their _most important_ resources. 

  - This way, they can focus their budget and security resources where it matters most.

- So, security professionals must determine which of a business's assets are "most important" and then determine what constitutes as "adequate" protection. 

#### GRC Framework

One of the goals of GRC is to provide a framework for answering the questions: _"What assets are most important?"_ and _"What is adequate protection?"_. In particular:

  - **Risk Management** helps an organization identify which assets are most important and determine how they are most likely to be compromised. The business then uses this information to decide how to protect its most important and at-risk assets. This decision, in turn, informs the business as to what its security practices should be.

  - **Governance** provides management frameworks for implementing these security practices in the organization. It helps businesses decide how to enforce its security practices by developing _policies_, _standards_, _processes_, and _procedures_.

  - **Compliance** is the field that focuses on ensuring internal security policies are being followed, as well as verifying that the business abides by any relevant security laws.

Let's revisit the previous example of an insecure feature that may drive considerable profit: 

  - An organization may perform a **risk assessment** and conclude that the feature could lead to a 25% increase in quarterly profits, at the cost of exposing an isolated data server that contains customer names, usernames, and email addresses, but no other PII.

  - The security team may object to the feature on the grounds of insecurity. But, the business might decide that a breach of an isolated server with no truly confidential information would cost less to contain than they would gain by building the feature.

  - In this case, the business objective of meeting profit targets overrides the risk inherent in the strategy. 

  - However, if the feature exposed a core data server that contained customer SSN and credit card numbers, the business might decide that the feature isn't worth the risk to its customers' privacy, or the cost of being in violation of federal laws that mandate the careful protection of this data.

After making a decision, the business would update its security practices to manage the risk they've chosen to undertake and periodically verify that everyone is following the rules. This is where **governance** and **compliance** kick in.

Today's lesson will introduce how teams in a security departments interact, as well as how the behavior of an organization's employees— known as its **security culture**- influences both what these teams do and which security decisions the business makes.


### 02. Student Do: Weighing Security and Business Objectives (0:10)

### 03. Review: Business vs. Security (0:10)

### 04. Instructor Do: Security Culture Framework (0:15)

Some of the business plans that you analyzed in the previous activity implied major vulnerabilities. 

For example: Giving all developers access to all data and exposing administration servers to the internet.

  - Remind students that the first suggestions was made by the organization's _Director of Engineering_ and the latter by the _Director of IT_. 
  
  - However, both requests betray abundant disregard for data security.

  - These directors would not have made these requests if they understood how insecure they were and if they considered security an important goal for their teams. 

Ensuring the development of a strong organizational security posture begins by ensuring employees both _consider security important_ and _understand the security implications of their decisions_. 
 
 - These two factors ensure that employees do not make decisions that compromise the business's security due to either ignorance or disinterest.

When employees are invested in the organization's security and they understand how to "behave securely", the company is said to have a healthy **security culture**. Developing a healthy security is an important goal for security departments in all organizations.

**Security culture** is the way members of an organization think about and approach security issues. The health of an organization's security culture is determined by the following:

  - How important its employees consider security

  - How aware employees are with common security risks

  - Whether its employees know how to avoid insecure behavior

The organization from the previous exercise probably has an unhealthy security culture, because neither the Director of Engineering nor the Director of IT were aware of the security risks implicit in their requests. If they were aware, they simply didn't care.

- The effectiveness of an organization's security guidelines and controls ultimately depends on whether or not employees abide by those guidelines and controls. Therefore, employees must believe that security is important and follow security rules that the organization has in place.

Next, we'll study the **Security Culture Framework** in order to understand plans put in place to develop a healthy security culture that motivates employees to value security and trains employees on how to avoid insecure behavior.

#### The Security Culture Framework

Simply put, a Security Culture Framework is a process for identifying problems in an organization's security culture and developing plans to solve them. (Just another way cybersecurity professionals are assessing threats and mitigating risks).

- Bad security culture can lead to a breach: Target had alerts that indicated there was a potential security issue, but the security teams had so many alerts that they missed the identification of this critical security alert. A good security culture would have made sure all their staff paid close attention to all critical alerts

Let's look at the following steps of developing a Security Culture Framework:

  - **Step One: Measure and Set Goals**: We'll need to understand the current state of the organization's security culture.          
    
    - Start by identifying a particular security concern, such as employees downloading arbitrary files from emails. 
    
    - Then, define the behavior people should engage in. In this case, only download emails from trusted domains. 
    
    - Next, define a goal for how well you want the organization to perform: fewer than 5% of employees download untrusted files every month. 
    
    - Finally, measure how often employees currently perform proper practice. In this case, you could run a survey, or even have penetration testers send phishing emails to your organization and determine how many people they can infect. This data will serve as the baseline by which you will compare against the newly implemented security culture exercise.

  - **Step Two: Involve the Right People**: After defining a goal, inform the relevant employees of the new target. 

    - Meeting this particular goal requires input from the security department, but also from personnel in charge of Training and Internal Communications.

  - **Step Three: Create an Action Plan**: After the relevant stakeholders have been informed, develop an action plan. A plan typically involves developing a training exercise that addresses the security issue at hand. 

    - The Dangers of Malware
  
    - How Malware Spreads through Phishing
  
    - How Malware Spreads through Vishing
  
    - How to Avoid Phishing and Vishing Attacks
  
  - **Step Four: Execute the Plan**: After developing the plan, run the training. 
  
  - **Step Five: Measure Changes**: Collect data on how well people are adhering to the guidelines taught in the training and compare this to the measurements you took before training to determine if your exercise has been effective.

Next, we'll run through these steps using a new example:

#### Applying the Security Culture Framework

Let's use the following social engineering problem:

  - Employees are receiving emails to their company email address from external sources. 
  
  - The employees are then clicking on links and downloading attachments in these emails. 
  
  - The security team at the organization has determined that the links/downloads in many of these emails have been determined to contain malware.

Consider the following process to demonstrate how to address this email problem and improve security culture:

  - **Measure and Set Goals**: 

    - Begin by hiring a pentester to run a phishing campaign against your organization. They will send malicious files to everyone in the organization, and keep track of who downloads them. 
    
    - Use this data to determine two things: What percentage of employees download the files and exactly who downloads them. 
    
    - Suppose that 9% of employees download the malicious files. Based on these findings, set a goal that only 5% of employees download malicious files by the start of the next fiscal year.
    
    - In addition to this end goal, aim to train 25% of employees every quarter, until you've trained everyone by the end of the year.
  
  - **Involve the Right People**: 
    
    - Since this training will affect all members of the organization, you decide to inform the executive team about the problem and your decision to implement training. 

    - We'll cover specific roles in detail later. For now, likely inform at least the **CEO** and / or **CIO**, **Head of HR**, and whomever is in charge of internal communications and training. 
    
    - In addition, perhaps to draft a contract with the pentesting team that ran the original phishing campaign to ensure that they can run the same test next year to provide reliable measurements as to how effective the training has been.
  
  - **Create an Action Plan**: After getting clearance to run the training, plan to deliver an annual Cybersecurity Awareness Training event that teaches employees about:
    
    - The Dangers of Malware
    
    - How Malware Spreads through Phishing
    
    - How Malware Spreads through Vishing
    
    - How to Avoid Phishing and Vishing Attacks
  
  - **Execute the Plan**: After developing the training, run it and aim to train 25% of employees every quarter in accordance with your original goal.
  
  - **Measure Changes**: After training the entire company, have the pentesters run the same phishing campaign from before. You might find that only 6% of employees download malicious files. In this case, you observed a roughly 30% reduction in malicious file downloads, but didn't quite meet the initial goal. At this point, you would either revise that target, or run the training again until you get below 5%.

The details of this exercise will vary on a case-by-case basis. However, the high-level steps remain the same, regardless of context.

### 05. Student Do: Security Culture Framework Part 1  (0:15)


### 06. Instructor Review: Review Security Culture Framework Part 1 (0:10)


### 07. Instructor Do: Security Roles and Responsibilities (0:15)

These plans implies a lot of coordination. 

While this is ultimately a _security_ function, the logistics of executing it require input from many departments. You'll have to train 25% of the company each quarter which means grouping employees into cohorts; contacting them; tracking who's responded and who's delinquent; scheduling trainings; tracking attendance; etc.

- The following departments must be involved:

  - **Human Resources**: HR will be responsible for internal communications, scheduling trainings, and tracking attendance.
  
  - **Finance**: A project of this magnitude will draw considerable resources, and likely require budget approval from Finance.
  
  - **Security**: Security must develop the training exercise and collaborate with HR to determine details of scheduling and delivery.

  - These departments are the bare minimum for organizing trainings. Larger organizations will account for other department input. 

- Now we'll look at:

  - Which executive roles exist in most companies.

  - Which executive roles are relevant to security departments.

  - The responsibilities of the security department.

  - The structure of the security organization.

#### Executive Roles

All companies have a core leadership team that delegates the responsibility of a business's separate functions. This team usually consists of **C-Suite Officers**, such as the **Chief Executive Officer (CEO)**, **Chief Information Security Officer (CISO)**, and **Chief Operating Officer (COO)**.

The common C-Suite roles include: 

  - **Chief Executive Officer (CEO)**
    
    - The CEO is responsible for plotting the overall direction of the company. 
    
    - Responsibilities include: conceiving and communicating a corporate mission or ultimate goal; determining what the business should focus on in order to meet those goals; assessing risks; and setting standards of social responsibility for the organization.

    - The CEO reports to the **Board of Directors**. This is a group of individuals, elected by shareholders, which holds the CEO accountable for meeting the demands of those shareholders. They are also able to replace executives in the event of under performance or scandal.
  
  - **Chief Operating Officer (COO)**

    -  The COO is responsible for ensuring a business is able to function effectively day-to-day and typically reports directly to the CEO. 

    - Responsibilities include: monitoring day-to-day operations; keeping the CEO apprised of significant achievements and setbacks; overseeing people management (hiring, promotion, firing); 
    
    - The COO improves efficiency by developing and disseminating **Standard Operating Procedures**, or _"standard ways of doing common, important things"_.
  
  - **Chief Financial Officer (CFO)**:

    - The CFO is responsible for charting and monitoring the company's financial trajectory. 
    
    - In other words, they are ultimately responsible for good **budgeting**, which helps ensure that the company uses its cash wisely.

    - The CFO typically reports directly to the CEO.

  - **Chief Information Officer (CIO)**: 
  
    - The CIO is responsible for developing IT systems that support the business. 
    
    
    - Responsibilities include: setting up corporate networks; provisioning services like VPN; setting up and recycling employee devices; ceasing servers for data storage and internal application development

    - The CIO typically reports to the CEO. 


  - **Chief Information Security Officer (CISO)**

    - The CISO is responsible for managing risk to an organization's data throughout its life cycle. In other words, the CISO is responsible for ensuring that the company's data is safe from the time it's collected to the time it's stored and retrieved. 
    
    - Responsibilities include: Overseeing a security operations organization, which identifies, contains, and responds to threats; developing and disseminating information security policies; developing and disseminating training to personnel; working with the CIO to coordinate implementation of security policies by IT Teams

    - Traditionally, the CISO reports to the CIO. However, it's increasingly common for the CISO to report directly to the CEO, as data security is becoming increasingly important for organizations everywhere. 
    
  - Other Instances: 

    - Some organizations have additional roles, such as a **Chief Technology Officer (CTO)** or **Chief Product Officer (CPO)**. 

    - Some organizations _only_ have a CISO and not a CIO. In this case, the CISO serves both responsibilities.

Organizations have roles outside of C-Suite roles: 

  - **Vice Presidents (VPs)** can exist in any department and typically report to their C-Level officers. 

    - VPs are accountable for a broad but well-specified portion of their Officer's general responsibility. 

    - For example, a CIO might have a **Vice President of Networking** who manages all networks. Vice Presidents, in turn, often manage **Directors**.

  - **Directors** handle specific functions under VPs. 

    - For example, the VP of Networking might have a **Director of IT**, responsible for building and configuring networks; and a **Director of Network Security**, responsible for securing those networks.

    - A Director of Networking in a large company would likely need to manage many facets of the network, in many places, all at once. 
    
    - For example, they might be responsible for ensuring internal support tickets are reviewed within 24 hours; guaranteeing core data servers perform as required; and overseeing core software updates across the server infrastructure. The Director's role might be to prioritize these responsibilities, and decide which teams should receive the most funding and support.

  - **Managers** will coordinate segmented portions of work under Directors. 

    - For instance, the Director of Networking might hire a dedicated **Performance Manager**, who would be responsible for ensuring data servers run efficiently. Their responsibilities might include identifying when servers are performing poorly, and planning work to fix such issues as they arise.

Finally, each manager would hire a team of **Engineers** to delegate the implementation of work to. 

  - For example, if the Performance Manager identifies a serious routing bottleneck in the network structure, they might assign two **Network Engineers** to solve the problem together. They would be responsible for actually fixing the problem, and validating their fix.

An example reporting structure hierarchy:

  - The **Network Engineers** would report their success or failure to the Performance Manager.

  - The **Performance Manager** would receive reports from several Network Engineers, each working on different tasks. They would use these reports to inform the Director of IT if the organization is meeting its network performance targets.

  - The **Director of IT** would receive reports from several managers, each in charge of a different aspect of the network. They would use these reports to tell the **VP of Networking** which functions of the IT department are going well (e.g., performance is good, but updates are being applied too slowly). They might also decide whether their managers need to hire larger teams or if the business needs to invest in training.

  - The **VP of Networking** would receive reports from all of their Directors. They would use these reports to determine the overall health of the company's networking teams and infrastructure, and how well they help the organization achieves its goal. They might also give their Directors input on how to prioritize based on the company vision. E.g., a VP of Networking might encourage her Director of Network Security to change strategies and prioritize strong security over ease of use, because the CEO has determined that the company should become an industry leader in client data privacy.

Not all organizations have all these layers of management and the responsibilities of each role are less clearly defined the further down the hierarchy you proceed. However, the roles and general responsibilities we discussed  are commonly found in most organizations with mature security functions.

No we will proceed by exploring the common roles and responsibilities in a security department.

#### The Responsibilities of the Security Department

The CISO is responsible for protecting the company's data. There are many ways to meet this broad goal, but organizations often have the following functions in-house:

  - **Network Security** is in charge of securing networks and implementing network security policies. This group also manages services like the corporate VPN, etc.

  - **Incident Response** is in charge of identifying and responding to security breaches. IR is responsible for SOCs, which monitor the organization's devices for incidents. IR is also responsible for escalating serious breaches to the executive team for handling.

  - **Application Security** is in charge of ensuring that any software or web applications developed in-house is secure. This security prevents disasters such as insecure internal messaging apps that leak confidential information, etc.

The individuals who manage these functions often carry the following titles and mention their responsibilities:

  - A **Director of Networking** or **Director of Network Security** is often in charge of networks. They are responsible for purchasing or leasing, configuring, maintaining, and troubleshooting the organization's network infrastructure.  

  - A **IR Manager** or a  **SOC Manager** will manage an IR tram. The titles refer to the same responsibilities. They are responsible for consistently identifying and containing breaches as they occur, and instructing the Director of Networking as to how to better secure the organization's networks to prevent breaches in the future.

  - A **Security Architect** is typically in charge of application security. They are responsible for ensuring that internally developed applications meet security standards. This means minimizing the number of breaches due to the application; ensuring these applications pass security audits; and teaching developers to follow best practices of secure development.

These managers often hire the following roles:

  - A Director of Networking often has **system administrators**, **network administrators**, and physical **network technicians** on staff. They may also manage a Help Desk.

  - A SOC Manager employs **SOC Analysts**, also known as **Security Analysts** or **Incident Handlers**.

  - A Security Architect typically manages **Security Engineers** and **Software Engineers**.

### 08. Student Do: Designing a Security Org Chart (0:20)


### 09. Review: Creating a Security Organization Chart (0:15)


### 10. Break (0:10)


### 11. Revisiting the Security Culture Framework (0:15)

Now that we have a greater understanding of the organizational layout of business, we can switch back to Security Culture Framework.

Consider the following hypothetical social engineering example involving email phishing examines: 

-  Employees are receiving emails to their company email address from external sources. The employees are then clicking on links and downloading attachments in these emails. The security team at the organization has determined that the links/downloads in many of these emails have been determined to contain malware.

Let's walk through the following steps again, with the added context and additional information of coordinating with other team members. 

 - Be creative and engaging with how you move from step-to-step. 
 - Ask students guiding questions after each step that will lead into next step. 
 - Some suggestions are provided below, but feel free to ask your own questions. 

To facilitate this discussion, consult the following file, which contains the steps and information: [File: Security Culture Framework](Stu_SecCultureFramework.md)

Below is a step-by-step guide for approaching the problem:

- **Step 1**: The Security Culture Framework (SCF) Team meets privately to assess the impact of the phishing incident and understands the risk future campaigns pose to the organization. This discussion includes:

  - An assessment of the damages incurred by the previous phishing incident.

  - A measurement of how many employees download malicious files, obtained by having a pentesting firm launch a phishing attack against the company. This assessment might find a 10% click-through rate, meaning that 10% of employees download malicious email attachments.

  - Setting a target click-through rate. The team might decide that a 5% click-through rate is acceptable.

- **Step 2**: The SCF Team Manager (in this case, the IR manager) meets with the CISO to explain that the previous phishing attack was successful because 10% of employees often download arbitrary files from arbitrary email addresses. Then, they request a budget to execute a plan to bring this number down to 5% and explain how this would be profitable for the business.

- **Step 3**: The SCF Team develops a training plan that educates employees.

  - In addition, the SCF Team develops a _Supplemental Security Awareness_ training plan. This plan will be delivered only to employees who continue to click malicious links after training.

- **Step 4**: After developing the training, the SCF Team decides on incentives and disincentives. These incentives/disincentives will be awarded based on how employees behave during penetration tests and security audits. Since employees won't know exactly when these assessments are being conducted, the team expects greater adherence to the new download guidelines.

  - **Incentives for Not Clicking Through During Assessment**: $40 Gift Card, Free or Discounted Security Conference Attendance, Additional Vacation Time

  - **Disincentive for Clicking Through During Assessment**: Supplemental Security Awareness Training, Additional Random Device Audits for One Quarter

- **Step 5**: The SCF Team collaborates with HR to determine the best dates to run trainings. During these meetings, the HR Team explains that the most reliable way to ensure 100% attendance over the course of the next fiscal year is to have quarterly training sessions, and train 25% of employees each time. Together, they coordinate the specific dates and location of the training.

- **Step 6**: The SCF Team collaborates with Communications to develop and distribute information about the training.

- **Step 7**: The SCF Team sets up and runs the training as scheduled.

- **Step 8**: Every quarter, the SCF Team contracts the same pentesting firm to run the phishing campaign against all employees who have already been 
trained.

- **Step 9**: After every test, the SCF Team will identify employees who still clicked malicious links, and make them go through _Supplemental Security Awareness_ training. In addition, they will check to make sure that the click-through rate drops closer to 5%.

- **Step 10**: After training the entire company, the SCF Team will run a final phishing campaign to evaluate the overall effectiveness of the training. If they find that the click-through rate is 5% or lower, it can be considered a success. Otherwise, they may decide to run the training for an additional year, or take a different approach to solving the problem.

Review the steps again by considering the following recap questions :

  - **When Will the Plan Be Executed?**: 
  
    - The SCF and HR Teams agree to run the training once every quarter and train 25% of employees each time. They do this to ensure that they can train 100% of employees over the course of the year, and move people between sessions if necessary.
  
  - **When Will You Measure Progress?**: 
  
    - The SCF Team decides to run a phishing campaign every quarter. Each time, they'll run the campaign only against the most recently trained cohort. After all cohorts have been trained, they will run a final assessment to evaluate how well everyone adheres to the new guidelines over time.
  
  - **How Will You Quantify Progress?**: 
  
    - The SCF Team decided to quantify the _click-through rate_, which is the percentage of employees who download malicious links from emails. Their ultimate goal is to bring this number from 10% down to 5% after training.

The company can take different approaches in the event the SCF Team missed their target. If the click-through rate _increased_, for example, they would choose a different strategy altogether. If it lowered to 6%, but not 5%, they might simply run the training again.


### 12. Student Do: Security Culture Framework Part 2 (0:20)


### 13. Review: Review Security Culture Part 2 (0:10)

### 14. Security Controls (0:10)

Training won't address the problem in the short term: It will take at least a quarter to train just 25% of the company. Improving the organization's security culture is a valuable long-term outcome, but the issue also needs to be mitigated immediately.

- In addition to training, the organization can implement **security controls** that prevent the problem independent of the training.

  - For example, the firm might implement a content filter that prevents employees from downloading files from emails that didn't come from a company email address.

- Security controls address the problem from two angles:

  - First, it addresses _employee behavior_ and security culture by educating the organization in best practices.

  - Second, it addresses the issue directly by "patching" the vulnerability.

- Layering security controls is fundamental for an important security design framework known as **defense in depth**.

We'll proceed by covering different types of access control and using them to further explore the concept of defense in depth.

#### Security Controls

A **security control** as any system, process, or technology that protects the confidentiality, integrity, and accessibility of a resource.

Controls can be **administrative**, **technical**, or **physical** in nature. Consider the following examples of each type of control:

  - **Administrative**: Requiring employees to adhere to training guidelines.

  - **Technical**: Forcing developers to authenticate using SSH keys rather than passwords.

  - **Physical**: Protecting a building by requiring key-card access.

The controls of each type can have different goals:

- **Preventive** controls _prevent_ access with _physical_ or _logical/technical_ barriers. Key-card access constitutes a preventive control.

- **Deterrent** controls _discourage_ attackers from attempting to access a resource. 

- **Detective** controls do not protect access to a confidential resource. Rather, they _identify and record_ attempts at access.

- **Corrective** controls attempt to fix an incident and possibly prevent reoccurrence.

- **Compensating** controls do not prevent attacks, but restore the function of compromised systems.

Note: These categories are important to know for the Security+ Exam.

Regardless of type, all controls seek to restrain or respond to _access_ to a given resource. **Access control** is the practice of controlling who can access which resources. We will learn more about access controls in future units. For now, here are some high level examples of controls for specific domains:

  - **Linux**: File permissions act as access controls by preventing users from modifying files they don't own.
  - **Networks**: Firewalls control access to networks.
  - **IR**: Monitoring systems act as _detective_ controls.


Controlling access often also implies tracking **identity**, as seen with key cards. Together, these make up the field of **Identity and Access Management (IAM)**.

#### Defense in Depth

**Defense in Depth** is a concept in which multiple defenses are used to secure a resource. For example, a secure network might protect an SSH server in three ways:

  - Hiding it behind a firewall that only forwards connections from the corporate VPN.
  - Forcing users to authenticate with SSH keys _and_ passwords.
  - Requiring them to generate new keys, with new strong passwords, every quarter.

- Acknowledge the nature of the controls above:

  - **Technical**: Protect the server with a firewall. Require password-protected key authentication.

  - **Procedural**: Invalidate keys every quarter and require users to generate new ones.
  
- Since security is ensured by implementing three layers of protection, the SSH server has **control diversity**, because it is protected with multiple methods. 

- These securities are probably excessive protection for an SSH server, but it illustrates the principle of Defense in Depth: Defending the system in multiple ways ensures that it remains protected _even if one of them fails_. 

This concept is known as **redundancy**. Redundancy is achieved because:
  
  - Protecting the SSH server with a firewall prevents unwanted connections from unintentional attackers.
  
  - In the event an attacker bypasses the VPN, they still can't easily compromise the server. Since it forces users to authenticate with SSH keys _and_ passwords, they can't easily brute-force the login. In addition, they would be unable to use even a valid, stolen SSH key without also uncovering its password. Thus, requiring password-protected SSH keys, in itself, affords two layers of protection.
  
  - In the event an attacker does steal both a valid SSH key _and_ its password, they would only be able to compromise the server for a limited amount of time, since the stolen key would be invalidated in at most three months.

- Ensuring redundancy eliminates the inherent risk of **single points of failure**. If the system above only had a single control, that control would be its single point of failure. An attacker could compromise the system by breaking just a _single_ control.

- In addition to Technical and Procedural controls, defense in depth strategies can be built with:
  
  - **Personnel Security**: Issuing ID cards to all employees.
  
  - **Physical Security**: Requiring ID cards for access to physical buildings.

- The training plan developed in the previous class exercises addresses _personnel security_. However, applying the principle of defense in depth suggests that the action plan should include alternative measures to address the "tailgating" problem.

### 15. Student Do: Implementing Security Controls (0:10)

### 16.  Review: Implementing Security Controls (0:10)

### 17. Wrap-Up and Summary (0:05)

Many organizations settle on a set of such "good behaviors" that they want employees to engage in. These sets of rules form standards, polices, and procedures.

- These "rules", as well as controls like encryption and keycard access, are only good if they're obeyed.

These considerations relate to the study of **governance**, the field of enforcing these standards, policies, and procedures, such that they are always obeyed. 

Now that we have a good understanding of how organizations begin to develop best practices, we can study how it codifies these practices into standards and applies ideas from governance to keep them enforced.

---

&copy; 2020 Trilogy Education Services