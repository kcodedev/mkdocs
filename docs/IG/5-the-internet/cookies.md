# Cookies: What Are They? 🍪✨

```mermaid
sequenceDiagram
    participant Browser as 🌐 Browser
    participant Website as 🌍 Website

    Browser->>Website: GET /homepage
    Website-->>Browser: Here's the page + Set-Cookie (favorite_cookie=choc_chip)
    Note over Browser: Stores cookie 🍪

    Note over Browser,Website: Later that day...
    Browser->>Website: GET /homepage<br/>Cookie: favorite_cookie=choc_chip
    Website-->>Browser: Welcome back!<br/>We remember you prefer<br/>chocolate chip cookies! 😊
```

Cookies are small pieces of data stored by your web browser when you visit websites. They help websites remember information about you to improve your browsing experience. 🌐💾

---

## Common Uses of Cookies 🍩

Cookies can be used for:

- **Saving personal details** like your name or preferences 👤💡  
- **Tracking user preferences** such as language or theme 🎨🌍  
- **Holding items in an online shopping cart** so they don’t disappear 🛒✨  
- **Storing login details** to keep you signed in 🔑👀  

---

## Types of Cookies 🍪🔍

- **Session Cookies** ⏳  
  These cookies last only while you are browsing a website. Once you close the browser, session cookies are deleted. They help websites remember your actions during a visit. 🧹

- **Persistent Cookies** 📂  
  These cookies stay on your device for a set period, even after you close the browser. They remember things like login info or preferences for future visits. 🗂️📅

---

## Why Are Some Cookies Controversial? ⚠️🕵️‍♀️

Some cookies are used to **track users across multiple websites** to gather data about browsing habits. This data is often used for targeted advertising. 🎯📊

- **Privacy Concerns:** Many people find this tracking intrusive because it feels like being watched online. 👀🚫  
- **Data Sharing:** Some companies share or sell this data to third parties without clear consent. 🤝💸

Because of these concerns, many browsers now offer options to block or limit tracking cookies. 🚫🍪

