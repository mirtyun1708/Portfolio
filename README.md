# Ex01 Portfolio
## Date:

## AIM
To create a Portfolio using HTML and CSS.

## ALGORITHM
### STEP 1
Create an HTML file (index.html)

### STEP 2
Create a CSS file (style.css)

### STEP 3
Include a navigation bar with links to different sections.

### STEP 4
Add structured sections for introduction, about, projects, and contact details.

### STEP 5
Define global styles for fonts, colors, and layout.

### STEP 6
Style the header, navigation bar, and sections.

### STEP 7
Use Flexbox or CSS Grid for layout design.

### STEP 8
Add hover effects and transitions for interactivity.

### STEP 9
Add Images and Media.

### STEP 10
Use optimized images for a professional look.

### STEP 11
Open the HTML file in a browser to check layout and functionality.

### STEP 12
Fix styling issues and refine content placement.

### STEP 13
Deploy the Portfolio.

### STEP 14
Upload to GitHub Pages for free hosting.

## PROGRAM
```

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mirtyunjay S — Software Developer </title>
<meta name="description" content="Mirtyunjay S — Computer Science Engineering student and aspiring software developer. Full-stack projects, ML work, and web development.">
<meta name="keywords" content="Mirtyunjay S, Software Developer, Full Stack Developer, Java Developer">
<meta name="author" content="Mirtyunjay S">

<!-- Open Graph -->
<meta property="og:title" content="Mirtyunjay S — Software Developer Portfolio">
<meta property="og:description" content="Building Modern Web Applications & Intelligent Software Solutions.">
<meta property="og:type" content="website">

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">

<style>
/* =========================================================
   Manikandan M — PORTFOLIO STYLESHEET
   Design tokens, base, components, animations, responsive
   ========================================================= */

/* ---------- 1. DESIGN TOKENS ---------- */
:root{
  /* Colors */
  --bg-primary:#0a0e1a;
  --bg-secondary:#0f1420;
  --bg-tertiary:#131a2b;
  --surface: rgba(255,255,255,0.04);
  --surface-hover: rgba(255,255,255,0.07);
  --border: rgba(255,255,255,0.08);
  --border-strong: rgba(255,255,255,0.16);

  --accent-blue:#4f7cff;
  --accent-purple:#8b5cf6;
  --accent-cyan:#22d3ee;
  --gradient-main: linear-gradient(135deg, var(--accent-blue), var(--accent-purple));
  --gradient-alt: linear-gradient(135deg, var(--accent-cyan), var(--accent-blue));

  --text-primary:#e8ecf5;
  --text-secondary:#9aa5c0;
  --text-muted:#6b7488;

  /* Typography */
  --font-display:'Space Grotesk', sans-serif;
  --font-body:'Inter', sans-serif;
  --font-mono:'JetBrains Mono', monospace;

  /* Layout */
  --max-width: 1180px;
  --radius-sm: 8px;
  --radius-md: 14px;
  --radius-lg: 22px;
  --nav-height: 76px;

  /* Motion */
  --ease: cubic-bezier(.22,1,.36,1);
  --t-fast: .25s;
  --t-med: .5s;
  --t-slow: .9s;
}

/* ---------- 2. RESET & BASE ---------- */
*,*::before,*::after{ box-sizing:border-box; margin:0; padding:0; }
html{ scroll-behavior:smooth; }
body{
  background:var(--bg-primary);
  color:var(--text-primary);
  font-family:var(--font-body);
  line-height:1.6;
  overflow-x:hidden;
  -webkit-font-smoothing:antialiased;
}
img{ max-width:100%; display:block; }
a{ color:inherit; text-decoration:none; }
ul{ list-style:none; }
button{ font-family:inherit; cursor:pointer; border:none; background:none; color:inherit; }
input,textarea{ font-family:inherit; }
:focus-visible{ outline:2px solid var(--accent-cyan); outline-offset:3px; border-radius:4px; }

.container{ max-width:var(--max-width); margin:0 auto; padding:0 24px; }

@media (prefers-reduced-motion: reduce){
  *{ animation-duration:0.01ms !important; animation-iteration-count:1 !important; transition-duration:0.01ms !important; scroll-behavior:auto !important; }
}

/* ---------- 3. BACKGROUND LAYERS ---------- */
#network-canvas{
  position:fixed; inset:0; z-index:-2; width:100%; height:100%;
  background:
    radial-gradient(ellipse 60% 50% at 20% 10%, rgba(79,124,255,0.12), transparent 60%),
    radial-gradient(ellipse 60% 50% at 85% 30%, rgba(139,92,246,0.10), transparent 60%),
    var(--bg-primary);
}
.grid-overlay{
  position:fixed; inset:0; z-index:-1; pointer-events:none;
  background-image:
    linear-gradient(rgba(255,255,255,0.025) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,0.025) 1px, transparent 1px);
  background-size:44px 44px;
  mask-image: radial-gradient(ellipse 70% 60% at 50% 20%, black 20%, transparent 75%);
}
.cursor-glow{
  position:fixed; top:0; left:0; width:420px; height:420px; z-index:-1;
  background: radial-gradient(circle, rgba(79,124,255,0.14), rgba(139,92,246,0.06) 40%, transparent 70%);
  border-radius:50%;
  transform:translate(-50%,-50%);
  pointer-events:none;
  transition: opacity .3s ease;
  will-change: transform;
}
@media (hover:none){ .cursor-glow{ display:none; } }

/* ---------- 4. LOADER ---------- */
.loader{
  position:fixed; inset:0; z-index:9999;
  background:var(--bg-primary);
  display:flex; flex-direction:column; align-items:center; justify-content:center; gap:22px;
  transition: opacity .6s var(--ease), visibility .6s var(--ease);
}
.loader.hidden{ opacity:0; visibility:hidden; pointer-events:none; }
.loader-inner{ font-family:var(--font-mono); font-size:2.4rem; font-weight:600; display:flex; gap:4px; }
.loader-bracket{ color:var(--accent-blue); animation: pulseFade 1.4s ease-in-out infinite; }
.loader-text{ background:var(--gradient-main); -webkit-background-clip:text; background-clip:text; color:transparent; }
.loader-bar{ width:180px; height:3px; background:var(--border); border-radius:4px; overflow:hidden; }
.loader-bar span{ display:block; height:100%; width:40%; background:var(--gradient-main); animation: loaderSlide 1.1s ease-in-out infinite; }
@keyframes loaderSlide{ 0%{ transform:translateX(-100%);} 50%{transform:translateX(120%);} 100%{transform:translateX(280%);} }
@keyframes pulseFade{ 0%,100%{opacity:1;} 50%{opacity:.3;} }

/* ---------- 5. NAVBAR ---------- */
.navbar{
  position:fixed; top:0; left:0; right:0; z-index:1000;
  height:var(--nav-height);
  display:flex; align-items:center;
  background: rgba(10,14,26,0.55);
  backdrop-filter: blur(16px) saturate(140%);
  -webkit-backdrop-filter: blur(16px) saturate(140%);
  border-bottom:1px solid transparent;
  transition: border-color var(--t-fast) var(--ease), background var(--t-fast) var(--ease);
}
.navbar.scrolled{ border-bottom-color: var(--border); background: rgba(10,14,26,0.8); }
.nav-container{
  width:100%; max-width:var(--max-width); margin:0 auto; padding:0 24px;
  display:flex; align-items:center; justify-content:space-between;
}
.logo{ font-family:var(--font-mono); font-weight:600; font-size:1.15rem; letter-spacing:-.02em; }
.logo-bracket{ color:var(--accent-purple); }
.logo .accent{ color:var(--accent-cyan); }

.nav-links{ display:flex; gap:2rem; }
.nav-link{
  position:relative; font-size:.92rem; color:var(--text-secondary); font-weight:500;
  padding:6px 2px; transition: color var(--t-fast) var(--ease);
}
.nav-link::after{
  content:''; position:absolute; left:0; bottom:-2px; width:0; height:2px;
  background:var(--gradient-main); transition: width var(--t-fast) var(--ease);
}
.nav-link:hover, .nav-link.active{ color:var(--text-primary); }
.nav-link:hover::after, .nav-link.active::after{ width:100%; }

.nav-toggle{ display:none; flex-direction:column; gap:5px; width:26px; z-index:1001; }
.nav-toggle span{ height:2px; width:100%; background:var(--text-primary); border-radius:2px; transition: all var(--t-fast) var(--ease); }
.nav-toggle.open span:nth-child(1){ transform: translateY(7px) rotate(45deg); }
.nav-toggle.open span:nth-child(2){ opacity:0; }
.nav-toggle.open span:nth-child(3){ transform: translateY(-7px) rotate(-45deg); }

/* ---------- 6. BUTTONS ---------- */
.btn{
  position:relative; overflow:hidden;
  display:inline-flex; align-items:center; justify-content:center; gap:8px;
  padding:14px 30px; border-radius:50px; font-weight:600; font-size:.95rem;
  transition: transform var(--t-fast) var(--ease), box-shadow var(--t-fast) var(--ease), background var(--t-fast) var(--ease);
  white-space:nowrap;
}
.btn-primary{ background:var(--gradient-main); color:#fff; box-shadow:0 8px 24px -8px rgba(79,124,255,0.55); }
.btn-primary:hover{ transform:translateY(-3px); box-shadow:0 14px 30px -8px rgba(79,124,255,0.7); }
.btn-outline{ border:1px solid var(--border-strong); color:var(--text-primary); background:var(--surface); }
.btn-outline:hover{ background:var(--surface-hover); transform:translateY(-3px); border-color: var(--accent-blue); }
.btn-sm{ padding:9px 18px; font-size:.82rem; }

.ripple::before{
  content:''; position:absolute; border-radius:50%; background:rgba(255,255,255,0.35);
  transform:translate(-50%,-50%) scale(0); width:10px; height:10px; pointer-events:none;
  opacity:0; left:var(--rx,50%); top:var(--ry,50%);
}
.ripple.rippling::before{ animation: rippleAnim .6s ease-out; }
@keyframes rippleAnim{ 0%{ transform:translate(-50%,-50%) scale(0); opacity:.6;} 100%{ transform:translate(-50%,-50%) scale(26); opacity:0;} }

/* ---------- 7. GLASSMORPHISM CARD ---------- */
.glass-card{
  background: var(--surface);
  border:1px solid var(--border);
  border-radius: var(--radius-md);
  backdrop-filter: blur(14px);
  -webkit-backdrop-filter: blur(14px);
  transition: transform var(--t-med) var(--ease), border-color var(--t-fast) var(--ease), box-shadow var(--t-med) var(--ease), background var(--t-fast) var(--ease);
}
.glass-card:hover{
  transform: translateY(-6px);
  border-color: var(--border-strong);
  background: var(--surface-hover);
  box-shadow: 0 20px 40px -20px rgba(79,124,255,0.35);
}

/* ---------- 8. TEXT HELPERS ---------- */
.gradient-text{
  background:var(--gradient-main); -webkit-background-clip:text; background-clip:text; color:transparent;
}
.section-eyebrow{
  font-family:var(--font-mono); font-size:.8rem; letter-spacing:.14em; text-transform:uppercase;
  color:var(--accent-cyan); margin-bottom:.6rem; display:block;
}
.section-title{ font-family:var(--font-display); font-size:clamp(2rem,4vw,2.8rem); font-weight:700; margin-bottom:3rem; letter-spacing:-.02em; }

/* ---------- 9. HERO ---------- */
.hero{
  min-height:100vh; display:flex; flex-direction:column; justify-content:center;
  padding: calc(var(--nav-height) + 40px) 24px 60px;
  position:relative;
}
.hero-container{
  max-width:var(--max-width); margin:0 auto; width:100%;
  display:grid; grid-template-columns: 1.15fr .85fr; gap:3rem; align-items:center;
}
.hero-eyebrow{
  display:inline-flex; align-items:center; gap:8px;
  font-family:var(--font-mono); font-size:.82rem; color:var(--accent-cyan);
  border:1px solid var(--border); padding:6px 14px; border-radius:50px; margin-bottom:1.6rem;
  background:var(--surface);
}
.dot{ width:7px; height:7px; border-radius:50%; background:var(--accent-cyan); animation: dotPulse 1.6s ease-in-out infinite; }
@keyframes dotPulse{ 0%,100%{ box-shadow:0 0 0 0 rgba(34,211,238,.5);} 50%{ box-shadow:0 0 0 6px rgba(34,211,238,0);} }

.hero-title{
  font-family:var(--font-display); font-weight:700; letter-spacing:-.03em;
  font-size:clamp(2.2rem, 5vw, 3.6rem); line-height:1.1; margin-bottom:.8rem;
}
.hero-role{
  font-family:var(--font-mono); font-size:clamp(1.1rem,2.4vw,1.5rem); color:var(--text-secondary);
  margin-bottom:1.2rem; min-height:2rem;
}
.hero-role #typed-text{ color:var(--accent-blue); }
.cursor-blink{ animation: blink 1s step-end infinite; color:var(--accent-purple); }
@keyframes blink{ 50%{ opacity:0; } }

.hero-tagline{ font-size:1.05rem; color:var(--text-secondary); max-width:520px; margin-bottom:.5rem; }
.hero-location{ color:var(--text-muted); font-size:.9rem; margin-bottom:2rem; }
.hero-buttons{ display:flex; gap:1rem; flex-wrap:wrap; margin-bottom:2rem; }

.hero-socials{ display:flex; gap:1rem; }
.social-icon{
  width:44px; height:44px; border-radius:50%; display:flex; align-items:center; justify-content:center;
  border:1px solid var(--border); background:var(--surface); color:var(--text-secondary);
  transition: all var(--t-fast) var(--ease);
}
.social-icon:hover{ color:#fff; border-color:var(--accent-blue); background:var(--gradient-main); transform:translateY(-4px); }
.float-icon{ animation: floatY 3.4s ease-in-out infinite; }
.float-icon:nth-child(2){ animation-delay:.3s; }
.float-icon:nth-child(3){ animation-delay:.6s; }
@keyframes floatY{ 0%,100%{ transform:translateY(0);} 50%{ transform:translateY(-7px);} }

/* Hero visual / profile */
.hero-visual{ display:flex; justify-content:center; }
.profile-frame{ position:relative; width:320px; height:320px; }
.profile-ring{
  position:absolute; inset:-16px; border-radius:50%;
  background:conic-gradient(from 0deg, var(--accent-blue), var(--accent-purple), var(--accent-cyan), var(--accent-blue));
  animation: spin 8s linear infinite;
  opacity:.6; filter: blur(1px);
}
.profile-ring::after{
  content:''; position:absolute; inset:10px; border-radius:50%; background:var(--bg-primary);
}
@keyframes spin{ to{ transform:rotate(360deg); } }
.profile-photo{
  position:absolute; inset:0; border-radius:50%; overflow:hidden;
  border:3px solid var(--bg-primary); box-shadow:0 20px 50px -12px rgba(79,124,255,.5);
}
.profile-photo img{ width:100%; height:100%; object-fit:cover; }
.badge{
  position:absolute; padding:8px 14px; border-radius:50px; font-size:.8rem; font-weight:600;
  background:var(--surface); border:1px solid var(--border-strong); backdrop-filter: blur(10px);
  animation: floatY 4s ease-in-out infinite;
}
.badge-1{ top:8%; left:-14%; animation-delay:.2s; }
.badge-2{ bottom:14%; right:-16%; animation-delay:.6s; }
.badge-3{ bottom:-4%; left:8%; animation-delay:1s; }

.scroll-indicator{
  position:absolute; bottom:24px; left:50%; transform:translateX(-50%);
  display:flex; flex-direction:column; align-items:center; gap:8px;
  color:var(--text-muted); font-size:.75rem; letter-spacing:.08em; text-transform:uppercase;
}
.scroll-mouse{ width:24px; height:38px; border:2px solid var(--border-strong); border-radius:14px; position:relative; }
.scroll-wheel{ position:absolute; top:6px; left:50%; width:4px; height:8px; background:var(--accent-blue); border-radius:2px; transform:translateX(-50%); animation: scrollWheel 1.6s ease-in-out infinite; }
@keyframes scrollWheel{ 0%{ opacity:1; top:6px;} 100%{ opacity:0; top:20px;} }

/* ---------- 10. SECTION WRAPPERS ---------- */
.section{ padding:120px 0; position:relative; }
.section-alt{ background: linear-gradient(180deg, transparent, rgba(255,255,255,0.015), transparent); }

/* ---------- 11. ABOUT ---------- */
.about-grid{ display:grid; grid-template-columns:repeat(2,1fr); gap:1.5rem; margin-bottom:4rem; }
.about-card{ padding:2rem; }
.about-card h3{ font-family:var(--font-display); color:var(--accent-cyan); margin-bottom:.8rem; font-size:1.15rem; }
.about-card p{ color:var(--text-secondary); font-size:.96rem; }

.stats-grid{ display:grid; grid-template-columns:repeat(4,1fr); gap:1.5rem; }
.stat-card{
  text-align:center; padding:2rem 1rem; border-radius:var(--radius-md);
  background:var(--surface); border:1px solid var(--border);
}
.stat-number{ font-family:var(--font-display); font-size:2.6rem; font-weight:700; background:var(--gradient-main); -webkit-background-clip:text; background-clip:text; color:transparent; }
.stat-plus{ font-size:1.6rem; font-weight:700; color:var(--accent-purple); }
.stat-label{ color:var(--text-secondary); font-size:.88rem; margin-top:.4rem; }

/* ---------- 12. SKILLS ---------- */
.skills-grid{ display:grid; grid-template-columns:repeat(2,1fr); gap:1.5rem; }
.skill-category{ padding:2rem; }
.skill-category h3{ font-family:var(--font-display); margin-bottom:1.4rem; font-size:1.2rem; }
.skill-bar{ margin-bottom:1.1rem; }
.skill-bar:last-child{ margin-bottom:0; }
.skill-info{ display:flex; justify-content:space-between; font-size:.85rem; color:var(--text-secondary); margin-bottom:6px; }
.bar-track{ height:8px; background:var(--bg-tertiary); border-radius:6px; overflow:hidden; }
.bar-fill{ height:100%; width:0%; border-radius:6px; background:var(--gradient-main); transition: width 1.4s var(--ease); position:relative; }
.bar-fill::after{ content:''; position:absolute; inset:0; background:linear-gradient(90deg, transparent, rgba(255,255,255,.35), transparent); animation: shimmer 2.4s ease-in-out infinite; }
@keyframes shimmer{ 0%{ transform:translateX(-100%);} 100%{ transform:translateX(200%);} }

.tag-cloud{ display:flex; flex-wrap:wrap; gap:.7rem; }
.tag{
  padding:9px 16px; border-radius:50px; font-size:.85rem; border:1px solid var(--border-strong);
  background:var(--bg-tertiary); color:var(--text-secondary); transition: all var(--t-fast) var(--ease);
}
.tag:hover{ color:#fff; background:var(--gradient-alt); border-color:transparent; transform:translateY(-3px); }

/* ---------- 13. PROJECTS ---------- */
.projects-grid{ display:grid; grid-template-columns:repeat(3,1fr); gap:1.8rem; }
.project-card{ overflow:hidden; display:flex; flex-direction:column; }
.project-image{ aspect-ratio:16/10; overflow:hidden; }
.project-image img{ width:100%; height:100%; object-fit:cover; transition: transform .6s var(--ease); }
.project-card:hover .project-image img{ transform:scale(1.08); }
.project-body{ padding:1.6rem; display:flex; flex-direction:column; gap:.8rem; flex:1; }
.project-body h3{ font-family:var(--font-display); font-size:1.15rem; }
.project-body p{ color:var(--text-secondary); font-size:.9rem; flex:1; }
.tech-tags{ display:flex; flex-wrap:wrap; gap:.5rem; }
.tech-tags span{ font-family:var(--font-mono); font-size:.72rem; padding:4px 10px; border-radius:6px; background:var(--bg-tertiary); color:var(--accent-cyan); }
.project-links{ display:flex; gap:.8rem; margin-top:.4rem; }

/* ---------- 14. EXPERIENCE ---------- */
.experience-grid{ display:grid; grid-template-columns:repeat(3,1fr); gap:1.6rem; }
.exp-card{ padding:2rem; text-align:center; }
.exp-icon{ font-size:2.2rem; margin-bottom:1rem; }
.exp-card h3{ font-family:var(--font-display); margin-bottom:.6rem; }
.exp-placeholder{ color:var(--text-secondary); font-size:.88rem; }

/* ---------- 15. EDUCATION TIMELINE ---------- */
.timeline{ position:relative; max-width:800px; margin:0 auto; }
.timeline::before{
  content:''; position:absolute; left:50%; top:0; bottom:0; width:2px;
  background:linear-gradient(var(--accent-blue), var(--accent-purple)); transform:translateX(-50%);
}
.timeline-item{ position:relative; width:50%; padding:0 3rem 3rem; }
.timeline-item:nth-child(odd){ left:0; text-align:right; }
.timeline-item:nth-child(even){ left:50%; text-align:left; }
.timeline-dot{
  position:absolute; top:6px; width:16px; height:16px; border-radius:50%;
  background:var(--gradient-main); box-shadow:0 0 0 4px var(--bg-primary), 0 0 0 5px var(--border-strong);
}
.timeline-item:nth-child(odd) .timeline-dot{ right:-8px; }
.timeline-item:nth-child(even) .timeline-dot{ left:-8px; }
.timeline-content{ padding:1.5rem; display:inline-block; text-align:left; width:100%; }
.timeline-year{ font-family:var(--font-mono); font-size:.75rem; color:var(--accent-cyan); text-transform:uppercase; letter-spacing:.08em; }
.timeline-content h3{ font-family:var(--font-display); margin:.4rem 0; font-size:1.1rem; }
.timeline-content p{ color:var(--text-secondary); font-size:.9rem; }

/* ---------- 16. CERTIFICATES SLIDER ---------- */
.cert-slider-wrap{ display:flex; align-items:center; gap:1rem; }
.cert-slider{ display:flex; gap:1.5rem; overflow-x:auto; scroll-behavior:smooth; padding:.5rem; scrollbar-width:none; }
.cert-slider::-webkit-scrollbar{ display:none; }
.cert-card{ min-width:220px; padding:2rem 1.5rem; text-align:center; flex-shrink:0; }
.cert-logo{ font-size:2.4rem; margin-bottom:.8rem; }
.cert-card h3{ font-family:var(--font-display); margin-bottom:.4rem; font-size:1.05rem; }
.cert-card p{ color:var(--text-muted); font-size:.82rem; }
.cert-arrow{
  flex-shrink:0; width:44px; height:44px; border-radius:50%; border:1px solid var(--border-strong);
  background:var(--surface); color:var(--text-primary); display:flex; align-items:center; justify-content:center;
  transition: all var(--t-fast) var(--ease);
}
.cert-arrow:hover{ background:var(--gradient-main); border-color:transparent; }

/* ---------- 17. RESUME ---------- */
.resume-card{
  display:flex; align-items:center; justify-content:space-between; gap:2rem; flex-wrap:wrap;
  padding:3rem; text-align:left;
}
.resume-card p{ color:var(--text-secondary); margin-top:.4rem; }

/* ---------- 18. CONTACT ---------- */
.contact-grid{ display:grid; grid-template-columns:1.2fr .8fr; gap:2rem; }
.contact-form-card{ padding:2.4rem; }
.form-group{ position:relative; margin-bottom:1.6rem; }
.form-group input, .form-group textarea{
  width:100%; background:var(--bg-tertiary); border:1px solid var(--border); border-radius:var(--radius-sm);
  padding:16px 14px 8px; color:var(--text-primary); font-size:.95rem; resize:vertical;
  transition: border-color var(--t-fast) var(--ease);
}
.form-group textarea{ padding-top:20px; }
.form-group input:focus, .form-group textarea:focus{ border-color:var(--accent-blue); outline:none; }
.form-group label{
  position:absolute; left:14px; top:14px; color:var(--text-muted); font-size:.95rem; pointer-events:none;
  transition: all var(--t-fast) var(--ease);
}
.form-group input:focus + label,
.form-group input:not(:placeholder-shown) + label,
.form-group input:valid + label,
.form-group textarea:focus + label,
.form-group textarea:valid + label{
  top:5px; font-size:.7rem; color:var(--accent-cyan);
}
.form-status{ margin-top:1rem; font-size:.88rem; color:var(--accent-cyan); min-height:1.2em; }

.contact-info{ display:flex; flex-direction:column; gap:1rem; }
.contact-item{ display:flex; align-items:center; gap:1rem; padding:1.2rem 1.4rem; }
.contact-icon{ font-size:1.4rem; }
.contact-item h4{ font-family:var(--font-display); font-size:.95rem; margin-bottom:2px; }
.contact-item p{ color:var(--text-secondary); font-size:.85rem; }
.contact-item p a:hover{ color:var(--accent-cyan); }
.map-placeholder{
  padding:2.4rem 1rem; text-align:center; color:var(--text-muted); font-size:.9rem;
  border-style:dashed;
}

/* ---------- 19. FOOTER ---------- */
.footer{ padding:3rem 0; border-top:1px solid var(--border); text-align:center; }
.footer-container{ display:flex; flex-direction:column; align-items:center; gap:1rem; }
.footer-socials{ display:flex; gap:1.6rem; }
.footer-socials a{ color:var(--text-secondary); font-size:.88rem; transition: color var(--t-fast); }
.footer-socials a:hover{ color:var(--accent-cyan); }
.footer-copy, .footer-made{ color:var(--text-muted); font-size:.82rem; }
.heart{ display:inline-block; animation: heartbeat 1.4s ease-in-out infinite; }
@keyframes heartbeat{ 0%,100%{ transform:scale(1);} 50%{ transform:scale(1.25);} }

/* ---------- 20. BACK TO TOP ---------- */
.back-to-top{
  position:fixed; bottom:28px; right:28px; width:48px; height:48px; border-radius:50%;
  background:var(--gradient-main); color:#fff; display:flex; align-items:center; justify-content:center;
  box-shadow:0 10px 24px -8px rgba(79,124,255,0.6);
  opacity:0; visibility:hidden; transform:translateY(16px);
  transition: all var(--t-fast) var(--ease); z-index:900;
}
.back-to-top.show{ opacity:1; visibility:visible; transform:translateY(0); }
.back-to-top:hover{ transform:translateY(-4px); }

/* ---------- 21. SCROLL REVEAL ---------- */
.reveal-up, .reveal-left, .reveal-right{ opacity:0; transition: opacity .8s var(--ease), transform .8s var(--ease); }
.reveal-up{ transform:translateY(36px); }
.reveal-left{ transform:translateX(-40px); }
.reveal-right{ transform:translateX(40px); }
.reveal-up.in-view, .reveal-left.in-view, .reveal-right.in-view{ opacity:1; transform:translate(0,0); }

/* Stagger children of grids */
.about-grid .reveal-up:nth-child(2){ transition-delay:.08s; }
.about-grid .reveal-up:nth-child(3){ transition-delay:.16s; }
.skills-grid .skill-category:nth-child(2){ transition-delay:.08s; }
.skills-grid .skill-category:nth-child(3){ transition-delay:.16s; }
.skills-grid .skill-category:nth-child(4){ transition-delay:.24s; }
.projects-grid .project-card:nth-child(2){ transition-delay:.1s; }
.projects-grid .project-card:nth-child(3){ transition-delay:.2s; }
.experience-grid .exp-card:nth-child(2){ transition-delay:.1s; }
.experience-grid .exp-card:nth-child(3){ transition-delay:.2s; }

/* ---------- 22. RESPONSIVE ---------- */
@media (max-width: 1024px){
  .hero-container{ grid-template-columns:1fr; text-align:center; }
  .hero-eyebrow{ margin-inline:auto; }
  .hero-buttons, .hero-socials{ justify-content:center; }
  .hero-visual{ order:-1; margin-bottom:1rem; }
  .profile-frame{ width:240px; height:240px; }
  .about-grid, .skills-grid{ grid-template-columns:1fr; }
  .projects-grid{ grid-template-columns:repeat(2,1fr); }
  .contact-grid{ grid-template-columns:1fr; }
}

@media (max-width: 860px){
  .nav-links{
    position:fixed; top:var(--nav-height); left:0; right:0; bottom:0;
    flex-direction:column; gap:0; background:rgba(10,14,26,0.98); backdrop-filter:blur(20px);
    padding:2rem; transform:translateX(100%); transition: transform var(--t-med) var(--ease);
  }
  .nav-links.open{ transform:translateX(0); }
  .nav-links li{ width:100%; border-bottom:1px solid var(--border); }
  .nav-links a{ display:block; padding:1rem 0; font-size:1.05rem; }
  .nav-toggle{ display:flex; }
  .stats-grid{ grid-template-columns:repeat(2,1fr); }
  .projects-grid{ grid-template-columns:1fr; }
  .experience-grid{ grid-template-columns:1fr; }
  .timeline::before{ left:20px; }
  .timeline-item, .timeline-item:nth-child(odd), .timeline-item:nth-child(even){
    width:100%; left:0; text-align:left; padding:0 0 2.5rem 3.2rem;
  }
  .timeline-item:nth-child(odd) .timeline-dot, .timeline-item:nth-child(even) .timeline-dot{ left:12px; right:auto; }
  .resume-card{ flex-direction:column; text-align:center; }
}

@media (max-width: 560px){
  .hero-buttons{ flex-direction:column; width:100%; }
  .hero-buttons .btn{ width:100%; }
  .badge{ display:none; }
  .section{ padding:80px 0; }
  .stats-grid{ grid-template-columns:1fr 1fr; }
  .cert-card{ min-width:170px; }
}

</style>
</head>
<body>

<!-- ================= LOADER ================= -->
<div class="loader" id="loader" aria-hidden="true">
  <div class="loader-inner">
    <span class="loader-bracket">&lt;</span>
    <span class="loader-text">NS</span>
    <span class="loader-bracket">/&gt;</span>
  </div>
  <div class="loader-bar"><span></span></div>
</div>

<!-- ================= BACKGROUND LAYERS ================= -->
<canvas id="network-canvas" aria-hidden="true"></canvas>
<div class="cursor-glow" id="cursorGlow" aria-hidden="true"></div>
<div class="grid-overlay" aria-hidden="true"></div>

<!-- ================= NAVBAR ================= -->
<header class="navbar" id="navbar">
  <nav class="nav-container">
    <a href="#home" class="logo">
      <span class="logo-bracket">&lt;</span>Mirtyunjay S<span class="accent">.</span>dev<span class="logo-bracket">/&gt;</span>
    </a>

    <ul class="nav-links" id="navLinks">
      <li><a href="#home" class="nav-link active" data-section="home">Home</a></li>
      <li><a href="#about" class="nav-link" data-section="about">About</a></li>
      <li><a href="#skills" class="nav-link" data-section="skills">Skills</a></li>
      <li><a href="#projects" class="nav-link" data-section="projects">Projects</a></li>
      <li><a href="#experience" class="nav-link" data-section="experience">Experience</a></li>
      <li><a href="#education" class="nav-link" data-section="education">Education</a></li>
      <li><a href="#certificates" class="nav-link" data-section="certificates">Certificates</a></li>
      <li><a href="#resume" class="nav-link" data-section="resume">Resume</a></li>
      <li><a href="#contact" class="nav-link" data-section="contact">Contact</a></li>
    </ul>

    <button class="nav-toggle" id="navToggle" aria-label="Toggle navigation menu" aria-expanded="false">
      <span></span><span></span><span></span>
    </button>
  </nav>
</header>

<main id="home">

  <!-- ================= HERO ================= -->
  <section class="hero" id="hero">
    <div class="hero-container">

      <div class="hero-text reveal-left">
        <p class="hero-eyebrow"><span class="dot"></span> Available for opportunities</p>
        <h1 class="hero-title">
          Hi, I'm <span class="gradient-text">Mirtyunjay S</span>
        </h1>
        <h2 class="hero-role">
          <span id="typed-text"></span><span class="cursor-blink">|</span>
        </h2>
        <p class="hero-tagline">Building Modern Web Applications &amp; Intelligent Software Solutions.</p>
        <p class="hero-location">📍 Thiruvallur, Tamil Nadu, India</p>

        <div class="hero-buttons">
          <a href="assets/Mirtyunjay S Resume.pdf" class="btn btn-primary ripple" download>
            <span>Download Resume</span>
          </a>
          <a href="#contact" class="btn btn-outline ripple">
            <span>Contact Me</span>
          </a>
        </div>

        <div class="hero-socials">
          <a href="https://github.com/" target="https://github.com/mirtyun1708" rel="noopener" class="social-icon float-icon" aria-label="GitHub">
            <svg viewBox="0 0 24 24" width="22" height="22"><path fill="currentColor" d="M12 .5C5.73.5.98 5.24.98 11.5c0 4.98 3.23 9.2 7.71 10.7.56.1.77-.24.77-.54 0-.27-.01-1.15-.02-2.09-3.14.68-3.8-1.34-3.8-1.34-.51-1.3-1.25-1.65-1.25-1.65-1.02-.7.08-.69.08-.69 1.13.08 1.72 1.16 1.72 1.16 1 1.72 2.63 1.22 3.27.94.1-.73.4-1.22.72-1.5-2.51-.29-5.15-1.26-5.15-5.6 0-1.24.44-2.25 1.16-3.04-.12-.29-.5-1.45.11-3.02 0 0 .95-.3 3.11 1.16a10.8 10.8 0 0 1 5.66 0c2.16-1.46 3.11-1.16 3.11-1.16.61 1.57.23 2.73.11 3.02.72.79 1.16 1.8 1.16 3.04 0 4.35-2.65 5.31-5.17 5.59.41.35.77 1.04.77 2.11 0 1.53-.01 2.75-.01 3.13 0 .3.2.65.78.54A10.52 10.52 0 0 0 23.02 11.5C23.02 5.24 18.27.5 12 .5Z"/></svg>
          </a>
          <a href="https://linkedin.com/" target="https://www.linkedin.com/in/mrityunjay-s-65b448371/" rel="noopener" class="social-icon float-icon" aria-label="LinkedIn">
            <svg viewBox="0 0 24 24" width="22" height="22"><path fill="currentColor" d="M20.45 20.45h-3.55v-5.57c0-1.33-.02-3.04-1.85-3.04-1.86 0-2.14 1.45-2.14 2.94v5.67H9.36V9h3.41v1.56h.05c.47-.9 1.63-1.85 3.36-1.85 3.6 0 4.27 2.37 4.27 5.45v6.29ZM5.34 7.43a2.06 2.06 0 1 1 0-4.12 2.06 2.06 0 0 1 0 4.12ZM7.12 20.45H3.56V9h3.56v11.45ZM22.22 0H1.77C.8 0 0 .78 0 1.75v20.5C0 23.22.8 24 1.77 24h20.45c.98 0 1.78-.78 1.78-1.75V1.75C24 .78 23.2 0 22.22 0Z"/></svg>
          </a>
          <a href="sundarrajmani81@gmail.com@gmail.com" class="social-icon float-icon" aria-label="Email">
            <svg viewBox="0 0 24 24" width="22" height="22"><path fill="currentColor" d="M2 4h20a1 1 0 0 1 1 1v14a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V5a1 1 0 0 1 1-1Zm19.4 2.1-9.4 7.2L2.6 6.1V6l9.4 7.2L21.4 6v.1Z"/></svg>
          </a>
        </div>
      </div>

      <div class="hero-visual reveal-right">
        <div class="profile-frame">
          <div class="profile-ring"></div>
          <div class="profile-photo">
            <img src="c:\Users\admin\Downloads\Image_Editor.png" alt="Profile Photo of Mirtyunjay S" />
          </div>
          <div class="badge badge-1">☕ Java</div>
          <div class="badge badge-2">⚛ React</div>
          <div class="badge badge-3">🐍 Python</div>
        </div>
      </div>
    </div>

    <a href="#about" class="scroll-indicator" aria-label="Scroll to About section">
      <span class="scroll-mouse"><span class="scroll-wheel"></span></span>
      <span class="scroll-label">Scroll</span>
    </a>
  </section>

  <!-- ================= ABOUT ================= -->
  <section class="section" id="about">
    <div class="container">
      <p class="section-eyebrow reveal-up">Get to know me</p>
      <h2 class="section-title reveal-up">About <span class="gradient-text">Me</span></h2>

      <div class="about-grid">
        <div class="glass-card about-card reveal-left">
          <h3>Who I Am</h3>
          <p>I am a Computer Science Engineering student passionate about software development and problem-solving. I enjoy building responsive websites, full-stack web applications, and continuously learning modern technologies.</p>
        </div>
        <div class="glass-card about-card reveal-up">
          <h3>My Passion</h3>
          <p>Turning ideas into working software — from clean interfaces to well-structured logic — and understanding how every layer of an application fits together.</p>
        </div>
        <div class="glass-card about-card reveal-up">
          <h3>Career Objective</h3>
          <p>My goal is to become a software engineer where I can build impactful products and continuously improve my skills alongside talented teams.</p>
        </div>
        <div class="glass-card about-card reveal-right">
          <h3>What Motivates Me</h3>
          <p>The moment a piece of code finally works, and the satisfaction of solving a problem that seemed impossible an hour before — that's what keeps me building.</p>
        </div>
      </div>

      <div class="stats-grid reveal-up">
        <div class="stat-card">
          <span class="stat-number" data-count="2">0</span><span class="stat-plus">+</span>
          <p class="stat-label">Projects Completed</p>
        </div>
        <div class="stat-card">
          <span class="stat-number" data-count="15">0</span><span class="stat-plus">+</span>
          <p class="stat-label">Certificates Earned</p>
        </div>
        <div class="stat-card">
          <span class="stat-number" data-count="20">0</span><span class="stat-plus">+</span>
          <p class="stat-label">Technologies Learned</p>
        </div>
        <div class="stat-card">
          <span class="stat-number" data-count="200">0</span><span class="stat-plus">+</span>
          <p class="stat-label">Coding Hours</p>
        </div>
      </div>
    </div>
  </section>

  <!-- ================= SKILLS ================= -->
  <section class="section section-alt" id="skills">
    <div class="container">
      <p class="section-eyebrow reveal-up">What I work with</p>
      <h2 class="section-title reveal-up">My <span class="gradient-text">Skills</span></h2>

      <div class="skills-grid">
        <div class="glass-card skill-category reveal-up">
          <h3>Languages</h3>
          <div class="skill-bar"><div class="skill-info"><span>Java</span><span>85%</span></div><div class="bar-track"><div class="bar-fill" data-width="85"></div></div></div>
          <div class="skill-bar"><div class="skill-info"><span>Python</span><span>80%</span></div><div class="bar-track"><div class="bar-fill" data-width="80"></div></div></div>
          <div class="skill-bar"><div class="skill-info"><span>JavaScript</span><span>78%</span></div><div class="bar-track"><div class="bar-fill" data-width="78"></div></div></div>
          <div class="skill-bar"><div class="skill-info"><span>SQL</span><span>75%</span></div><div class="bar-track"><div class="bar-fill" data-width="75"></div></div></div>
          <div class="skill-bar"><div class="skill-info"><span>HTML</span><span>92%</span></div><div class="bar-track"><div class="bar-fill" data-width="92"></div></div></div>
          <div class="skill-bar"><div class="skill-info"><span>CSS</span><span>88%</span></div><div class="bar-track"><div class="bar-fill" data-width="88"></div></div></div>
        </div>

        <div class="glass-card skill-category reveal-up">
          <h3>Frameworks</h3>
          <div class="skill-bar"><div class="skill-info"><span>React</span><span>75%</span></div><div class="bar-track"><div class="bar-fill" data-width="75"></div></div></div>
          <div class="skill-bar"><div class="skill-info"><span>Node.js</span><span>72%</span></div><div class="bar-track"><div class="bar-fill" data-width="72"></div></div></div>
          <div class="skill-bar"><div class="skill-info"><span>Express.js</span><span>70%</span></div><div class="bar-track"><div class="bar-fill" data-width="70"></div></div></div>
          <div class="skill-bar"><div class="skill-info"><span>Django</span><span>60%</span></div><div class="bar-track"><div class="bar-fill" data-width="60"></div></div></div>
        </div>

        <div class="glass-card skill-category reveal-up">
          <h3>Tools</h3>
          <div class="skill-bar"><div class="skill-info"><span>Git</span><span>85%</span></div><div class="bar-track"><div class="bar-fill" data-width="85"></div></div></div>
          <div class="skill-bar"><div class="skill-info"><span>GitHub</span><span>85%</span></div><div class="bar-track"><div class="bar-fill" data-width="85"></div></div></div>
          <div class="skill-bar"><div class="skill-info"><span>VS Code</span><span>95%</span></div><div class="bar-track"><div class="bar-fill" data-width="95"></div></div></div>
          <div class="skill-bar"><div class="skill-info"><span>MySQL</span><span>78%</span></div><div class="bar-track"><div class="bar-fill" data-width="78"></div></div></div>
          <div class="skill-bar"><div class="skill-info"><span>MongoDB</span><span>68%</span></div><div class="bar-track"><div class="bar-fill" data-width="68"></div></div></div>
          <div class="skill-bar"><div class="skill-info"><span>Vercel</span><span>80%</span></div><div class="bar-track"><div class="bar-fill" data-width="80"></div></div></div>
        </div>

        <div class="glass-card skill-category reveal-up">
          <h3>Other Skills</h3>
          <div class="tag-cloud">
            <span class="tag">Problem Solving</span>
            <span class="tag">Data Structures</span>
            <span class="tag">Algorithms</span>
            <span class="tag">REST APIs</span>
            <span class="tag">Responsive Design</span>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ================= PROJECTS ================= -->
  <section class="section" id="projects">
    <div class="container">
      <p class="section-eyebrow reveal-up">Selected work</p>
      <h2 class="section-title reveal-up">My <span class="gradient-text">Projects</span></h2>

      <div class="projects-grid">

        <article class="project-card glass-card reveal-up">
          <div class="project-image">
            <img src="c:\Users\nithi\OneDrive\Pictures\Screenshots\Screenshot 2026-07-18 135456.png" alt="AVS Flour & Rice Mill Website project preview" loading="lazy">
          </div>
          <div class="project-body">
            <h3>AVS Flour &amp; Rice Mill Website</h3>
            <p>A modern, responsive business website featuring an image gallery and integrated Google Maps for easy customer navigation to the mill.</p>
            <div class="tech-tags">
              <span>HTML</span><span>CSS</span><span>JavaScript</span><span>Google Maps API</span>
            </div>
            <div class="project-links">
              <a href="#" class="btn btn-sm btn-outline ripple">GitHub</a>
              <a href="#" class="btn btn-sm btn-primary ripple">Live Demo</a>
            </div>
          </div>
        </article>

        <article class="project-card glass-card reveal-up">
          <div class="project-image">
            <img src="c:\Users\nithi\OneDrive\Pictures\Screenshots\Screenshot 2026-07-18 140203.png">
          </div>
          <div class="project-body">
            <h3>Brain Tumor Segmentation using ML</h3>
            <p>A medical AI project applying image processing and machine learning techniques to segment and identify tumor regions in brain MRI scans.</p>
            <div class="tech-tags">
              <span>Python</span><span>Machine Learning</span><span>Image Processing</span><span>Medical AI</span>
            </div>
            <div class="project-links">
              <a href="#" class="btn btn-sm btn-outline ripple">GitHub</a>
              <a href="#" class="btn btn-sm btn-primary ripple">Live Demo</a>
            </div>
          </div>
        </article>

        <article class="project-card glass-card reveal-up">
          <div class="project-image">
            <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA2MDAgMzQwIj4KICA8ZGVmcz4KICAgIDxsaW5lYXJHcmFkaWVudCBpZD0iYyIgeDE9IjAiIHkxPSIwIiB4Mj0iMSIgeTI9IjEiPgogICAgICA8c3RvcCBvZmZzZXQ9IjAlIiBzdG9wLWNvbG9yPSIjNGY3Y2ZmIi8+PHN0b3Agb2Zmc2V0PSIxMDAlIiBzdG9wLWNvbG9yPSIjOGI1Y2Y2Ii8+CiAgICA8L2xpbmVhckdyYWRpZW50PgogIDwvZGVmcz4KICA8cmVjdCB3aWR0aD0iNjAwIiBoZWlnaHQ9IjM0MCIgZmlsbD0iIzBmMTQyMCIvPgogIDxyZWN0IHg9IjQwIiB5PSI0MCIgd2lkdGg9IjUyMCIgaGVpZ2h0PSIyNjAiIHJ4PSIxMiIgZmlsbD0iI2ZmZmZmZiIgb3BhY2l0eT0iMC4wNSIvPgogIDxjaXJjbGUgY3g9IjEyMCIgY3k9IjEwMCIgcj0iMjQiIGZpbGw9InVybCgjYykiIG9wYWNpdHk9IjAuNyIvPgogIDxyZWN0IHg9IjE2MCIgeT0iODgiIHdpZHRoPSIxNjAiIGhlaWdodD0iMTAiIHJ4PSI0IiBmaWxsPSIjZmZmZmZmIiBvcGFjaXR5PSIwLjIiLz4KICA8cmVjdCB4PSIxNjAiIHk9IjEwNiIgd2lkdGg9IjEwMCIgaGVpZ2h0PSI4IiByeD0iNCIgZmlsbD0iI2ZmZmZmZiIgb3BhY2l0eT0iMC4xMiIvPgogIDxyZWN0IHg9IjgwIiB5PSIxNjAiIHdpZHRoPSI0NDAiIGhlaWdodD0iOCIgcng9IjQiIGZpbGw9IiNmZmZmZmYiIG9wYWNpdHk9IjAuMSIvPgogIDxyZWN0IHg9IjgwIiB5PSIxODAiIHdpZHRoPSIzODAiIGhlaWdodD0iOCIgcng9IjQiIGZpbGw9IiNmZmZmZmYiIG9wYWNpdHk9IjAuMDgiLz4KICA8dGV4dCB4PSIzMDAiIHk9IjMxMCIgdGV4dC1hbmNob3I9Im1pZGRsZSIgZm9udC1mYW1pbHk9Im1vbm9zcGFjZSIgZm9udC1zaXplPSIxNiIgZmlsbD0iIzlhYTVjMCI+U3R1ZGVudCBQb3J0Zm9saW8gV2Vic2l0ZTwvdGV4dD4KPC9zdmc+Cg==" alt="Student portfolio website preview" loading="lazy">
          </div>
          <div class="project-body">
            <h3>Student Portfolio Website</h3>
            <p>A fully responsive personal portfolio built to showcase academic projects, skills, and achievements with clean, accessible design.</p>
            <div class="tech-tags">
              <span>HTML</span><span>CSS</span><span>JavaScript</span>
            </div>
            <div class="project-links">
              <a href="#" class="btn btn-sm btn-outline ripple">GitHub</a>
              <a href="#" class="btn btn-sm btn-primary ripple">Live Demo</a>
            </div>
          </div>
        </article>

      </div>
    </div>
  </section>

  <!-- ================= EXPERIENCE ================= -->
  <section class="section section-alt" id="experience">
    <div class="container">
      <p class="section-eyebrow reveal-up">Where I've contributed</p>
      <h2 class="section-title reveal-up">Experience</h2>

      <div class="experience-grid">
        <div class="glass-card exp-card reveal-up">
          <div class="exp-icon">💼</div>
          <h3>Internships</h3>
          <p class="exp-placeholder">Details to be added — currently seeking internship opportunities in software development.</p>
        </div>
        <div class="glass-card exp-card reveal-up">
          <div class="exp-icon">🧑💻</div>
          <h3>Freelance Work</h3>
          <p class="exp-placeholder">Details to be added — open to freelance web development projects.</p>
        </div>
        <div class="glass-card exp-card reveal-up">
          <div class="exp-icon">🌐</div>
          <h3>Open Source Contributions</h3>
          <p class="exp-placeholder">Details to be added — actively exploring open-source projects to contribute to.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- ================= EDUCATION ================= -->
  <section class="section" id="education">
    <div class="container">
      <p class="section-eyebrow reveal-up">My academic path</p>
      <h2 class="section-title reveal-up">Education</h2>

      <div class="timeline">
        <div class="timeline-item reveal-left">
          <div class="timeline-dot"></div>
          <div class="glass-card timeline-content">
            <span class="timeline-year">Current</span>
            <h3>BE — Computer Science Engineering</h3>
            <p>CGPA: <strong></strong> 7.9/ 10</p>
          </div>
        </div>
        <div class="timeline-item reveal-right">
          <div class="timeline-dot"></div>
          <div class="glass-card timeline-content">
            <span class="timeline-year">Completed</span>
            <h3>Central Board Of Secondary Education (12th)</h3>
            <p>Percentage: <strong></strong>66%</p>
          </div>
        </div>
        <div class="timeline-item reveal-left">
          <div class="timeline-dot"></div>
          <div class="glass-card timeline-content">
            <span class="timeline-year">Completed</span>
            <h3>Central Board Of Secondary Education (10th)</h3>
            <p>Percentage: <strong>80</strong>%</p>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ================= CERTIFICATES ================= -->
  <section class="section section-alt" id="certificates">
    <div class="container">
      <p class="section-eyebrow reveal-up">Continuous learning</p>
      <h2 class="section-title reveal-up">Certificates</h2>

      <div class="cert-slider-wrap reveal-up">
        <button class="cert-arrow cert-prev" id="certPrev" aria-label="Previous certificate">&#10094;</button>
        <div class="cert-slider" id="certSlider">
          <div class="cert-card glass-card">
            <div class="cert-logo">🎓</div>
            <h3>Coursera</h3>
            <p>Certificate placeholder</p>
          </div>
          <div class="cert-card glass-card">
            <div class="cert-logo">💼</div>
            <h3>LinkedIn Learning</h3>
            <p>Certificate placeholder</p>
          </div>
          <div class="cert-card glass-card">
            <div class="cert-logo">📘</div>
            <h3>NPTEL</h3>
            <p>Certificate placeholder</p>
          </div>
          <div class="cert-card glass-card">
            <div class="cert-logo">🧠</div>
            <h3>Udemy</h3>
            <p>Certificate placeholder</p>
          </div>
          <div class="cert-card glass-card">
            <div class="cert-logo">🏆</div>
            <h3>Others</h3>
            <p>Certificate placeholder</p>
          </div>
        </div>
        <button class="cert-arrow cert-next" id="certNext" aria-label="Next certificate">&#10095;</button>
      </div>
    </div>
  </section>

  <!-- ================= RESUME ================= -->
  <section class="section" id="resume">
    <div class="container">
      <div class="glass-card resume-card reveal-up">
        <div>
          <p class="section-eyebrow">Take a copy with you</p>
          <h2 class="section-title" style="margin-bottom:.5rem;">My <span class="gradient-text">Resume</span></h2>
          <p>Get a complete overview of my education, skills, and projects in a single document.</p>
        </div>
        <a href="assets/Mirtyunjay S/Resume.pdf" class="btn btn-primary ripple" download>
          <span>⬇ Download Resume</span>
        </a>
      </div>
    </div>
  </section>

  <!-- ================= CONTACT ================= -->
  <section class="section section-alt" id="contact">
    <div class="container">
      <p class="section-eyebrow reveal-up">Let's talk</p>
      <h2 class="section-title reveal-up">Get In <span class="gradient-text">Touch</span></h2>

      <div class="contact-grid">
        <div class="glass-card contact-form-card reveal-left">
          <form id="contactForm" novalidate>
            <div class="form-group">
              <input type="text" id="name" name="name" required>
              <label for="name">Your Name</label>
            </div>
            <div class="form-group">
              <input type="email" id="email" name="email" required>
              <label for="email">Your Email</label>
            </div>
            <div class="form-group">
              <input type="text" id="subject" name="subject" required>
              <label for="subject">Subject</label>
            </div>
            <div class="form-group">
              <textarea id="message" name="message" rows="5" required></textarea>
              <label for="message">Your Message</label>
            </div>
            <button type="submit" class="btn btn-primary ripple" id="sendBtn">
              <span>Send Message</span>
            </button>
            <p class="form-status" id="formStatus" role="status" aria-live="polite"></p>
          </form>
        </div>

        <div class="contact-info reveal-right">
          <div class="glass-card contact-item">
            <span class="contact-icon">✉️</span>
            <div><h4>Email</h4><p>sundarrajmani81@gmail.com</p></div>
          </div>
          <div class="glass-card contact-item">
            <span class="contact-icon">📞</span>
            <div><h4>Phone</h4><p>+91 8870438324</p></div>
          </div>
          <div class="glass-card contact-item">
            <span class="contact-icon">📍</span>
            <div><h4>Location</h4><p>Thiruvallur, Tamil Nadu, India</p></div>
          </div>
          <div class="glass-card contact-item">
            <span class="contact-icon">💻</span>
            <div><h4>GitHub</h4><p><a href="https://github.com/" target="_blank" rel="noopener">https://github.com/mirtyun1708</a></p></div>
          </div>
          <div class="glass-card contact-item">
            <span class="contact-icon">🔗</span>
            <div><h4>LinkedIn</h4><p><a href="https://linkedin.com/" target="_blank" rel="noopener">https://www.linkedin.com/in/mrityunjay-s-65b448371/</a></p></div>
          </div>
          <div class="glass-card map-placeholder">
            <p>🗺️ Google Maps Embed Placeholder</p>
          </div>
        </div>
      </div>
    </div>
  </section>

</main>

<!-- ================= FOOTER ================= -->
<footer class="footer">
  <div class="container footer-container">
    <a href="#home" class="logo">
      <span class="logo-bracket">&lt;</span>Mirtyunjay S<span class="accent">.</span><span class="logo-bracket">/&gt;</span>
    </a>
    <div class="footer-socials">
      <a href="https://github.com/" target="_blank" rel="noopener" aria-label="GitHub">GitHub</a>
      <a href="https://linkedin.com/" target="_blank" rel="noopener" aria-label="LinkedIn">LinkedIn</a>
      <a href="Mirtyun07052007@example.com" aria-label="Email">Email</a>
    </div>
    <p class="footer-copy">© <span id="year"></span> Mirtyunjay S. All rights reserved.</p>
    <p class="footer-made">Made with <span class="heart">❤️</span> by Mirtyunjay S</p>
  </div>
</footer>

<button class="back-to-top" id="backToTop" aria-label="Back to top">
  <svg viewBox="0 0 24 24" width="20" height="20"><path fill="currentColor" d="m12 5-7 7h4v7h6v-7h4z"/></svg>
</button>

<script>
/* =========================================================
Manikandan M — PORTFOLIO SCRIPT
   Vanilla JS: loader, nav, typing, particles, reveal, etc.
   ========================================================= */

document.addEventListener('DOMContentLoaded', () => {

  /* ---------- FOOTER YEAR ---------- */
  const yearEl = document.getElementById('year');
  if (yearEl) yearEl.textContent = new Date().getFullYear();

  /* ---------- 1. LOADER ---------- */
  const loader = document.getElementById('loader');
  window.addEventListener('load', () => {
    setTimeout(() => loader && loader.classList.add('hidden'), 500);
  });
  // Fallback in case load event already fired
  setTimeout(() => loader && loader.classList.add('hidden'), 2500);

  /* ---------- 2. NAVBAR: scroll state + mobile toggle + active link ---------- */
  const navbar = document.getElementById('navbar');
  const navToggle = document.getElementById('navToggle');
  const navLinks = document.getElementById('navLinks');
  const navLinkItems = document.querySelectorAll('.nav-link');

  window.addEventListener('scroll', () => {
    navbar.classList.toggle('scrolled', window.scrollY > 30);
    toggleBackToTop();
    updateActiveNav();
  }, { passive: true });

  navToggle.addEventListener('click', () => {
    const isOpen = navLinks.classList.toggle('open');
    navToggle.classList.toggle('open', isOpen);
    navToggle.setAttribute('aria-expanded', isOpen);
  });

  navLinkItems.forEach(link => {
    link.addEventListener('click', () => {
      navLinks.classList.remove('open');
      navToggle.classList.remove('open');
      navToggle.setAttribute('aria-expanded', 'false');
    });
  });

  const sections = document.querySelectorAll('main section[id], .hero');
  function updateActiveNav(){
    let current = 'home';
    sections.forEach(sec => {
      const rect = sec.getBoundingClientRect();
      if (rect.top <= 120 && rect.bottom >= 120) current = sec.id;
    });
    navLinkItems.forEach(link => {
      link.classList.toggle('active', link.dataset.section === current);
    });
  }

  /* ---------- 3. TYPING ANIMATION ---------- */
  const typedTextEl = document.getElementById('typed-text');
  const roles = ['Software Developer', 'Java Developer', 'Full Stack Learner', 'Problem Solver', 'Tech Enthusiast'];
  let roleIndex = 0, charIndex = 0, deleting = false;

  function typeLoop(){
    if (!typedTextEl) return;
    const current = roles[roleIndex];

    if (!deleting){
      charIndex++;
      typedTextEl.textContent = current.slice(0, charIndex);
      if (charIndex === current.length){
        deleting = true;
        setTimeout(typeLoop, 1400);
        return;
      }
    } else {
      charIndex--;
      typedTextEl.textContent = current.slice(0, charIndex);
      if (charIndex === 0){
        deleting = false;
        roleIndex = (roleIndex + 1) % roles.length;
      }
    }
    setTimeout(typeLoop, deleting ? 40 : 85);
  }
  typeLoop();

  /* ---------- 4. CURSOR GLOW ---------- */
  const cursorGlow = document.getElementById('cursorGlow');
  if (cursorGlow && matchMedia('(hover: hover)').matches){
    window.addEventListener('mousemove', e => {
      cursorGlow.style.transform = `translate(${e.clientX}px, ${e.clientY}px) translate(-50%, -50%)`;
    }, { passive: true });
  }

  /* ---------- 5. FLOATING PARTICLE NETWORK BACKGROUND ---------- */
  const canvas = document.getElementById('network-canvas');
  const ctx = canvas ? canvas.getContext('2d') : null;
  let particles = [];
  let animFrame;

  function resizeCanvas(){
    if (!canvas) return;
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  }

  function initParticles(){
    if (!canvas) return;
    const count = window.innerWidth < 700 ? 34 : 68;
    particles = Array.from({ length: count }, () => ({
      x: Math.random() * canvas.width,
      y: Math.random() * canvas.height,
      vx: (Math.random() - 0.5) * 0.35,
      vy: (Math.random() - 0.5) * 0.35,
      r: Math.random() * 1.6 + 0.6
    }));
  }

  const reduceMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

  function drawParticles(){
    if (!ctx) return;
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    particles.forEach(p => {
      p.x += p.vx;
      p.y += p.vy;
      if (p.x < 0 || p.x > canvas.width) p.vx *= -1;
      if (p.y < 0 || p.y > canvas.height) p.vy *= -1;

      ctx.beginPath();
      ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
      ctx.fillStyle = 'rgba(120,150,255,0.55)';
      ctx.fill();
    });

    const maxDist = 140;
    for (let i = 0; i < particles.length; i++){
      for (let j = i + 1; j < particles.length; j++){
        const dx = particles[i].x - particles[j].x;
        const dy = particles[i].y - particles[j].y;
        const dist = Math.sqrt(dx * dx + dy * dy);
        if (dist < maxDist){
          ctx.beginPath();
          ctx.moveTo(particles[i].x, particles[i].y);
          ctx.lineTo(particles[j].x, particles[j].y);
          ctx.strokeStyle = `rgba(139,92,246,${0.18 * (1 - dist / maxDist)})`;
          ctx.lineWidth = 1;
          ctx.stroke();
        }
      }
    }
    animFrame = requestAnimationFrame(drawParticles);
  }

  if (canvas && ctx){
    resizeCanvas();
    initParticles();
    if (!reduceMotion) drawParticles();
    window.addEventListener('resize', () => {
      resizeCanvas();
      initParticles();
    });
  }

  /* ---------- 6. SCROLL REVEAL (IntersectionObserver) ---------- */
  const revealEls = document.querySelectorAll('.reveal-up, .reveal-left, .reveal-right');
  const revealObserver = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting){
        entry.target.classList.add('in-view');
        revealObserver.unobserve(entry.target);
      }
    });
  }, { threshold: 0.15, rootMargin: '0px 0px -60px 0px' });
  revealEls.forEach(el => revealObserver.observe(el));

  /* ---------- 7. ANIMATED STAT COUNTERS ---------- */
  const statNumbers = document.querySelectorAll('.stat-number');
  const statObserver = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting){
        animateCount(entry.target);
        statObserver.unobserve(entry.target);
      }
    });
  }, { threshold: 0.4 });
  statNumbers.forEach(el => statObserver.observe(el));

  function animateCount(el){
    const target = parseInt(el.dataset.count, 10) || 0;
    const duration = 1400;
    const start = performance.now();

    function step(now){
      const progress = Math.min((now - start) / duration, 1);
      const eased = 1 - Math.pow(1 - progress, 3);
      el.textContent = Math.floor(eased * target);
      if (progress < 1) requestAnimationFrame(step);
      else el.textContent = target;
    }
    requestAnimationFrame(step);
  }

  /* ---------- 8. ANIMATED SKILL BARS ---------- */
  const skillBars = document.querySelectorAll('.bar-fill');
  const barObserver = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting){
        entry.target.style.width = entry.target.dataset.width + '%';
        barObserver.unobserve(entry.target);
      }
    });
  }, { threshold: 0.3 });
  skillBars.forEach(bar => barObserver.observe(bar));

  /* ---------- 9. CERTIFICATE SLIDER ---------- */
  const certSlider = document.getElementById('certSlider');
  const certPrev = document.getElementById('certPrev');
  const certNext = document.getElementById('certNext');

  function certScrollAmount(){
    const card = certSlider.querySelector('.cert-card');
    return card ? card.offsetWidth + 24 : 240;
  }
  certNext && certNext.addEventListener('click', () => {
    certSlider.scrollBy({ left: certScrollAmount(), behavior: 'smooth' });
  });
  certPrev && certPrev.addEventListener('click', () => {
    certSlider.scrollBy({ left: -certScrollAmount(), behavior: 'smooth' });
  });

  /* ---------- 10. RIPPLE BUTTON EFFECT ---------- */
  document.querySelectorAll('.ripple').forEach(btn => {
    btn.addEventListener('click', function (e) {
      const rect = this.getBoundingClientRect();
      this.style.setProperty('--rx', `${e.clientX - rect.left}px`);
      this.style.setProperty('--ry', `${e.clientY - rect.top}px`);
      this.classList.remove('rippling');
      // force reflow to restart animation
      void this.offsetWidth;
      this.classList.add('rippling');
    });
  });

  /* ---------- 11. BACK TO TOP ---------- */
  const backToTop = document.getElementById('backToTop');
  function toggleBackToTop(){
    backToTop.classList.toggle('show', window.scrollY > 500);
  }
  backToTop.addEventListener('click', () => {
    window.scrollTo({ top: 0, behavior: 'smooth' });
  });

  /* ---------- 12. CONTACT FORM (front-end only) ---------- */
  const contactForm = document.getElementById('contactForm');
  const formStatus = document.getElementById('formStatus');
  const sendBtn = document.getElementById('sendBtn');

  contactForm.addEventListener('submit', (e) => {
    e.preventDefault();
    if (!contactForm.checkValidity()){
      formStatus.textContent = 'Please fill in all fields correctly.';
      formStatus.style.color = '#ff8080';
      return;
    }

    sendBtn.disabled = true;
    const originalText = sendBtn.querySelector('span').textContent;
    sendBtn.querySelector('span').textContent = 'Sending...';

    // Simulated send — replace with real endpoint (e.g. Formspree, EmailJS) when ready.
    setTimeout(() => {
      formStatus.style.color = 'var(--accent-cyan)';
      formStatus.textContent = 'Thanks for reaching out! I will get back to you soon.';
      sendBtn.querySelector('span').textContent = originalText;
      sendBtn.disabled = false;
      contactForm.reset();
    }, 1200);
  });

  /* ---------- 13. MOUSE PARALLAX ON HERO VISUAL ---------- */
  const profileFrame = document.querySelector('.profile-frame');
  const heroSection = document.querySelector('.hero');
  if (profileFrame && heroSection && matchMedia('(hover: hover)').matches){
    heroSection.addEventListener('mousemove', (e) => {
      const { innerWidth, innerHeight } = window;
      const x = (e.clientX / innerWidth - 0.5) * 16;
      const y = (e.clientY / innerHeight - 0.5) * 16;
      profileFrame.style.transform = `translate(${x}px, ${y}px)`;
    });
    heroSection.addEventListener('mouseleave', () => {
      profileFrame.style.transform = 'translate(0,0)';
    });
  }

  /* Initial calls */
  updateActiveNav();
  toggleBackToTop();
});

</script>
</body>
</html>
```


## OUTPUT
<img width="1906" height="1134" alt="Screenshot 2026-08-18 110825" src="https://github.com/user-attachments/assets/ef1dcbbb-cff8-4f7f-80ec-0551e05936fe" />


## RESULT
The program for creating Portfolio using HTML and CSS is executed successfully.
