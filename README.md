[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.me/SASAICAGENCY)


tarteaucitron.js
================
Comply to the european cookie law is simple with the french *tarte au citron*.

# What is this script?
The european cookie law regulates the management of cookies and you should ask your visitors their consent before exposing them to third party services.

Clearly this script will:
- Disable all services by default,
- Display a banner on the first page view and a small one on other pages,
- Display a panel to allow or deny each services one by one,
- Activate services on the second page view if not denied,
- Store the consent in a cookie for 365 days.

Bonus:
- Load service when user click on Allow (without reload of the page),
- Incorporate a fallback system (display a link instead of social button and a static banner instead of advertising).

## Supported services
* Advertising network
  * Amazon
  * Clicmanager
  * Criteo
  * FERank (pub)
  * Google Adsense
  * Google Adsense Search (form)
  * Google Adsense Search (result)
  * Google Adwords (conversion)
  * Google Adwords (remarketing)
  * Pubdirecte
  * Twenga
  * vShop

* APIs
  * Google jsapi
  * Google Maps
  * Google Tag Manager
  * Timeline JS
  * Typekit (adobe)

* Audience measurement
  * Alexa
  * Clicky
  * Crazyegg
  * FERank
  * Get+
  * Google Analytics (ga.js)
  * Google Analytics (universal)
  * StatCounter
  * VisualRevenue
  * Xiti

* Comment
  * Disqus
  * Facebook (commentaire)
  
* Marketing Automation & CRM
  * Mautic
  * Webmecanik Automation
  
* Social network
  * AddThis
  * AddToAny (feed)
  * AddToAny (share)
  * eKomi
  * Facebook
  * Facebook (like box)
  * Google+
  * Google+ (badge)
  * Linkedin
  * Pinterest
  * Shareaholic
  * ShareThis
  * Twitter
  * Twitter (cards)
  * Twitter (timelines)

* Support
  * UserVoice
  * Zopim

* Video
  * Calameo
  * Dailymotion
  * Prezi
  * SlideShare
  * Vimeo
  * YouTube


## Visitors outside the EU
In PHP for example, you can bypass all the script by setting this var `tarteaucitron.user.bypass = true;` if the visitor is not in the EU.

## Tested on
- IE 6+
- FF 3+
- Safari 4+
- Chrome 14+
- Opera 10+

# Installation guide
[Visit opt-out.ferank.eu](https://opt-out.ferank.eu/)


# How to use

```html
<script type="text/javascript" src="/tarteaucitron/tarteaucitron.js"></script>

<script type="text/javascript">
tarteaucitron.init({
    "privacyUrl": "", /* Privacy policy url */

    "hashtag": "#tarteaucitron", /* Open the panel with this hashtag */
    "cookieName": "tarteaucitron", /* Cookie name */

    "orientation": "middle", /* Banner position (top - bottom) */
    "showAlertSmall": true, /* Show the small banner on bottom right */
    "cookieslist": true, /* Show the cookie list */

    "adblocker": false, /* Show a Warning if an adblocker is detected */
    "AcceptAllCta" : true, /* Show the accept all button when highPrivacy on */
    "highPrivacy": true, /* Disable auto consent */
    "handleBrowserDNTRequest": false, /* If Do Not Track == 1, disallow all */

    "removeCredit": false, /* Remove credit link */
    "moreInfoLink": true, /* Show more info link */
    "useExternalCss": false, /* If false, the tarteaucitron.css file will be loaded */

    //"cookieDomain": ".my-multisite-domaine.fr", /* Shared cookie for subdomain website */

    "readmoreLink": "/cookiespolicy" /* Change the default readmore link pointing to tarteaucitron.io */
});
</script>
```

# Create custom service
```js
tarteaucitron.services.mycustomservice = {
  "key": "mycustomservice",
  "type": "ads|analytic|api|comment|other|social|support|video",
  "name": "MyCustomService",
  "needConsent": true,
  "cookies": ['cookie', 'cookie2'],
  "readmoreLink": "/custom_read_more", // If you want to change readmore link
  "js": function () {
    "use strict";
    // When user allow cookie
  },
  "fallback": function () {
    "use strict";
    // when use deny cookie
  }
};
```
