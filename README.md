<!doctype html>
<html lang="da">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>T&T STUDIO</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    .brand { letter-spacing: 0.06em; }
    html { scroll-behavior: smooth; }
  </style>
</head>
<body class="bg-gradient-to-b from-slate-900 to-slate-800 text-slate-100 min-h-screen">
  <nav class="bg-slate-800/70 backdrop-blur-md fixed w-full top-0 z-50 shadow-lg">
    <div class="max-w-6xl mx-auto flex justify-between items-center py-3 px-6">
      <h1 class="text-2xl font-extrabold brand">T&amp;T <span class="text-emerald-400">STUDIO</span></h1>
      <ul class="hidden md:flex gap-6 text-slate-300 font-medium">
        <li><a href="#about" class="hover:text-emerald-400">Om os</a></li>
        <li><a href="#pricing" class="hover:text-emerald-400">Priser</a></li>
        <li><a href="#experience" class="hover:text-emerald-400">Erfaring</a></li>
        <li><a href="#contact" class="hover:text-emerald-400">Kontakt</a></li>
      </ul>
      <div id="user-area"></div>
    </div>
  </nav>

  <main class="pt-24 max-w-5xl mx-auto p-6">
    <section id="login-screen" class="text-center bg-slate-800/60 rounded-2xl p-8 shadow-2xl">
      <h2 class="text-3xl font-bold mb-3">Velkommen til T&amp;T Studio</h2>
      <p class="mb-4 text-slate-300">Log ind med Discord for at se priser, erfaring og kontaktinformation.</p>
      <a id="discord-login" class="inline-block px-8 py-3 rounded-xl bg-emerald-500 text-slate-900 font-semibold hover:opacity-90 transition">Log ind med Discord</a>
      <p class="mt-4 text-slate-500 text-sm">Vi bruger kun din Discord-identitet (display name + avatar) — intet andet gemmes.</p>
    </section>

    <section id="content" class="hidden space-y-10 mt-10">
      <article id="about" class="p-6 bg-slate-800/60 rounded-2xl shadow-lg">
        <h2 class="text-3xl font-bold mb-2 text-emerald-400">Om T&amp;T Studio</h2>
        <p class="text-slate-300">Vi udvikler og sælger professionelle FiveM ESX-filer og Discord-bots. Vores mål er kvalitet, ydeevne og hurtig levering. Vi hjælper både små og store communities med skræddersyede løsninger.</p>
      </article>

      <article id="pricing" class="p-6 bg-slate-800/60 rounded-2xl shadow-lg">
        <h2 class="text-3xl font-bold mb-2 text-emerald-400">Priser</h2>
        <ul class="mt-4 space-y-3 text-slate-200">
          <li class="flex justify-between border-b border-slate-700 pb-2"><span>ESX Starter</span><span>150 DKK</span></li>
          <li class="flex justify-between border-b border-slate-700 pb-2"><span>ESX Komplett</span><span>400 DKK</span></li>
          <li class="flex justify-between border-b border-slate-700 pb-2"><span>Discord Bot (basis)</span><span>200 DKK</span></li>
          <li class="flex justify-between border-b border-slate-700 pb-2"><span>Custom Bot / Integration</span><span>Efter aftale</span></li>
        </ul>
        <p class="mt-4 text-slate-400 text-sm">Kontakt os for tilpassede løsninger og pakkeløsninger.</p>
      </article>

      <article id="experience" class="p-6 bg-slate-800/60 rounded-2xl shadow-lg">
        <h2 class="text-3xl font-bold mb-2 text-emerald-400">Erfaring</h2>
        <p class="text-slate-300">Med over 3 års erfaring i udvikling af FiveM / ESX scripts og bots til mere end 50 Discord-servere, leverer vi stabile, optimerede og veldokumenterede systemer. Vi er passionerede gamere og udviklere med fokus på performance og brugervenlighed.</p>
      </article>

      <article id="contact" class="p-6 bg-slate-800/60 rounded-2xl shadow-lg">
        <h2 class="text-3xl font-bold mb-2 text-emerald-400">Kontakt os</h2>
        <p class="text-slate-300 mb-4">Har du spørgsmål eller ønsker en specialopgave? Kontakt os direkte via Discord eller formularen nedenfor.</p>
        <form class="space-y-4" onsubmit="event.preventDefault(); alert('Tak for din besked!');">
          <input type="text" placeholder="Dit navn" required class="w-full p-3 rounded-lg bg-slate-700 border border-slate-600 focus:border-emerald-400 focus:outline-none">
          <input type="email" placeholder="Din e-mail" required class="w-full p-3 rounded-lg bg-slate-700 border border-slate-600 focus:border-emerald-400 focus:outline-none">
          <textarea placeholder="Din besked..." required class="w-full p-3 h-32 rounded-lg bg-slate-700 border border-slate-600 focus:border-emerald-400 focus:outline-none"></textarea>
          <button type="submit" class="w-full py-3 bg-emerald-500 text-slate-900 font-semibold rounded-lg hover:opacity-90 transition">Send besked</button>
        </form>
      </article>
    </section>

    <div id="error" class="hidden mt-4 text-red-400 text-center"></div>
  </main>

  <footer class="mt-10 py-6 text-center text-slate-500 text-sm border-t border-slate-700">
    <p>© 2025 T&amp;T Studio — Alle rettigheder forbeholdes</p>
    <div class="mt-2 flex justify-center gap-4 text-slate-400">
      <a href="https://discord.gg/" class="hover:text-emerald-400" target="_blank">Discord</a>
      <a href="#" class="hover:text-emerald-400">GitHub</a>
      <a href="#" class="hover:text-emerald-400">Kontakt</a>
    </div>
  </footer>

  <script>
    const CLIENT_ID = 'YOUR_CLIENT_ID';
    const REDIRECT_URI = window.location.origin + window.location.pathname;
    const SCOPE = 'identify';
    const RESPONSE_TYPE = 'token';

    function getDiscordAuthUrl() {
      const base = 'https://discord.com/api/oauth2/authorize';
      const params = new URLSearchParams({
        client_id: CLIENT_ID,
        redirect_uri: REDIRECT_URI,
        response_type: RESPONSE_TYPE,
        scope: SCOPE,
        prompt: 'consent'
      });
      return base + '?' + params.toString();
    }

    const loginBtn = document.getElementById('discord-login');
    const loginScreen = document.getElementById('login-screen');
    const content = document.getElementById('content');
    const userArea = document.getElementById('user-area');
    const errorBox = document.getElementById('error');

    loginBtn.addEventListener('click', () => {
      if (CLIENT_ID === 'YOUR_CLIENT_ID') {
        alert('Indsæt din Discord CLIENT_ID i index.html før du bruger login.');
        return;
      }
      window.location.href = getDiscordAuthUrl();
    });

    function parseHash(hash) {
      if (!hash) return {};
      return Object.fromEntries(new URLSearchParams(hash.replace(/^#/, '')));
    }

    function saveToken(tokenObj) {
      localStorage.setItem('discord_token', JSON.stringify(tokenObj));
    }
    function loadToken() {
      try { return JSON.parse(localStorage.getItem('discord_token')); } catch(e){return null;}
    }

    async function fetchDiscordUser(token) {
      const resp = await fetch('https://discord.com/api/users/@me', {
        headers: { Authorization: `Bearer ${token}` }
      });
      if (!resp.ok) throw new Error('Kunne ikke hente brugerinfo: ' + resp.status);
      return await resp.json();
    }

    function showContentForUser(user) {
      loginScreen.classList.add('hidden');
      content.classList.remove('hidden');
      userArea.innerHTML = `
        <div class="flex items-center gap-3">
          <img src="https://cdn.discordapp.com/avatars/${user.id}/${user.avatar}.png?size=64" alt="avatar" class="w-10 h-10 rounded-full border-2 border-emerald-400" onerror="this.style.display='none'" />
          <div class="text-right">
            <div class="font-semibold">${user.username}#${user.discriminator}</div>
            <button id="logout" class="text-xs mt-1 underline hover:text-emerald-400">Log ud</button>
          </div>
        </div>
      `;
      document.getElementById('logout').addEventListener('click', () => {
        localStorage.removeItem('discord_token');
        window.location.href = REDIRECT_URI;
      });
    }

    (async function init(){
      const hashData = parseHash(window.location.hash);
      if (hashData.access_token) {
        saveToken({ access_token: hashData.access_token, expires_in: hashData.expires_in, obtained_at: Date.now() });
        history.replaceState(null, '', REDIRECT_URI);
      }
      const tokenObj = loadToken();
      if (!tokenObj || !tokenObj.access_token) {
        loginScreen.classList.remove('hidden');
        content.classList.add('hidden');
        return;
      }
      try {
        const user = await fetchDiscordUser(tokenObj.access_token);
        showContentForUser(user);
      } catch (err) {
        console.error(err);
        localStorage.removeItem('discord_token');
        loginScreen.classList.remove('hidden');
        content.classList.add('hidden');
        errorBox.textContent = 'Log ind mislykkedes. Token er muligvis udløbet. Prøv igen.';
        errorBox.classList.remove('hidden');
      }
    })();
  </script>
</body>
</html>
