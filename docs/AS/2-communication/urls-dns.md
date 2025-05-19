# 🔗 How URLs and DNS Work Together to Locate Web Resources

When you type a **Uniform Resource Locator (URL)** into your browser, a series of steps happen behind the scenes to fetch the right content. This process relies heavily on the **Domain Name Service (DNS)**.

---

## 🧐 1. What Is a URL?

A **URL** is the address you enter to locate a resource (web page, image, video) on the World Wide Web. It has several parts:

scheme://[username:password@]host[:port]/path[?query][#fragment]


| Example                                  | Purpose                                                              | Emoji |
|------------------------------------------|----------------------------------------------------------------------|-------|
| `https`                                  | Defines the protocol (HTTP, HTTPS, FTP, etc.)                        | 🔒    |
| `user`                                   | (Optional) credentials for protected resources                       | 👤    |
| `pass`                                   | (Optional) paired with username                                      | 🔑    |
| `www.example.com`                        | The domain name (or IP) of the server                                | 🌐    |
| `:443`                                   | (Optional) network port; defaults to 80 for HTTP, 443 for HTTPS       | 🚪    |
| `/folder/page.html`                      | Location of the resource on the server                               | 🗂️    |
| `?id=123&sort=asc`                       | (Optional) parameters passed to dynamic pages or APIs                | ❓    |
| **Fragment**   | `#section2`                              | (Optional) in-page anchor                                           | 📌    |

**Example URL:**  
https://www.example.com:443/path/to/page.html?search=network#top


---

## 🔄 2. URL Resolution Steps

1. **Parse the URL**: Browser breaks it into scheme, host, port, path, etc.

2. **DNS Lookup**: Browser asks a DNS resolver: “What is the IP address of `www.example.com`?” DNS returns an IP (e.g., `93.184.216.34`).  

3. **Establish Connection**: Browser opens a connection to that IP. For a HTTPS connection a TLS handshake is performed 🔒.

4. **Send HTTP Request**: e.g. `GET /path/to/page.html?search=network HTTP/1.1`  

5. **Receive Response**: Server sends back HTML, JSON, images, etc.

6. **Render Content**: Browser parses HTML/CSS/JS and displays the page.

---
