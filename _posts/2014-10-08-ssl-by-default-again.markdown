---
layout: post
title: SSL by default, again
date: '2014-10-08 15:54:37'
---

Thanks to some [recent changes by CloudFlare](https://blog.cloudflare.com/introducing-universal-ssl/) I'm now able to serve content from the site again via SSL, by default. In addition, if your browser supports SPDY [that will now work too!](https://blog.cloudflare.com/the-little-extra-that-comes-with-universal-ssl/)

I had [previously setup SSL](https://vmstan.com/https/) on the site using my own certificate, but that was back when I was doing my own hosting of Ghost through Rackspace. I have since [moved to hosted Ghost](https://vmstan.com/ghost-io/) which did not offer the ability to do this. (They do however, provide SSL for the administration portal.)

I really liked CloudFlare's explination of why this important, so rather than rewrite it, I'll just let them explain:
> Having cutting-edge encryption may not seem important to a small blog, but it is critical to advancing the encrypted-by-default future of the Internet. Every byte, however seemingly mundane, that flows encrypted across the Internet makes it more difficult for those who wish to intercept, throttle, or censor the web. In other words, ensuring your personal blog is available over HTTPS makes it more likely that a human rights organization or social media service or independent journalist will be accessible around the world. Together we can do great things.

Let's do some great things.