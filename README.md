<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>OSINT Framework - Security Web Tools</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
<style>
body {
    margin: 0;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    min-height: 100vh;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    display: flex;
    flex-direction: column;
    align-items: center;
    color: #333;
}

header, footer {
    width: 100%;
    background: linear-gradient(90deg, #0052D4, #4364F7, #6FB1FC);
    color: white;
    text-align: center;
    padding: 30px 20px;
    font-family: 'Times New Roman', Times, serif;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}

header h1 {
    margin: 0;
    font-size: 2.5em;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
}

header p {
    margin: 10px 0 0;
    font-size: 1.2em;
}

main {
    width: 100%;
    max-width: 1200px;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
}

.mindmap {
    background: linear-gradient(135deg, #043031, #0b6f73);
    color: white;
    width: 90%;
    max-width: 1000px;
    padding: 30px;
    border-radius: 15px;
    box-shadow: 0 8px 20px rgba(0,0,0,0.3);
    position: relative;
    overflow: hidden;
}

.mindmap::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 5px;
    background: linear-gradient(90deg, #00eaff, #007bff);
}

.mindmap ul {
    list-style: none;
    padding-left: 0;
    margin: 0;
}

.mindmap li {
    margin: 10px 0;
    position: relative;
}

.mindmap li::before {
    content: '';
    position: absolute;
    left: -20px;
    top: 10px;
    width: 15px;
    height: 2px;
    background: #00eaff;
}

.mindmap li::after {
    content: '';
    position: absolute;
    left: -20px;
    top: 0;
    width: 2px;
    height: 100%;
    background: #00eaff;
}

.mindmap li:last-child::after {
    height: 10px;
}

.category {
    font-size: 1.5em;
    font-weight: bold;
    color: #00eaff;
    cursor: pointer;
    display: flex;
    align-items: center;
    transition: color 0.3s ease;
}

.category:hover {
    color: #ffffff;
}

.category i {
    margin-right: 10px;
}

.category-toggle {
    margin-left: auto;
    background: linear-gradient(45deg, #00eaff, #007bff);
    border: none;
    border-radius: 50%;
    width: 30px;
    height: 30px;
    color: white;
    font-size: 14px;
    cursor: pointer;
    transition: transform 0.3s ease;
}

.category-toggle:hover {
    transform: scale(1.1);
}

.sub-tools {
    display: none;
    padding-left: 30px;
    margin-top: 10px;
}

.tool {
    font-size: 1.2em;
    color: #00eaff;
    cursor: pointer;
    display: flex;
    align-items: center;
    transition: color 0.3s ease;
    margin: 5px 0;
}

.tool:hover {
    color: #ffffff;
}

.tool i {
    margin-right: 10px;
}

.tool-info {
    display: none;
    padding: 15px;
    background: rgba(0,0,0,0.2);
    border-radius: 8px;
    margin-top: 10px;
    border-left: 4px solid #00eaff;
}

.tool-info h3 {
    margin: 0 0 10px 0;
    color: #00eaff;
    cursor: pointer;
    transition: color 0.3s ease;
}

.tool-info h3:hover {
    color: #ffffff;
}

.tool-info p {
    margin: 0;
    line-height: 1.5;
}

footer {
    margin-top: auto;
    padding: 20px;
}

footer hr {
    border: none;
    height: 1px;
    background: linear-gradient(90deg, transparent, #fff, transparent);
    margin: 20px 0;
}

footer p, footer h2 {
    margin: 5px 0;
    font-size: 0.9em;
}

@media (max-width: 768px) {
    .mindmap {
        width: 95%;
        padding: 20px;
    }
    header h1 {
        font-size: 2em;
    }
    .category {
        font-size: 1.3em;
    }
    .tool {
        font-size: 1em;
    }
}
</style>
<script>
function toggleCategory(id) {
    const subTools = document.getElementById(id);
    const toggleBtn = event.target.closest('.category').querySelector('.category-toggle');
    if (subTools.style.display === 'block') {
        subTools.style.display = 'none';
        toggleBtn.innerHTML = '<i class="fas fa-plus"></i>';
    } else {
        subTools.style.display = 'block';
        toggleBtn.innerHTML = '<i class="fas fa-minus"></i>';
    }
}

function toggleTool(id) {
    const info = document.getElementById(id);
    if (info.style.display === 'block') {
        info.style.display = 'none';
    } else {
        info.style.display = 'block';
    }
}

function redirectTo(url) {
    window.open(url, '_blank');
}
</script>
</head>
<body>

<header>
<h1><i class="fas fa-shield-alt"></i>Security Web Tools</h1>
<p>Interactive Mind Map Website-based Tools</p>
</header>

<main>
<div class="mindmap">
<ul>
    <!-- 1. IP / Network / DNS -->
    <li>
        <div class="category" onclick="toggleCategory('ip-tools')">
            <i class="fas fa-network-wired"></i> IP / Network / DNS Tools
            <button class="category-toggle"><i class="fas fa-plus"></i></button>
        </div>
        <ul id="ip-tools" class="sub-tools">
            <li class="tool" onclick="toggleTool('ip1-info')">
                <i class="fas fa-search"></i> NSLookup
            </li>
            <div id="ip1-info" class="tool-info">
                <h3 onclick="redirectTo('https://nslookup.io')">NSLookup</h3>
                <p>This tool is used to find DNS records of a domain name. It helps identify IP address, name servers, and mail servers. Useful for network troubleshooting and basic reconnaissance.</p>
            </div>
            <li class="tool" onclick="toggleTool('ip2-info')">
                <i class="fas fa-check-circle"></i> DNS Checker
            </li>
            <div id="ip2-info" class="tool-info">
                <h3 onclick="redirectTo('https://dnschecker.org')">DNS Checker</h3>
                <p>Checks DNS propagation across different countries. Helps verify whether DNS changes are updated globally. Commonly used by network and system administrators.</p>
            </div>
            <li class="tool" onclick="toggleTool('ip3-info')">
                <i class="fas fa-eye"></i> ViewDNS
            </li>
            <div id="ip3-info" class="tool-info">
                <h3 onclick="redirectTo('https://viewdns.info')">ViewDNS</h3>
                <p>Provides multiple DNS-related lookup services. Includes reverse IP, WHOIS, and DNS history. Useful for investigating websites and servers.</p>
            </div>
            <li class="tool" onclick="toggleTool('ip4-info')">
                <i class="fas fa-dumpster"></i> DNSDumpster
            </li>
            <div id="ip4-info" class="tool-info">
                <h3 onclick="redirectTo('https://dnsdumpster.com')">DNSDumpster</h3>
                <p>Used for DNS reconnaissance and mapping domains. Finds subdomains, hosts, and network structure. Helpful during security assessments.</p>
            </div>
            <li class="tool" onclick="toggleTool('ip5-info')">
                <i class="fas fa-map-marker-alt"></i> IPLocation
            </li>
            <div id="ip5-info" class="tool-info">
                <h3 onclick="redirectTo('https://iplocation.net')">IPLocation</h3>
                <p>Shows geographical location of an IP address. Displays country, ISP, and region details. Useful for tracking suspicious IPs.</p>
            </div>
            <li class="tool" onclick="toggleTool('ip6-info')">
                <i class="fas fa-tools"></i> HackerTarget IP Tools
            </li>
            <div id="ip6-info" class="tool-info">
                <h3 onclick="redirectTo('https://hackertarget.com/ip-tools/')">HackerTarget IP Tools</h3>
                <p>Provides multiple IP and network analysis tools. Includes traceroute, port scan, and DNS lookup. Used for learning and security testing.</p>
            </div>
        </ul>
    </li>

    <!-- 2. Domain & WHOIS -->
    <li>
        <div class="category" onclick="toggleCategory('domain-tools')">
            <i class="fas fa-globe"></i> Domain & WHOIS Tools
            <button class="category-toggle"><i class="fas fa-plus"></i></button>
        </div>
        <ul id="domain-tools" class="sub-tools">
            <li class="tool" onclick="toggleTool('domain1-info')">
                <i class="fas fa-user"></i> WHOIS
            </li>
            <div id="domain1-info" class="tool-info">
                <h3 onclick="redirectTo('https://whois.com')">WHOIS</h3>
                <p>Displays domain ownership information. Shows registrar, registration date, and expiry date. Helpful to identify website owners.</p>
            </div>
            <li class="tool" onclick="toggleTool('domain2-info')">
                <i class="fas fa-certificate"></i> ICANN Lookup
            </li>
            <div id="domain2-info" class="tool-info">
                <h3 onclick="redirectTo('https://icann.org/wicf')">ICANN Lookup</h3>
                <p>Official WHOIS lookup by ICANN. Provides accurate domain registration details. Trusted source for domain verification.</p>
            </div>
            <li class="tool" onclick="toggleTool('domain3-info')">
                <i class="fas fa-tools"></i> CentralOps
            </li>
            <div id="domain3-info" class="tool-info">
                <h3 onclick="redirectTo('https://centralops.net')">CentralOps</h3>
                <p>Combines WHOIS, DNS, and network tools. Helps analyze domains and IP addresses. Useful for basic cyber investigations.</p>
            </div>
            <li class="tool" onclick="toggleTool('domain4-info')">
                <i class="fas fa-search"></i> Reverse WHOIS
            </li>
            <div id="domain4-info" class="tool-info">
                <h3 onclick="redirectTo('https://viewdns.info/reversewhois/')">Reverse WHOIS</h3>
                <p>Finds other domains registered with same details. Helps identify related or fake websites. Useful in phishing investigations.</p>
            </div>
        </ul>
    </li>

    <!-- 3. Email Investigation -->
    <li>
        <div class="category" onclick="toggleCategory('email-tools')">
            <i class="fas fa-envelope"></i> Email Investigation Tools
            <button class="category-toggle"><i class="fas fa-plus"></i></button>
        </div>
        <ul id="email-tools" class="sub-tools">
            <li class="tool" onclick="toggleTool('email1-info')">
                <i class="fas fa-exclamation-triangle"></i> Have I Been Pwned
            </li>
            <div id="email1-info" class="tool-info">
                <h3 onclick="redirectTo('https://haveibeenpwned.com')">Have I Been Pwned</h3>
                <p>Checks whether an email was leaked in data breaches. Shows breach source and date information. Helps users know if their account is compromised.</p>
            </div>
        </ul>
    </li>

    <!-- 4. URL / Redirect -->
    <li>
        <div class="category" onclick="toggleCategory('url-tools')">
            <i class="fas fa-link"></i> URL / Redirect Analysis
            <button class="category-toggle"><i class="fas fa-plus"></i></button>
        </div>
        <ul id="url-tools" class="sub-tools">
            <li class="tool" onclick="toggleTool('url1-info')">
                <i class="fas fa-route"></i> WhereGoes
            </li>
            <div id="url1-info" class="tool-info">
                <h3 onclick="redirectTo('https://wheregoes.com')">WhereGoes</h3>
                <p>Tracks URL redirections step-by-step. Shows final destination of shortened links. Helps detect suspicious redirects.</p>
            </div>
            <li class="tool" onclick="toggleTool('url2-info')">
                <i class="fas fa-expand"></i> CheckShortURL
            </li>
            <div id="url2-info" class="tool-info">
                <h3 onclick="redirectTo('https://checkshorturl.com')">CheckShortURL</h3>
                <p>Expands shortened URLs to original links. Helps avoid phishing and malicious links. Very useful for link safety checks.</p>
            </div>
            <li class="tool" onclick="toggleTool('url3-info')">
                <i class="fas fa-scan"></i> URLScan
            </li>
            <div id="url3-info" class="tool-info">
                <h3 onclick="redirectTo('https://urlscan.io')">URLScan</h3>
                <p>Scans websites and shows behavior details. Displays requests, scripts, and IP data. Used for website threat analysis.</p>
            </div>
            <li class="tool" onclick="toggleTool('url4-info')">
                <i class="fas fa-server"></i> HTTPStatus
            </li>
            <div id="url4-info" class="tool-info">
                <h3 onclick="redirectTo('https://httpstatus.io')">HTTPStatus</h3>
                <p>Checks HTTP response codes of websites. Helps identify server errors and redirects. Useful for debugging web issues.</p>
            </div>
            <li class="tool" onclick="toggleTool('url5-info')">
                <i class="fas fa-check"></i> Redirect Checker
            </li>
            <div id="url5-info" class="tool-info">
                <h3 onclick="redirectTo('https://redirect-checker.org')">Redirect Checker</h3>
                <p>Checks redirect chain of a URL. Shows whether link is safe or suspicious. Helpful for security and SEO analysis.</p>
            </div>
        </ul>
    </li>

    <!-- 5. Malware -->
    <li>
        <div class="category" onclick="toggleCategory('malware-tools')">
            <i class="fas fa-virus"></i> Malware / URL Analysis
            <button class="category-toggle"><i class="fas fa-plus"></i></button>
        </div>
        <ul id="malware-tools" class="sub-tools">
            <li class="tool" onclick="toggleTool('malware1-info')">
                <i class="fas fa-shield-virus"></i> VirusTotal
            </li>
            <div id="malware1-info" class="tool-info">
                <h3 onclick="redirectTo('https://virustotal.com')">VirusTotal</h3>
                <p>Scans files and URLs using multiple antivirus engines. Detects malware, phishing, and suspicious behavior. Very popular security analysis tool.</p>
            </div>
        </ul>
    </li>

    <!-- 6. Reverse Image -->
    <li>
        <div class="category" onclick="toggleCategory('image-tools')">
            <i class="fas fa-images"></i> Reverse Image Search
            <button class="category-toggle"><i class="fas fa-plus"></i></button>
        </div>
        <ul id="image-tools" class="sub-tools">
            <li class="tool" onclick="toggleTool('image1-info')">
                <i class="fas fa-search-plus"></i> TinEye
            </li>
            <div id="image1-info" class="tool-info">
                <h3 onclick="redirectTo('https://tineye.com')">TinEye</h3>
                <p>Finds where an image appears on the internet. Helps identify fake or reused images. Useful for image verification and OSINT.</p>
            </div>
        </ul>
    </li>
</ul>
</div>
</main>

<footer>
<hr>
<p><i>By</i></p>
<p><i>Nitharshana N | Tharani C | Lithika V</i></p>
<h2>&copy; Copyright</h2>
</footer>

</body>
</html>
