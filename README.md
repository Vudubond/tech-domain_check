Script: domain_check
Author: Peter Elsner <peter.elsner@webpros.com>
Purpose: Get information on all domains on a cPanel server.
Created: 08/29/2024

You can run it without arguments and it will run it on all domains listed in /etc/userdomains
You can also run it with domain names as arguments to run it only for those domains.

```
# ./domain_check
Domain: testdomain.com [ addon ] - ( user1 )
    \_ A Record: 15.197.142.173 -  [ HOSTED ELSEWHERE ]
    \_ A Record: 3.33.152.147 -  [ HOSTED ELSEWHERE ]
    \_ MX Record: 0 mailstore1.secureserver.net. -  [ HOSTED ELSEWHERE ]
    \_ MX Record: 10 smtp.secureserver.net. -  [ HOSTED ELSEWHERE ]
    \_ Name Server: ns62.domaincontrol.com.
    \_ Name Server: ns61.domaincontrol.com.
================================================================================
Domain: sub.testdomain.com [ sub ] - ( user1 )
    \_ A Record: 172.241.25.87 -  [ HOSTED HERE ]
================================================================================
Domain: sub2.someotherdomain.com [ sub ] - ( user2 )
    \_ A Record: 172.241.25.87 -  [ HOSTED HERE ]
================================================================================
```

```
# ./domain_check domain1.com domain2.net domain3.com domain4.com domain5.net
Domain: domain1.com [ addon ] - ( user1 )
    \_ A Record: 64.34.75.145 -  [ HOSTED ELSEWHERE ]
    \_ MX Record: 0 craigrowland.com. -  [ HOSTED ELSEWHERE ]
    \_ Name Server: ns2.hostpapa.com.
    \_ Name Server: ns1.hostpapa.com.
================================================================================
Domain: domain2.net [ main ] - ( user2 )
    \_ A Record: 104.21.0.112 -  [ CloudFlare IP ]
    \_ A Record: 172.67.150.232 -  [ CloudFlare IP ]
    \_ MX Record: 81 route3.mx.cloudflare.net. -  [ CloudFlare IP ]
    \_ MX Record: 68 route2.mx.cloudflare.net. -  [ CloudFlare IP ]
    \_ MX Record: 31 route1.mx.cloudflare.net. -  [ CloudFlare IP ]
    \_ Name Server: ray.ns.cloudflare.com.
    \_ Name Server: bingo.ns.cloudflare.com.
================================================================================
Domain: domain3.com [ main ] - ( user3 )
    \_ A Record: 172.241.24.165 -  [ HOSTED HERE ]
    \_ MX Record: 0 corsersac.com. -  [ HOSTED ELSEWHERE ]
    \_ Name Server: ns3.siteocity.com.
    \_ Name Server: ns2.siteocity.com.
    \_ Name Server: ns4.siteocity.com.
    \_ Name Server: ns1.siteocity.com.
================================================================================
Domain: domain4.com [ addon ] - ( user4 )
DNS Error:  NXDOMAIN
================================================================================
================================================================================
Domain: domain5.net [ main ] - ( user5 )
    \_ A Record: 172.241.25.87 -  [ HOSTED HERE ]
    \_ MX Record: 0 domain5.net. -  [ HOSTED ELSEWHERE ]
    \_ Name Server: ns2.siteocity.com.
    \_ Name Server: ns1.siteocity.com.
    \_ Name Server: ns3.siteocity.com.
    \_ Name Server: ns4.siteocity.com.
================================================================================
```

You can also create a report by using tee.

```
./domain_check | tee mydomainreport.txt
```

Then to view the report, use less -R mydomainreport.txt


