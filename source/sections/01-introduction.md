# 1. Introduction

Insight Rx, Inc ("Insight Rx") is committed to ensuring the confidentiality, privacy, integrity, and availability of all electronic protected health information (ePHI) it receives, maintains, processes and/or transmits on behalf of its Customers. As providers of compliant, hosted infrastructure used by health technology vendors, developers, designers, agencies, custom development shops, and enterprises, Insight Rx strives to maintain compliance, proactively address information security, mitigate risk for its Customers, and assure known breaches are completely and effectively communicated in a timely manner. The following documents address core policies used by Insight Rx to maintain compliance and assure the proper protections of infrastructure used to store, process, and transmit ePHI for Insight Rx Customers.

Insight Rx provides secure and compliant cloud-based software. This hosted software falls into two broad categories: 1) **Platform as a Service (PaaS)** and 2) **Platform Add-ons**. These Categories are cited throughout polices as Customers in each category inherit different policies, procedures, and obligations from Insight Rx.

## 1.1 Platform as a Service (PaaS)

PaaS Customers utilize hosted software and infrastructure from Insight Rx to deploy, host, and scale custom developed applications and configured databases. These customers are deployed into compliant containers run on systems secured and managed by Insight Rx. Insight Rx does not have insight or access into application level data of PaaS Customers and, as such, does not have the ability to secure or manage risk associated with application level vulnerabilities and security weaknesses. Insight Rx makes every effort to reduce the risk of unauthorized disclosure, access, and/or breach of PaaS Customer data through network (firewalls, dedicated IP spaces, etc) and server settings (encryption at rest and in transit, OSSEC throughout the Platform, etc).

PaaS Customers can opt for a list of Services from Insight Rx, which include Backup Service, Logging Service, IDS Service, and Disaster Recovery Service. These services are not standard and PaaS Customers must sign up for them in order for Insight Rx to manage these areas of security and compliance.

## 1.2 Platform Add-ons

Add-ons are compliant API-driven services that are offered as part of the Insight Rx Platform. These services currently include our Backend as a Service and secure Messaging Service. With Add-ons, Insight Rx has access to data models and manages all application level configurations and security.

In the future there may be 3rd party Add-on services available as part of the Insight Rx Platform. These 3rd party, or Partner, Services will be fully reviewed by Insight Rx to assure they do not have a negative impact on Insight Rx's information security and compliance posture.

## 1.3 Compliance Inheritance

Insight Rx provides compliant hosted software infrastructure for its Customers. Insight Rx has been through a HIPAA compliance audit by a national third-party compliance firm to validate and map organizational policies and technical controls to HIPAA rules. Insight Rx's company policies, procedures, and technologies are HITRUST Certified. Insight Rx's service offerings are available on AWS, Azure, Rackspace, and SoftLayer; current production systems on these platforms are included in Insight Rx's third-party audits and HITRUST certification.

Insight Rx signs business associate agreements (BAAs) with its Customers. These BAAs outline Insight Rx obligations and Customer obligations, as well as liability in the case of a breach. In providing infrastructure and managing security configurations that are a part of the technology requirements that exist in HIPAA and HITRUST, as well as future compliance frameworks, Insight Rx manages various aspects of compliance for Customers. The aspects of compliance that Insight Rx manages for Customers are inherited by Customers, and Insight Rx assumes the risk associated with those aspects of compliance. In doing so, Insight Rx helps Customers achieve and maintain compliance, as well as mitigates Customers risk.

Insight Rx does not act as a covered entity. When Insight Rx does operate as a business associate (not a subcontractor), Insight Rx does not interface with users to obtain or provide access to ePHI. Access to ePHI is through our customers' applications.

Certain aspects of compliance cannot be inherited. Because of this, Insight Rx Customers, in order to achieve full compliance or HITRUST Certification, must implement certain organizational policies. These policies and aspects of compliance fall outside of the services and obligations of Insight Rx.

Mappings of HIPAA Rules to Insight Rx controls and a mapping of what Rules are inherited by Customers, both Platform Customers and Add-on Customers, are covered in [§2](#2.-hipaa-inheritance).

## 1.4 Insight Rx Organizational Concepts

The physical infrastructure environment is hosted at [Rackspace](https://www.rackspace.com/), [Amazon Web Services](https://aws.amazon.com/) (AWS), [Microsoft Azure](https://azure.microsoft.com/), and [IBM SoftLayer](http://www.softlayer.com/). The network components and supporting network infrastructure are contained within the Rackspace, AWS, Azure, and SoftLayer infrastructures and managed by Rackspace, AWS, Microsoft, and IBM (respectively). Insight Rx does not have physical access into the network components. The Insight Rx environment consists of Cisco firewalls; nginx web servers; Java, Python, and Go application servers; Percona and PostgreSQL database servers; Logstash logging servers; Linux Ubuntu monitoring servers; Windows Server virtual machines; Chef and Salt configuration management servers; OSSEC IDS services; Docker containers; and developer tool servers running on Linux Ubuntu.

Within the Insight Rx Platform on Rackspace, AWS, Azure, and SoftLayer, all data transmission is encrypted and all hard drives are encrypted so data at rest is also encrypted; this applies to all servers - those hosting Docker containers, databases, APIs, log servers, etc. Insight Rx assumes all data *may* contain ePHI, even though our Risk Assessment does not indicate this is the case, and provides appropriate protections based on that assumption.

In the case of PaaS Customers, it is the responsibility of the Customer to restrict, secure, and assure the privacy of all ePHI data at the Application Level, as this is not under the control or purview of Insight Rx.

The data and network segmentation mechanism differs depending on the primitives offered by the underlying cloud provider infrastructure:

* Within Rackspace, hosted load balancers segment data and traffic while Cisco firewalls route traffic to private subnets for PaaS Customers and for Platform Add-ons.
* Within AWS, hosted load balancers segment data across dedicated Virtual Private Clouds for PaaS Customers and for Platform Add-ons.
* Within Azure, hosted load balancers segment data across dedicated Virtual Networks for PaaS Customers and for Platform Add-ons.
* Within SoftLayer, hosted load balancers segment data across dedicated Private Networks for PaaS Customers and for Platform Add-ons.

The result of segmentation strategies employed by Insight Rx effectively create RFC 1918, or dedicated, private segmented and separated networks and IP spaces, for each PaaS Customer and for Platform Add-ons.

Additionally, IPtables is used on each each server for logical segmentation. IPtables is configured to restrict access to only justified ports and protocols. Insight Rx has implemented strict logical access controls so that only authorized personnel are given access to the internal management servers. The environment is configured so that data is transmitted from the load balancers to the application servers over an TLS encrypted session.

In the case of Platform Add-ons, once the data is received from the application server, a series of Application Programming Interface (API) calls is made to the database servers where the ePHI resides. The ePHI is separated into PostgreSQL and Percona databases through programming logic built, so that access to one database server will not present you with the full ePHI spectrum.

The VPN server, nginx web server, and application servers are externally facing and accessible via the Internet. The database servers, where the ePHI resides, are located on the internal Insight Rx network and can only be accessed through a bastion host over a VPN connection. Access to the internal database is restricted to a limited number of personnel and strictly controlled to only those personnel with a business-justified reason. Remote access to internal servers is not accessible except through load balancers.

All Platform Add-ons and operating systems are tested end-to-end for usability, security, and impact prior to deployment to production.

## 1.5 Requesting Audit and Compliance Reports

Insight Rx, at its sole discretion, shares audit reports, including its HITRUST reports and Corrective Action Plans (CAPs), with customers on a case by case basis. All audit reports are shared under explicit NDA in Insight Rx format between Insight Rx and party to receive materials. Audit reports can be requested by Insight Rx workforce members for Customers or directly by Insight Rx Customers.

The following process is used to request audit reports:

1. Email is sent to team@insight-rx.com. In the email, please specify the type of report being requested and any required timelines for the report.
2. Insight Rx staff will log an Issue with the details of the request into the Insight Rx Compliance Review Activities Project on JIRA. JIRA is used to track requests status and outcomes.
3. Insight Rx will confirm if a current NDA is in place with the party requesting the audit report. If there is no NDA in place, Insight Rx will send one for execution.
4. Once it has been confirmed that an NDA is executed, Insight Rx staff will move the JIRA Issue to "Under Review".
5. The Insight Rx Security Officer or Privacy Officer must Approve or Reject the Issue. If the Issue is rejected, Insight Rx will notify the requesting party that we cannot share the requested report.
4. If the Issue has been Approved, Insight Rx will send the customer the requested audit report and complete the JIRA Issue for the request.

## 1.6 Version Control

Refer to the GitHub repository at [https://github.com/catalyzeio/policies/](https://github.com/catalyzeio/policies/) for the full version history of these policies.
