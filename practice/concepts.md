======concepts======
{{{
Classical security concepts
Terminology sequence: weakness -> vulnerability -> attack
Weakness can be introduced into product during these development stages: design -> coding -> configuration -> product usage.

Weakness can be a vulnerability.
Some vulnerabilities can be used for attack.
Attacks is what causes damage to companies.
  Damage can be financial, reputational, …
Threat is a possible danger that might exploit a vulnerability to breach security and therefore cause possible harm.

APT (Advanced Persistent Threat) is a continuous, targeted computer hacking processes, involving various attacks with known vulnerabilities and 0-days.

Average hacker’s persistence in infrastructure during APT is 9 months.
Majority of company’s breaches are started with: phishing or watering hole attack.
Mitigation:

company should implement defense mechanisms for its protection
company should take measures in area of damage minimization

Duck-hunting attack - compromisation using physical intrusion. (e.g. hacker came into company with malicious usb stick, did smth tricky and went out).
}}}
======Intruder model======
{{{
external (not companie’s employee / ousider)
intruder has no access to system
intruder has unprivileged access to system
intruder has privileged access to system

[[internal]] (company’s employee)
intruder has unprivileged access to system
intruder has privileged access to system
}}}
======C I A ======
{{{
CIA - information security (wikipedia) key concepts
Confidentiality
Integrity
Availability
}}}
======AAA======
{{{
Authentication
Authorization
Accounting
}}}
======STRIDE======
{{{
STRIDE (model of threats developed by Microsoft)

Spoofing of user identity
Tampering
Repudiation
Information disclosure (privacy breach or data leak)
Denial of service (DoS)
Elevation of privilege
}}}
======access control ======
{{{
Discretionary access control
Mandatory access control
Role-based access control (RBAC)
BAD principle: Security through obscurity
GOOD principle: Strict access control (+ isolation (e.g. VPN, firewall)) (minimal privileges concept)
}}}
======Searching vuln======
{{{
manual audit
security scanners
source-code analysis (static, dynamic)
monitoring systems (log analysis)
fuzzing
}}}
======securing yourself======
{{{
Known vulnerabilities:
get security updates in a regular manner
resolve security issues (came from IT department, SOC, …)

Unknown vulnerabilities and threats:
Implement various security solutions: IDS, IPS, WAF, AntiVirus, SOC (SIEM, DLP, IRP, …) …
}}}
{{{
Networking, defence in depth
concept: defense exists on every level (DMZ-vs-internal is an old concept)
perimeter defense (Firewall, IDS, IPS, …)
defense inside (IPsec, TLS, …)
devices/hosts defense (patching, antiviruses, …)
enryption, access rights, minimal privileges principle
attack-surface minimization
if possible: out of band management (isolated network for administrators)
}}}
======audit ======
{{{
Comparison of application security testing approaches
}}}
{{{
Approaches in providing penetration testing:
blackBox - nothing is known about system, usually an external pentest
greybox - some information about system is known, can be external or internal pentest
whitebox - more of a security assessment rather than a pentest (with access to source code, configurations, …)
}}}
======service======
{{{
Penetration Testing (pentest)
Security Analysis
Vulnerability Scanning
Red Team Assessment
Blue Team
Purple Team
Security Audit (not technical)
}}}
======entry points======
{{{
client’s devices (theft / hacking) (smartphone / laptop / wifi-router / …)
server side service (hacking) with sensitive information
infrastructure (free-wifi / guest-wifi / internet-cafe / …)
social engineering (malicious email / run executable / insert flash-card / …)
attack from inside (intentional / unintentional) (employee foolishness / ex-admin / outsource IT administration / …)
}}}
======Kill-Chain ======
{{{
reconnaissance - harvesting e-mail addresses, conference information, …
weaponization - coupling exploit backdoor into deliverable payload
delivery - delivering weaponized bundle to the victim via e-mail, web, usb, …
exploitation - exploiting a vulnerability to execute code on victim’s system
installation - installing malware on the asset
Command and Control (C2) - command channel for remote manipulation of victim’s system
Action on Objectives - the attacker performs the steps to achieve his actual goals inside the victim’s network
This is active attack process that takes months, and thousands of small steps, in order to achieve
Perimeter-focused defences (e.g. firewalls, sandboxes, antiviruses) cannot provide 100% protection.
Harden your inside security (minimal privileges concept, updates, …) and use breach detection systems.
}}}
======Postexploitation ======
{{{
Collect information about system
Privilege escalation
Credentials collection
Installation (fixation in system)
Concealment
Destructive actions
}}}
======Business related ======
{{{
Objects-subjects:

devices
applications
network
data
people
}}}
======best practices======
{{{
Every process TOP 5 best practices

don’t overcarry
don’t undercarry
principle of “least access”
keep documented, controle and manage
create “bad day plan”
}}}
======undertake======
{{{
implement SDL (Secure Development Lifecycle)
run bug-bounty programs / pay for pentests and security assessments
build SIEM
be compliant with best practices / standards
develop and implement secure companie’s processes
}}}
======pentest input ======
{{{
network segmentation (users, DMZ, processing, technology)
ACL / firewall
available applications / DBMS (production and testing)
wifi-networks
user’s blocking
}}}
======Pentest report======
{{{
executive summary
scope of work and limitations
description of the system under test - artifact of our own analysis at the end of the project
risk analysis - agreed with the client before tests
findings & recommendations
conclusions
}}}
======Assets======
{{{
Information is an asset which has value and must be protected.

individual-related:

credentials for various resources
personal data (name, date of birth, …)
information on the activities and assets of the individual (including social relations)
own data (pictures, documents, programs, …)
business-related:

database data (e.g. employer’s data, customers’s data, product’s data, …)
corporate secrets (e.g. developed source code, …)
data of processes support system
licenses
Threats:

data/money theft/loss
publication of data (reputation concerns)
DoS (availability issues)
}}}
======Attackers======
{{{
script kiddies
Advanced hackers (APT)
Insiders
}}}
======Possible targets======
{{{
governments: IS - critical, budget - unlimited
big-organizations: IS - business, budget - limited
small-organizatins/private security: IS - personal data, budget - none

dozen of employee
IT companies: no administrators
(programmers takes admin functions)
no budget for security
no strict IT-processes
 
small network
BYOD - bring your own device
data: client’s personal data
}}}
======Overall threats======
{{{
disasters: fire, flood, electricity fault, …
hardware break/theft
}}}
======Eliminating risks======
{{{
move risks to other’s responsibility area (e.g. provider’s)
duplication and redundancy
administration/update problems
updates
Implement security solutions and security processes, …

plan in case “everything went wrong”
}}}
======Malware ======
{{{
Malware protection methods
Technical products concepts

code emulation
sandboxing (run sample in virtual environment / machines)
hueristic analysis
behavioral analysis (e.g. syscalls interception)
environment virtualization (all changes to disk are temporary until reboot)
}}}
======wifi sec======
{{{
Components of complex Wifi security system

access control
user’s authentication
encryption
Wifi intrusion detection system
outsider’s devices detection
monitor radio interference and DoS
monitor vulnerabilities at wireless network
increase security level (e.g., management frame protection, …)

authentication and authorization (X.509)
configure vlan for traffic separation
use firewalls at L2 layer
use encryption thoughout network
detect integrity violation in network
enable security at end-point devices
}}}
======DLP ======
{{{
real time workflow (example based on arcsight)
Two general DLP approaches:

system learns some samples of confidential documents, constructs rules for engine and every end-point can filter traffic by classifying it.
This approach has complex software, however does not require expensive hardware.
samples: websense (the best, however very expensive, every 3 years you will pay 100% for license)

all data collected from proxy, emails, end-points, etc. are stored to high-performance hard drives for further manual analysis. System usually store logs for last several months.
This approach has simple software, however requires expensive technical equipment (hard drives).
samples: searchinform, infowatch, …
}}}
======Leaking assets======
{{{
general data leak paths:
email
web-resources (file shares, messengers, …)
usb-drives
camera photos or videos
write something on paper
personal will just memorize smth and reproduce it outside

leaking data presentation:
encrypted archives, docs, …
photos
The Art Of Forensics
}}}
======Honeypot======
{{{
simulates easy-to-own server
constantly watched by security professionals
must be isolated from other network’s resources
may discover attack on its first steps
allows to study hackers, their methods and toolkit
}}}
