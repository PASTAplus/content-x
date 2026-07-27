# Responsible Use of EDI API Access Keys with Data Catalogs

[TOC]

Do not panic! We recognize that the use of EDI API Access Keys for data catalogs is not a perfect solution for strong authentication against malicious access to the EDI data repository, but it will provide more friction for abusers and give us better knowledge of where an attack originates if one occurs.

*If you suspect an access key has been compromised, you should immediately revoke it and then create a new key for use on your website. Please let us know if this occurs so that we can monitor any attempted use of this access key. If we suspect that your access key has been compromised, we will monitor it for abuse and revoke it if necessary, letting you know as soon as possible of the situation. Continued abuse of access keys may require custom solutions.* 

Different catalogs will have different approaches to using access keys. The following are suggestions for reducing the threat surface of your catalog when using EDI API Access Keys:

## 1. Only use zero-member "Group" Keys

- **Only use access keys created for zero-member groups:** Zero-member groups are groups that contain no members, but still conveys an "authenticated" level of access to reach through the API. Never use this group when assigning permissions to data packages. ([see this video](https://youtu.be/fieZSmHk2H4))
- **Never use profile-based access keys:** A profile-based access key is one that has permissions associated with the user of the profile. This access key should be treated like your own personal password; never share or expose it to other users or the public, like on a website.
- **Rotate your access keys regularly:** Consider changing your access keys on a regular basis (e.g., monthly or quarterly). Doing so will keep escaped keys from being abused.

## 2. Never Save Access Keys on Public Webpages or in Code Repositories

- **Keep keys out of plaintext:** Never paste the API key into page copy, public HTML code, or shared open documents.
- **Avoid publishing access keys in code repositories, like GitHub or GitLab:** Use placeholder or template keys when storing code in these repositories. Only add access keys to code on web servers where you have complete control. If you must save your access key in a code repository, consider making that repository private.

## 3. Hide or Obfuscate Download Links Behind Buttons

- **Don't use direct download links:** Avoid placing standard `<a href="https://pasta.lternet.edu/...">` text links on your website that point directly to the EDI data repository, as web crawlers and automated bots can easily follow and scrape those links, especially when access keys are attached to the URL.
- **Use interactive click actions:** Set up data repository access as a button click or trigger that loads desired API links on demand using your website builder's action settings or basic JavaScript. Common approaches include a) hiding the data repository link behind a JavaScript button, b) encoding raw links into a Base64 string that can be decoded using a Base64 decoder, or c) breaking up the data repository links into fragments that are indiscernible by robot scrapers, assembling them only on request. The goal is to make scraping for direct links to the data repository more difficult, not impossible. See [here](/resources/obsfucate) as example of how to obsfucate a URL.

## 4. Use CAPTCHA-based Guards on your Catalog Websites

- **Invisible CAPTCHA applications are effective:** Applications like Cloudflare Turnstile or Google reCAPTCHA v3 are easy to install and provide a first-line of defense against automated bots and scrapers.
