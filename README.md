<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VIP Multi-Platform Video Downloader</title>
    <!-- Bootstrap and Custom Fonts -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700&family=Roboto:wght@300;500&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <!-- Google AdSense Script (Replace with your publisher ID) -->
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-XXXXXXXXXXXXXXXX" crossorigin="anonymous"></script>
    <style>
        body {
            background: linear-gradient(135deg, #000000, #1a1a1a);
            color: #f4f4f4;
            font-family: 'Roboto', sans-serif;
            overflow-x: hidden;
        }
        .vip-header {
            background: linear-gradient(90deg, #FFD700, #FFA500);
            color: #000;
            padding: 20px;
            text-align: center;
            box-shadow: 0 4px 10px rgba(255, 215, 0, 0.5);
        }
        .vip-header h1 {
            font-family: 'Playfair Display', serif;
            font-size: 2.5rem;
            margin: 0;
        }
        .vip-badge {
            background: #FFD700;
            color: #000;
            padding: 5px 10px;
            border-radius: 20px;
            font-weight: bold;
            display: inline-block;
            margin-left: 10px;
        }
        .container {
            max-width: 700px;
            margin-top: 30px;
            background: rgba(255, 255, 255, 0.05);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.5);
            backdrop-filter: blur(10px);
        }
        .btn-vip {
            background: linear-gradient(45deg, #FFD700, #FFA500);
            color: #000;
            border: none;
            padding: 12px 25px;
            border-radius: 25px;
            font-weight: 500;
            transition: all 0.3s ease;
        }
        .btn-vip:hover {
            transform: scale(1.05);
            box-shadow: 0 4px 15px rgba(255, 215, 0, 0.5);
        }
        .progress {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
        }
        .progress-bar {
            background: linear-gradient(90deg, #FFD700, #FFA500);
            transition: width 0.5s ease;
        }
        .alert {
            border-radius: 10px;
            backdrop-filter: blur(5px);
        }
        video {
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.5);
        }
        .history {
            margin-top: 20px;
            background: rgba(255, 255, 255, 0.05);
            padding: 15px;
            border-radius: 10px;
        }
        .history h5 {
            color: #FFD700;
        }
        .ad-banner {
            text-align: center;
            margin: 20px 0;
        }
        .footer {
            text-align: center;
            padding: 20px;
            background: rgba(0, 0, 0, 0.8);
            color: #ccc;
            margin-top: 30px;
        }
        .footer a {
            color: #FFD700;
            text-decoration: none;
        }
        .fade-in {
            animation: fadeIn 1s ease-in;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>
    <!-- VIP Header -->
    <div class="vip-header fade-in">
        <h1><i class="fas fa-crown"></i> VIP Multi-Platform Video Downloader <span class="vip-badge">PREMIUM</span></h1>
        <p>Exclusive downloads from Instagram, YouTube, and Facebook in one VIP hub.</p>
    </div>

    <!-- Top Ad Banner -->
    <div class="ad-banner">
        <ins class="adsbygoogle"
             style="display:block"
             data-ad-client="ca-pub-XXXXXXXXXXXXXXXX"
             data-ad-slot="YYYYYYYYYY"
             data-ad-format="auto"
             data-full-width-responsive="true"></ins>
        <script>
             (adsbygoogle = window.adsbygoogle || []).push({});
        </script>
    </div>

    <div class="container fade-in">
        <p class="text-center">Paste any Instagram Reel, YouTube Video, or Facebook Video URL for instant VIP download.</p>
        
        <div class="input-group mb-3">
            <span class="input-group-text"><i class="fas fa-link"></i></span>
            <input type="text" id="videoUrl" class="form-control" placeholder="https://www.instagram.com/reel/... or youtube.com/watch?v=... or facebook.com/..." />
            <button class="btn btn-vip" id="fetchBtn" onclick="fetchVideo()"><i class="fas fa-download"></i> Fetch VIP Download</button>
        </div>
        
        <div class="form-check mb-3">
            <input class="form-check-input" type="checkbox" id="vipMode" />
            <label class="form-check-label" for="vipMode">
                Enable VIP Mode (Auto-download after fetch)
            </label>
        </div>
        
        <button class="btn btn-warning mb-3" id="retryBtn" onclick="fetchVideo()" style="display: none;"><i class="fas fa-redo"></i> Retry</button>
        
        <div id="progress" class="progress mb-3" style="display: none;">
            <div class="progress-bar" role="progressbar" style="width: 0%"></div>
        </div>
        
        <div id="result" class="alert alert-info" style="display: none;"></div>
        
        <video id="preview" controls class="mt-3" style="display: none;"></video>
        
        <div id="caption" class="alert alert-secondary mt-3" style="display: none;">
            <strong><i class="fas fa-comment"></i> Title/Caption:</strong> <span id="captionText">No title/caption available.</span>
        </div>
        
        <div id="downloadOptions" style="display: none;">
            <h5><i class="fas fa-cogs"></i> Select VIP Quality:</h5>
            <select id="qualitySelect" class="form-select mb-3"></select>
            <button class="btn btn-vip" onclick="downloadSelected()"><i class="fas fa-arrow-down"></i> Download Now</button>
        </div>
        
        <div class="history">
            <h5><i class="fas fa-history"></i> Recent Downloads (VIP History)</h5>
            <ul id="historyList" class="list-group list-group-flush">
                <!-- History items will be added here -->
            </ul>
        </div>
    </div>

    <!-- Bottom Ad Banner -->
    <div class="ad-banner">
        <ins class="adsbygoogle"
             style="display:block"
             data-ad-client="ca-pub-XXXXXXXXXXXXXXXX"
             data-ad-slot="ZZZZZZZZZZ"
             data-ad-format="auto"
             data-full-width-responsive="true"></ins>
        <script>
             (adsbygoogle = window.adsbygoogle || []).push({});
        </script>
    </div>

    <!-- Footer -->
    <div class="footer">
        <p>&copy; 2023 VIP Downloader. <a href="#">Privacy Policy</a> | <a href="#">Terms of Service</a> | <a href="#">Contact VIP Support</a></p>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    <script>
        let videoData = null;
        let downloadHistory = JSON.parse(localStorage.getItem('vipHistory')) || [];

        // Load history on page load
        function loadHistory() {
            const historyList = document.getElementById('historyList');
            historyList.innerHTML = '';
            downloadHistory.forEach((item, index) => {
                const li = document.createElement('li');
                li.className = 'list-group-item bg-transparent text-light';
                li.innerHTML = `<i class="fas fa-video"></i> ${item.title || 'Video'} - ${new Date(item.date).toLocaleString()}`;
                historyList.appendChild(li);
            });
        }
        loadHistory();

        async function fetchVideo() {
            const url = document.getElementById('videoUrl').value;
            const resultDiv = document.getElementById('result');
            const progressBar = document.querySelector('.progress-bar');
            const progressDiv = document.getElementById('progress');
            const preview = document.getElementById('preview');
            const captionDiv = document.getElementById('caption');
            const captionText = document.getElementById('captionText');
            const downloadOptions = document.getElementById('downloadOptions');
            const qualitySelect = document.getElementById('qualitySelect');
            const retryBtn = document.getElementById('retryBtn');
            const fetchBtn = document.getElementById('fetchBtn');
            const vipMode = document.getElementById('vipMode').checked;

            // Reset UI with animations
            resultDiv.style.display = 'none';
            progressDiv.style.display = 'block';
            progressBar.style.width = '0%';
            preview.style.display = 'none';
            captionDiv.style.display = 'none';
            downloadOptions.style.display = 'none';
            retryBtn.style.display = 'none';
            fetchBtn.disabled = true;

            if (!navigator.onLine) {
                resultDiv.innerHTML = '<i class="fas fa-wifi"></i> Offline. Check your VIP connection.';
                resultDiv.className = 'alert alert-danger';
                resultDiv.style.display = 'block';
                progressDiv.style.display = 'none';
                retryBtn.style.display = 'block';
                fetchBtn.disabled = false;
                return;
            }

            if (!url) {
                resultDiv.innerHTML = '<i class="fas fa-exclamation-triangle"></i> Please enter a URL.';
                resultDiv.className = 'alert alert-danger';
                resultDiv.style.display = 'block';
                progressDiv.style.display = 'none';
                fetchBtn.disabled = false;
                return;
            }

            // Detect platform
            let platform = '';
            if (url.includes('instagram.com/reel/')) {
                platform = 'instagram';
            } else if (url.includes('youtube.com/watch?v=')) {
                platform = 'youtube';
            } else if (url.includes('facebook.com')) {
                platform = 'facebook';
            } else {
                resultDiv.innerHTML = '<i class="fas fa-exclamation-triangle"></i> Invalid URL. Only Instagram Reels, YouTube Videos, or Facebook Videos are supported.';
                resultDiv.className = 'alert alert-danger';
                resultDiv.style.display = 'block';
                progressDiv.style.display = 'none';
                fetchBtn.disabled = false;
                return;
            }

            try {
                progressBar.style.width = '25%';
                await new Promise(resolve => setTimeout(resolve, 300));
                progressBar.style.width = '50%';

                let apiUrl = '';
                if (platform === 'instagram') {
                    apiUrl = `https://api.instadownloader.org/download?url=${encodeURIComponent(url)}`;
                } else if (platform === 'youtube') {
                    apiUrl = `https://api.y2mate.com/v2/analyze?url=${encodeURIComponent(url)}`;
                } else if (platform === 'facebook') {
                    apiUrl = `https://api.fbdown.net/download?url=${encodeURIComponent(url)}`;
                }

                const response = await fetch(apiUrl);
                const data = await response.json();

                progressBar.style.width = '75%';
                await new Promise(resolve => setTimeout(resolve, 300));
                progressBar.style.width = '100%';

                let success = false;
                let videoUrl = '';
                let title = '';
                let qualities = [];

                if (platform === 'instagram' && data.success && data.video_url) {
                    success = true;
                    videoUrl = data.video_url;
                    title = data.caption || 'Instagram Reel';
                    qualities = data.qualities || [];
                } else if (platform === 'youtube' && data.status === 'ok' && data.vid) {
                    success = true;
                    videoUrl = data.video_url || '';
                    title = data.title || 'YouTube Video';
                    qualities = data.formats || [];
                } else if (platform === 'facebook' && data.success && data.video_url) {
                    success = true;
                    videoUrl = data.video_url;
                    title = data.title || 'Facebook Video';
                    qualities = data.qualities || [];
                }

                if (success) {
                    videoData = { videoUrl, title, qualities, platform };
                    resultDiv.innerHTML = `<i class="fas fa-check-circle"></i> VIP Fetch Complete for ${platform.charAt(0).toUpperCase() + platform.slice(1)}! Preview below.`;
                    resultDiv.className = 'alert alert-success';
                    resultDiv.style.display = 'block';

                    if (videoUrl) {
                        preview.src = videoUrl;
                        preview.style.display = 'block';
                    }

                    captionText.innerText = title;
                    captionDiv.style.display = 'block';

                    qualitySelect.innerHTML = '';
                    if (qualities.length > 0) {
                        qualities.forEach((q, i) => {
                            const opt = document.createElement('option');
                            opt.value = i;
                            opt.text = `${q.quality || q.resolution} (${q.size}) - VIP Quality`;
                            qualitySelect.appendChild(opt);
                        });
                    } else {
                        qualitySelect.innerHTML = '<option value="0">Default VIP Quality</option>';
                    }
                    downloadOptions.style.display = 'block';

                    // VIP Mode: Auto-download
                    if (vipMode) {
                        setTimeout(() => downloadSelected(), 1000);
                    }

                    // Add to history
                    const historyItem = { title, date: new Date().toISOString(), platform };
                    downloadHistory.unshift(historyItem);
                    if (downloadHistory.length > 5) downloadHistory.pop();
                    localStorage.setItem('vipHistory', JSON.stringify(downloadHistory));
                    loadHistory();
                } else {
                    throw new Error(`VIP Fetch Failed for ${platform}. Check URL.`);
                }
            } catch (error) {
                resultDiv.innerHTML = '<i class="fas fa-times-circle"></i> Error: ' + error.message;
                resultDiv.className = 'alert alert-danger';
                resultDiv.style.display = 'block';
                retryBtn.style.display = 'block';
            } finally {
                progressDiv.style.display = 'none';
                fetchBtn.disabled = false;
            }
        }

        function downloadSelected() {
            if (!videoData) return;
            const selectedIndex = document.getElementById('qualitySelect').value;
            let downloadUrl = videoData.videoUrl;

            if (videoData.qualities && videoData.qualities[selectedIndex]) {
                downloadUrl = videoData.qualities[selectedIndex].url || videoData.qualities[selectedIndex].video_url;
            }

            const link = document.createElement('a');
            link.href = downloadUrl;
            link.download = `vip_${videoData.platform}_video.mp4`;
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        }
    </script>
</body>
</html>
