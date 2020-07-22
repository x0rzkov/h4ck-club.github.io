```
IP Address Tracking
Cookie Tracking
ETag Tracking
Digital Fingerprinting
browser fingerprint
Script-Based Fingerprinting
Canvas Fingerprinting

```
```
proxy chain
tor
```
```
The login page will redirect to the favicon if the user is already logged in, or it will serve a regular HTML page if the user is not.
So, the script creates an (invisible) <img> element for every website which points to the login page (which might redirect to the favicon). If it receives an image, the user is already logged in and the onLoad() callback will fire. Otherwise, it will get an HTML page, so the onError() callback will fire.
It could work with any image on the website, not just the favicon.
Though the redirect works only with images hosted on the same domain. The favicon was the only image I could find on twitter.com or facebook.com.
I reported this bug to every company listed there, but all of them said it is not relevant to their users' privacy.

This is showing that I'm logged in to Facebook but I don't have an account there anymore.

```
```
Panopticlick (https://panopticlick.eff.org)
DeviceInfo (https://www.deviceinfo.me)
Browserleaks (https://browserleaks.com)
AmIUnique (https://amiunique.org)
https://robinlinus.github.io/socialmedia-leak/
https://osint.link/#privacy
https://www.secjuice.com/finding-real-ips-of-origin-servers-behind-cloudflare-or-tor/
```
