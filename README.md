<h1>Phishing Investigation with Chronicle</h1>

<h2>Description</h2>
I received an alert regarding a phishing email sent to an employee, which contained a suspicious domain: <em>signin.office365x24.com</em>. My objective is to investigate whether other employees have also received phishing emails associated with this domain and determine if any have accessed the site, signaling a potential breach.
<h2>Program Walk-through:</h2>

<h3>1. Perform a Domain Search</h3>
<p align="center">
<img src="https://i.imgur.com/EWt7iVG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>After typing <strong>signin.office365x24.com</strong> and clicking <strong>Search</strong>, under <strong>DOMAINS</strong>, <em>signin.office365x24.com</em> will be listed. This indicates that the domain exists in the ingested data.</p>

<p>The following are observed in the <strong>Domain View</strong>:</p>
<ul>
  <li><strong>VT CONTEXT:</strong> This section provides the VirusTotal information available for the domain.</li>
  <li><strong>WHOIS:</strong> This section provides a summary of information about the domain using WHOIS, a free and publicly available directory that includes information about registered domain names, such as the name and contact information of the domain owner. In cybersecurity, this information is helpful in assessing a domain's reputation and determining the origin of malicious websites.</li>
  <li><strong>Prevalence:</strong> This section provides a graph that outlines the historical prevalence of the domain. This can be helpful when you need to determine whether the domain has been accessed previously. Usually, less prevalent domains may indicate a greater threat.</li>
  <li><strong>RESOLVED IPS:</strong> This insight card provides additional context about the domain, such as the IP address that maps to <em>signin.office365x24.com</em>, which is <em>40.100.174.34</em>. Clicking on this IP will run a new search for the IP address in Chronicle. Insight cards can be helpful in expanding the domain investigation and further investigating an indicator to determine whether there is a broader compromise.</li>
  <li><strong>SIBLING DOMAINS:</strong> This insight card provides additional context about the domain. Sibling domains share a common top or parent domain. For example, here the sibling domain is listed as <em>login.office365x24.com</em>, which shares the same top domain <em>office365x24.com</em> with the domain I am investigating: <em>signin.office365x24.com</em>.</li>
  <li><strong>TIMELINE:</strong> This tab provides information about the events and interactions made with this domain. Click <strong>EXPAND ALL</strong> to reveal the details about the HTTP requests made, including GET and POST requests. A GET request retrieves data from a server while a POST request submits data to a server.</li>
  <li><strong>ASSETS:</strong> This tab provides a list of the assets that have accessed the domain.</li>
</ul>
 
<br/>

<br/> 
 
<h3>2. Investigate the Threat Intelligence Data</h3>
<p align="center">
<img src="https://i.imgur.com/LLdHzVI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Clicking on <strong>VTContext</strong> will assess the VirusTotal information about this domain. Shown here are the vendors that have flagged this domain as malicious.
<br/>
<br/>

<h3>3. Investigate the Affected Assets and Events</h3>
<p align="center">
<img src="https://i.imgur.com/AKBbZGl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
The events and assets associated with the domain are categorized under the <strong>Assets</strong> and <strong>Timeline</strong> tabs. The <strong>Assets</strong> tab provides the date and time of access for each asset that interacted with the domain, while the <strong>Timeline</strong> tab offers detailed insights into HTTP requests, including GET and POST requests. Notably, POST requests are particularly valuable as they indicate data transmission to the domain, suggesting a potential successful phishing attempt. The assets involved in sending data were identified as <strong>Ashton Davidson</strong>, <strong>Emil Palmer</strong>, and <strong>Warren Morris</strong>. 
<br/>
<br/>
<h3>4. Investigate the Resolved IP Address</h3>
<p align="center">
<img src="https://i.imgur.com/vIVn2Wo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p align="center">
<img src="https://i.imgur.com/cCbnFy7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>Attackers often reuse the same infrastructure for multiple attacks, resulting in several domain names resolving to the same IP address. In this case, under the <strong>Resolved IPs</strong> section, IP address <strong>40.100.174.34</strong> is mapped to <em>signin.office365x24.com</em>. By selecting this IP, a new search is initiated within Chronicle.</p>

<p>In the <strong>Timeline</strong> tab, a new POST request is observed, suggesting that an asset may have been compromised. The affected asset is identified as <strong>Warren Morris</strong>. Additional domains linked to this IP address are also displayed, providing further context for the investigation.</p>

<h2>Conclusion</h2>
In the rapidly evolving landscape of cybersecurity, understanding the intricacies of network traffic and user interactions with potentially malicious domains is essential for effective threat detection and response. Tools like Google Chronicle enable security professionals to analyze vast amounts of data, correlating user activities with indicators of compromise. By effectively utilizing these platforms, organizations can gain valuable insights into suspicious behaviors, identify compromised assets, and enhance their overall security posture.

As demonstrated in the investigation of suspicious domain interactions, identifying GET and POST requests is crucial in assessing the nature of user engagements with potentially harmful entities. Security teams must remain vigilant in monitoring all aspects of network traffic, recognizing that not all interactions are straightforward and that some users may be affected indirectly or in less obvious ways.
