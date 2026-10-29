<!DOCTYPE html>
<html lang="ro">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dragoș Orlenschi | Personal Hub</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-color: #0d0f12;
            --card-bg: rgba(22, 27, 34, 0.7);
            --border-color: rgba(255, 255, 255, 0.1);
            --text-main: #f0f6fc;
            --text-muted: #8b949e;
            --accent-blue: #58a6ff;
            --accent-purple: #bc8cff;
            --accent-red: #f85149;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 20px;
            background-image: 
                radial-gradient(circle at 15% 15%, rgba(88, 166, 255, 0.08) 0%, transparent 40%),
                radial-gradient(circle at 85% 85%, rgba(188, 140, 255, 0.08) 0%, transparent 40%);
        }

        /* Continuous Blurring for Locked State */
        .content-wrapper {
            max-width: 800px;
            width: 100%;
            filter: blur(15px);
            pointer-events: none;
            user-select: none;
            transition: filter 0.4s ease;
        }

        body.unlocked .content-wrapper {
            filter: blur(0);
            pointer-events: auto;
            user-select: auto;
        }

        /* Password Modal Overlay */
        .password-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(13, 15, 18, 0.85);
            backdrop-filter: blur(20px);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            transition: opacity 0.4s ease, visibility 0.4s ease;
        }

        body.unlocked .password-overlay {
            opacity: 0;
            visibility: hidden;
        }

        .password-card {
            background: var(--card-bg);
            border: 1px solid var(--border-color);
            padding: 32px;
            border-radius: 20px;
            width: 90%;
            max-width: 380px;
            text-align: center;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.6);
        }

        .password-card h2 {
            font-size: 1.4rem;
            margin-bottom: 8px;
        }

        .password-card p {
            color: var(--text-muted);
            font-size: 0.9rem;
            margin-bottom: 20px;
        }

        .password-input {
            width: 100%;
            padding: 12px 16px;
            border-radius: 10px;
            border: 1px solid var(--border-color);
            background: rgba(0, 0, 0, 0.4);
            color: var(--text-main);
            font-size: 1rem;
            outline: none;
            margin-bottom: 12px;
            text-align: center;
            letter-spacing: 2px;
            transition: border-color 0.2s ease;
        }

        .password-input:focus {
            border-color: var(--accent-blue);
        }

        .password-btn {
            width: 100%;
            padding: 12px;
            border-radius: 10px;
            border: none;
            background: linear-gradient(135deg, var(--accent-blue), var(--accent-purple));
            color: #0d0f12;
            font-weight: 700;
            font-size: 1rem;
            cursor: pointer;
            transition: opacity 0.2s ease;
        }

        .password-btn:hover {
            opacity: 0.9;
        }

        .error-msg {
            color: var(--accent-red);
            font-size: 0.85rem;
            margin-top: 10px;
            display: none;
        }

        /* Layout Elements */
        header { text-align: center; margin-bottom: 40px; }
        .avatar {
            width: 96px; height: 96px; border-radius: 50%;
            background: linear-gradient(135deg, var(--accent-blue), var(--accent-purple));
            display: flex; align-items: center; justify-content: center;
            font-size: 36px; font-weight: 800; color: #0d0f12;
            margin: 0 auto 20px auto; box-shadow: 0 0 25px rgba(88, 166, 255, 0.2);
        }
        h1 {
            font-size: 2.5rem; font-weight: 800; letter-spacing: -0.5px; margin-bottom: 8px;
            background: linear-gradient(90deg, #ffffff, #8b949e);
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
        }
        .subtitle { font-size: 1.1rem; color: var(--text-muted); font-weight: 400; }
        .badge-container { display: flex; gap: 10px; justify-content: center; margin-top: 15px; flex-wrap: wrap; }
        .badge {
            background: rgba(255, 255, 255, 0.05); border: 1px solid var(--border-color);
            padding: 6px 14px; border-radius: 20px; font-size: 0.85rem; color: var(--accent-blue); font-weight: 600;
        }
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px; margin-top: 20px; }
        .card {
            background: var(--card-bg); border: 1px solid var(--border-color);
            border-radius: 16px; padding: 24px; backdrop-filter: blur(12px); transition: all 0.3s ease;
        }
        .card:hover { transform: translateY(-5px); border-color: rgba(88, 166, 255, 0.4); }
        .card h2 { font-size: 1.25rem; margin-bottom: 10px; }
        .card p { color: var(--text-muted); font-size: 0.95rem; line-height: 1.5; }
        footer { margin-top: 50px; text-align: center; color: var(--text-muted); font-size: 0.85rem; }
    </style>
</head>
<body>

    <!-- Overlay Acces Protejat -->
    <div class="password-overlay" id="pwdOverlay">
        <div class="password-card">
            <h2>🔒 Zone Protejată</h2>
            <p>Introdu parola pentru a accesa site-ul</p>
            <input type="password" id="pwdInput" class="password-input" placeholder="Parolă..." autofocus>
            <button onclick="checkPassword()" class="password-btn">Deblochează</button>
            <p id="errorMsg" class="error-msg">Parolă incorectă!</p>
        </div>
    </div>

    <!-- Conținut Site -->
    <div class="content-wrapper">
        <header>
            <div class="avatar">D</div>
            <h1>Dragoș Orlenschi</h1>
            <p class="subtitle">Bio-Chemistry Student & Tech Enthusiast</p>
            
            <div class="badge-container">
                <span class="badge">🧬 Bio-Chimie</span>
                <span class="badge">💻 Web Development</span>
                <span class="badge">⚙️ Dev Setup</span>
            </div>
        </header>

        <div class="grid">
            <div class="card">
                <h2>🧪 Profil</h2>
                <p>Elev la profilul de Bio-Chimie, pasionat de tehnologie, configurări de sisteme și optimizări web.</p>
            </div>

            <div class="card">
                <h2>🛠️ Proiecte</h2>
                <p>Acest site este găzduit direct pe GitHub Pages și configurat custom folosind propriul domeniu <code>dragosorl.me</code>.</p>
            </div>

            <div class="card">
                <h2>⚡ Lab & Setup</h2>
                <p>Experimentez cu unelte moderne de dezvoltare, securitate digitală, rețelistică și automatizări în Python.</p>
            </div>
        </div>

        <footer>
            <p>© 2026 dragosorl.me • Powered by GitHub Pages</p>
        </footer>
    </div>

    <script>
        // ============================================================
        // CONFIGURARE PAROLE (AICI ADAUGI SAU SCHIMBI PAROLELE)
        // ============================================================
        const VALID_PASSWORDS = [
            "dragos2026",    // Parola ta principală
            "admin",         // Exemplu: Parolă secundară (poți adăuga altele între ghilimele)
            "secret123"      // Exemplu: Altă parolă permisă
        ];

        // Verifică dacă utilizatorul a deblocat deja sesiunea curentă
        if (sessionStorage.getItem('siteUnlocked') === 'true') {
            document.body.classList.add('unlocked');
        }

        function checkPassword() {
            const inputVal = document.getElementById('pwdInput').value;
            const errorMsg = document.getElementById('errorMsg');

            // Verificăm dacă parola introdusă există în lista de parole valide
            if (VALID_PASSWORDS.includes(inputVal)) {
                document.body.classList.add('unlocked');
                sessionStorage.setItem('siteUnlocked', 'true');
            } else {
                errorMsg.style.display = 'block';
                document.getElementById('pwdInput').value = '';
            }
        }

        // Permite deblocarea apăsând tasta Enter
        document.getElementById('pwdInput').addEventListener('keypress', function (e) {
            if (e.key === 'Enter') {
                checkPassword();
            }
        });
    </script>
</body>
</html>

