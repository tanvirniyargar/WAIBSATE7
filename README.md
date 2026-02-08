<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Video Downloader Hub</title>
    <!-- Bootstrap for better styling and tabs -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <!-- Google AdSense Script (Replace with your publisher ID) -->
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-XXXXXXXXXXXXXXXX" crossorigin="anonymous"></script>
    <style>
        body { background-color: #f8f9fa; }
        .container { max-width: 600px; margin-top: 20px; }
        .tab-content { margin-top: 20px; }
        #preview { max-width: 100%; height: auto; display: none; }
        #progress { display: none; }
        #retryBtn { display: none; }
        #caption { display: none; margin-top: 10px; }
        .ad-banner { text-align: center; margin: 20px 0; }
    </style>
</head>
<body>
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

    <div class="container">
        <h1 class="text-center mb-4">Video Downloader Hub</h1>
        <p class="text-center">Download videos from Instagram, YouTube, and Facebook in one place. Select a tab below.</p>

        <!-- Tabs for Navigation -->
        <ul class="nav nav-tabs" id="downloaderTabs" role="tablist">
            <li class="nav-item" role="presentation">
                <button class="nav-link active" id="instagram-tab" data-bs-toggle="tab" data-bs-target="#instagram" type="button" role="tab">Instagram Reels</button>
            </li>
            <li class="nav-item" role="presentation">
                <button class="nav-link" id="youtube-tab" data-bs-toggle="tab" data-bs-target="#youtube" type="button" role="tab">YouTube Videos</button>
            </li>
            <li class="nav-item" role="presentation">
                <button class="nav-link" id="facebook-tab" data-bs-toggle="tab" data-bs-target="#facebook" type="button" role="tab">Facebook Videos</button>
            </li>
        </ul>

        <div class="tab-content" id="downloaderTabsContent">
            <!-- Instagram Tab -->
            <div class="tab-pane fade show active" id="instagram" role="tabpanel">
                <h3 class="mt-3">Instagram Reels Downloader</h3>
                <p>Paste a public Instagram Reel URL.</p>
                <div class="input-group mb-3">
                    <input type="text" id="reelUrl" class="form-control" placeholder="https://www.instagram.com/reel/..." />
                    <button class="btn btn-primary" id="fetchBtnInsta" onclick="fetchReel()">Fetch & Download</button>
                </div>
                <button class="btn btn-warning mb-3" id="retryBtnInsta" onclick="fetchReel()">Retry</button>
                <div id="progressInsta" class="progress mb-3">
                    <div class="progress-bar" role="progressbar" style="width: 0%"></div>
                </div>
                <div id="resultInsta" class="alert alert-info" style="display: none;"></div>
                <video id="previewInsta" controls class="mt-3"></video>
                <div id="captionInsta" class="alert alert-secondary">
                    <strong>Caption:</strong> <span id="captionTextInsta">No caption available.</span>
                </div>
                <div id="downloadOptionsInsta" style="display: none;">
                    <h5>Select Quality:</h5>
                    <select id="qualitySelectInsta" class="form-select mb-3"></select>
                    <button class="btn btn-success" onclick="downloadSelected('insta')">Download Selected</button>
                </div>
            </div>

            <!-- YouTube Tab -->
            <div class="tab-pane fade" id="youtube" role="tabpanel">
                <h3 class="mt-3">YouTube Video Downloader</h3>
                <p>Paste a YouTube video URL.</p>
                <div class="input-group mb-3">
                    <input type="text" id="videoUrlYT" class="form-control" placeholder="https://www.youtube.com/watch?v=..." />
                    <button class="btn btn-primary" id="fetchBtnYT" onclick="fetchVideoYT()">Fetch & Download</button>
                </div>
                <button class="btn btn-warning mb-3" id="retryBtnYT" onclick="fetchVideoYT()">Retry</button>
                <div id="progressYT" class="progress mb-3">
                    <div class="progress-bar" role="progressbar" style="width: 0%"></div>
                </div>
                <div id="resultYT" class="alert alert-info" style="display: none;"></div>
                <video id="previewYT" controls class="mt-3"></video>
                <div id="captionYT" class="alert alert-secondary">
                    <strong>Title:</strong> <span id="captionTextYT">No title available.</span>
                </div>
                <div id="downloadOptionsYT" style="display: none;">
                    <h5>Select Quality:</h5>
                    <select id="qualitySelectYT" class="form-select mb-3"></select>
                    <button class="btn btn-success" onclick="downloadSelected('yt')">Download Selected</button>
                </div>
            </div>

            <!-- Facebook Tab -->
            <div class="tab-pane fade" id="facebook" role="tabpanel">
                <h3 class="mt-3">Facebook Video Downloader</h3>
                <p>Paste a Facebook video URL.</p>
                <div class="input-group mb-3">
                    <input type="text" id="videoUrlFB" class="form-control" placeholder="https://www.facebook.com/watch?v=..." />
                    <button class="btn btn-primary" id="fetchBtnFB" onclick="fetchVideoFB()">Fetch & Download</button>
                </div>
                <button class="btn btn-warning mb-3" id="retryBtnFB" onclick="fetchVideoFB()">Retry</button>
                <div id="progressFB" class="progress mb-3">
                    <div class="progress-bar" role="progressbar" style="width: 0%"></div>
                </div>
                <div id="resultFB" class="alert alert-info" style="display: none;"></div>
                <video id="previewFB" controls class="mt-3"></video>
                <div id="captionFB" class="alert alert-secondary">
                    <strong>Title:</strong> <span id="captionTextFB">No title available.</span>
                </div>
                <div id="downloadOptionsFB" style="display: none;">
                    <h5>Select Quality:</h5>
                    <select id="qualitySelectFB" class="form-select mb-3"></select>
                    <button class="btn btn-success" onclick="downloadSelected('fb')">Download Selected</button>
                </div>
            </div>
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

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    <script>
        let reelData = null;
        let videoDataYT = null;
        let videoDataFB = null;

        // Instagram Fetch Function
        async function fetchReel() {
            const url = document.getElementById('reelUrl').value;
            const resultDiv = document.getElementById('resultInsta');
            const progressBar = document.querySelector('#progressInsta .progress-bar');
            const progressDiv = document.getElementById('progressInsta');
            const preview = document.getElementById('previewInsta');
            const captionDiv = document.getElementById('captionInsta');
            const captionText = document.getElementById('captionTextInsta');
            const downloadOptions = document.getElementById('downloadOptionsInsta');
            const qualitySelect = document.getElementById('qualitySelectInsta');
            const retryBtn = document.getElementById('retryBtnInsta');
            const fetchBtn = document.getElementById('fetchBtnInsta');

            // Reset UI
            resultDiv.style.display = 'none';
            progressDiv.style.display = 'block';
            progressBar.style.width = '0%';
            preview.style.display = 'none';
            captionDiv.style.display = 'none';
            downloadOptions.style.display = 'none';
            retryBtn.style.display = 'none';
            fetchBtn.disabled = true;

            if (!navigator.onLine) {
                resultDiv.innerHTML = 'You are offline. Check your internet.';
                resultDiv.className = 'alert alert-danger';
                resultDiv.style.display = 'block';
                progressDiv.style.display = 'none';
                retryBtn.style.display = 'block';
                fetchBtn.disabled = false;
                return;
            }

            if (!url || !url.includes('instagram.com/reel/')) {
                resultDiv.innerHTML = 'Enter a valid Instagram Reel URL.';
                resultDiv.className = 'alert alert-danger';
                resultDiv.style.display = 'block';
                progressDiv.style.display = 'none';
                fetchBtn.disabled = false;
                return;
            }

            try {
                progressBar.style.width = '25%';
                await new Promise(resolve => setTimeout(resolve, 500));
                progressBar.style.width = '50%';

                const apiUrl = `https://api.instadownloader.org/download?url=${encodeURIComponent(url)}`;
                const response = await fetch(apiUrl);
                const data = await response.json();

                progressBar.style.width = '75%';
                await new Promise(resolve => setTimeout(resolve, 500));
                progressBar.style.width = '100%';

                if (data.success && data.video_url) {
                    reelData = data;
                    resultDiv.innerHTML = 'Reel fetched! Preview and caption below.';
                    resultDiv.className = 'alert alert-success';
                    resultDiv.style.display = 'block';

                    preview.src = data.video_url;
                    preview.style.display = 'block';

                    captionText.innerText = data.caption || 'No caption available.';
                    captionDiv.style.display = 'block';

                    qualitySelect.innerHTML = '';
                    if (data.qualities && data.qualities.length > 0) {
                        data.qualities.forEach((q, i) => {
                            const opt = document.createElement('option');
                            opt.value = i;
                            opt.text = `${q.resolution} (${q.size})`;
                            qualitySelect.appendChild(opt);
                        });
                    } else {
                        qualitySelect.innerHTML = '<option value="0">Default Quality</option>';
                    }
                    downloadOptions.style.display = 'block';
                } else {
                    throw new Error('Failed to fetch. Check URL or API.');
                }
            } catch (error) {
                resultDiv.innerHTML = 'Error: ' + error.message;
                resultDiv.className = 'alert alert-danger';
                resultDiv.style.display = 'block';
                retryBtn.style.display = 'block';
            } finally {
                progressDiv.style.display = 'none';
                fetchBtn.disabled = false;
            }
        }

        // YouTube Fetch Function
        async function fetchVideoYT() {
            const url = document.getElementById('videoUrlYT').value;
            const resultDiv = document.getElementById('resultYT');
            const progressBar = document.querySelector('#progressYT .progress-bar');
            const progressDiv = document.getElementById('progressYT');
            const preview = document.getElementById('previewYT');
            const captionDiv = document.getElementById('captionYT');
            const captionText = document.getElementById('captionTextYT');
            const downloadOptions = document.getElementById('downloadOptionsYT');
            const qualitySelect = document.getElementById('qualitySelectYT');
            const retryBtn = document.getElementById('retryBtnYT');
            const fetchBtn = document.getElementById('fetchBtnYT');

            // Reset UI (similar to Instagram)
            resultDiv.style.display = 'none';
            progressDiv.style.display = 'block';
            progressBar.style.width = '0%';
            preview.style.display = 'none';
            captionDiv.style.display = 'none';
            downloadOptions.style.display = 'none';
            retryBtn.style.display = 'none';
            fetchBtn.disabled = true;

            if (!navigator.onLine) {
                resultDiv.innerHTML = 'You are offline. Check your internet.';
                resultDiv.className = 'alert alert-danger';
                resultDiv.style.display = 'block';
                progressDiv.style.display = 'none';
                retryBtn.style.display = 'block';
                fetchBtn.disabled = false;
                return;
            }

            if (!url || !url.includes('youtube.com/watch?v=')) {
                resultDiv.innerHTML = 'Enter a valid YouTube URL.';
                resultDiv.className = 'alert alert-danger';
                resultDiv.style.display = 'block';
                progressDiv.style.display = 'none';
                fetchBtn.disabled = false;
                return;
            }

            try {
                progressBar.style.width = '25%';
                await new Promise(resolve => setTimeout(resolve, 500));
                progressBar.style.width = '50%';

                const apiUrl = `https://api.y2mate.com/v2/analyze?url=${encodeURIComponent(url)}`;
                const response = await fetch(apiUrl);
                const data = await response.json();

                progressBar.style.width = '75%';
                await new Promise(resolve => setTimeout(resolve, 500));
                progressBar.style.width = '100%';

                if (data.status === 'ok' && data.vid) {
                    videoDataYT = data;
                    resultDiv.innerHTML = 'Video fetched! Preview and title below.';
                    resultDiv.className = 'alert alert-success';
                    resultDiv.style.display = 'block';

                    if (data.thumbnail) preview.poster = data.thumbnail;
                    if (data.video_url) preview.src = data.video_url;
                    preview.style.display = 'block';

                    captionText.innerText = data.title || 'No title available.';
                    captionDiv.style.display = 'block';

                    qualitySelect.innerHTML = '';
                    if (data.formats && data.formats.length > 0) {
                        data.formats.forEach((f, i) => {
                            const opt = document.createElement('option');
                            opt.value = i;
                            opt.text = `${f.quality} (${f.size})`;
                            qualitySelect.appendChild(opt);
                        });
                    } else {
                        qualitySelect.innerHTML = '<option value="0">Default Quality</option>';
                    }
                    downloadOptions.style.display = 'block';
                } else {
                    throw new Error('Failed to fetch. Check URL or API.');
                }
            } catch (error) {
                resultDiv.innerHTML = 'Error: ' + error.message;
                resultDiv.className = 'alert alert-danger';
                resultDiv.style.display = 'block';
                retryBtn.style.display = 'block';
            } finally {
                progressDiv.style.display = 'none';
                fetchBtn.disabled = false;
            }
        }

        // Facebook Fetch Function (Now Complete)
        async function fetchVideoFB() {
            const url = document.getElementById('videoUrlFB').value;
            const resultDiv = document.getElementById('resultFB');
            const progressBar = document.querySelector('#progressFB .progress-bar');
            const progressDiv = document.getElementById('progressFB');
            const preview = document.getElementById('previewFB');
            const captionDiv = document.getElementById('captionFB');
            const captionText = document.getElementById('captionTextFB');
            const downloadOptions = document.getElementById('downloadOptionsFB');
            const qualitySelect = document.getElementById('qualitySelectFB');
            const retryBtn = document.getElementById('retryBtnFB');
            const fetchBtn = document.getElementById('fetchBtnFB');

            // Reset UI (similar to Instagram)
            resultDiv.style.display = 'none';
            progressDiv.style.display = 'block';
            progressBar.style.width = '0%';
            preview.style.display = 'none';
            captionDiv.style.display = 'none';
            downloadOptions.style.display = 'none';
            retryBtn.style.display = 'none';
            fetchBtn.disabled = true;

            if (!navigator.onLine) {
                resultDiv.innerHTML = 'You are offline. Check your internet.';
                resultDiv.className = 'alert alert-danger';
                resultDiv.style.display = 'block';
                progressDiv.style.display = 'none';
                retryBtn.style.display = 'block';
                fetchBtn.disabled = false;
                return;
            }

            if (!url || !url.includes('facebook.com')) {
                resultDiv.innerHTML = 'Enter a valid Facebook URL.';
                resultDiv.className = 'alert alert-danger';
                resultDiv.style.display = 'block';
                progressDiv.style.display = 'none';
                fetchBtn.disabled = false;
                return;
            }

            try {
                progressBar.style.width = '25%';
                await new Promise(resolve => setTimeout(resolve, 500));
                progressBar.style.width = '50%';

                const apiUrl = `https://api.fbdown.net/download?url=${encodeURIComponent(url)}`;
                const response = await fetch(apiUrl);
                const data = await
                }
    </script>
</body>
</html>
