<!DOCTYPE html>
<html lang="id">
<head>
    <style>
        body {
            position: relative;
        }

        /* Tambahkan waktu di pojok kanan atas */
        .current-time {
            position: absolute;
            top: 20px;
            right: 20px;
            font-size: 18px;
        }

        /* Tambahkan tanggal dan negara di pojok kiri atas */
        .date-and-country {
            position: absolute;
            top: 20px;
            left: 20px;
            font-size: 18px;
        }

        /* Tambahkan animasi */
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* Tambahkan informasi baterai di pojok kanan atas (di bawah waktu) */
        .battery-info {
            position: absolute;
            top: 50px; /* Di bawah waktu */
            right: 20px;
            font-size: 16px;
            animation: fadeIn 2s ease-in-out; /* Tambahkan animasi fade-in */
        }

        /* Tambahkan informasi ping di pojok kiri atas (di bawah tanggal dan negara) */
        .ping-info {
            position: absolute;
            top: 50px; /* Di bawah tanggal dan negara */
            left: 20px;
            font-size: 16px;
            animation: fadeIn 2s ease-in-out; /* Tambahkan animasi fade-in */
        }

        /* Tambahkan informasi runtime handphone di pojok kanan atas (di bawah baterai) */
        .runtime-info {
            position: absolute;
            top: 80px; /* Di bawah baterai */
            right: 20px;
            font-size: 16px;
            animation: fadeIn 2s ease-in-out; /* Tambahkan animasi fade-in */
        }

        /* Tambahkan informasi FPS di pojok kiri atas (di bawah ping) */
        .fps-info {
            position: absolute;
            top: 80px; /* Di bawah ping */
            left: 20px;
            font-size: 16px;
            animation: fadeIn 2s ease-in-out; /* Tambahkan animasi fade-in */
        }
    </style>
</head>
<body>
    <!-- Tambahkan elemen waktu -->
    <div class="current-time" id="current-time"></div>

    <!-- Tambahkan elemen tanggal dan negara -->
    <div class="date-and-country">
        <span id="current-date"></span> | <span id="current-country">Indonesia</span>
    </div>

    <!-- Tambahkan informasi baterai -->
    <div class="battery-info" id="battery-info"></div>

    <!-- Tambahkan informasi ping -->
    <div class="ping-info" id="ping-info"></div>

    <!-- Tambahkan informasi runtime handphone -->
    <div class="runtime-info" id="runtime-info"></div>

    <!-- Tambahkan informasi FPS -->
    <div class="fps-info" id="fps-info"></div>

    <script>
        // Script untuk menampilkan waktu
        function updateTime() {
            const now = new Date();
            const options = { hour: 'numeric', minute: 'numeric', second: 'numeric', hour12: false };
            const timeString = now.toLocaleString('en-US', options);
            document.getElementById('current-time').textContent = timeString;
        }

        // Script untuk menampilkan tanggal
        function updateDate() {
            const now = new Date();
            const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
            const dateString = now.toLocaleDateString('id-ID', options);
            document.getElementById('current-date').textContent = dateString;
        }

        // Script untuk mendapatkan informasi baterai
        function updateBattery() {
            navigator.getBattery().then(function(battery) {
                const batteryInfo = Math.floor(battery.level * 100) + "%";
                document.getElementById('battery-info').textContent = "Battery: " + batteryInfo;
            }).catch(function(err) {
                console.log("Error getting battery information: ", err);
            });
        }

        // Script untuk mendapatkan informasi ping
        function updatePing() {
            const startTime = Date.now();
            const img = new Image();
            img.onload = function() {
                const endTime = Date.now();
                const ping = endTime - startTime + "ms";
                document.getElementById('ping-info').textContent = "Ping: " + ping;
            };
            img.onerror = function() {
                document.getElementById('ping-info').textContent = "Ping: Error";
            };
            img.src = "https://www.google.com/images/phd/px.gif?t=" + startTime;
        }

        // Script untuk mendapatkan informasi runtime handphone
        function updateRuntime() {
            navigator.getBattery().then(function(battery) {
                const timeRemaining = battery.dischargingTime;
                const hours = Math.floor(timeRemaining / 60);
                const minutes = timeRemaining % 60;
                document.getElementById('runtime-info').textContent = "Runtime: " + hours + "h " + minutes + "m";
            }).catch(function(err) {
                console.log("Error getting battery information: ", err);
            });
        }

        // Script untuk mendapatkan informasi FPS
        function updateFPS() {
            let lastCalledTime = performance.now();
            let frames = 0;
            function update() {
                frames++;
                const delta = performance.now() - lastCalledTime;
                if (delta >= 1000) {
                    const fps = Math.round(frames * 1000 / delta);
                    document.getElementById('fps-info').textContent = "FPS: " + fps;
                    frames = 0;
                    lastCalledTime = performance.now();
                }
                requestAnimationFrame(update);
            }
            update();
        }

        // Panggil fungsi-fungsi untuk pertama kali
        updateTime();
        updateDate();
        updateBattery();
        updatePing();
        updateRuntime();
        updateFPS();

        // Perbarui waktu setiap detik
        setInterval(updateTime, 1000);
    </script>
</body>
</html>


<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Profil Keren</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css">
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: 'Poppins', Arial, sans-serif;
            background: url('https://telegra.ph/file/dbdfdc0a1d8038a09952f.jpg') no-repeat center center fixed;
            background-size: cover;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
            color: white;
            text-shadow: 1px 1px 5px black;
            animation: backgroundAnimation 20s infinite alternate;
        }

        .profile-card {
            background: rgba(0, 0, 0, 0.8);
            border-radius: 15px;
            padding: 30px;
            width: 350px;
            text-align: center;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.6);
            transition: transform 0.3s, box-shadow 0.3s;
            animation: fadeIn 1.5s ease-in-out;
        }

        .profile-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 16px 32px rgba(0, 0, 0, 0.8);
        }

        .profile-card img {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            border: 3px solid white;
            margin-bottom: 15px;
            box-shadow: 0 0 15px rgba(255, 255, 255, 0.6);
            animation: rotateProfile 9s linear infinite;
            transition: transform 0.3s;
        }

        .profile-card:hover img {
            transform: scale(1.1);
        }

        .profile-card h2 {
            margin: 15px 0;
            font-size: 26px;
            letter-spacing: 1px;
            transition: color 0.3s;
        }

        .profile-card:hover h2 {
            color: #ffcc00;
        }

        .profile-card p {
            font-size: 18px;
            line-height: 1.6;
            margin-bottom: 20px;
            animation: slideIn 1.5s ease-in-out;
        }

        .social-icons {
            margin-top: 25px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .social-icons a {
            color: white;
            text-decoration: none;
            margin: 0 12px;
            font-size: 26px;
            transition: transform 0.3s, color 0.3s;
            position: relative;
        }

        .social-icons a:hover {
            color: #ffcc00;
        }

        .social-icons a::before {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            background: rgba(255, 255, 255, 0.3);
            border-radius: 50%;
            z-index: -1;
            transition: transform 0.4s ease-out;
            transform: scale(0);
        }

        .social-icons a:hover::before {
            transform: scale(2);
        }

        /* Tambahkan CSS untuk ikon sociabuz */
        .social-icons a.sociabuz {
            color: #FF6600; /* Warna Sociabuz */
        }

        .social-icons a.sociabuz:hover {
            color: #FF6600; /* Warna Sociabuz saat Hover */
        }

        /* Ganti ikon Sociabuz */
        .social-icons a.sociabuz::before {
            content: "\f2c0"; /* Unicode untuk ikon Anime Face */
            font-family: "Font Awesome 5 Free";
            font-weight: 900;
            font-style: normal;
        }

        .social-icons a.sociabuz:hover::before {
            transform: scale(2);
        }

        @keyframes backgroundAnimation {
            0% { background-position: center; }
            100% { background-position: top left; }
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: scale(0.8);
            }
            to {
                opacity: 1;
                transform: scale(1);
            }
        }

        @keyframes rotateProfile {
            from {
                transform: rotate(0deg);
            }
            to {
                transform: rotate(360deg);
            }
        }

        @keyframes slideIn {
            from {
                transform: translateY(100%);
            }
            to {
                transform: translateY(0);
            }
        }
    </style>
</head>
<body>
    <div class="profile-card">
        <img src="https://telegra.ph/file/4ccca01111815f68c2ca2.jpg" alt="Profile Picture">
        <h2 id="profile-name">Kazami Kazuki</h2>
        <p>Jangan lupa beraq.</p>
        <div class="social-icons">
            <a href="https://www.facebook.com/profile.php?id=61554711097077&mibextid=rS40aB7S9Ucbxw6v" target="_blank" class="facebook"><i class="fab fa-facebook"></i></a>
            <a href="https://youtube.com/@florynfeatfuze?si=YoIed1UnZjlUu5nf" target="_blank" class="youtube"><i class="fab fa-youtube"></i></a>
            <a href="https://x.com/Kazukikazami03" target="_blank" class="twitter"><i class="fab fa-twitter"></i></a>
            <a href="https://www.instagram.com/isaacwestcott3?igsh=YzljYTk1ODg3Zg==" target="_blank" class="instagram"><i class="fab fa-instagram"></i></a>
            <a href="tiktok.com/@tokisakikurumi__12peluru" target="_blank" class="tiktok"><i class="fab fa-tiktok"></i></a>
            <a href="https://maohgakuin.com" target="_blank" class="globe"><i class="fas fa-globe"></i></a>
            
            <!-- Ganti ikon Sociabuz -->
            <a href="https://sociabuz.com/kazuki" target="_blank" class="sociabuz"><i class="far fa-laugh-beam"></i></a>
        </div>
    </div>
</body>
</html>
