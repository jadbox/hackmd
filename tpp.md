# Token Permissioned Pages <img src="https://emojipedia-us.s3.dualstack.us-west-1.amazonaws.com/thumbs/320/twitter/259/coin_1fa99.png" height="32"/> <img src="https://emojipedia-us.s3.dualstack.us-west-1.amazonaws.com/thumbs/320/google/263/bridge-at-night_1f309.png" height="32"/> <img src="https://emojipedia-us.s3.dualstack.us-west-1.amazonaws.com/thumbs/240/twitter/259/globe-with-meridians_1f310.png" height="32"/>

*What's this about?*

If you observe Patreon, the act of subcribing to a creator gives you access to private content they post on platform. Perhaps we can give creators an even more powerful platform- the ability to directly own their own subscribtions via crypto token ownership, and be able to permission gate any content on the Internet (be it in the cloud, self-hosted, or decentralized swarms).  

The Token Permissioned Pages platform [TPP] is a special reverse proxy that acts like an authorization gateway that gates by token balance requirement to Internet webpages. In other words, it's a paywall over any unlisted webcontent, but only requires token ownership rather requiring a transaction for access. By just requiring token ownership for access, it reduces gas costs and requires transaction-free minimal effort on the user to access web content.

## ⚡ Use-cases

* Any content meant for only a token community to have access
  * newsletters
  * blog
  * splash page
  * unlisted youtube video links
  * unlisted podcasts


## 👯 Compatibility
* Any ERC-20 token is supported
* ERC-721 is not supported (yet!)
* Supported wallets
  * Metamask
  * Wallet Connect
  * Roll
  * Coinbase wallet
* IPFS links are only supported via ipfs http gateways. Native IPFS support is on the roadmap.
* DAT links are also currently unsupported

## 📖 Terminology

* *Source URL* is the URL you provide TPP to secretly tunnel public traffic to if the user has enough token balance
* *Proxy URL* the public TPP link that serves content from the *source url*.

## ⭐️ Limitations and notes
* **Important**: ensure your source URL is blocked from search engines via a robots.txt or *noindex* metatag (https://support.google.com/webmasters/answer/93710?hl=en)
* User sessions and cookies from the origin will not work that well with the TPP proxy. It's recommended to stick with static pages/spa that do not rely on user sessions.
* Currently both the source url and TPP shared link are limtied to HTTP protocol only. We're in the process of investigating future HTTPS support.

## 🏃 Getting Started: generate a link

Use the below link and replace the attributes: **url**, **token** (address), and (min) **balance** to what you need. The resulting json will have url and social fields for the proxy links.

### Example link request:

http://gen.link.collab.land/gen?url=GOOGLE.COM&token=0x6b175474e89094c44da98b954eedeac495271d0f&balance=3

### Response:

The response will be a json with two keys. The "url" key will be the direct link that can be sent to an audience directly to use. The "social" key is a special url that works better for posted the link on Twitter on social platforms, but this link requires an extra redirect for the user to visit the link.

**Schema:**
```js
{"url": "http://xxx", "social": "https://xxx"}
```

**Example response:**
```js
{
"url":"http://50334b501623351369115d3c56ed95.4c3e2af38f9dba84dfab4f4e10d1112399e37b3a1692300345db7a6fc73.1afbf0b0d63650b06916433cd282a.705c39d52fa241f0302fd785cdb2d.c9ff7a1fad04c.link.collab.land/",
"social":"http://50334b501623351369115d3c56ed95.4c3e2af38f9dba84dfab4f4e10d1112399e37b3a1692300345db7a6fc73.1afbf0b0d63650b06916433cd282a.705c39d52fa241f0302fd785cdb2d.c9ff7a1fad04c.link.collab.land/tppsocial/"
}
```