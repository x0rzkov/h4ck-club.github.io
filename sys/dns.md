# Domain Name System
```
WTF IS DNS?
The Domain Name System{s}(DNS) is essentially a phonebook of the Internet. To access information and websites online, this is achieved via the use of domain names, like zsec.uk. Web browsers(Browsers) interact with Internet Protocol (IP) addresses. The service translates human readable domain names into computer readable IP addresses to enable browsers to load resources on the Internet.

Every device connected to the Internet will have a unique IP address which other machines use to find the device. DNS servers eliminate the need for humans to memorize IP addresses such as 10.10.200.1 (in IPv4), or more complex newer alphanumeric IP addresses such as FE80::0202:B3FF:FE1E:8329 (in IPv6).
DNS as described above basically translates domain names into ip addresses, a DNS lookup(i.e how you browse to a site), can be split up into a series of steps;

1) A user types ‘zsec.uk’ into their web browser and the request travels into the Internet and is received by a DNS recursive resolver.
2) The resolver then queries a DNS root nameserver(explained below) (.).
3) The root server then takes the request and responds to the resolver with the address of a Top Level Domain (TLD) DNS server (such as .com, .uk or etc), which stores the information for the domains belonging to that TLD(i.e any .uk domain for the .uk TLD DNS Server). When searching for zsec.uk, our request is pointed toward the .uk TLD.
4) The resolver then makes a request to the .uk TLD server. Which then responds with the IP address of the domain's name server, zsec.uk.
5) Lastly, the recursive resolver sends a query to the domain’s nameserver. The IP address for blog.zsec.uk is then returned to the resolver from the nameserver.
6) The DNS resolver then responds to the web browser with the IP address of the domain requested initially and then the browser makes a request to the IP address.
7) Finally, the server at that IP returns the webpage to be rendered in the browser and the browser renders it.

There are four separate types of server involved in loading a web page, a DNS recursor and three different name servers:

1) DNS recursor - A DNS recursor is designed to receive queries and lookups from applications such as web browsers. Normally the recursor is then responsible for making additional requests in order to satisfy the client’s DNS query. For example if you want to browse to blog.zsec.uk, a recursor will go away and make the other requests required to gain information to render and load the site. The other requests are made to the root, TLD and authorative name servers which are described below.
2) Root nameserver - The root server is the first step in translating (resolving) human readable host names into IP addresses. It is similar to an index in a library that points to different racks of books - typically it serves as a reference to other more specific locations of information.
3) Top Level Domain(TLD) nameserver - The top level domain server (TLD) can be thought of as a specific aisle of books in a library. This nameserver is the next step in the search for a specific IP address, and it hosts the last area of a hostname (In zsec.uk, the TLD server is “uk”).
4) Authoritative nameserver - This final nameserver can be thought of as a dictionary on a rack of books, in which a specific name can be translated into its definition. The authoritative nameserver is the last stop in the nameserver query. If the authoritative name server has access to the requested record, it will return the IP address for the requested hostname back to the DNS Recursor (the librarian) that made the initial request.

DIFFERENT RECORD TYPES
Now that we're all on the same page as to how DNS works and what it is, next up is the different types of record. Basically when you do a DNS lookup, normally your browser will be looking for an IP address to render a site however DNS is much more feature rich. It has other types of records that can be returned based on the type of lookup.

There are a few different types of DNS record, a quick overview of each is explained in the list below.
	A: An A record specifies IP address (IPv4) for given host. A records are used for conversion of domain names to corresponding IP addresses.
	AAAA: Much like an A record, a AAAA (also quad-A record) specifies IPv6 address for given host. So it works the same way as the A record and the difference is the type of IP address.
	CNAME: A CNAME record is like a redirector in that it specifies a domain name that has to be queried in order to resolve the original DNS query. Therefore CNAME records are used for creating aliases of domain names.
	TXT: A TXT record stores a variety of information but in the name it is a text record, usually referenced for validation information or other auxiliary information about a domain. TXT records are used for protocols such as SPF, DKIM and DMARC to secure mail transfer, these are explained below.
	MX: A MX record also known as mail exchanger record specifies the mail server responsible for accepting email messages on behalf of a domain name.Typically a domain will have a primary MX record and in some cases, a secondary or multiple secondary MX records for load balancing and redundancy.
	PTR: A PTR record also known as a pointer, enables reverse DNS lookups, which are instead of lookup up a domain and getting an A record, you can lookup an IP address and get a domain. It ties an IP up with a domain name. For this reason, a PTR record is often referred to as a Reverse DNS Record. The main purpose of a PTR record is mostly administrative as it confirms that an IP is in fact used with a particular domain.
	SOA: SOA stands for start of authority, this record is typically used for administrative functionality as it holds information surrounding the DNS zone information. It stores the following info;
		Name of the server that supplied the data for the zone;
		Administrator of the zone;
		Current version of the data file;
		Number of seconds a secondary name server should wait before checking for updates;
		Number of seconds a secondary name server should wait before retrying a failed zone transfer;
		The maximum number of seconds that a secondary name server can use data before it must either be refreshed or expire;
		A default number of seconds for the time-to-live file on resource records.
	HINFO: The HINFO record is used less often now however it holds information about the host CPU type and operating system. It was intended to allow protocols to optimize processing when communicating with similar peers. Currently it is used by CloudFlare when a lookup of type ANY is issued.
	There are many more DNS records but the above are the most commonly used or referred to.

###### FACILITATING ATTACKS WITH DNS
Now that you know how this all works, next I'll touch on some of the attacks and info that an attacker can gain from DNS enumeration.

###### DNS ENUMERATION
There are a few techniques that can be leveraged to use DNS as a reconnaicence tool, these are detailed below. While these are not exploits, they leverage functionality for malicious purposes.

###### ZONE TRANSFERS
A zone transfer is a method that an administrator can leverage to replicate DNS databases across a group of DNS servers. The actual method for a zone transfer is perfectly fine between DNS servers as it is intended to share zones information, they can leak a lot of information that would otherwise not be available to an attacker.
While DNS records are not sensitive individually, if an attacker manages to obtain a copy of the entire DNS zone for a domain they can proceed to obtain a complete listing of all the hosts associated on that particular zone and thus leverage this to find interesting looking sub domains.

###### SUBDOMAINS
Subdomain enumeration outside of a zone transfer can be achieved by querying a DNS resolver with a list of names, if the name is valid the resolver will show an associated DNS record. Subdomain enumeration is an essential part of conducting recon. Attackers typically map out the digital footprint of the target in order to find weak spots such as interesting domain names, or records pointing to internal hostnames which could be leveraged for accessing an internal network.

###### ATTACKING DIFFERENT RECORDS
There are a multitude of different attacks that can be carried out against speciifc DNS records, ranging from subdomain takeovers through to commmand and control over DNS. Threat actors and attackers are always looking for different new methods for attacks. A few examples of attack types include:

	Subdomain Takeovers: Takeovers work when a company has a CNAME record setup, whereby a domain; example.zsec.uk is pointing to a content delivery network or even non existent area and an attacker claims the domain or area to deliver their own content thus taking over the subdomain. This type of attack is often found to be used by attackers hoping to phish from intenral domains, it is also found alot on bug bounty schemes and has a varying pay table.
	DNS Command and Control (C2): In the most locked down environments often DNS traffic should be allowed to resolve internal or external domains. As an attacker we can leverage this as a communication channel between a target host and the command and control server. Commands and data are included inside DNS queries and responses which aid in hiding how an attack is being conducted.
	Exfiltration: Similar to the C2 explained above, information can be exfiltrated over DNS by leveraging the TXT record, blobs of (usually base64) encoded data can be set in txt records that when lookedup by an attacker can extract info and data from inside an organisation's network.
	There are many other attacks and techniques that leverage DNS and new ones are being discovered all the time.
```
