<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Security Web Tools</title>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">

<style>
/* ===== RESET ===== */
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

/* ===== BODY ===== */
body{
    font-family:'Segoe UI',Tahoma,sans-serif;
    min-height:100vh;
    background:linear-gradient(135deg,#667eea,#764ba2);
    display:flex;
    flex-direction:column;
}

/* ===== HEADER ===== */
header{
    width:100%;
    background:linear-gradient(90deg,#0052D4,#4364F7,#6FB1FC);
    color:white;
    text-align:center;
    padding:35px 20px;
    box-shadow:0 4px 10px rgba(0,0,0,0.25);
}

header h1{
    font-size:2.6rem;
}

header p{
    margin-top:10px;
    font-size:1.2rem;
}

/* ===== MAIN ===== */
main{
    flex:1;
    width:100%;
    display:flex;
    justify-content:center;
    padding:50px 20px;
}

/* ===== CONTAINER ===== */
.container{
    width:100%;
    max-width:1200px;
}

/* ===== MINDMAP CARD ===== */
.mindmap{
    background:linear-gradient(135deg,#043031,#0b6f73);
    color:white;
    width:100%;
    padding:35px;
    border-radius:18px;
    box-shadow:0 15px 35px rgba(0,0,0,0.35);
    position:relative;
}

.mindmap::before{
    content:"";
    position:absolute;
    top:0;
    left:0;
    width:100%;
    height:6px;
    background:linear-gradient(90deg,#00eaff,#007bff);
    border-radius:18px 18px 0 0;
}

/* ===== LIST ===== */
.mindmap ul{
    list-style:none;
}

/* ===== CATEGORY ===== */
.category{
    display:flex;
    align-items:center;
    gap:12px;
    font-size:1.5rem;
    font-weight:bold;
    color:#00eaff;
    background:rgba(255,255,255,0.1);
    padding:14px 16px;
    border-radius:10px;
    cursor:pointer;
    margin:18px 0;
}

.category:hover{
    background:rgba(255,255,255,0.2);
    color:white;
}

.category-toggle{
    margin-left:auto;
    width:32px;
    height:32px;
    border:none;
    border-radius:50%;
    background:#00eaff;
    color:black;
    cursor:pointer;
}

/* ===== SUB TOOLS ===== */
.sub-tools{
    display:none;
    margin-left:25px;
    margin-top:10px;
}

/* ===== TOOL ===== */
.tool{
    font-size:1.15rem;
    color:#00eaff;
    cursor:pointer;
    display:flex;
    align-items:center;
    gap:10px;
    padding:8px;
    border-radius:8px;
}

.tool:hover{
    background:rgba(255,255,255,0.15);
    color:white;
}

/* ===== TOOL INFO ===== */
.tool-info{
    display:none;
    background:rgba(0,0,0,0.25);
    border-left:4px solid #00eaff;
    border-radius:10px;
    padding:15px;
    margin:10px 0 15px 20px;
}

.tool-info h3{
    color:#00eaff;
    cursor:pointer;
}

.tool-info h3:hover{
    text-decoration:underline;
}

.tool-info p{
    margin-top:8px;
    line-height:1.6;
}

/* ===== FOOTER ===== */
footer{
    width:100%;
    background:linear-gradient(90deg,#0052D4,#4364F7,#6FB1FC);
    color:white;
    text-align:center;
    padding:20px;
}

footer hr{
    border:none;
    height:1px;
    background:linear-gradient(90deg,transparent,#fff,transparent);
    margin:12px 0;
}

/* ===== RESPONSIVE ===== */
@media(max-width:768px){
    header h1{font-size:2rem;}
    .category{font-size:1.25rem;}
    .tool{font-size:1rem;}
    .mindmap{padding:25px;}
}
</style>

<script>
function toggleCategory(id){
    const el=document.getElementById(id);
    const icon=event.currentTarget.querySelector('.category-toggle i');

    if(el.style.display==="block"){
        el.style.display="none";
        icon.className="fas fa-plus";
    }else{
        el.style.display="block";
        icon.className="fas fa-minus";
    }
}

function toggleTool(id){
    const el=document.getElementById(id);
    el.style.display=(el.style.display==="block")?"none":"block";
}

function openLink(url){
    window.open(url,"_blank");
}
</script>
</head>

<body>

<header>
<h1><i class="fas fa-shield-alt"></i> Security Web Tools</h1>
<p>Interactive Mind Map – Website-based Security Tools</p>
</header>

<main>
<div class="container">
<div class="mindmap">

<!-- IP / Network / DNS -->
<div class="category" onclick="toggleCategory('ip')">
<i class="fas fa-network-wired"></i> IP / Network / DNS Tools
<button class="category-toggle"><i class="fas fa-plus"></i></button>
</div>
<ul id="ip" class="sub-tools">
<li class="tool" onclick="toggleTool('ip1')"><i class="fas fa-search"></i> NSLookup</li>
<div id="ip1" class="tool-info">
<h3 onclick="openLink('https://nslookup.io')">NSLookup</h3>
<p>Used to find DNS records like IP address, name servers and mail servers.</p>
</div>
</ul>

<!-- Domain -->
<div class="category" onclick="toggleCategory('domain')">
<i class="fas fa-globe"></i> Domain & WHOIS Tools
<button class="category-toggle"><i class="fas fa-plus"></i></button>
</div>
<ul id="domain" class="sub-tools">
<li class="tool" onclick="toggleTool('d1')"><i class="fas fa-user"></i> WHOIS</li>
<div id="d1" class="tool-info">
<h3 onclick="openLink('https://whois.com')">WHOIS</h3>
<p>Shows domain ownership and registration details.</p>
</div>
</ul>

<!-- Email -->
<div class="category" onclick="toggleCategory('email')">
<i class="fas fa-envelope"></i> Email Investigation Tools
<button class="category-toggle"><i class="fas fa-plus"></i></button>
</div>
<ul id="email" class="sub-tools">
<li class="tool" onclick="toggleTool('e1')"><i class="fas fa-exclamation-triangle"></i> Have I Been Pwned</li>
<div id="e1" class="tool-info">
<h3 onclick="openLink('https://haveibeenpwned.com')">Have I Been Pwned</h3>
<p>Checks whether an email was leaked in data breaches.</p>
</div>
</ul>

</div>
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
