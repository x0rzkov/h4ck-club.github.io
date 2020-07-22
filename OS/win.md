###### windows enumeration
```
enumeration
privilege escalation
powershell empire
reverse shell
```
```
About Windows
www.ultimatewindowssecurity.com
C:\Windows\System32 Files Explained
Microsoft security bulletins
MSRC - microsoft security bulletins created based on MSRC portal API
What’s new in Windows 10 - check the “Security” paragraph
windowsserverdocs, windowsserverdocs security


Active Directory domain structure


Технический справочник по Active Directory для Microsoft Windows Server 2003 Логическая структура Active Directory

Active Directory (AD) is a forest with several root domains (e.g. for different companie’s deparments).

Each domain is ruled by some Domain Controller (DC). In forest all DC replecates data between themselves (all DC trusts to each other).
Some DC are selected as “masters” (or PDC - primary domain controller). They may carry out some actions that can fulfilled only on master DC.
(forest level: schema master, domain naming master; domain level: RID master, PDC emulator, infrastructure master) (AD FSMO roles)

AD catalogs:

domain catalog (contains security descriptors) - stores information about users/groups/computers
global catalog - a distributed data repository that contains a searchable, partial representation of every object in every domain in a multidomain Active Directory Domain Services (AD DS) forest. (the global catalog is stored on domain controllers)
general scheme catalog (???) - contains scheme of the whole forest (scheme - list of available object’s attributes) (general for the whole forest) (its permissions inherited from root domain catalog)
general configuration catalogue (???) - information about forest configuration (domaines structure, replication topology, …) and configuration of some applications (e.g. Exchange server, ISA, SharePoint, …) (its permissions inherited from root domain catalog)
applications partitions catalogue (???) (e.g. partition for DNS service) (permissions inheritence specified separately from some domain catalog)
LDAP (Lightweight Directory Access Protocol) - an open, vendor-neutral, industry standard application protocol for accessing and maintaining distributed directory information services over an Internet Protocol (IP) network.

Hierarchy:

c= country/region - recognized only by LDAP
dc= domain component (o= organization - “o” may be used by LDAP instead of dc)
domain component has its own GPO (+ inherited GPO)
ou= organizational unit - hierarchy (tree) within a domain. OU is a container that can be hold other objects and is used to group objects together for administrative purposes. (examples: set of computers, contacts, groups, printers, users, shared folders, …)
Domain’s ACL lists can refer to OU in order to set permissions.
cn= common name: user, group, computer or container.
Container is smth similar to OU, except for linking GPO (Group Policy Object) and delegating administration to a container. Container can be “promoted” to OU. (What does CN stand for)
Examples of full names:

each object has its GUID (unique 128-bit string)
dn - destinguished name: /O=Internet/DC=COM/DC=SavillTech/CN=Users/CN=John Savill
CN=John Savill,CN=Users,DC=SavillTech,DC=COM,O=Internet
LDAP url: LDAP://titanic.savilltech.com/ou=Sales,cn=JSavill,dc=SavillTech,dc=com
LDAP canonical name: savilltech.com/Sales/Jsavill
UPN - user’s principal name: jsavill@savilltech.com
RID cycling - domain objects enumeration attack by bruteforcing or guessing SIDs (because RID is sequential)
impacket script: lookupsid.py "DOMAIN/username:passwd@10.0.0.2"



SID - security identifier
SID - Security identifier, e.g. S-1-5-21-549688327-91903405-2500298261-1000 - S-1-5-21 used for most accounts, 549688327-91903405-2500298261 is a domain SID, 1000 - RID - account’s id.
Some standard SIDs:

User's SIDs:
Group SIDs:


Microsoft/Windows authentication/security tokens, …
Usefull articles:

Security and protection
Permissions vs Privileges: permissions apply to objects, privileges (rights) apply to user account actions. A privilege overrides a permission.



Windows tokens


Usefull artices:

How access tokens work
An access token contains a security identifier (SID) for the user, all of the SIDs for the groups to which the user belongs, and the user’s privileges. Whenever a thread or process interacts with a securable object or tries to perform a system task that requires privileges, the operating system checks the effective access token to determine its level of authorization:

Primary token - access token typically assigned to a process to represent the default security information for that process.
Filtered token - access token with admin privileges removed (Win Vista +)
Impersonation token - access token used by thread temporary to operate on behalf of other impersonated user.
Restricted token - a primary or impersonation access token that has been modified by the CreateRestrictedToken function in order to restrict process/thread in its ability to access securable objects or perform privileged operations.
After security token is set, any changes to account will not take effect until new token will be generated at next relogin action.

Windows tokens can be of 4 impersonation levels:

Anonymous (never been supported) - the client is anonymous to the service. The service can impersonate the client but the impersonation token does not contain any information about the client.
Identify - the service can get the identity of the client and can use this information in its own security mechanism, but it cannot impersonate the client.
Impersonate - the service can impersonate the client. If the service is on the same computer as the client process, it can access network resources on behalf of the client. If the service is on a remote computer, it can impersonate the client only when accessing resources on the service’s computer.
Delegate (Kerberos only - NO NTLM) (Windows 2000 +) - the service can impersonate the client not only when it accesses resources on the service’s computer but also when it accesses resources on other computers.
Check Kerberos delegation for more information.
RDP - the only microsoft service, which transfers user’s credentials (login and password (or ntlm hash)) to remote computer.
security concern: RDP-mitm can result in leaking plaintext login and password.



NTLM


Related phrases: NT Lan Manager / Integrated Windows Authentication / HTTP Negotiate authentication / NT Authentication / NTLM Authentication / Domain authentication / Windows Integrated Authentication / Windows NT Challenge-Response authentication / Windows Authentication

Be carefull often people mean “NetNTLM” while saying “NTLM”. NetNTLM is a challenge-response mechanism, it can be easily eavesdropped or MITMed in order to further bruteforce. NTLM required time synchronization, the difference must not exceed ≈ 30 minutes.

Username and domain are always passed in plaintext during authentication.

Authentication by IP address use NTLM by default (not Kerberous) (e.g. authentication to smb share).

Windows RDP client’s SSO is based on passing the actual username and password/ntlm credentials to the server. Kerberous is NOT supported at all.

Microsoft Negotiate - selects between kerberos (preferable) or NTLM authentication and their versions.

Kerberos


Usefull artices:

How the Kerberos version 5 authentication protocol works
kerberos standard (ietf.org) ; KDC (Key Destribution Center) / TGS (Ticket Granting Server); MIT kerberos
Kerberos technical supplement for windows
Protocol Transition with Constrained Delegation - microsoft’s technical supplement; Web service security patterns - community technical preview - the whole technical supplement about authentication, etc.
Windows server 2003 Kerberos extensions (protocol transition, constrained delegation)
Overview of web publishing concepts

About single sign-on
About delegation of credentials
About Kerberos constrained delegation
Kerberos Delegation, SPNs and More…
Active Directory Security Risk #101: Kerberos Unconstrained Delegation
Trust? Years to earn, seconds to break
Session Tickets (kerberos protocol). Ticket contains its start and expiration dates, session key for server to authenticate client (session key is encrypted on server’s key, known only to server and KDC).

Session tickets are used only to authenticate new connections with servers (when a session ticket expires, ongoing operations are not interrupted).
Session ticket can be renewable or not (if not - after expiration user has to request new ticket). Renewable ticket can be renewed just before the renew-till time (user’s long-term key will not be required).
Session ticket’s mechanism requires time synchronization for Kerberous realm (by default GPO sets maximal time difference to ≈ 5 minutes).

KDC can generate for a user referral ticket (a TGT encrypted with interdomain key shared between KDCs). It enables user to request other domain’s KDC for keys and tickets in other domain’s services.
For this to operate domains must share interdomain keys (e.g. establish trust relationship).
In case there is multiple domains, user may get referral ticket to domain’s B KDC, that will give the referral ticket to domain C, …


Unconstrained\constrained Kerberos delegation (article with good explanation)
Information here may be inaccurate, sorry guyes and ladies.

SPN - Service Principal Name (e.g. service/host.domain, ldap/my_computer.lab)

The situation: User — authenticates at —> Service1 — works on behalf of user —> Service2
e.g. user got access to frontend server and frontend server got access to backend server on behalf of that user

Solution:

According to Kerberos traditional standard:

Proxy tickets - tickets got by client (hand by KDC) for frontend server to access backend server on user’s behalf. User request special proxy ticket to hand it to frontend server.
Problem: user must know about backend service and request appropriate ticket for frontend server. (If proxy tickets is allowed for the client PROXIABLE flag will be set in TGT)
forwardable tickets, unconstrained delegation
Microsoft’s Active Directory solutions:

unconstrained delegation, forwardable tickets (very insecure) - “trust this computer for delegation to any service (Kerberos only)” - Kerberos passes user’s “forward TGT” ticket with TGS. “Forward TGT” generated during user’s Service1 TGS ticket generation (it is called forwardable TGT)
security concern: therefore Service1 compromisation results in ability to steal any user’s TGT ticket (attack is restricted to users visited the service)

Realizations:

(Microsoft/MIT) forwardable TGT has FORWARDABLE flag, forwarded TGT or any its derivatives (e.g. TGS) has FORWARDED flag. Forwardable TGT passed to service to work on behalf of user.
(MIT) during AS request user appends Service1’s network address (not ip, SPN most likely), which will be inserted into TGT and will allow Service1 to use it.
constrained delegation - “trust this computer to specified services only”
Constrained delegation gives to the service/SPN the permission to impersonate any user before allowed and specified services/SPNs (every SPN has its own list).
Constrained delegation is restricted to services in a single domain.

(S4U2Self) protocol transition extension - using any authentication
Service1 implements its own authentication mechanism (anything not even Kerberos) and upon successful authentication of some User1 requests Kerberos User1’s Service1 TGS ticket. Protocol transition is used to initialize a WindowsIdentity object with valid user ID/account as it has just accessed Service1 using Kerberous protocol.
technically: Service1 requests Kerberos for user’s TGS ticket to Service1 (identity Service1 specifies any UserID/UPN in its request).
security concern - Service1 can impersonate any user before any allowed Service2.

(S4U2Proxy) native constrained delegation extension - Kerberos only
Service1 requests Kerberos for User1’s Service2 TGS ticket specifying User1’s Service1 ticket obtained either through KRB_TGS_REQ to Service1 or the protocol transition extension.
security concern - Service1 can impersonate any user visited Service1 before any allowed Service2.



Constrained delegation can be used without protocol transition extension.
Only services with SPN can be added to contrained delegation list
Only service with SPN can be granted delegation right (constrained/unconstrained)
Constrained delegation restriction: any user can be flagged as not permitted for delegation.
Delegation works only for Windows 2000 +. User’s and service’s accounts must be enabled for delegation. If service works under Local System account, the computer must be trusted for delegation)
security concern:
Kerberos requires SPN to generate a TGS ticket to service (using SPN kerberos destinguish services)
By default, all of the standard services use a HOST-based SPN, which is configured when the operating system is installed. Therefore if you have delegation access to service XXX/host.domain you also have delegation access to YYY/host.domain

For some users impersonation can be prohibited in active directory (and must be, e.g. Domain Administrators).

Trusted Computing Base (TCB) privileges - an account with TCB privileges can act as part of the operating system when it performs operations (e.g. impersonation operations).

Services can run under these local accounts: Local System, Local Service, Network Service or under AD (Active Directory) managed account.



Security drawbacks


high-level:
centralization

SSO - Single-Sign On - is the key reason attacks similar to pass-the-hash exists
DC and Kerberos servers are the key point of failure (or comprometation)
Kerberos relies on time synchronization (time difference below 5 minutes)
encryption problems

microsoft introduced encryption at smb 3.0, however it breaks compatibility with old systems
by default client does not sign its messages. Only domain controller sign its messages, however it is not required by client-side.
LDAP signs its messages
lots of proprietary protocols not secure, however required because of backward compatibility
backward compatibility - lots of old decisions can not be abandoned



realization key-points, weaknesses and vulnerabilities
Windows credentials storages

LSA (Local Security Authority) storage (includes lsass.exe process) - the process managing authentication. Its memory dump may contain a lot of sensitive information (e.g. usernames, passwords, ntlm hashes, tickets, …)
Protected Group protects lsass from storing user’s hash after user logged off (lsass process will be cleared).
ntds.dit + SYSTEM files - contains sensitive data for Active Directory catalogue (at Domain Controller) (Как устроен ntds.dit? (хабр))
SAM database + SYSTEM - Security Account Manager database - used to store local user accounts (contain data (e.g. NTLM hashes) encrypted using a 128-bit RC4 encryption key) (SAM is mounted into windows registry)
  ntdsxtract - example: python dsusers.py ntds.dit.export/datatable.4 ntds.dit.export/link_table.7 ./work --name USERNAME --syshive SYSTEM --supplcreds --passwordhashes --lmoutfile ./lm --ntoutfile ./nt --pwdformat john
LSA secrets - windows store here credentials for services, that configured to run under specified user and password for autologon feature
credentials can be dumped through post/windows/gather/lsa_secrets
Cached logon credentials - by default windows stores data for last 10 logged in users with their passwords(hashes)
reason: enables users to login again without connection to Domain Controller
cached creds can not be used for pass-the-hash, however can be bruteforced (can be dumped via module post/windows/gather/cachedump)
stored at HKEY_LOCAL_MACHINE\SECURITY\Cache in format: RC4(username | nt-hash) (mscash2) at lsass.exe process or NL$ registry section
Credential manager - a special vault, where can be stored any data by any application (e-mail, web authentication, form autocomplete, remote desktop passwords, …), passwords for saved network passwords, scheduled tasks, … Data is stored in ≈plain text
Attacks

pass-the-hash
Keys: NTLM is RC4-HMAC (without SALT), AES keys (they use 4096 iterations of PBKDF2 (salted))
ntlm hashes is everything attacker needs to pass challenge-response mechanism
overpass-the-hash - when you use pass-the-hash in order to get the kerberos ticket.
pass-the-ticket - in case we stole the TGT ticket (or at least session TGS ticket for service A) we can act on behalf of user
TGT ticket contains all account’s policy (disabled, expired, group membership, etc. in the format of PAC data structure) - it is ALL stored at client-side
Golden ticket - customly constructed ticket. Attacker who leaked krbtgt hash (from KDC) can generate TGT tickets for any user (even not existant) with any groups and metadata. It is a very stable method to get persistant in the domain.
Silver ticket - similar idea to golden ticket, except that service’s hash is used to generate ticket to access service. The main purpose is stealth.



Kerberos 5 has no guaranteed means to validate the account at KDC when presented with a TGT.
  If the TGT is older than 20 minutes, the KDC will validate the account before issuing TGS tickets.
    solution: check username and user’s RID during golden-ticket generation
  All TGS tickets issued during this 20 minutes will be valid until expiration date (usually 10 or 6 hours).



Kerberos & KRBTGT: Active Directory’s domain kerberos service account
KDC’s long-term key (krbtgt) does NOT change for years (because it is changed only during domain functional level upgrade or at recovery process).
Resetting the KRBTGT account password is only supported in a WS2008+ domain functional level. When the DFL is raised from 2003 to 2008 (or higher), the KRBTGT account password is changed automatically.
In any domain exists two accounts: krbtgt and secondary krbtgt_NNNNN, if you change krbtgt password, the TGT tickets will be still valid, because of krbtgt_NNNNN which will have old password. However if your domain has been compromised, krbtgt password must be changed twice in order to change passwords for both accounts. Choosing this path will likely require rebooting application servers (or at least re-starting application services to get them talking Kerberos correctly again).



pass-the-cache - some technic related to AD ticket’s cache


Weaknesses

Each machine in the domain (every server, every workstation) every 20-90 minutes requests Domain Controller for fresh GPO (group policy) to be applied (with localsystem NT SYSTEM rights).
That is why MITM, spoofing, smb relay/hijacking, etc. attacks DO VALUE.
SMB relay/hijacking - MITM between client and service. (one of implemented defenses is filtration of computer’s connection to itself)

SMB relay custom patches:

MS08-068 - prevents relaying back the challenge keys from where they were issued (however it does not stop cross protocol attack variation)
MS16-075 - fix cross-protocol back smb-relay variation
MS16-077 - prohibit WPAD resolution through netbios
NTLM problems (pass-the-hash and offline netNTLM bruteforce) is widespread. It concerns a lot of services: VPN, email, SMB share, AD, Microsoft accounts, …, everything with NTLM/domain authorization.
Windows will use NTLM for any file:// urls in corporate network (e.g. browsers Edge/IE, outlook, … will follow file:// links like a smb share) OR web-site may request NTLM authentication. Leak-NTLM-hash-via-HTML
  impact: user deanonymization (username, domain), relay attack, password brute force
  defense: forbid any smb traffic out of your intranet !
  http://witch.valdikss.org.ru - test your browser for leaking netNTLM hash via file://. (Caution probably it WILL leak your netNTLM (объяснение (RU)))

Windows name resolution order (What is LLMNR & WPAD and How to Abuse Them During Pentest ?):
DNS names always has trailing dot (e.g. www.google.com.), netbios names has NO trailing dot.
  impact: cross-domain policy bypass -> impact: session manipulation, phishing, etc.
  defense: prohibit broadcast netbios-ns resolve by means of group policy on every station

C:\Windows\System32\drivers\etc\hosts
DNS cache
DNS server
C:\Windows\System32\drivers\etc\lmhosts.sam
LLMNR broadcast query
NetBIOS-NS broadcast query
Windows prefer netbios-ns over DNS. Attacker may easily implement netbios name spoofing attack (netbios-ns is based on broadcast requests).


Enhancing windows security (general recommendations)


Awesome Windows Domain Hardening Awesome - awesomeness

Usefull articles (general security):

Securing Privileged Access
Privileged Access Management for Active Directory Domain Services
AD FS 2016 Operations - access control for Active Directory Federation Services
Best practices for securing Active Directory Federation Services
Usefull articles (concrete recommendations):

Protecting windows networks - dealing with credential theft
Advanced Threat Analytics suspicious activity guide
Pass the hash explained my Microsoft
How pass-the-hash works, Mitigating Pass-the-Hash and Other Credential Theft v1, Mitigating Pass-the-Hash and Other Credential Theft v2
Detecting Forged Kerberos Ticket (Golden Ticket & Silver Ticket) Use in Active Directory


Recommendations:

disable broadcast netbios-ns to protect from spoofing. As a result only DNS will remain as resolution service.
set to enabled GPO: Computer Configuration\Administrative Templates\Network\DNS Client\Turn Off Multicast Name Resolution

NTLM protection:

disable storing in memory (lsass.exe) cleartext passwords:

Install KB2871997 (Win7, WS2008R2) (Windows8.1+, WS2012+ has it by default) (2014)
reg add HKLM\SYSTEM\CurrentControlSet\Control\SecurityProviders\WDigest /v UseLogonCredential /t REG_DWORD /d 0 (reboot is required)
set timeout to remove credentials (e.g. ntlm) from lsass: reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa /v TokenLeakDetectDelaySecs /t REG_DWORD /d 30 (requires KB2871997) (KB3126593 (2016) enables this option automatically)
not recommended for user’s laptops, because it will complicate consequent user’s logon in case Domain Controller became unavailable

disable LM-hash generation: reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa /v NoLmHash /t REG_DWORD /d 1 ((Vista/MS2008+ disabled by default))
fully disable support for LM-hash authentication: reg add HKLM\System\CurrentControlSet\control\LSA /v LMCompatibilityLevel /t REG_DWORD /d 5
set at least NTLMv2 for GPO: Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options\Network Security: Restrict NTLM: NTLM authentication in this domain
set to disabled GPO: Computer Configuration\Windows Settings\Security Settings\Account Policies\Password Policy\Store password using reversible encryption for all users in the domain
Mimikatz protection:

configure Computer Configuration\Windows Settings\Security Settings\Local Policies\User Rights Assignment\Debug programs - options controls users with SeDebugPrivilege
SeDebugPrivilege allows to debug processes owned by other users (by default only administrators group privilege). security impact: user can debug other privileged process and run privileged commands on behalf of other user.
fully disabling SeDebugPrivilege can break some functionality, e.g. local administrators require this privilege to upgrade software like Microsoft SQL Server.
set to enabled GPO: Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options\Network access: Do not allow storage of passwords and credentials for network authentication
it prohibits storing passwords in Credential Manager and storing passwords for schedulled tasks
as a result users will have to enter passwords to access shares, etc. once again
set to enabled GPO: Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options\Network Security: Do not store LAN manager hash value on next password change
reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\LSA /v RunAsPPL /t REG_DWORD /d 1 - run several processes (e.g. lsass.exe) as protected process - Configuring Additional LSA Protection - this will rectrict process to load unsigned code (anyway, signed mimikatz with expired certificate can deal with it using driver trick, however it will make some noise in event logs)

reg add HKLM\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0 /v NtlmMinClientSec /t REG_DWORD /d 0x20000000 - require 128-bit encryption
reg add HKLM\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0 /v NtlmMinServerSec /t REG_DWORD /d 0x20000000 - require 128-bit encryption
domain protection:

all security patches in your infrastructure must be installed
prohibit usage of Domain Administrator’s accounts anywhere except Domain Controllers
DO NOT use your Domain Admin’s account anywhere except Domain Controller

secure ldap:
disable ldap null base search access
disable ldap null bind (anonymous)
force logoff for idle RDP sessions: configure GPO’s Computer Configuration\Policies\Administrative Templates\Windows Components\Remote Desktop Services\Remote Desktop Session Host\Session Time Limits
harden logon possibilities:

GPO: Computer Configuration\Windows Settings\Security Settings\Local Policies\User Rights Assignment\Deny access to this computer from the network
GPO: Computer Configuration\Windows Settings\Security Settings\Local Policies\User Rights Assignment\Deny logon as a batch job
GPO: Computer Configuration\Windows Settings\Security Settings\Local Policies\User Rights Assignment\Deny logon as a service
GPO: Computer Configuration\Windows Settings\Security Settings\Local Policies\User Rights Assignment\Deny logon locally
GPO: Computer Configuration\Windows Settings\Security Settings\Local Policies\User Rights Assignment\Deny logon through Remote Desktop Services
GPO: Computer Configuration\Windows Settings\Security Settings\Local Policies\User Rights Assignment\Enable computer and user accounts to be trusted for delegation
restrict RDP access (specifically deny it for not domain users)
add privileged users to Protected Users group (WS2012 R2 +) (How to configure protected accounts) (for Win7, WS2008R2 - KB2871997 required)

This will enhance security a lot:

no NTLM, WDigest, CredSSP, only Kerberos authentication
Kerberos will use only strong cryptography (no DES or RC4)
delegation is prohibited (“Account is sensitive and cannot be delegated” field)
long-term keys are disabled, after TGT expiration user will be prompted for password again
user’s credentials will not be cached
enable for privileged accounts option: Account is sensitive and can not be delegated
disable credentials caching for stationary PCs/servers (affected users will not be unable to login into computers while there is no connection to Domain Controller, it is critical for users with laptops):

reg add “HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon” /v CachedLogonsCount /t REG_SZ 0 (the default value is 10)
set to 0 GPO: Computer Configuration\Windows Settings\Local Policy\Security Options\Interactive Logon: Number of previous logons to cache (in case domain controller is not available)
disable showing account’s details on the sign-in screen:

GPO: Computer Configuration\Policies\Administrative Templates\System\Logon\Block user from showing account details on sign-in - prevents users from showing account details on the sign-in screen
GPO: Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options\Don’t display last signed-in - prevents the username of the last user to sign in from being shown
GPO: Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options\Don’t display username at sign-in - prevents the username from being shown at Windows sign-in and immediately after credentials are entered and before the desktop appears
block any netbios, 445, … traffic from corporate network to internet using firewall (in order to prevent netNTLM leak and offline bruteforce by an attacker)
defensive mechanisms:

Windows Defender Credential Guard (WS2016+, Win10+) - Protect derived domain credentials with Windows Defender Credential Guard
Restrict with AppLocker applications like procdump, Kaspersky’s debug diagnostic
Enable Advanced Audit Policy under Advanced Audit Policy Configuration\Object Access\Audit Kernel Object (L"S:(AU;SAFA;0x0010;;;WD)") - SACL process will log all processes attempting to access lsass.exe process
enable PowerShell logging with GPO: Computer Configuration\Policies\Administrative Templates\Windows Components\Windows PowerShell set to *
additional protections:

disable legacy and broadcast protocols and WPAD
enforce SMB signing within domain


Microsoft’s security mechanisms (there is more of them)


Usefull articles:

Security and Protection
Credentials:
Credential Guard
LAPS
Windows 10 Microsoft Passport
Multi-factor authentication (MFA): Windows Hello, Configure AD FS 2016 and Azure MFA
Runtime:
Protected process
UAC (User Access Control) (UAC brief summary). When an administrator logs on, the user is assigned two separate access tokens: a full administrator access token and a standard user access token.
The full administrator access token is not invoked until the user attempts to perform an administrative task. In other words, if you log on as a member of the local administrators group, you will run with your administrative privileges disabled until you attempt to run an application or task that has been marked to require administrative privileges.
When UAC is enabled, local administrator accounts run as standard user accounts until elevation is required. (Run as administrator - runs application with administrator access token)
AppLocker helps you control which apps and files users can run. These include executable files, scripts, Windows Installer files, dynamic-link libraries (DLLs), packaged apps, and packaged app installers. (Various antivirus vendors also offer their applocker realizations)
Device Guard
Encryption:
Bitlocker
More:
Windows Information Protection (WIP), formerly known as Enterprise Data Protection (EDP)
CIG (Code Integrity Guard) - (good to be applied for guarding drivers)
CIGslip - technic to inject unsigned code into CIG-protected applications. Rough description: attacker can inject code into non-CIG process and afterwards infect CIG-protected process from infected non-CIG process.
Trusted Platform Module
Monitoring:
Microsoft’s Advanced Threat Analytics (MATA)
It can detect some types of attacks, but not all, and only detect (not prevent).
Azure management - monitoring, Operation management suite (???)
Infrastructure:
Windows Server Update Services (WSUS)
System Center Configuration Manager (SCCM)


Some (mostly Microsoft’s) “concepts”
SOAP (Simple Object Access Protocol). SOAP allows processes on disparate operating systems to communicate using XML
WS-Management (Web-service management protocol) - inherently this is the expansion of SOAP protocol over HTTP(S)
WMI (Windows management instrumentation) - Microsoft’s implementation of Web-Based Enterprise Management (WBEM). WMI uses the Common Information Model (CIM) industry standard to represent systems, applications, networks, devices, and other managed components.


COM (Component Object Model) - a Microsoft’s framework for developing and supporting program component objects (aimed to provide similar capabilities as CORBA)
CORBA (Common Object Request Broker Architecture) - an architecture and specification for creating, distributing, and managing distributed program objects in a network. It allows programs at different locations and developed by different vendors to communicate in a network through an “interface broker.”
CORBA was developed by a consortium of vendors through the Object Management Group (OMG).
DCOM (Distributed COM) (Distributed Component Object Model) - a proprietary Microsoft technology for communication between software components on networked computers (dcomcnfg.exe)
DCOM is a set of Microsoft concepts and program interfaces in which client program objects can request services from server program objects on other computers in a network

RPC (Remote Procedure Calls) - a protocol that one program can use to request a service from a program located in another computer on a network without having to understand the network’s details.
RPC under the hood: smb connect to DC -> request IPC$ share -> bind to SAMR named pipe -> Makes multiple SAMR queries (EnumDomains, LookupDomains, LookupNames, QueryUserInfo, GetGroupsForUser, …)
Some MS-RPC require local admin priveleges (e.g. svcctl - manipulate services, atsvc - manipulate tasks, DCOM), others don’t (e.g. samr, lsarpc)
  (samr - Security Account Manager Remote) - query local SAM db (users, groups, …)
  (lsarpc - query Local Security Authority for SIDs, policies, …)
Programmically:

WMI works over DCOM, COM/DCOM works over RPC. DCOM requires additional connection (over dynamically allocated port).

RPC: service RpcSs, listens 135/tcp port, (uses $IPC share)
DCOM: service dcomlaunch works over RPC, uses additional dynamically allocated port (default 1024-65535 scope can be changed in dcomcnfg.exe -> Computers -> My computer -> Properties -> Protocol set -> DCOM protocols -> Properties -> Add range -> reboot)
WMI: service Winmgmt + application %systemroot%\system32\wbem\unsecapp.exe
MS-SAMR/SAM (Security Account Manager Remote Protocol), MS-LSAD (Local Security Authority (Domain Policy) Remote Protocol)
both protocols leverage RPC and use SMB (Server Message Block)

NetBios - kernel driver netbt.sys



MSF (Microsoft Solutions Framework) - Microsoft’s own best practices software development guidance
MSF had three key elements: it used a lifecycle approach, it embedded risk management into every phase, and it used a team model to assign responsibility
MOF (Microsoft Operations Framework) - Microsoft’s specific best practices guidance based on its own internal best practices, the best practices of its consulting arm, of its customers, and combined with ITIL guidance. (mofcomp.exe - MOF compiler)
MOF has the same three key elements at its core, as MSF


IPMI (Intelligent Platform Management Interface) - a set of computer interface specifications for an autonomous computer subsystem that provides management and monitoring capabilities independently of the host system’s CPU, firmware (BIOS or UEFI) and operating system
IPMI sub-system consists of main controller (BMC - Baseboard management controller) - and other management controllers among different system submodules
RMCP (Remote Management Control Protocol) - protocol for managing systems with IPMI
```
