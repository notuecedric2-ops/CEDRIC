<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mon Lecteur IPTV Privé</title>
    <!-- Lecteur Vidéo Video.js pour supporter le format M3U8 (HLS) -->
    <link href="https://zencdn.net" rel="stylesheet" />
    <style>
        body { font-family: Arial, sans-serif; background: #121212; color: #fff; text-align: center; margin: 0; padding: 20px; }
        .hidden { display: none !important; }
        #login-container { max-width: 400px; margin: 100px auto; padding: 30px; background: #1e1e1e; border-radius: 8px; box-shadow: 0 4px 10px rgba(0,0,0,0.5); }
        input, button, select { padding: 12px; margin: 10px 0; width: 100%; border-radius: 4px; border: none; font-size: 16px; box-sizing: border-box; }
        input { background: #333; color: #fff; }
        button { background: #00ADB5; color: white; font-weight: bold; cursor: pointer; }
        button:hover { background: #008088; }
        #app-container { max-width: 800px; margin: 0 auto; }
        .video-js { margin: 20px auto; width: 100%; max-width: 720px; height: 405px; border-radius: 8px; }
    </style>
</head>
<body>

    <!-- ÉCRAN DE SÉCURITÉ -->
    <div id="login-container">
        <h2>Accès Restreint</h2>
        <p>Veuillez entrer le code d'accès pour lire les chaînes.</p>
        <input type="password" id="access-code" placeholder="Entrez le code ici...">
        <button onclick="checkCode()">Valider</button>
        <p id="error-msg" style="color: #ff4a4a; display: none;">Code incorrect !</p>
    </div>

    <!-- ÉCRAN PRINCIPAL (IPTV) -->
    <div id="app-container" class="hidden">
        <h1>📺 Mon Espace IPTV Libre de Droits</h1>
        
        <label for="channel-select">Choisir une chaîne :</label>
        <select id="channel-select" onchange="changeChannel(this.value)">
            <option value="">-- Sélectionnez une chaîne --</option>
            <!-- Flux de test libres de droits (France 24 et Arte) -->
            <option value="https://france24.com">France 24 (Direct)</option>
            <option value="https://akamaihd.net">Arte (Direct)</option>
        </select>

        <div class="video-container">
            <video id="my-video" class="video-js vjs-default-skin vjs-big-play-centered" controls preload="auto" width="720" height="405">
                <p class="vjs-no-js">Pour voir cette vidéo, activez JavaScript ou utilisez un navigateur compatible.</p>
            </video>
        </div>
    </div>

    <!-- Scripts pour le lecteur -->
    <script src="https://zencdn.net"></script>
    <script>
        // 🔑 MODIFIEZ LE CODE D'ACCÈS ICI
        const CODE_CORRECT = "MonCodeSecret2026"; 

        // Initialisation du lecteur vidéo
        let player = videojs('my-video');

        // Fonction de vérification du code
        function checkCode() {
            const inputCode = document.getElementById('access-code').value;
            const errorMsg = document.getElementById('error-msg');

            if (inputCode === CODE_CORRECT) {
                document.getElementById('login-container').classList.add('hidden');
                document.getElementById('app-container').classList.remove('hidden');
            } else {
                errorMsg.style.display = 'block';
                document.getElementById('access-code').value = '';
            }
        }

        // Fonction pour changer de chaîne
        function changeChannel(url) {
            if (url) {
                player.src({ type: 'application/x-mpegURL', src: url });
                player.play();
            } else {
                player.reset();
            }
        }
    </script>
</body>
</html>
# CEDRIC
IPTV NOTUE
