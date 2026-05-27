<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Vimesh Weerasinghe - EEE Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Exo+2:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  *{margin:0;padding:0;box-sizing:border-box;}
  :root{
    --navy:#020b18;--navy2:#041020;--blue1:#0a1f3c;--blue2:#0d2b54;--blue3:#1a3a6b;
    --accent:#00c8ff;--accent2:#0080ff;--accent3:#4fc3f7;--gold:#ffd700;
    --text:#e0f2ff;--muted:#7bafd4;--white:#ffffff;
    --glow:0 0 20px rgba(0,200,255,0.3);--glow2:0 0 40px rgba(0,200,255,0.15);
  }
  html{scroll-behavior:smooth;}
  body{
    background:var(--navy);color:var(--text);
    font-family:'Exo 2',sans-serif;font-size:15px;line-height:1.7;
    min-height:100vh;overflow-x:hidden;
  }
  .grid-bg{
    position:fixed;inset:0;z-index:0;pointer-events:none;
    background-image:
      linear-gradient(rgba(0,200,255,0.03) 1px,transparent 1px),
      linear-gradient(90deg,rgba(0,200,255,0.03) 1px,transparent 1px);
    background-size:40px 40px;
  }
  .particles{position:fixed;inset:0;z-index:0;pointer-events:none;overflow:hidden;}
  .particle{
    position:absolute;width:2px;height:2px;border-radius:50%;
    background:var(--accent);opacity:0;
    animation:float linear infinite;
  }
  @keyframes float{
    0%{transform:translateY(100vh) translateX(0);opacity:0;}
    10%{opacity:0.6;}
    90%{opacity:0.3;}
    100%{transform:translateY(-100px) translateX(50px);opacity:0;}
  }
  .container{max-width:1100px;margin:0 auto;padding:0 20px;position:relative;z-index:1;}
  nav{
    position:fixed;top:0;left:0;right:0;z-index:100;
    background:rgba(2,11,24,0.92);backdrop-filter:blur(12px);
    border-bottom:1px solid rgba(0,200,255,0.15);
    padding:12px 0;
  }
  .nav-inner{max-width:1100px;margin:0 auto;padding:0 20px;display:flex;align-items:center;justify-content:space-between;}
  .nav-logo{font-family:'Orbitron',sans-serif;font-size:16px;font-weight:700;color:var(--accent);letter-spacing:2px;}
  .nav-logo span{color:var(--white);}
  .nav-links{display:flex;gap:28px;}
  .nav-links a{color:var(--muted);font-size:13px;letter-spacing:1px;text-decoration:none;text-transform:uppercase;transition:color 0.3s;font-weight:500;}
  .nav-links a:hover{color:var(--accent);}
  .hero{min-height:100vh;display:flex;align-items:center;padding:100px 0 60px;position:relative;overflow:hidden;}
  .hero-content{display:flex;align-items:center;gap:60px;width:100%;}
  .hero-text{flex:1;}
  .hero-badge{
    display:inline-flex;align-items:center;gap:8px;
    background:rgba(0,200,255,0.08);border:1px solid rgba(0,200,255,0.3);
    border-radius:50px;padding:6px 16px;margin-bottom:24px;
    font-size:12px;color:var(--accent);letter-spacing:1.5px;text-transform:uppercase;
  }
  .hero-badge::before{content:'';width:6px;height:6px;border-radius:50%;background:var(--accent);animation:pulse 2s infinite;}
  @keyframes pulse{0%,100%{opacity:1;}50%{opacity:0.3;}}
  .hero h1{
    font-family:'Orbitron',sans-serif;font-size:clamp(28px,4vw,52px);
    font-weight:900;line-height:1.1;margin-bottom:12px;
    background:linear-gradient(135deg,#fff 0%,var(--accent3) 50%,var(--accent) 100%);
    -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
  }
  .hero-sub{font-size:18px;color:var(--accent);font-weight:500;margin-bottom:8px;letter-spacing:1px;}
  .hero-desc{color:var(--muted);font-size:15px;max-width:520px;margin-bottom:32px;line-height:1.8;}
  .hero-ctas{display:flex;gap:14px;flex-wrap:wrap;}
  .btn-primary{
    background:linear-gradient(135deg,var(--accent2),var(--accent));
    color:#000;font-weight:700;padding:12px 28px;border-radius:6px;
    text-decoration:none;font-size:13px;letter-spacing:1px;text-transform:uppercase;
    transition:all 0.3s;box-shadow:var(--glow);
  }
  .btn-primary:hover{transform:translateY(-2px);box-shadow:0 0 30px rgba(0,200,255,0.5);}
  .btn-outline{
    border:1px solid rgba(0,200,255,0.5);color:var(--accent);
    padding:12px 28px;border-radius:6px;text-decoration:none;
    font-size:13px;letter-spacing:1px;text-transform:uppercase;transition:all 0.3s;
  }
  .btn-outline:hover{background:rgba(0,200,255,0.1);border-color:var(--accent);}
  .hero-avatar{flex-shrink:0;position:relative;}
  .avatar-ring{
    width:220px;height:220px;border-radius:50%;
    border:2px solid rgba(0,200,255,0.4);
    display:flex;align-items:center;justify-content:center;
    position:relative;animation:spin 20s linear infinite;
  }
  @keyframes spin{from{transform:rotate(0deg);}to{transform:rotate(360deg);}}
  .avatar-ring::before{content:'';position:absolute;inset:-8px;border-radius:50%;border:1px solid rgba(0,200,255,0.15);}
  .avatar-ring::after{content:'';position:absolute;inset:-16px;border-radius:50%;border:1px dashed rgba(0,200,255,0.08);}
  .avatar-inner{
    width:190px;height:190px;border-radius:50%;
    background:linear-gradient(135deg,var(--blue2),var(--blue3));
    display:flex;align-items:center;justify-content:center;
    font-family:'Orbitron',sans-serif;font-size:52px;font-weight:900;
    color:var(--accent);animation:spin 20s linear infinite reverse;
    border:3px solid rgba(0,200,255,0.3);position:relative;overflow:hidden;
  }
  .avatar-inner::before{content:'';position:absolute;inset:0;background:radial-gradient(circle at 30% 30%,rgba(0,200,255,0.2),transparent 60%);}
  .hero-stats{display:flex;gap:24px;margin-top:32px;}
  .stat{text-align:center;}
  .stat-num{font-family:'Orbitron',sans-serif;font-size:22px;font-weight:700;color:var(--accent);}
  .stat-label{font-size:11px;color:var(--muted);text-transform:uppercase;letter-spacing:1px;}
  section{padding:80px 0;}
  .section-label{display:flex;align-items:center;gap:16px;margin-bottom:48px;}
  .section-label::before{content:'//';font-family:'Orbitron',sans-serif;color:var(--accent);font-size:14px;}
  .section-label h2{font-family:'Orbitron',sans-serif;font-size:24px;font-weight:700;color:var(--white);letter-spacing:2px;text-transform:uppercase;}
  .section-label::after{content:'';flex:1;height:1px;background:linear-gradient(90deg,rgba(0,200,255,0.4),transparent);}
  .timeline{position:relative;padding-left:32px;}
  .timeline::before{content:'';position:absolute;left:0;top:0;bottom:0;width:1px;background:linear-gradient(180deg,var(--accent),var(--blue3),transparent);}
  .timeline-item{position:relative;margin-bottom:40px;}
  .timeline-item::before{content:'';position:absolute;left:-36px;top:8px;width:10px;height:10px;border-radius:50%;background:var(--accent);box-shadow:var(--glow);}
  .exp-card{
    background:linear-gradient(135deg,rgba(10,31,60,0.9),rgba(13,43,84,0.6));
    border:1px solid rgba(0,200,255,0.15);border-radius:8px;padding:20px 24px;
    transition:all 0.3s;position:relative;overflow:hidden;
  }
  .exp-card::before{content:'';position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,transparent,var(--accent),transparent);}
  .exp-card:hover{border-color:rgba(0,200,255,0.4);transform:translateX(4px);box-shadow:var(--glow2);}
  .exp-header{display:flex;justify-content:space-between;align-items:flex-start;gap:12px;margin-bottom:8px;}
  .exp-title{font-weight:600;font-size:16px;color:var(--white);}
  .exp-company{color:var(--accent);font-size:14px;font-weight:500;margin-bottom:4px;}
  .exp-date{font-family:'Orbitron',sans-serif;font-size:11px;color:var(--muted);background:rgba(0,200,255,0.08);border:1px solid rgba(0,200,255,0.2);padding:3px 10px;border-radius:4px;white-space:nowrap;flex-shrink:0;}
  .exp-bullets{list-style:none;margin-top:10px;}
  .exp-bullets li{color:var(--muted);font-size:13.5px;padding:3px 0 3px 16px;position:relative;}
  .exp-bullets li::before{content:'▹';position:absolute;left:0;color:var(--accent);font-size:12px;}
  .edu-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(300px,1fr));gap:20px;}
  .edu-card{background:linear-gradient(135deg,rgba(10,31,60,0.9),rgba(13,43,84,0.6));border:1px solid rgba(0,200,255,0.15);border-radius:8px;padding:20px 24px;transition:all 0.3s;position:relative;overflow:hidden;}
  .edu-card:hover{border-color:rgba(0,200,255,0.4);box-shadow:var(--glow2);}
  .edu-icon{font-size:28px;margin-bottom:10px;}
  .edu-degree{font-size:15px;font-weight:600;color:var(--white);margin-bottom:4px;}
  .edu-school{color:var(--accent);font-size:13px;margin-bottom:6px;}
  .edu-date{font-size:12px;color:var(--muted);}
  .edu-badge{display:inline-block;margin-top:8px;background:rgba(255,215,0,0.1);border:1px solid rgba(255,215,0,0.3);color:var(--gold);font-size:11px;padding:2px 10px;border-radius:4px;}
  .skills-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:16px;}
  .skill-card{background:rgba(10,31,60,0.8);border:1px solid rgba(0,200,255,0.12);border-radius:8px;padding:16px;transition:all 0.3s;text-align:center;}
  .skill-card:hover{border-color:rgba(0,200,255,0.5);background:rgba(13,43,84,0.9);box-shadow:var(--glow);}
  .skill-icon{font-size:28px;margin-bottom:8px;}
  .skill-name{font-size:13px;font-weight:600;color:var(--white);margin-bottom:4px;}
  .skill-tags{display:flex;flex-wrap:wrap;gap:4px;justify-content:center;margin-top:8px;}
  .tag{font-size:10px;padding:2px 8px;border-radius:3px;background:rgba(0,200,255,0.1);border:1px solid rgba(0,200,255,0.2);color:var(--accent3);}
  .projects-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(300px,1fr));gap:20px;}
  .project-card{background:linear-gradient(135deg,rgba(10,31,60,0.95),rgba(13,43,84,0.7));border:1px solid rgba(0,200,255,0.15);border-radius:10px;padding:24px;transition:all 0.3s;position:relative;overflow:hidden;display:flex;flex-direction:column;}
  .project-card::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(90deg,var(--accent2),var(--accent));}
  .project-card:hover{border-color:rgba(0,200,255,0.5);transform:translateY(-4px);box-shadow:0 20px 40px rgba(0,0,0,0.4),var(--glow2);}
  .project-year{font-size:11px;color:var(--muted);font-family:'Orbitron',sans-serif;letter-spacing:1px;margin-bottom:8px;}
  .project-title{font-size:16px;font-weight:600;color:var(--white);margin-bottom:10px;line-height:1.4;}
  .project-desc{font-size:13px;color:var(--muted);flex:1;line-height:1.7;}
  .project-techs{display:flex;flex-wrap:wrap;gap:6px;margin-top:14px;}
  .github-section{background:linear-gradient(135deg,rgba(10,31,60,0.9),rgba(13,43,84,0.6));border:1px solid rgba(0,200,255,0.2);border-radius:12px;padding:32px;position:relative;overflow:hidden;}
  .github-header{display:flex;align-items:center;gap:16px;margin-bottom:24px;}
  .github-logo{width:52px;height:52px;border-radius:50%;background:linear-gradient(135deg,var(--blue2),var(--blue3));display:flex;align-items:center;justify-content:center;border:2px solid rgba(0,200,255,0.3);font-size:28px;}
  .github-info h3{font-family:'Orbitron',sans-serif;font-size:18px;color:var(--white);font-weight:700;}
  .github-info p{color:var(--muted);font-size:13px;}
  .github-link{display:inline-flex;align-items:center;gap:8px;margin-top:6px;color:var(--accent);font-size:13px;text-decoration:none;transition:color 0.3s;}
  .github-link:hover{color:var(--white);}
  .github-stats{display:grid;grid-template-columns:repeat(4,1fr);gap:16px;margin-bottom:24px;}
  .gh-stat{background:rgba(0,200,255,0.05);border:1px solid rgba(0,200,255,0.15);border-radius:8px;padding:14px;text-align:center;}
  .gh-stat-num{font-family:'Orbitron',sans-serif;font-size:22px;font-weight:700;color:var(--accent);}
  .gh-stat-label{font-size:11px;color:var(--muted);margin-top:2px;text-transform:uppercase;letter-spacing:0.5px;}
  .contrib-grid{display:grid;grid-template-columns:repeat(52,1fr);gap:2px;padding:8px 0;}
  .contrib-cell{width:100%;aspect-ratio:1;border-radius:2px;background:rgba(0,200,255,0.05);transition:background 0.2s;}
  .contrib-cell.l1{background:rgba(0,200,255,0.15);}
  .contrib-cell.l2{background:rgba(0,200,255,0.3);}
  .contrib-cell.l3{background:rgba(0,200,255,0.55);}
  .contrib-cell.l4{background:rgba(0,200,255,0.85);}
  .contrib-cell:hover{transform:scale(1.4);}
  .repo-cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:14px;margin-top:20px;}
  .repo-card{background:rgba(2,11,24,0.7);border:1px solid rgba(0,200,255,0.15);border-radius:8px;padding:16px;transition:all 0.3s;}
  .repo-card:hover{border-color:rgba(0,200,255,0.4);background:rgba(10,31,60,0.9);}
  .repo-name{color:var(--accent);font-size:14px;font-weight:600;margin-bottom:4px;}
  .repo-desc{color:var(--muted);font-size:12px;line-height:1.6;}
  .repo-meta{display:flex;gap:12px;margin-top:10px;}
  .repo-lang{font-size:11px;color:var(--muted);display:flex;align-items:center;gap:4px;}
  .lang-dot{width:8px;height:8px;border-radius:50%;}
  .certs-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:14px;}
  .cert-card{background:rgba(10,31,60,0.7);border:1px solid rgba(0,200,255,0.12);border-radius:8px;padding:16px 18px;display:flex;align-items:center;gap:14px;transition:all 0.3s;}
  .cert-card:hover{border-color:rgba(0,200,255,0.4);box-shadow:var(--glow);}
  .cert-icon{font-size:22px;flex-shrink:0;}
  .cert-name{font-size:13px;font-weight:500;color:var(--white);line-height:1.4;}
  .cert-org{font-size:11px;color:var(--muted);margin-top:2px;}
  .contact-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:16px;}
  .contact-card{background:rgba(10,31,60,0.7);border:1px solid rgba(0,200,255,0.15);border-radius:8px;padding:20px;text-align:center;transition:all 0.3s;}
  .contact-card:hover{border-color:var(--accent);box-shadow:var(--glow);}
  .contact-icon{font-size:28px;margin-bottom:8px;}
  .contact-type{font-size:11px;color:var(--muted);text-transform:uppercase;letter-spacing:1px;margin-bottom:4px;}
  .contact-val{font-size:13px;color:var(--accent);word-break:break-all;}
  footer{border-top:1px solid rgba(0,200,255,0.1);padding:32px 0;text-align:center;color:var(--muted);font-size:13px;}
  footer span{color:var(--accent);}
  .chip-float{display:inline-flex;align-items:center;gap:6px;background:rgba(0,200,255,0.08);border:1px solid rgba(0,200,255,0.25);border-radius:50px;padding:5px 12px;font-size:12px;color:var(--accent3);margin:4px;animation:chipFloat 4s ease-in-out infinite;}
  .chip-float:nth-child(2){animation-delay:1s;}
  .chip-float:nth-child(3){animation-delay:2s;}
  @keyframes chipFloat{0%,100%{transform:translateY(0);}50%{transform:translateY(-5px);}}
  @media(max-width:768px){
    .hero-content{flex-direction:column-reverse;text-align:center;}
    .hero-ctas{justify-content:center;}
    .github-stats{grid-template-columns:repeat(2,1fr);}
    .nav-links{display:none;}
  }
</style>
</head>
<body>

<div class="grid-bg"></div>
<div class="particles" id="particles"></div>

<nav>
  <div class="nav-inner">
    <div class="nav-logo">V<span>imesh</span>.EEE</div>
    <div class="nav-links">
      <a href="#experience">Experience</a>
      <a href="#projects">Projects</a>
      <a href="#skills">Skills</a>
      <a href="#github">GitHub</a>
      <a href="#contact">Contact</a>
    </div>
  </div>
</nav>

<div class="hero">
  <div class="container">
    <div class="hero-content">
      <div class="hero-text">
        <div class="hero-badge">&#9889; Available for Opportunities</div>
        <h1>W.M Vimesh<br>Tharushan<br>Weerasinghe</h1>
        <p class="hero-sub">Electrical &amp; Electronic Engineer</p>
        <p class="hero-desc">BEng (Hons) EEE professional specialising in embedded systems, IoT, circuit design, and QA/QC. Driven by Industry 4.0/5.0 and intelligent automation — building resilient, smart engineering systems.</p>
        <div style="margin-bottom:20px;">
          <span class="chip-float">&#128268; Embedded Systems</span>
          <span class="chip-float">&#128225; IoT Integration</span>
          <span class="chip-float">&#129302; AI &amp; Data Science</span>
        </div>
        <div class="hero-ctas">
          <a href="mailto:vimeshtharu@gmail.com" class="btn-primary">Hire Me</a>
          <a href="https://lk.linkedin.com/in/vimesh-tharushan-314413307" class="btn-outline" target="_blank">LinkedIn &#8599;</a>
          <a href="https://github.com/vimeshtharu" class="btn-outline" target="_blank">GitHub &#8599;</a>
        </div>
        <div class="hero-stats">
          <div class="stat"><div class="stat-num">3+</div><div class="stat-label">Internships</div></div>
          <div class="stat"><div class="stat-num">4+</div><div class="stat-label">Projects</div></div>
          <div class="stat"><div class="stat-num">5+</div><div class="stat-label">Certifications</div></div>
          <div class="stat"><div class="stat-num">2026</div><div class="stat-label">BEng Grad</div></div>
        </div>
      </div>
      <div class="hero-avatar">
        <div class="avatar-ring">
          <div class="avatar-inner">VW</div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- EXPERIENCE -->
<section id="experience">
  <div class="container">
    <div class="section-label"><h2>Experience</h2></div>
    <div class="timeline">
      <div class="timeline-item">
        <div class="exp-card">
          <div class="exp-header">
            <div>
              <div class="exp-title">Trainee Electrical Engineer</div>
              <div class="exp-company">Hayleys Fentons Limited — R&amp;D / QA / QC (MEP)</div>
            </div>
            <div class="exp-date">08/2025 – 02/2026</div>
          </div>
          <ul class="exp-bullets">
            <li>Coordinated multiple projects using ProofHub, improving workflow efficiency and project delivery</li>
            <li>Supported R&amp;D initiatives and process improvements, contributing to smoother operations</li>
            <li>Assisted in energy audits and operational data analysis to identify optimisation opportunities</li>
            <li>Conducted electrical testing, QA/QC, and safety compliance audits</li>
            <li>Developed electrical systems for buildings — power distribution, lighting, grounding, lightning protection</li>
          </ul>
        </div>
      </div>
      <div class="timeline-item">
        <div class="exp-card">
          <div class="exp-header">
            <div>
              <div class="exp-title">R&amp;D Engineer Intern</div>
              <div class="exp-company">OREL Corporation — R&amp;D Department</div>
            </div>
            <div class="exp-date">01/2025 – 07/2025</div>
          </div>
          <ul class="exp-bullets">
            <li>Assisted in circuit design and PCB layout using EAGLE and Altium Designer</li>
            <li>Participated in IoT-embedded based product development projects</li>
            <li>Supported 3D printing tasks for rapid prototyping and enclosure development</li>
            <li>Contributed to design validation and firmware debugging of electronic circuits</li>
          </ul>
        </div>
      </div>
      <div class="timeline-item">
        <div class="exp-card">
          <div class="exp-header">
            <div>
              <div class="exp-title">Engineer Internship</div>
              <div class="exp-company">Trade Promotor Limited — Schindler Elevators</div>
            </div>
            <div class="exp-date">10/2024 – 01/2025</div>
          </div>
          <ul class="exp-bullets">
            <li>Serviced and maintained Schindler lifts, troubleshooting and resolving breakdowns efficiently</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- EDUCATION -->
<section id="education">
  <div class="container">
    <div class="section-label"><h2>Education</h2></div>
    <div class="edu-grid">
      <div class="edu-card">
        <div class="edu-icon">&#127891;</div>
        <div class="edu-degree">BEng (Hons) Electronic &amp; Electrical Engineering</div>
        <div class="edu-school">Liverpool John Moores University, UK (via SLIIT City University)</div>
        <div class="edu-date">2024 – 2026 | Results Pending</div>
        <span class="edu-badge">&#127978; UK Degree</span>
      </div>
      <div class="edu-card">
        <div class="edu-icon">&#128220;</div>
        <div class="edu-degree">Pearson HND — Electrical &amp; Electronic Engineering</div>
        <div class="edu-school">Pearson UK — SLTMOBITEL Nebula Institute of Technology</div>
        <div class="edu-date">2022 – 2024 | Walisara, Sri Lanka</div>
        <span class="edu-badge">&#129352; Merit Grade</span>
      </div>
      <div class="edu-card">
        <div class="edu-icon">&#128295;</div>
        <div class="edu-degree">PLC Certification</div>
        <div class="edu-school">University of Moratuwa</div>
        <div class="edu-date">Moratuwa, Sri Lanka</div>
        <span class="edu-badge">&#9989; Certified</span>
      </div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="container">
    <div class="section-label"><h2>Projects</h2></div>
    <div class="projects-grid">
      <div class="project-card">
        <div class="project-year">2025 – 2026 | FINAL YEAR</div>
        <div class="project-title">IoT Smart Assistive Wheelchair with Cloud-Integrated Patient Telemetry &amp; Live GPS Tracking</div>
        <div class="project-desc">ESP32-powered wheelchair with automated obstacle avoidance, dual-mode control (Joystick/App), real-time GPS and health monitoring via Arduino IoT Cloud. Firmware integrates sensors and motor drivers, prioritising safety and independence.</div>
        <div class="project-techs">
          <span class="tag">ESP32</span><span class="tag">Arduino IoT Cloud</span><span class="tag">GPS</span><span class="tag">C/C++</span><span class="tag">IoT</span>
        </div>
      </div>
      <div class="project-card">
        <div class="project-year">2025 | GROUP PROJECT</div>
        <div class="project-title">Raspberry Pi Smart Home Automation &amp; Security System</div>
        <div class="project-desc">Collaborative smart home platform using Raspberry Pi for automated control and security monitoring. Integrated multiple sensors for real-time environmental management and alerts.</div>
        <div class="project-techs">
          <span class="tag">Raspberry Pi</span><span class="tag">Python</span><span class="tag">IoT</span><span class="tag">Security</span>
        </div>
      </div>
      <div class="project-card">
        <div class="project-year">11/2023 – 06/2024</div>
        <div class="project-title">Arduino-Based Automatic Drug Dispenser</div>
        <div class="project-desc">IoT-enabled automatic medication dispenser with scheduled dispensing, real-time notifications, and remote monitoring capabilities to support patient compliance.</div>
        <div class="project-techs">
          <span class="tag">Arduino</span><span class="tag">IoT</span><span class="tag">C++</span><span class="tag">Sensors</span>
        </div>
      </div>
      <div class="project-card">
        <div class="project-year">11/2021 – 06/2022</div>
        <div class="project-title">Efficiency Analysis: Standard Motor vs Variable Speed Drive</div>
        <div class="project-desc">Comparative efficiency analysis between standard induction motors and variable speed drive systems, including energy consumption profiling, data analysis, and performance benchmarking.</div>
        <div class="project-techs">
          <span class="tag">MATLAB</span><span class="tag">Data Analysis</span><span class="tag">Energy Audit</span><span class="tag">VSD</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="container">
    <div class="section-label"><h2>Technical Skills</h2></div>
    <div class="skills-grid">
      <div class="skill-card">
        <div class="skill-icon">&#128300;</div>
        <div class="skill-name">Embedded Systems</div>
        <div class="skill-tags"><span class="tag">STM32</span><span class="tag">ESP32</span><span class="tag">Arduino</span><span class="tag">RPi</span></div>
      </div>
      <div class="skill-card">
        <div class="skill-icon">&#128187;</div>
        <div class="skill-name">Programming</div>
        <div class="skill-tags"><span class="tag">C</span><span class="tag">Python</span><span class="tag">VHDL</span><span class="tag">MATLAB</span></div>
      </div>
      <div class="skill-card">
        <div class="skill-icon">&#9889;</div>
        <div class="skill-name">Circuit Design</div>
        <div class="skill-tags"><span class="tag">EAGLE</span><span class="tag">Altium</span><span class="tag">PCB</span></div>
      </div>
      <div class="skill-card">
        <div class="skill-icon">&#127981;</div>
        <div class="skill-name">Industrial</div>
        <div class="skill-tags"><span class="tag">PLC</span><span class="tag">LabVIEW</span><span class="tag">FPGA</span><span class="tag">SCADA</span></div>
      </div>
      <div class="skill-card">
        <div class="skill-icon">&#128225;</div>
        <div class="skill-name">IoT &amp; Cloud</div>
        <div class="skill-tags"><span class="tag">IoT</span><span class="tag">MQTT</span><span class="tag">Cloud</span><span class="tag">APIs</span></div>
      </div>
      <div class="skill-card">
        <div class="skill-icon">&#128202;</div>
        <div class="skill-name">QA/QC &amp; Analysis</div>
        <div class="skill-tags"><span class="tag">Energy Audit</span><span class="tag">Testing</span><span class="tag">Compliance</span></div>
      </div>
      <div class="skill-card">
        <div class="skill-icon">&#129302;</div>
        <div class="skill-name">AI / ML</div>
        <div class="skill-tags"><span class="tag">AI/ML Stage 1</span><span class="tag">Big Data</span><span class="tag">IoT-AI</span></div>
      </div>
      <div class="skill-card">
        <div class="skill-icon">&#128208;</div>
        <div class="skill-name">Simulation</div>
        <div class="skill-tags"><span class="tag">ModelSim</span><span class="tag">MATLAB</span><span class="tag">LabVIEW</span></div>
      </div>
    </div>
  </div>
</section>

<!-- GITHUB -->
<section id="github">
  <div class="container">
    <div class="section-label"><h2>GitHub</h2></div>
    <div class="github-section">
      <div class="github-header">
        <div class="github-logo">&#128025;</div>
        <div class="github-info">
          <h3>vimeshtharu</h3>
          <p>Electrical Engineer · IoT Builder · Vibe Coder</p>
          <a href="https://github.com/vimeshtharu" class="github-link" target="_blank">github.com/vimeshtharu &#8599;</a>
        </div>
      </div>
      <div class="github-stats">
        <div class="gh-stat"><div class="gh-stat-num">4+</div><div class="gh-stat-label">Repos</div></div>
        <div class="gh-stat"><div class="gh-stat-num">ESP32</div><div class="gh-stat-label">Main MCU</div></div>
        <div class="gh-stat"><div class="gh-stat-num">IoT</div><div class="gh-stat-label">Focus</div></div>
        <div class="gh-stat"><div class="gh-stat-num">&#127472;&#127473;</div><div class="gh-stat-label">Sri Lanka</div></div>
      </div>
      <div style="font-size:12px;color:var(--muted);margin-bottom:8px;letter-spacing:1px;text-transform:uppercase;">Contribution Activity</div>
      <div class="contrib-grid" id="contrib"></div>
      <div class="repo-cards">
        <div class="repo-card">
          <div class="repo-name">&#128230; smart-wheelchair-iot</div>
          <div class="repo-desc">ESP32 IoT wheelchair with GPS tracking, health telemetry and obstacle avoidance</div>
          <div class="repo-meta"><span class="repo-lang"><span class="lang-dot" style="background:#e34c26;"></span>C++</span><span class="repo-lang">&#11088; IoT</span></div>
        </div>
        <div class="repo-card">
          <div class="repo-name">&#128230; rpi-smart-home</div>
          <div class="repo-desc">Raspberry Pi home automation &amp; security system with sensor integration</div>
          <div class="repo-meta"><span class="repo-lang"><span class="lang-dot" style="background:#3572A5;"></span>Python</span><span class="repo-lang">&#11088; RPi</span></div>
        </div>
        <div class="repo-card">
          <div class="repo-name">&#128230; drug-dispenser-arduino</div>
          <div class="repo-desc">IoT-enabled automatic medication dispenser with scheduled alerts</div>
          <div class="repo-meta"><span class="repo-lang"><span class="lang-dot" style="background:#e34c26;"></span>C++</span><span class="repo-lang">&#11088; Arduino</span></div>
        </div>
        <div class="repo-card">
          <div class="repo-name">&#128230; vsd-efficiency-analysis</div>
          <div class="repo-desc">MATLAB analysis comparing standard motors vs variable speed drives</div>
          <div class="repo-meta"><span class="repo-lang"><span class="lang-dot" style="background:#e16737;"></span>MATLAB</span><span class="repo-lang">&#11088; EEE</span></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CERTIFICATIONS -->
<section id="certifications">
  <div class="container">
    <div class="section-label"><h2>Certifications</h2></div>
    <div class="certs-grid">
      <div class="cert-card"><div class="cert-icon">&#129302;</div><div><div class="cert-name">AI/ML Engineer — Stage 1</div><div class="cert-org">SLIIT</div></div></div>
      <div class="cert-card"><div class="cert-icon">&#128187;</div><div><div class="cert-name">Diploma in ICT</div><div class="cert-org">Institute of IT Education, Sri Lanka</div></div></div>
      <div class="cert-card"><div class="cert-icon">&#127885;</div><div><div class="cert-name">Leadership &amp; Management</div><div class="cert-org">Great Learning (eCertificate)</div></div></div>
      <div class="cert-card"><div class="cert-icon">&#128225;</div><div><div class="cert-name">AI &amp; Big Data in IoT</div><div class="cert-org">Great Learning (eCertificate)</div></div></div>
      <div class="cert-card"><div class="cert-icon">&#9881;</div><div><div class="cert-name">C++ Complete Training Course</div><div class="cert-org">eCertificate (2022)</div></div></div>
      <div class="cert-card"><div class="cert-icon">&#127981;</div><div><div class="cert-name">PLC Certification</div><div class="cert-org">University of Moratuwa</div></div></div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="container">
    <div class="section-label"><h2>Contact</h2></div>
    <div class="contact-grid">
      <div class="contact-card"><div class="contact-icon">&#128241;</div><div class="contact-type">Phone</div><div class="contact-val">(+94) 768 774 133</div></div>
      <div class="contact-card"><div class="contact-icon">&#9993;</div><div class="contact-type">Email</div><div class="contact-val">vimeshtharu@gmail.com</div></div>
      <div class="contact-card"><div class="contact-icon">&#128188;</div><div class="contact-type">LinkedIn</div><div class="contact-val" style="font-size:12px;">vimesh-tharushan-314413307</div></div>
      <div class="contact-card"><div class="contact-icon">&#127760;</div><div class="contact-type">Website</div><div class="contact-val">linktr.ee/vimeshtharu</div></div>
      <div class="contact-card"><div class="contact-icon">&#128205;</div><div class="contact-type">Location</div><div class="contact-val">Sri Lanka &#127472;&#127473; | Open to Relocation</div></div>
    </div>
  </div>
</section>

<footer>
  <div class="container">
    <p style="font-family:'Orbitron',sans-serif;font-size:14px;margin-bottom:8px;"><span>W.M Vimesh Tharushan Weerasinghe</span></p>
    <p>BEng (Hons) EEE · Embedded Systems · IoT · QA/QC · Industry 4.0</p>
    <p style="margin-top:8px;font-size:11px;">Negombo, Sri Lanka &nbsp;·&nbsp; Flexible for International Relocation</p>
  </div>
</footer>

<script>
const pc=document.getElementById('particles');
for(let i=0;i<30;i++){
  const p=document.createElement('div');
  p.className='particle';
  p.style.left=Math.random()*100+'%';
  p.style.animationDuration=(8+Math.random()*12)+'s';
  p.style.animationDelay=(Math.random()*10)+'s';
  p.style.width=p.style.height=(Math.random()>0.7?3:2)+'px';
  pc.appendChild(p);
}
const contrib=document.getElementById('contrib');
for(let i=0;i<364;i++){
  const c=document.createElement('div');
  const r=Math.random();
  c.className='contrib-cell '+(r<0.4?'':r<0.6?'l1':r<0.75?'l2':r<0.88?'l3':'l4');
  contrib.appendChild(c);
}
</script>
</body>
</html>
