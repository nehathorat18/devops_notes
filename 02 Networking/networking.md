# 🌐 Networking Fundamentals

This document contains my notes and hands-on practice while learning networking concepts as part of my DevOps journey.

---

# OSI Model vs TCP/IP Model

The **OSI model** is a theoretical networking model with **7 layers** that explains how data travels across a network.

The **TCP/IP model** is the practical networking model used on the Internet. It consists of **4 layers** and is the foundation of modern communication.

## Comparison

| OSI Layer | TCP/IP Layer | Purpose |
|-----------|--------------|---------|
| Application | Application | HTTP, HTTPS, DNS, SSH |
| Presentation | Application | Data formatting & encryption |
| Session | Application | Session management |
| Transport | Transport | TCP & UDP |
| Network | Internet | IP addressing & routing |
| Data Link | Network Access | MAC addressing |
| Physical | Network Access | Cables, switches, signals |

---

# Protocol Stack

| Protocol | Layer |
|----------|-------|
| HTTP / HTTPS | Application |
| DNS | Application |
| SSH | Application |
| TCP / UDP | Transport |
| IP | Internet |

### Example

```bash
curl https://example.com
```

Application → TCP → IP

---

# Basic Networking Commands

| Command | Purpose |
|---------|---------|
| `hostname -I` | Show IP address |
| `ip addr show` | Display network interfaces |
| `ping <host>` | Test connectivity |
| `tracepath <host>` | Show packet route |
| `ss -tulpn` | Show listening ports |
| `netstat -an` | View network connections |
| `dig <domain>` | DNS lookup |
| `nslookup <domain>` | DNS lookup |
| `curl -I <url>` | Check HTTP response |

---

# Port Troubleshooting

Test a listening service:

```bash
nc -zv localhost <port>
```

If unreachable, check:

- Service status
- Firewall rules
- Listening ports

---

# Troubleshooting

### Fastest Connectivity Check

```bash
ping <host>
```

### DNS Issue

Check:

```bash
dig <domain>
nslookup <domain>
```

### HTTP 500 Error

- Check application logs
- Verify web server
- Test using `curl`

---

# DNS

When a domain like **google.com** is entered into a browser:

1. DNS resolves the domain name to an IP address.
2. The browser connects to the server.
3. An HTTP request is sent.
4. The server responds with the webpage.

## Common DNS Records

| Record | Purpose |
|---------|---------|
| A | Maps domain to IPv4 |
| AAAA | Maps domain to IPv6 |
| CNAME | Alias to another domain |
| MX | Mail server |
| NS | Authoritative name server |

---

# IP Addressing

## IPv4

An IPv4 address is a 32-bit address written as four decimal numbers.

Example:

```
192.168.1.10
```

## Public vs Private IP

| Type | Example |
|------|---------|
| Public | 8.8.8.8 |
| Private | 192.168.1.10 |

### Private IP Ranges

- 10.0.0.0/8
- 172.16.0.0/12
- 192.168.0.0/16

---

# CIDR & Subnetting

### What is /24?

A **/24** means the first **24 bits** identify the network.

### Usable Hosts

| CIDR | Hosts |
|------|------:|
| /24 | 254 |
| /16 | 65,534 |
| /28 | 14 |

### Common Subnet Masks

| CIDR | Subnet Mask |
|------|-------------|
| /24 | 255.255.255.0 |
| /16 | 255.255.0.0 |
| /28 | 255.255.255.240 |

### Why Subnet?

Subnetting divides a large network into smaller, manageable networks for better performance and security.

---

# Common Ports

| Port | Service |
|------|---------|
| 22 | SSH |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |
| 3306 | MySQL |
| 6379 | Redis |
| 27017 | MongoDB |

---

# Real-World Examples

### Accessing a Web Application

```bash
curl http://myapp.com:8080
```

Networking concepts involved:

- DNS resolves the domain
- IP identifies the destination
- TCP establishes the connection
- HTTP transfers data
- Port **8080** identifies the service

---

### Database Connectivity Issue

If an application cannot connect to **10.0.1.50:3306**:

- Test connectivity using `ping`
- Verify port **3306** is open
- Check firewall rules
- Ensure MySQL is running

---

# Key Learnings

- Learned the difference between the OSI and TCP/IP models.
- Understood DNS, IP addressing, subnetting, and common ports.
- Practiced networking commands for troubleshooting.
- Learned a basic workflow for diagnosing network and application issues.