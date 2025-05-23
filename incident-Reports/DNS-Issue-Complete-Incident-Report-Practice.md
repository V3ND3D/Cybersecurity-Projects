# Cybersecurity Incident Report:

# Network Traffic Analysis

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Part 1: Provide a summary of the problem found in the DNS and
ICMP</p>
<p>traffic log.</p></td>
</tr>
<tr class="even">
<td rowspan="2"><p>The network protocol analyzer logs indicate that
attempts to resolve the domain yummyrecipesforme.com using DNS (UDP port
53) fail due to an ICMP “destination port unreachable” error.</p>
<p>• The initial UDP request is sent from 192.51.100.15 (the client) to
203.0.113.2 (the DNS server) on port 53 to request an IP address for the
domain.</p>
<p>• The DNS server responds with an ICMP message stating that UDP port
53 is unreachable, indicating that no service is actively listening on
this port.</p>
<p>• This error repeats three times with different timestamps,
confirming that DNS resolution is unavailable.</p>
<p>Potential impact</p>
<p>Since DNS is essential for resolving domain names to IP addresses,
this failure prevents the affected system from accessing websites and
online services using domain names. Without a working DNS, the user
cannot reach the web page, causing network connectivity issues.</p></td>
</tr>
<tr class="odd">
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Part 2: Explain your analysis of the data and provide at least one
cause of the incident.</td>
</tr>
<tr class="even">
<td><p><strong>Time incident occurred:</strong></p>
<p>The incident was first recorded at <strong>13:24:32</strong>, based
on the timestamps in the network traffic logs. The issue persisted
through subsequent requests at <strong>13:26:32</strong> and
<strong>13:28:32</strong>, indicating an ongoing problem.</p>
<p><strong>How the IT team became aware of the incident:</strong></p>
<p>The IT team became aware of the issue when users reported an
inability to access the website <strong>yummyrecipesforme.com</strong>.
Attempts to visit the website resulted in a <strong>“destination port
unreachable”</strong> error. Upon further investigation using a network
protocol analyzer, the IT team confirmed that DNS resolution was failing
due to <strong>ICMP port 53 unreachable responses</strong> from the DNS
server.</p>
<p><strong>Actions taken by the IT department to investigate the
incident:</strong></p>
<p>1. <strong>Attempted direct access to the website</strong> – Users
were unable to reach the domain, prompting further investigation.</p>
<p>2. <strong>Used network protocol analysis (tcpdump)</strong> –
Captured traffic to analyze DNS queries and responses.</p>
<p>3. <strong>Examined the DNS query process</strong> – Confirmed that
DNS requests were sent but not successfully received.</p>
<p>4. <strong>Reviewed ICMP error messages</strong> – Identified
repeated responses indicating that <strong>UDP port 53 was
unreachable</strong> on the DNS server.</p>
<p><strong>Key findings of the IT department’s
investigation:</strong></p>
<p>• The issue affects <strong>UDP port 53</strong>, which is required
for DNS resolution.</p>
<p>• The <strong>DNS server at 203.0.113.2</strong> is either down or
misconfigured, preventing it from responding to queries.</p>
<p>• ICMP error messages confirm that the server is <strong>not
listening</strong> on port 53.</p>
<p>• The issue persists across multiple attempts, ruling out a temporary
network glitch.</p>
<p><strong>Likely cause of the incident:</strong></p>
<p>One likely cause is that <strong>the DNS service on the server at
203.0.113.2 is either down, misconfigured, or blocked by a firewall
policy</strong>. If the DNS server is not running or if firewall rules
have been changed to block UDP port 53, DNS queries would fail,
resulting in the ICMP “port unreachable” responses observed in the
logs.</p></td>
</tr>
</tbody>
</table>

Report summary:  
The **tcpdump** log reveals that multiple DNS queries were sent to
**203.0.113.2** for resolving **yummyrecipesforme.com**, but each
request resulted in an **ICMP "port 53 unreachable"** response. This
indicates that the DNS server is not responding to requests on its
designated port. Without DNS resolution, users cannot access the
intended website.

Analysis of the captured network traffic confirms that the issue is
persistent and affects all attempts to query the DNS server. The
repeated **ICMP unreachable** responses suggest that either the **DNS
service is down, misconfigured, or being blocked by firewall rules**.

A likely cause of the incident is that the **DNS server at 203.0.113.2
is not running or has been misconfigured, preventing it from handling
queries on UDP port 53**. A firewall rule change or network issue could
also be preventing communication with the server.

The next steps in troubleshooting include **checking the DNS server
status, verifying firewall rules, and ensuring that UDP port 53 is open
and properly forwarding requests**. If the server is down, restarting
the DNS service or switching to an alternate DNS server may resolve the
issue.

The suspected root cause is a **failure of the DNS service on
203.0.113.2, either due to an internal configuration issue or a
firewall/network restriction preventing access to port 53**.
