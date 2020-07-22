###### OSCP
```
ip discovery----------------
fping -ga 192.168.0.1/26 2>&1 < /dev/null | grep -v Unreachable
seq 254 | xargs -I N -P 1000 ping -q -c 1 192.168.0.N | grep -B 1 '1 received' | grep ping | cut -d " " -f 2
for i in `seq 1 255`; do ping -c 1 192.168.0.$i | tr \\n ' ' | awk '/1 received/ {print $2}'; done
fping -c 1 -f ip_list.txt 2>&1 | grep '84 bytes' | cut -d " " -f 1
```

###### awesome
| name                                                                                                                                                | technologies                                | notes |
|:----------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------|:------|
| [.NET Goat ](https://github.com/jerryhoff/WebGoat.NET/)                                                                                             | C#-                                         | -     |
| [21LTR](http://21ltr.com/scenes/)                                                                                                                   | -                                           | -     |
| [Acunetix Acuart](http://testphp.vulnweb.com/)                                                                                                      | Apache, PHP, MySQL                          | -     |
| [Acunetix Acublog](http://testaspnet.vulnweb.com/)                                                                                                  | IIS, ASP.NET, Microsoft SQL Server          | -     |
| [Acunetix Acuforum](http://testasp.vulnweb.com/)                                                                                                    | IIS, ASP, Microsoft SQL Server              | -     |
| [Acunetix SecurityTweets](http://testhtml5.vulnweb.com/)                                                                                            | nginx, Python, Flask, CouchDB               | -     |
| [BadStore](http://www.badstore.net/)                                                                                                                | -                                           | -     |
| [Bitnami Application Catalog](https://bitnami.com/stacks)                                                                                           | OS                                          | -     |
| [BodgeIt Store](http://code.google.com/p/bodgeit/)                                                                                                  | -                                           | -     |
| [Bricks ](http://sechow.com/bricks/index.html)                                                                                                      | PHP-                                        | -     |
| [Butterfly Security Project](http://thebutterflytmp.sourceforge.net/)                                                                               | -                                           | -     |
| [Bwapp](https://sourceforge.net/projects/bwapp/files/bee-box/)                                                                                      | web                                         | -     |
| [CTFd](https://github.com/isislab/CTFd)                                                                                                             | -                                           | -     |
| [Cenzic crackmebank](http://crackme.cenzic.com/)                                                                                                    | CentOS, Apache, PHP                         | -     |
| [Commix](https://github.com/stasinopoulos/commix-testbed)                                                                                           | -                                           | -     |
| [CryptOMG](https://github.com/SpiderLabs/CryptOMG)                                       | Web                                         | -     |
| [Cyclone Transfers](https://github.com/fridaygoldsmith/bwa_cyclone_transfers)                              | Ruby on Rails-                              | -     |
| [DE-ICE, hackerdemia](http://hackingdojo.com/downloads/iso/De-ICE_S1.110.iso)                            | -                                           | -     |
| [DE-ICE, hackerdemia](http://hackingdojo.com/downloads/iso/De-ICE_S1.120.iso)                            | -                                           | -     |
| [DE-ICE, hackerdemia](http://hackingdojo.com/downloads/iso/De-ICE_S1.123.iso)                            | -                                           | -     |
| [DE-ICE, hackerdemia](http://hackingdojo.com/downloads/iso/De-ICE_S2.100.iso)                            | -                                           | -     |
| [Damn Vulnerable](http://www.damnvulnerablelinux.org)                                | -                                           | -     |
| [Damn Vulnerable Linux](http://sourceforge.net/projects/virtualhacking/files/os/dvl/)                          | -                                           | -     |
| [Damn Vulnerable Linux – Virtual Hacking Lab](https://sourceforge.net/projects/virtualhacking/files/os/dvl/)    | OS                                          | -     |
| [Damn Vulnerable Node Application (DVNA)](https://github.com/quantumfoam/DVNA/)        | -                                           | -     |
| [Damn Vulnerable NodeJS Application (DVNA)](https://github.com/appsecco/dvna)      | Web                                         | -     |
| [Damn Vulnerable Router Firmware Project (DVRF)](https://github.com/praetorian-inc/DVRF) | Others                                      | -     |
| [Damn Vulnerable Thick Client App - DVTA](https://github.com/secvulture/dvta)        | C# .NET-                                    | -     |
| [Damn Vulnerable Web Application - DVWA](http://www.dvwa.co.uk/)         | PHP-                                        | -     |
| [Damn Vulnerable Web Services (DVWS)](https://github.com/snoopysecurity/dvws)            | Web                                         | -     |
| [Damn Vulnerable Web Sockets (DVWS)](https://github.com/interference-security/DVWS/)             | Web                                         | -     |
| [De-ICE HackerPedia PenTest LiveCDs](http://de-ice.net/hackerpedia/index.php/De-ICE.net_PenTest_Disks)             | -                                           | -     |
| [Default VMWare vSphere](http://www.vmware.com/products/vsphere/)                         | -                                           | -     |
| [Default Windows Clients](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise)                        | -                                           | -     |
| [Default Windows Server](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-technical-preview)                         | -                                           | -     |
| [Docker](https://www.docker.com/)                                         | -                                           | -     |
| [Drunk Admin Web Hacking Challenge](https://bechtsoudis.com/work-stuff/challenges/drunk-admin-web-hacking-challenge/                 )              | -                                           | -     |
| [Elastic Server](http://elasticserver.com)                                 | -                                           | -     |
| [Exploit KB Vulnerable Web App](http://exploit.co.il/projects/vuln-web-app/                                                      )                  | -                                           | -     |
| [Firing Range](https://public-firing-range.appspot.com/                                                         )                                   | Google App Engine                           | -     |
| [Foundstone Hackme Bank](http://www.mcafee.com/us/downloads/free-tools/hacme-bank.aspx                                    )                         | -                                           | -     |
| [Foundstone Hackme Books](http://www.mcafee.com/us/downloads/free-tools/hacmebooks.aspx                                    )                        | -                                           | -     |
| [Foundstone Hackme Casino](http://www.mcafee.com/us/downloads/free-tools/hacme-casino.aspx                                  )                       | -                                           | -     |
| [Foundstone Hackme Shipping](http://www.mcafee.com/us/downloads/free-tools/hacmeshipping.aspx                                 )                     | -                                           | -     |
| [Foundstone Hackme Travel](http://www.mcafee.com/us/downloads/free-tools/hacmetravel.aspx                                   )                       | -                                           | -     |
| [GameOver](http://sourceforge.net/projects/null-gameover/                                                   )                                       | -                                           | -     |
| [Google Gruyere](http://google-gruyere.appspot.com/start                                                          )                                 | Python, Google App Engine                   | -     |
| [HTS](https://www.hackthissite.org/                                                                    )                                            | Web                                         | -     |
| [HackLAB](http://www.rebootuser.com/?page_id=1041                                                          )                                        | OS                                          | -     |
| [HackYourselfFirst](http://hack-yourself-first.com/                                                                  )                              | IIS, ASP.NET                                | -     |
| [Hackademic Challenges](http://www.hackademic.eu                                                                         )                          | -                                           | -     |
| [Hackademic Challenges Project](https://www.owasp.org/index.php/OWASP_Hackademic_Challenges_Project                              )                  | PHP-                                        | -     |
| [Hackazon](https://github.com/rapid7/hackazon                                                               )                                       | REST and new-school                         | -     |
| [Hacking-Lab](http://www.hacking-lab.com/hl_livecd                                                             )                                    | -                                           | -     |
| [Hackxor](https://hackxor.net/                                                                             )                                        | Web                                         | -     |
| [Hackxor](https://sourceforge.net/projects/hackxor/                                                        )                                        | Web                                         | -     |
| [Hacme Bank](http://www.mcafee.com/us/downloads/free-tools/hacme-bank.aspx                                    )                                     | .NET-                                       | -     |
| [Hacme Bank Android](http://www.mcafee.com/us/downloads/free-tools/hacme-bank-android.aspx                            )                             | mobile                                      | -     |
| [Hacme Books](http://www.mcafee.com/us/downloads/free-tools/hacmebooks.aspx                                    )                                    | Java-                                       | -     |
| [Hacme Casino](http://www.mcafee.com/us/downloads/free-tools/hacme-casino.aspx                                  )                                   | Ruby on Rails-                              | -     |
| [Hacme Shipping](http://www.mcafee.com/us/downloads/free-tools/hacmeshipping.aspx                                 )                                 | ColdFusion-                                 | -     |
| [Hacme Travel](http://www.mcafee.com/us/downloads/free-tools/hacmetravel.aspx                                   )                                   | C++-                                        | -     |
| [Holynix](http://sourceforge.net/projects/holynix/files/                                                   )                                        | -                                           | -     |
| [IBM Altoro Mutual](http://demo.testfire.net/                                                                        )                              | IIS, ASP.NET                                | -     |
| [HackSys Extreme Vulnerable Driver](http://www.payatu.com/hacksys-extreme-vulnerable-driver/                                         )              | misc                                        | -     |
| [Fosscomm](https://github.com/nikosdano/fosscomm                                                            )                                       | misc                                        | -     |
| [IBM AltoroJ Mutual](http://www.altoromutual.com:8080/                                                                )                             | Tomcat, Java 3.1                            | -     |
| [IBM Hard Altoro Mutual](http://hard.altoromutual.com/                                                                    )                         | Tomcat, Java 3.1, MegaScript                | -     |
| [Juice Shop](https://www.owasp.org/index.php/OWASP_Juice_Shop_Project                                         )                                     | Node/JS-                                    | -     |
| [Katana](http://www.hackfromacave.com/katana.html                                                         )                                         | -                                           | -     |
| [Kioptrix](http://www.kioptrix.com/blog/                                                                    )                                       | -                                           | -     |
| [LAMP Security](https://sourceforge.net/projects/lampsecurity/                                                   )                                  | Web                                         | -     |
| [MCIR (Magical Code Injection Rainbow)](https://github.com/SpiderLabs/MCIR                                                               )          | -                                           | -     |
| [Mellivora](https://github.com/Nakiami/mellivora                                                             )                                      | -                                           | -     |
| [Metasploitable](https://sourceforge.net/projects/virtualhacking/files/os/metasploitable/                         )                                 | OS                                          | -     |
| [Metasploitable2](https://sourceforge.net/projects/metasploitable/                                                 )                                | OS                                          | -     |
| [Moth](http://www.bonsai-sec.com/en/research/moth.php                                                   )                                           | -                                           | -     |
| [Mutillidae](http://www.irongeek.com/i.php?page=mutillidae/mutillidae-deliberately-vulnerable-php-owasp-top-10)                                     | PHP-                                        | -     |
| [NETinVM](http://informatica.uv.es/~carlos/docencia/netinvm/                                               )                                        | -                                           | -     |
| [NOWASP / Mutillidae 2](http://sourceforge.net/projects/mutillidae                                                       )                          | -                                           | -     |
| [NightShade](https://github.com/UnrealAkama/NightShade                                                        )                                     | -                                           | -     |
| [NodeGoat](https://www.owasp.org/index.php/OWASP_Node_js_Goat_Project                                       )                                       | Node.js-                                    | -     |
| [OCCP](https://opencyberchallenge.net/                                                                  )                                           | -                                           | -     |
| [OSBoxes](https://www.osboxes.org/                                                                         )                                        | OS                                          | -     |
| [OWASP  (VWAD)](https://github.com/OWASP/OWASP-VWAD                                                              )                                  | Web                                         | -     |
| [OWASP BWA](http://code.google.com/p/owaspbwa/                                                               )                                      | -                                           | -     |
| [OWASP Bricks](https://sourceforge.net/projects/owaspbricks/                                                    )                                   | Web                                         | -     |
| [OWASP Broken Web Applications (BWA) Project](https://code.google.com/archive/p/owaspbwa/                                                      )    | Web                                         | -     |
| [OWASP Hackademic](http://hackademic1.teilar.gr/                                                                    )                               | -                                           | -     |
| [OWASP Hackademic Challenges](https://code.google.com/archive/p/owasp-hackademic-challenges/                                   )                    | Web                                         | -     |
| [OWASP Juice Shop](https://juice-shop.herokuapp.com/                                                                )                               | Node.js                                     | -     |
| [OWASP Mutillidae II](https://sourceforge.net/projects/mutillidae/                                                     )                            | Web                                         | -     |
| [OWASP NodeGoat](http://nodegoat.herokuapp.com/                                                                   )                                 | Node.js                                     | -     |
| [OWASP Security Shepherd](https://github.com/OWASP/SecurityShepherd                                                        )                        | Web                                         | -     |
| [OWASP SiteGenerator](https://www.owasp.org/index.php/OWASP_SiteGenerator                                              )                            | Web                                         | -     |
| [OWASP Vicnum](http://vicnum.ciphertechs.com/                                                                   )                                   | Apache, PHP, Perl                           | -     |
| [OWASP WebGoat .Net](https://github.com/jerryhoff/WebGoat.NET/                                                        )                             | Web                                         | -     |
| [Open Cyber Challenge Platform (OCCP)](https://opencyberchallenge.net/                                                                  )           | OS                                          | -     |
| [PHDays iBank CTF](http://blog.phdays.com/2012/05/once-again-about-remote-banking.html                              )                               | -                                           | -     |
| [PenTest Laboratory](http://pentestlab.org/lab-in-a-box/                                                              )                             | -                                           | -     |
| [Pentester Lab](https://www.pentesterlab.com/exercises                                                           )                                  | -                                           | -     |
| [PentesterLab](https://pentesterlab.com/                                                                        )                                   | -                                           | -     |
| [Peruggia](http://peruggia.sourceforge.net/                                                                 )                                       | PHP-                                        | -     |
| [Project GameOver](http://null.co.in/2012/06/14/gameover-web-pentest-learning-platform                              )                               | -                                           | -     |
| [PuzzleMall](http://code.google.com/p/puzzlemall/                                                             )                                     | -                                           | -     |
| [PwnOS](http://www.pwnos.com/                                                                            )                                          | OS                                          | -     |
| [RPISEC/MBE](https://github.com/RPISEC/MBE                                                                    )                                     | binary                                      | -     |
| [Rails Goat](https://www.owasp.org/index.php/OWASP_Rails_Goat_Project                                         )                                     | Ruby on Rails-                              | -     |
| [Rails Vulnerable](https://github.com/jobertabma/vulnerable                                                         )                               | Web                                         | -     |
| [Rapid7 Hackazon](http://hackazon.webscantest.com/                                                                 )                                | Apache, PHP, Ajax, JSONm XML, Gwt, AMF      | -     |
| [Rapid7 WebScanTest](http://webscantest.com/                                                                          )                             | Apache, PHP                                 | -     |
| [RebootUser Vulnix](http://www.rebootuser.com/?page_id=1041                                                          )                              | -                                           | -     |
| [SQL Injection Labs](https://github.com/himadriganguly/sqlilabs                                                       )                             | Web                                         | -     |
| [SQL injection test environment](https://github.com/sqlmapproject/testenv                                                         )                 | PHP-                   SQLmap               | -     |
| [SQLI Labs](https://github.com/Audi-1/sqli-labs                                                              )                                      | Web                                         | -     |
| [SQLol](https://github.com/SpiderLabs/SQLol                                                              )                                          | PHP-                                        | -     |
| [SecGame # 1 Sauron](http://sg6-labs.blogspot.co.uk/2007/12/secgame-1-sauron.html                                     )                             | -                                           | -     |
| [SecuriBench](http://suif.stanford.edu/~livshits/securibench/                                                  )                                    | -                                           | -     |
| [SecuriBench Micro](http://suif.stanford.edu/%7Elivshits/work/securibench-micro/                                     )                              | Java-                                       | -     |
| [SecuriBench:](http://suif.stanford.edu/~livshits/securibench                                                   )                                   | -                                           | -     |
| [Security Shepherd-](https://www.owasp.org/index.php/OWASP_Security_Shepherd                                          )                             | Java-                                       | -     |
| [SentinelTestbed](https://github.com/dobin/SentinelTestbed                                                         )                                | -                                           | -     |
| [SmartDataCenter](https://github.com/joyent/sdc                                                                    )                                | -                                           | -     |
| [SmartOS](https://smartos.org/                                                                             )                                        | -                                           | -     |
| [SocketToMe](http://digi.ninja/projects/sockettome.php                                                        )                                     | -                                           | -     |
| [SocketToMe](https://digi.ninja/projects/sockettome.php                                                       )                                     | Web                                         | -     |
| [Stanford SecuriBench](https://suif.stanford.edu/~livshits/securibench/                                                 )                           | Web                                         | -     |
| [Testsparker ASP.NET](http://aspnet.testsparker.com/                                                                   )                            | Windows, IIS, ASP.NET, Microsoft SQL Server | -     |
| [Testsparker PHP](http://php.testsparker.com/                                                                      )                                | Windows, Apache, PHP, MySQL                 | -     |
| [Testsparker SPA  (Angular)](http://angular.testsparker.com/                                                                  )                     | Ubuntu, Apache, PHP, Angular 5, MySQL       | -     |
| [The BodgeIt Store](https://github.com/psiinon/bodgeit                                                               )                              | Web                                         | -     |
| [The ButterFly – Security Project](https://sourceforge.net/projects/thebutterflytmp/                                                )               | Web                                         | -     |
| [The Hacker Games](https://www.scriptjunkie.us/2012/04/the-hacker-games/                                            )                               | OS                                          | -     |
| [TurnKey Linux](http://www.turnkeylinux.org/                                                                     )                                  | -                                           | -     |
| [TurnKey Linux:](http://www.turnkeylinux.org                                                                      )                                 | -                                           | -     |
| [UltimateLAMP](http://www.amanhardikar.com/mindmaps/practice-links.html                                         )                                   | -                                           | -     |
| [UltimateLAMP:](http://www.amanhardikar.com/mindmaps/practice-links.html                                         )                                  | -                                           | -     |
| [Vagrant](https://www.vagrantup.com/                                                                       )                                        | -                                           | -     |
| [Virtual Hacking Lab:](http://sourceforge.net/projects/virtualhacking/files                                             )                           | -                                           | -     |
| [VirtualBox Virtual Appliances](https://virtualboximages.com/                                                                    )                  | -                                           | -     |
| [VirtualBoxes](http://virtualboxes.org/images/                                                                  )                                   | -                                           | -     |
| [VulnApp](http://www.nth-dimension.org.uk/blog.php?id=88                                                   )                                        | -                                           | -     |
| [VulnApp](http://www.nth-dimension.org.uk/blog.php?id=88                                                   )                                        | .NET-                                       | -     |
| [VulnApp](https://www.nth-dimension.org.uk/blog.php?id=88                                                  )                                        | Web                                         | -     |
| [VulnHub](https://www.vulnhub.com/                                                                         )                                        | OS                                          | -     |
| [Vulnerable App & Attacker App](https://github.com/clarkio/vulnerable-app                                                        )                  | Web                                         | -     |
| [Vulnerable Java based Web Application](https://github.com/CSPF-Founder/JavaVulnerableLab                                                )          | Web                                         | -     |
| [Vulnerable Node](https://github.com/cr0hn/vulnerable-node                                                         )                                | Web                                         | -     |
| [Vulnerable Web App](http://exploit.co.il/hacking/exploit-kb-vulnerable-web-app/                                      )                             | -                                           | -     |
| [Vulnerable Web Application Project](https://www.owasp.org/index.php/OWASP_Vulnerable_Web_Application                                 )             | PHP-                                        | -     |
| [Vulnserver](http://www.thegreycorner.com/2010/12/introducing-vulnserver.html                                 )                                     | -                                           | -     |
| [Vulnserver](http://www.thegreycorner.com/2010/12/introducing-vulnserver.html                                 )                                     | misc                                        | -     |
| [WAED](http://www.waed.info                                                                             )                                           | -                                           | -     |
| [WIVET Web Input Vector Extractor Teaser](https://code.google.com/p/wivet/                                                                 )        | -                                           | -     |
| [WackoPicko](https://github.com/adamdoupe/WackoPicko                                                          )                                     | PHP-                                        | -     |
| [Web App Vuln Scanner Eval Project](https://github.com/sectooladdict/wavsep                                                          )              | Java-                                       | -     |
| [Web Security Dojo](https://sourceforge.net/projects/websecuritydojo/                                                )                              | Web                                         | -     |
| [WebGoat](https://github.com/WebGoat/WebGoat                                                               )                                        | Web                                         | -     |
| [WebGoat](https://www.owasp.org/index.php/Category:OWASP_WebGoat_Project                                   )                                        | Java-                                       | -     |
| [WebGoat.NET](https://github.com/jerryhoff/WebGoat.NET/                                                        )                                    | -                                           | -     |
| [WebGoatPHP](https://www.owasp.org/index.php/WebGoatPHP                                                       )                                     | PHP-                                        | -     |
| [WebSecurity Dojo](http://www.mavensecurity.com/web_security_dojo/                                                  )                               | -                                           | -     |
| [XAMPP](https://www.apachefriends.org/index.html                                                         )                                          | -                                           | -     |
| [XMLmao](https://github.com/SpiderLabs/XMLmao                                                             )                                         | -                                           | -     |
| [XVWA](https://github.com/s4n7h0/xvwa                                                                   )                                           | -                                           | -     |
| [Zap WAVE](http://code.google.com/p/zaproxy/downloads/detail?name=zap-wave-0.1.zip                          )                                       | -                                           | -     |
| [bWAPP](http://www.mmeit.be/bwapp/                                                                       )                                          | -                                           | -     |
| [bee-box](http://sourceforge.net/projects/bwapp/files/bee-box/                                             )                                        | -                                           | -     |
| [binjitsu](https://github.com/binjitsu/binjitsu                                                             )                                       | -                                           | -     |
| [btslab](https://github.com/CSPF-Founder/btslab/                                                          )                                         | PHP-  flash-based xss SSRF and SSI          | -     |
| [exploit-exercises](http://exploit-exercises.com/download                                                            )                              | -                                           | -     |
| [exploit.co.il Vulnerable Web](https://sourceforge.net/projects/exploitcoilvuln/                                                )                   | Web                                         | -     |
| [google-gruyere](https://google-gruyere.appspot.com/                                                              )                                 | Web                                         | -     |
| [hackerdemia](http://hackingdojo.com/downloads/iso/De-ICE_S1.123.iso                                           )                                    | -                                           | -     |
| [hackxor](http://hackxor.sourceforge.net/cgi-bin/index.pl                                                  )                                        | -                                           | -     |
| [hdojo](http://hackingdojo.com/downloads/iso/De-ICE_S1.110.iso                                           )                                          | -                                           | -     |
| [hdojo](http://hackingdojo.com/downloads/iso/De-ICE_S1.120.iso                                           )                                          | -                                           | -     |
| [hdojo](http://hackingdojo.com/downloads/iso/De-ICE_S2.100.iso                                           )                                          | -                                           | -     |
| [heorot: DE-ICE, hackerdemia](http://hackingdojo.com/downloads/iso/De-ICE_S1.100.iso                                           )                    | -                                           | -     |
| [neutronstar](http://neutronstar.org/goatselinux.html                                                          )                                    | -                                           | -     |
| [pWnOS](http://www.pwnos.com/                                                                            )                                          | -                                           | -     |
| [scriptjunkie.us](http://www.scriptjunkie.us/2012/04/the-hacker-games                                              )                                | -                                           | -     |
| [sqli-labs](https://github.com/Audi-1/sqli-labs                                                              )                                      | -                                           | -     |
| [sqlilabs](https://github.com/himadriganguly/sqlilabs                                                       )                                       | -                                           | -     |
| [twitterlike](https://github.com/sakti/twitterlike                                                             )                                    | PHP-  git                                   | -     |
| [vSphere Hypervisor](https://www.vmware.com/products/vsphere-hypervisor/                                              )                             | -                                           | -     |
    
###### sites 
| name                                                             | tech | notes |
|:-----------------------------------------------------------------|:-----|:------|
| [hACME Game](http://www.hacmegame.org)                           | site | -     |
| [XSS Game](https://xss-game.appspot.com)                         | site | -     |
| [Embedded Security CTF](https://microcorruption.com )            | site | -     |
| [EnigmaGroup](http://www.enigmagroup.org/ )                      | site | -     |
| [Escape](http://escape.alf.nu/)                                  | site | -     |
| [Exploit Exercises](http://exploit-exercises.com)                | site | -     |
| [Smash The Stack](http://www.smashthestack.org)                  | site | -     |
| [Security Treasure Hunt](http://www.securitytreasurehunt.com)    | site | -     |
| [TheBlackSheep and Erik](http://www.bright-shadows.net)          | site | -     |
| [Root Me](http://www.root-me.org/?lang=e)                        | site | -     |
| [Hacker Challenge](http://www.dareyourmind.net)                  | site | -     |
| [HackThis](http://www.hackthis.co.uk)                            | site | -     |
| [Gh0st Lab](http://www.gh0st.net)                                | site | -     |
| [Hacker Test](http://www.hackertest.net)                         | site | -     |
| [RootContest](http://rootcontest.com)                            | site | -     |
| [SQLZoo](http://sqlzoo.net/hack)                                 | site | -     |
| [ThisIsLegal](http://thisislegal.com)                            | site | -     |
| [WabLab](http://www.wablab.com/hackm)                            | site | -     |
| [Try2Hack](http://www.try2hack.nl)                               | site | -     |
| [XSS: Can You XSS This?](http://canyouxssthis.com/HTMLSanitizer) | site | -     |
| [XSS: ProgPHP](http://xss.progphp.com)                           | site | -     |
| [pwn0](https://pwn0.com/home.ph)                                 | site | -     |
| [Halls Of Valhalla](http://halls-of-valhalla.org/beta/challenge) | site | -     |
| [Hack The Box](https://hackthebox.e)                             | site | -     |
| [Hack This Site](http://www.hackthissite.org)                    | site | -     |
| [Hacking-Lab](https://www.hacking-lab.com)                       | site | -     |
| [Hack.me](https://hack.m)                                        | site | -     |
| [HackQuest](http://www.hackquest.com)                            | site | -     |
| [Play on Demand](https://pod.cybersecuritychallenge.org.uk)      | site | -     |
| [Hax.Tor](http://hax.tor.hu)                                     | site | -     |
| [PentestIT](http://www.pentestit.ru/en)                          | site | -     |
| [OverTheWire](http://www.overthewire.org/wargames)               | site | -     |

###### vendor 
| name                                                 | tech | notes |
|:-----------------------------------------------------|:-----|:------|
| [Acunetix acuart](http://testphp.vulnweb.com)        | -    | -     |
| [Mavituna testsparker](http://aspnet.testsparker.co) | -    | -     |
| [HP freebank](http://zero.webappsecurity.com)        | -    | -     |
| [IBM altoromutual](http://demo.testfire.net)         | -    | -     |
| [Mavituna testsparker](http://php.testsparker.co)    | -    | -     |
| [NTOSpider Test Site](http://www.webscantest.com/)   | -    | -     |
| [Acunetix acublog](http://testaspnet.vulnweb.com)    | -    | -     |
| [Acunetix acuforum](http://testasp.vulnweb.com)      | -    | -     |

###### mobile 
| name                                                                             | tools | notes |
|:---------------------------------------------------------------------------------|:------|:------|
| [OWASP GoatDroid Project](https://github.com/jackMannino/OWASP-GoatDroid-Projec) | -     | -     |
| [NcN Wargame](http://noconname.org/evento/wargame)                               | -     | -     |
| [OWASP Goatdroid](https://github.com/jackMannino/OWASP-GoatDroid-Projec)         | -     | -     |
| [ExploitMe Mobile Android Labs](http://securitycompass.github.io/AndroidLabs)    | -     | -     |
| [InsecureBank](http://www.paladion.net/downloadapp.htm)                          | -     | -     |
| [OWASP iGoat](https://code.google.com/archive/p/owasp-igoat)                     | -     | -     |
| [Damn Vulnerable iOS App (DVIA)](http://damnvulnerableiosapp.com)                | -     | -     |
| [Damn Vulnerable iOS App (DVIA)](https://github.com/prateek147/DVI)              | -     | -     |
| [Damn Vulnerable iOS App (DVIA-2)](https://github.com/prateek147/DVIA-v)         | -     | -     |
| [ExploitMe Mobile iPhone Labs](http://securitycompass.github.io/iPhoneLabs)      | -     | -     |
| [FirefoxOS (DVFA)](https://github.com/pwnetrationguru/dvfa)                      | -     | -     |
| [iPhone Labs](https://github.com/SecurityCompass/iPhoneLab)                      | -     | -     |
| [Android Labs](https://github.com/securitycompass/AndroidLab)                    | -     | -     |
| [Damn Vulnerable Android App (DVAA)](https://code.google.com/archive/p/dva)      | -     | -     |
| [Damn Vulnerable Android App (DVAA)](https://code.google.com/p/dvaa)             | -     | -     |

###### binary 
| name                                          | tools | notes |
|:----------------------------------------------|:------|:------|
| [war games](https://overthewire.org/wargames) | -     | -     |
| [pwnable.kr](http://pwnable.kr)               | -     | -     |
| [jarvsioj](https://www.jarvisoj.com)          | -     | -     |
| [ringerzer0team](https://ringzer0ctf.com)     | -     | -     |
| [ropemporium](https://ropemporium.com)        | -     | -     |
    
###### crypto
| name                                                                    | type | notes |
|:------------------------------------------------------------------------|:-----|:------|
| [cryptopals](https://cryptopals.co)                                     | -    | -     |
| [cryptochallenge.io](https://cryptochallenge.io)                        | -    | -     |
| [w3challs](https://w3challs.com/challenges/crypto)                      | -    | -     |
| [enigmagroup](http://www.enigmagroup.org/)                              | -    | -     |
| [cryptOMG](https://github.com/SpiderLabs/CryptOM)                       | -    | -     |
| [praetorian](https://www.praetorian.com/challenges/crypto)              | -    | -     |
| [cryptoPKI](https://seedsecuritylabs.org/Labs_16.04/Crypto/Crypto_PKI/) | -    | -     |

###### CTF 
| name                                                           | status | notes |
|:---------------------------------------------------------------|:-------|:------|
| [CTFtime (Details of CTF Challenges)](http://ctftime.org/ctf)  | -      | -     |
| [shell-storm Repo](http://shell-storm.org/repo/CT)             | -      | -     |
| [CAPTF Repo](http://captf.com)                                 | -      | -     |
| [CTF write-ups repository](https://github.com/ctf)             | -      | -     |
| [Reddit CTF Announcements](http://www.reddit.com/r/securityct) | -      | -     |

###### Older 
| name                                                                                           | desc | notes |
|:-----------------------------------------------------------------------------------------------|:-----|:------|
| [Exploit-DB](http://www.exploit-db.com)                                                        | -    | -     |
| [Old Apps](http://www.oldapps.com)                                                             | -    | -     |
| [Old Version](http://www.oldversion.com)                                                       | -    | -     |
| [VirtualHacking Repo](https://sourceforge.net/projects/virtualhacking/files/apps%40realworld/) | -    | -     |

##### misc 
| name                                                                                                   | desc | notes |
|:-------------------------------------------------------------------------------------------------------|:-----|:------|
| [irtuaPlant](https://github.com/jseidl/virtuaplan)                                                     | -    | -     |
| [ulnVoIP](http://www.rebootuser.com/?page_id=104)                                                      | -    | -     |
| [ulnVPN](http://www.rebootuser.com/?page_id=104)                                                       | -    | -     |
| [NS3](http://sourceforge.net/projects/gns-)                                                            | -    | -     |
| [AMPP](https://www.apachefriends.org/index.htm)                                                        | -    | -     |
| [Morning Catch](http://blog.cobaltstrike.com/2014/08/06/introducing-morning-catch-a-phishing-paradise) | -    | -     |
| [DVRF](https://github.com/praetorian-inc/DVR)                                                          | -    | -     |
| [AWBO](https://labs.snort.org/awbo/awbo.htm)                                                           | -    | -     |
