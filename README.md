<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>You Fed An Animal! 🐾</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700;800&display=swap');

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    min-height: 100vh;
    background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
    font-family: 'Poppins', sans-serif;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px;
    overflow-x: hidden;
  }

  /* floating paws background */
  .paws {
    position: fixed;
    inset: 0;
    pointer-events: none;
    overflow: hidden;
    z-index: 0;
  }
  .paw {
    position: absolute;
    font-size: 24px;
    opacity: 0.06;
    animation: floatUp linear infinite;
  }

  @keyframes floatUp {
    0%   { transform: translateY(100vh) rotate(0deg); opacity: 0; }
    10%  { opacity: 0.06; }
    90%  { opacity: 0.06; }
    100% { transform: translateY(-120px) rotate(360deg); opacity: 0; }
  }

  .card {
    position: relative;
    z-index: 1;
    background: rgba(255,255,255,0.05);
    backdrop-filter: blur(16px);
    border: 1px solid rgba(255,255,255,0.12);
    border-radius: 24px;
    padding: 48px 40px;
    max-width: 480px;
    width: 100%;
    text-align: center;
    box-shadow: 0 32px 64px rgba(0,0,0,0.4);
  }

  /* checkmark badge */
  .check-badge {
    width: 72px;
    height: 72px;
    background: linear-gradient(135deg, #10b981, #059669);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0 auto 20px;
    font-size: 32px;
    box-shadow: 0 8px 24px rgba(16,185,129,0.4);
    animation: popIn 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  }
  @keyframes popIn {
    0%   { transform: scale(0); opacity: 0; }
    100% { transform: scale(1); opacity: 1; }
  }

  .title {
    font-size: 28px;
    font-weight: 800;
    color: #ffffff;
    margin-bottom: 8px;
    line-height: 1.2;
  }
  .title span { color: #10b981; }

  .subtitle {
    font-size: 15px;
    color: rgba(255,255,255,0.6);
    margin-bottom: 28px;
    line-height: 1.6;
  }

  /* animal image */
  .animal-frame {
    position: relative;
    margin: 0 auto 28px;
    width: 220px;
    height: 220px;
  }
  .animal-frame img {
    width: 220px;
    height: 220px;
    border-radius: 50%;
    object-fit: cover;
    border: 4px solid rgba(255,255,255,0.15);
    box-shadow: 0 12px 32px rgba(0,0,0,0.4);
  }
  /* ring animation */
  .ring {
    position: absolute;
    inset: -8px;
    border-radius: 50%;
    border: 3px solid #10b981;
    animation: pulse-ring 2s ease-out infinite;
    opacity: 0;
  }
  .ring:nth-child(2) { animation-delay: 0.6s; }
  @keyframes pulse-ring {
    0%   { transform: scale(0.9); opacity: 0.6; }
    100% { transform: scale(1.15); opacity: 0; }
  }

  .animal-name {
    font-size: 13px;
    font-weight: 600;
    color: #10b981;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    margin-bottom: 6px;
  }

  /* stat pill */
  .stat-pill {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: rgba(16,185,129,0.12);
    border: 1px solid rgba(16,185,129,0.3);
    border-radius: 40px;
    padding: 10px 20px;
    margin-bottom: 28px;
  }
  .stat-pill .num {
    font-size: 22px;
    font-weight: 800;
    color: #10b981;
  }
  .stat-pill .label {
    font-size: 13px;
    color: rgba(255,255,255,0.7);
    text-align: left;
    line-height: 1.3;
  }

  /* message box */
  .message {
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.08);
    border-radius: 14px;
    padding: 18px 20px;
    margin-bottom: 28px;
    font-size: 14px;
    color: rgba(255,255,255,0.75);
    line-height: 1.7;
  }
  .message strong { color: #ffffff; }

  /* cta button */
  .btn-follow {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    width: 100%;
    padding: 16px;
    background: linear-gradient(135deg, #7c5cfc, #5b3de8);
    color: white;
    font-size: 15px;
    font-weight: 700;
    border: none;
    border-radius: 14px;
    cursor: pointer;
    text-decoration: none;
    transition: transform 0.15s, box-shadow 0.15s;
    box-shadow: 0 8px 24px rgba(124,92,252,0.4);
    margin-bottom: 12px;
  }
  .btn-follow:hover { transform: translateY(-2px); box-shadow: 0 12px 32px rgba(124,92,252,0.5); }

  .btn-share {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    width: 100%;
    padding: 14px;
    background: rgba(255,255,255,0.06);
    border: 1px solid rgba(255,255,255,0.12);
    color: rgba(255,255,255,0.8);
    font-size: 14px;
    font-weight: 600;
    border-radius: 14px;
    cursor: pointer;
    transition: background 0.15s;
    font-family: 'Poppins', sans-serif;
  }
  .btn-share:hover { background: rgba(255,255,255,0.1); }

  .footer-note {
    margin-top: 20px;
    font-size: 12px;
    color: rgba(255,255,255,0.3);
  }

  /* confetti */
  .confetti-piece {
    position: fixed;
    width: 10px;
    height: 10px;
    border-radius: 2px;
    animation: confettiFall linear forwards;
    z-index: 999;
    pointer-events: none;
  }
  @keyframes confettiFall {
    0%   { transform: translateY(-20px) rotate(0deg); opacity: 1; }
    100% { transform: translateY(100vh) rotate(720deg); opacity: 0; }
  }
</style>
</head>
<body>

<!-- Floating paw background -->
<div class="paws" id="paws"></div>

<div class="card">
  <div class="check-badge">✓</div>

  <div class="title">You just fed<br><span>1 animal! 🐾</span></div>
  <div class="subtitle">The ad you completed helps us care for the world's strangest animals. Every click counts.</div>

  <div class="animal-frame">
    <div class="ring"></div>
    <div class="ring"></div>
    <!--
      Replace the src below with any animal image URL you want.
      Free options: unsplash.com, pexels.com — just right-click an image and copy link.
      Example: src="https://images.unsplash.com/photo-1564349683136-77e08dba1ef7?w=400"
    -->
    <img src="https://images.unsplash.com/photo-1630231618273-ece163251589?fm=jpg&q=60&w=3000&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" alt="Animal" id="animal-img"/>
  </div>

  <div class="animal-name" id="animal-name">🦔 Today's Animal</div>

  <div class="stat-pill">
    <div class="num">1</div>
    <div class="label">animal fed<br>thanks to you</div>
  </div>

  <div class="message">
    <strong>Thank you so much!</strong> The ad revenue from your click goes directly toward feeding and caring for the weird and wonderful animals we post every day. You're officially one of the good ones 🙏
  </div>

  <!--
    Replace YOUR_INSTAGRAM_USERNAME below with your actual Instagram username
  -->
  <a class="btn-follow" href="https://instagram.com/some_strange_animals" target="_blank">
    📸 Follow us for daily weird animals
  </a>

  <button class="btn-share" onclick="shareIt()">
    🔗 Share this & feed another animal
  </button>

  <div class="footer-note">Ad revenue • Animal care • 100% free for you</div>
</div>

<script>
  // ── Floating paws ────────────────────────────────────────────────────────────
  const pawContainer = document.getElementById("paws");
  for (let i = 0; i < 18; i++) {
    const paw = document.createElement("div");
    paw.className = "paw";
    paw.textContent = ["🐾","🐾","🦔","🐊","🦜","🐸"][Math.floor(Math.random()*6)];
    paw.style.left = Math.random() * 100 + "vw";
    paw.style.fontSize = (16 + Math.random() * 24) + "px";
    paw.style.animationDuration = (8 + Math.random() * 12) + "s";
    paw.style.animationDelay = (Math.random() * 10) + "s";
    pawContainer.appendChild(paw);
  }

  // ── Confetti on load ─────────────────────────────────────────────────────────
  const colors = ["#10b981","#7c5cfc","#f59e0b","#ef4444","#00c2cb","#ffffff"];
  function launchConfetti() {
    for (let i = 0; i < 60; i++) {
      setTimeout(() => {
        const el = document.createElement("div");
        el.className = "confetti-piece";
        el.style.left = Math.random() * 100 + "vw";
        el.style.background = colors[Math.floor(Math.random() * colors.length)];
        el.style.width  = (6 + Math.random() * 8) + "px";
        el.style.height = (6 + Math.random() * 8) + "px";
        el.style.animationDuration = (1.5 + Math.random() * 2) + "s";
        document.body.appendChild(el);
        setTimeout(() => el.remove(), 3500);
      }, i * 30);
    }
  }
  launchConfetti();

  // ── Rotate animal names ──────────────────────────────────────────────────────
  const animals = [
    "🦔 Hedgehog", "🐊 Caiman", "🦜 Parrot", "🐸 Axolotl",
    "🦎 Chameleon", "🐙 Octopus", "🦩 Flamingo", "🐡 Pufferfish"
  ];
  document.getElementById("animal-name").textContent =
    animals[Math.floor(Math.random() * animals.length)];

  // ── Share button ─────────────────────────────────────────────────────────────
  function shareIt() {
    if (navigator.share) {
      navigator.share({
        title: "I just fed an animal for free! 🐾",
        text: "Click this link to feed a weird animal — it's completely free!",
        url: window.location.href
      });
    } else {
      navigator.clipboard.writeText(window.location.href);
      alert("Link copied! Share it to feed another animal 🐾");
    }
  }
</script>
</body>
</html>
