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
            --accent-green: #3fb950;
            --accent-purple: #bc8cff;
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

        .container {
            max-width: 800px;
            width: 100%;
        }

        header {
            text-align: center;
            margin-bottom: 40px;
        }

        .avatar {
            width: 96px;
            height: 96px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--accent-blue), var(--accent-purple));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 36px;
            font-weight: 800;
            color: #0d0f12;
            margin: 0 auto 20px auto;
            box-shadow: 0 0 25px rgba(88, 166, 255, 0.2);
        }

        h1 {
            font-size: 2.5rem;
            font-weight: 800;
            letter-spacing: -0.5px;
            margin-bottom: 8px;
            background: linear-gradient(90deg, #ffffff, #8b949e);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .subtitle {
            font-size: 1.1rem;
            color: var(--text-muted);
            font-weight: 400;
        }

        .badge-container {
            display: flex;
            gap: 10px;
            justify-content: center;
            margin-top: 15px;
            flex-wrap: wrap;
        }

        .badge {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--border-color);
            padding: 6px 14px;
            border-radius: 20px;
            font-size: 0.85rem;
            color: var(--accent-blue);
            font-weight: 600;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .card {
            background: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 16px;
            padding: 24px;
            backdrop-filter: blur(12px);
            transition: all 0.3s ease;
        }

        .card:hover {
            transform: translateY(-5px);
            border-color: rgba(88, 166, 255, 0.4);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
        }

        .card h2 {
            font-size: 1.25rem;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .card p {
            color: var(--text-muted);
            font-size: 0.95rem;
            line-height: 1.5;
        }

        footer {
            margin-top: 50px;
            text-align: center;
            color: var(--text-muted);
            font-size: 0.85rem;
        }

        footer a {
            color: var(--accent-blue);
            text-decoration: none;
        }

        footer a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>

    <div class="container">
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

</body>
</html>
