<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Last Miles AI – Smarter final-mile delivery</title>
<style>
:root{--bg:#EEF2F4;--ink:#12232B;--muted:#4D6068;--line:#C9D4D9;--accent:#0A7C86;--hot:#F2542D;--card:#FFFFFF}
@media (prefers-color-scheme:dark){:root{--bg:#0E1A20;--ink:#E7EEF1;--muted:#9AAEB7;--line:#27404B;--accent:#3CC4CF;--hot:#FF7A57;--card:#14262E}}
*{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{font-family:"Trebuchet MS","Segoe UI",Helvetica,Arial,sans-serif;background:var(--bg);color:var(--ink);line-height:1.6}
h1,h2,h3{font-family:Georgia,"Times New Roman",serif;line-height:1.15;font-weight:700}
a{color:inherit}
:focus-visible{outline:3px solid var(--hot);outline-offset:3px}
.wrap{max-width:1040px;margin:0 auto;padding:0 24px}
nav{display:flex;justify-content:space-between;align-items:center;padding:22px 0}
.logo{font-family:Georgia,serif;font-weight:700;font-size:1.25rem;text-decoration:none}
.logo span{color:var(--hot)}
nav ul{display:flex;gap:24px;list-style:none;font-size:.95rem}
nav a{text-decoration:none;color:var(--muted)}
nav a:hover{color:var(--ink)}
.hero{padding:56px 0 40px;display:grid;grid-template-columns:1.1fr .9fr;gap:40px;align-items:center}
.hero h1{font-size:clamp(2.3rem,5vw,3.8rem);margin-bottom:20px}
.hero p{color:var(--muted);font-size:1.1rem;max-width:46ch;margin-bottom:28px}
.btn{display:inline-block;background:var(--ink);color:var(--bg);padding:14px 26px;border-radius:6px;text-decoration:none;font-weight:700;border:0;cursor:pointer;font-size:1rem}
.btn.alt{background:transparent;color:var(--ink);border:2px solid var(--ink);margin-left:10px}
.map{background:var(--card);border:1px solid var(--line);border-radius:12px;padding:14px}
.map svg{width:100%;height:auto;display:block}
.road{stroke:var(--line);stroke-width:2;fill:none}
.route{stroke:var(--accent);stroke-width:4;fill:none;stroke-linecap:round;stroke-dasharray:600;stroke-dashoffset:600;animation:draw 3s ease forwards}
@keyframes draw{to{stroke-dashoffset:0}}
.stop{fill:var(--card);stroke:var(--accent);stroke-width:3}
.depot{fill:var(--hot)}
.map small{display:block;color:var(--muted);font-size:.85rem;margin-top:8px}
@media (prefers-reduced-motion:reduce){.route{animation:none;stroke-dashoffset:0}}
.stats{display:flex;flex-wrap:wrap;gap:40px;padding:28px 0;border-top:1px solid var(--line);border-bottom:1px solid var(--line)}
.stats b{font-family:Georgia,serif;font-size:2rem;display:block}
.stats span{color:var(--muted);font-size:.9rem}
section{padding:72px 0}
section h2{font-size:clamp(1.7rem,3.5vw,2.4rem);margin-bottom:14px;max-width:22ch}
.lead{color:var(--muted);max-width:56ch;margin-bottom:36px}
.grid{display:grid;grid-template-columns:repeat(3,1fr);gap:28px}
.grid h3{font-size:1.25rem;margin-bottom:8px;padding-top:14px;border-top:3px solid var(--accent)}
.grid p{color:var(--muted);font-size:.97rem}
.calc{background:var(--card);border:1px solid var(--line);border-radius:12px;padding:28px;display:grid;grid-template-columns:1fr 1fr;gap:32px}
.calc label{display:block;font-weight:700;margin:14px 0 4px;font-size:.95rem}
.calc input[type=range]{width:100%;accent-color:var(--accent)}
.calc output{color:var(--accent);font-weight:700}
.result{background:var(--bg);border-radius:10px;padding:22px;display:flex;flex-direction:column;justify-content:center}
.result b{font-family:Georgia,serif;font-size:2.4rem;color:var(--accent)}
.result p{color:var(--muted);font-size:.9rem;margin-bottom:12px}
form{display:grid;gap:14px;max-width:460px}
input,textarea{width:100%;padding:12px 14px;border:1px solid var(--line);border-radius:6px;background:var(--card);color:var(--ink);font:inherit}
.ok{color:var(--accent);font-weight:700;min-height:1.5em}
footer{padding:32px 0;border-top:1px solid var(--line);color:var(--muted);font-size:.9rem}
.sr{position:absolute;left:-9999px}
@media (max-width:760px){.hero,.calc,.grid{grid-template-columns:1fr}nav ul{display:none}.btn.alt{margin:10px 0 0}}
</style>
</head>
<body>
<div class="wrap">
  <nav>
    <a class="logo" href="#">Last Miles <span>AI</span></a>
    <ul><li><a href="#how">How it works</a></li><li><a href="#savings">Savings</a></li><li><a href="#contact">Contact</a></li></ul>
  </nav>

  <header class="hero">
    <div>
      <h1>The final mile is the costliest. We make it the smartest.</h1>
      <p>Last Miles AI plans routes, predicts delivery windows and re-routes drivers in real time, so more parcels arrive on the first attempt.</p>
      <a class="btn" href="#contact">Book a demo</a><a class="btn alt" href="#savings">Estimate savings</a>
    </div>
    <div class="map" aria-label="Optimised delivery route example">
      <svg viewBox="0 0 400 300" role="img" aria-label="Route from depot through six stops">
        <path class="road" d="M0 80H400M0 160H400M0 240H400M70 0V300M180 0V300M290 0V300"/>
        <path class="route" d="M50 240 L70 240 L70 160 L180 160 L180 80 L290 80 L290 160 L330 160 L330 240 L180 240"/>
        <circle class="stop" cx="70" cy="160" r="8"/><circle class="stop" cx="180" cy="80" r="8"/>
        <circle class="stop" cx="290" cy="80" r="8"/><circle class="stop" cx="330" cy="160" r="8"/>
        <circle class="stop" cx="330" cy="240" r="8"/><circle class="stop" cx="180" cy="240" r="8"/>
        <circle class="depot" cx="50" cy="240" r="11"/>
      </svg>
      <small>Orange: depot. Teal: the route our engine chose for six stops.</small>
    </div>
  </header>

  <div class="stats">
    <div><b>−23%</b><span>kilometres driven</span></div>
    <div><b>+18%</b><span>first-attempt deliveries</span></div>
    <div><b>&lt;2 min</b><span>to re-plan a full fleet</span></div>
  </div>

  <section id="how">
    <h2>From order to doorstep, handled</h2>
    <p class="lead">Connect your order system once. The platform does the planning, tracking and customer messaging.</p>
    <div class="grid">
      <div><h3>Route optimisation</h3><p>Balances distance, time windows, vehicle capacity and driver shifts across the whole fleet at once.</p></div>
      <div><h3>Live re-routing</h3><p>Traffic, a missed address or a cancelled order triggers a new plan within seconds, sent to the driver's phone.</p></div>
      <div><h3>Accurate ETAs</h3><p>Customers get a narrow delivery window and updates by SMS or email, which cuts "where is my order" calls.</p></div>
    </div>
  </section>

  <section id="savings" style="padding-top:0">
    <h2>Estimate your yearly savings</h2>
    <p class="lead">A rough guide using a 23% reduction in route distance. Your real result depends on your network.</p>
    <div class="calc">
      <div>
        <label for="v">Vehicles <output id="vo">20</output></label>
        <input id="v" type="range" min="1" max="200" value="20">
        <label for="k">Kilometres per vehicle per day <output id="ko">120</output></label>
        <input id="k" type="range" min="20" max="400" value="120">
        <label for="c">Cost per km (fuel, wear, time) <output id="co">0.60</output></label>
        <input id="c" type="range" min="0.2" max="2" step="0.05" value="0.6">
      </div>
      <div class="result">
        <p>Estimated annual saving</p>
        <b id="out">$0</b>
        <p style="margin-top:10px">Based on 300 working days a year.</p>
      </div>
    </div>
  </section>

  <section id="contact" style="padding-top:0">
    <h2>See it on your own routes</h2>
    <p class="lead">Send us a sample day of orders and we'll show you the optimised plan.</p>
    <form id="f">
      <div><label for="n" class="sr">Name</label><input id="n" placeholder="Your name" required></div>
      <div><label for="e" class="sr">Email</label><input id="e" type="email" placeholder="Work email" required></div>
      <div><label for="m" class="sr">Message</label><textarea id="m" rows="4" placeholder="Tell us about your fleet and daily volume"></textarea></div>
      <button class="btn" type="submit">Request demo</button>
      <div class="ok" id="ok" role="status"></div>
    </form>
  </section>

  <footer>© 2026 Last Miles AI. All rights reserved.</footer>
</div>
<script>
const $=id=>document.getElementById(id);
function calc(){
  const v=+$('v').value,k=+$('k').value,c=+$('c').value;
  $('vo').textContent=v;$('ko').textContent=k;$('co').textContent=c.toFixed(2);
  $('out').textContent='$'+Math.round(v*k*c*300*0.23).toLocaleString('en-US');
}
['v','k','c'].forEach(i=>$(i).addEventListener('input',calc));calc();
$('f').addEventListener('submit',e=>{
  e.preventDefault();
  $('ok').textContent='Thanks, '+$('n').value+'. We\'ll reply to '+$('e').value+' within one business day.';
  e.target.reset();
});
</script>
</body>
</html>
