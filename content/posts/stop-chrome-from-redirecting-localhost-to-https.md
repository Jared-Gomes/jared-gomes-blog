---
title: How to stop Chrome from redirecting localhost to HTTPS
date: 2020-01-24
published: true
tags: ['Troubleshooting']
series: false
canonical_url: false
cover_image: ./images/this-site-cant-provide-a-secure-connection.png
description: 'Learn how to fix Chrome Domain Security Policies issues in 3 steps. Developing multiple projects on localhost can present issues when one uses HTTPS.'
---

## Chrome keeps redirecting my localhost project to HTTPS

### "This site can't provide a secure connection"

This issue occurs when you have previously worked on a project that used an SSL certificate and was accessed through `https://localhost`.

This is due to the domain security policy in Chrome relating to HTTP Strict Transport Security (HSTS). Once a domain has used the HTTPS protocol, Chrome will always redirect the the secure version of the domain.

Luckily this is a very easy problem to fix.

## How to delete domain security policies in Chrome

This issue can be solved in three easy steps:

1. Navigate to: [chrome://net-internals/#hsts](chrome://net-internals/#hsts)
2. Under "Delete domain security policies", enter: `localhost` as the domain
3. Click delete

You're all set! You should now be able to access `http://localhost` without Chrome throwing any errors!
