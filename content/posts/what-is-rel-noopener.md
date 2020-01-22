---
title: What is rel="noopener"? Noopener explained
date: 2020-01-22
published: true
tags: ['Security', 'Best Practices']
series: false
canonical_url: false
description: 'Noopener is an HTML attribute that you can add to &lt;a> tags that use target=”_blank” to open a page in a new tab. It provides your website with small performance gains but more importantly addresses a security vulnerability.'
---

## What is rel=”noopener”?

Noopener is an HTML attribute that you can add to `<a>` tags that use `target=”_blank”` to open a page in a new tab.

For links that open in a new tab, you should be using the attribute `rel=”noopener”`. It provides your website with small performance gains but more importantly addresses a security vulnerability.

## Performance

Modern browsers utilize multiple processes to increase performance. Most of the time, each separate tab will occupy its own process. The JavaScript running on that tab will be contained inside of its respective process.

When a link opens a new tab, certain browsers may run the new page on the same process. This will lead to decreased performance and thus you always want to use `rel=”noopener”` on any links with `target=”_blank”` (links that open a new tab).

Chrome 67+ is not affected by this due to a feature called **Site Isolation**.
Firefox is currently implementing this feature.

## Security

The biggest benefit from using this attribute is the security it provides your website.
When opening a new tab through a link, the `window` object of the originating page becomes exposed to the new page through the `window.opener` property.

This means that the opened page has **_full_** control over your originating page's `window` object. This is a serious cross-site issue! This means that opened page could navigate the original page to a new one that is designed to phish credentials or one with other malicious intent.

## Google Lighthouse

Google's site audit, Lighthouse, considers using `rel=”noopener”` as a best practice. If you're looking to improve your lighthouse score, you definitely want to make sure you're utilizing this best practice.
General consensus is that using this attribute does not affect your page's SEO but in my opinion it doesn't hurt to utilize. Especially considering it improves the security of your website, it is a no-brainer to use this.

When auditing your website with the tool, it searches for any links using `target=”_blank”` that don't use `rel="noopener"` or `rel="noreferrer"`.

**NOTE:** Lighthouse will ignore any links that go to the same origin (website). However, it is still recommended to apply this practice for the performance benefits.

## rel="noreferrer"

Using the attribute `rel="noreferrer"` has the same effect as using `rel="noopener"` but also stops the `Referer` header from being sent to the opened page.
The `Referer` header displays the URL of who linked them to the current page.

## Takeaway

Whenever you use:

`<a target="_blank" href="//google.com">Google</a>`

without `rel="noopener"` you decrease the performance of your site, introduce a security vulnerability, and reduce your Lighthouse score.

Changing it to:

`<a target="_blank" rel="noopener" href="//google.com">Google</a>`

or

`<a target="_blank" rel="noreferrer" href="//google.com">Google</a>`

fixes all the mentioned issues.
