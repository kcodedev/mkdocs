# 🛡️ Network Security

## 🔥 Firewalls

![Firewall](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6f/Firewall-X400.png/960px-Firewall-X400.png)

- Firewalls can be software or hardware.
- They monitor and controls network traffic based on predefined security rules.
- Firewalls examine packets based on source/destination IP addresses, ports, and protocols.
- Firewalls can block traffic to specific ports associated with applications (e.g., block port 80/443 for web browsing, port 25 for email, or custom ports for games/apps).

## 🌐 Proxy Servers

### Forward Proxy
![Forward](https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Forward_proxy_h2g2bob.svg/640px-Forward_proxy_h2g2bob.svg.png)

- **Forward Proxy**: Intercepts client requests to the internet, providing anonymity by masking the client's IP address. It can also cache content, filter malicious sites, and enforce access policies.

### Reverse Proxy
![Reverse](https://upload.wikimedia.org/wikipedia/commons/thumb/6/67/Reverse_proxy_h2g2bob.svg/640px-Reverse_proxy_h2g2bob.svg.png)

- **Reverse Proxy**: Sits in front of web servers, receiving client requests and forwarding them to the appropriate server. It enhances security, load balancing, and performance through caching and SSL termination.
- **Rate Limiting**: A feature often implemented in reverse proxies to control the number of requests a client can make in a given time period. This helps prevent DDoS attacks by limiting excessive traffic from a single source, ensuring server availability during high-volume attempts to overwhelm the system.