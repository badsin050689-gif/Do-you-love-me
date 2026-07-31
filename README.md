# Do-you-love-me
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Do you love me?</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap" rel="stylesheet">
 
    <style>
        *, *::before, *::after {
            box-sizing: border-box;
        }
 
        body {
            background-color: #000000;
            margin: 0;
            padding: 0;
            overflow: hidden;
            height: 100vh;
            font-family: 'Press Start 2P', monospace;
        }
        .wrapper {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 10;
        }
        .pixel-window {
            background-color: #000000;
            border: 6px double #ffffff;
            width: 400px;
            max-width: 90%;
            box-shadow: 12px 12px 0px #1a1a1a;
        }
 
        .window-bar {
            border-bottom: 4px solid #ffffff;
            padding: 10px;
            display: flex;
            gap: 6px;
        }
 
        .window-dot {
            width: 8px;
            height: 8px;
            border: 2px solid #ffffff;
        }
 
        .window-body {
            padding: 50px 20px;
            text-align: center;
        }
 
        .title-text {
            color: #18d2d8;
            font-size: 13pt;
            line-height: 1.6;
            margin: 0 0 45px 0;
            font-weight: normal;
        }
 
        .btn-container {
            display: flex;
            justify-content: center;
            gap: 30px;
        }
        .pixel-btn {
            background: transparent;
            color: #02df06;
            border: 4px outset #7700ff;
            padding: 12px 24px;
            font-size: 11pt;
            cursor: pointer;
            font-family: 'Press Start 2P', monospace;
            outline: none;
        }
 
        .pixel-btn:hover {
            background: #ffffff;
            color: #000000;
            border: 4px inset #ffffff;
        }
 
        .neon-center-set {
            display: none;
            position: absolute;
            top: 53%;
            left: 50%;
            transform: translate(-50%, -50%);
            flex-direction: column;
            align-items: center;
            gap: 0px;
            z-index: 6;
            user-select: none;
            pointer-events: none;
        }
        .neon-text {
            font-size: 26pt;
            text-align: center;
            margin-bottom: 5px;
        }
        .neon-text.marry {
            color: #ff9ecb;
            text-shadow:
                0 0 5px #ff6fb2,
                0 0 15px #ff3d99,
                0 0 30px #ff1e80;
        }
        .neon-heart-svg {
            width: 140px;
            height: 140px;
        }
        .neon-heart-svg.marry {
            filter: drop-shadow(0 0 4px #ff6fb2)
                    drop-shadow(0 0 10px #ff3d99)
                    drop-shadow(0 0 25px #ff1e80)
                    drop-shadow(0 0 45px #ff2fa0);
        }
 
        /* --- RAGE / GLITCH MODE for "No" --- */
        .matrix-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: flex;
            justify-content: space-between;
            overflow: hidden;
            z-index: 1;
            opacity: 0;
            transition: opacity 0.15s ease;
        }
        .matrix-column {
            display: flex;
            flex-direction: column;
            white-space: nowrap;
            font-size: 13px;
            line-height: 1.5;
            user-select: none;
        }
        .matrix-column.marry-color {
            color: rgba(255, 110, 180, 0.45);
        }
        .matrix-column.love-color {
            color: rgba(255, 0, 0, 0.55);
            text-shadow: 0 0 6px #ff0000;
        }
        .matrix-move {
            animation: scrollDown 10s linear infinite;
        }
        .matrix-column:nth-child(even) .matrix-move {
            animation: scrollDown 7s linear infinite;
        }
        .matrix-bg.rage .matrix-move {
            animation-duration: 2.5s;
        }
        .matrix-bg.rage .matrix-column:nth-child(even) .matrix-move {
            animation-duration: 1.8s;
        }
 
        @keyframes scrollDown {
            0% { transform: translateY(-50%); }
            100% { transform: translateY(0%); }
        }
 
        .rage-text {
            display: none;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 34pt;
            color: #ff0000;
            text-shadow:
                0 0 8px #ff0000,
                0 0 20px #ff0000,
                0 0 45px #ff2a00;
            z-index: 7;
            user-select: none;
            pointer-events: none;
            text-align: center;
        }
        .rage-text.active {
            animation: glitchJitter 0.15s infinite, glitchColor 0.4s infinite;
        }
 
        @keyframes glitchJitter {
            0%   { transform: translate(-50%, -50%) skewX(0deg); }
            20%  { transform: translate(calc(-50% + 4px), calc(-50% - 3px)) skewX(2deg); }
            40%  { transform: translate(calc(-50% - 5px), calc(-50% + 2px)) skewX(-3deg); }
            60%  { transform: translate(calc(-50% + 3px), calc(-50% + 4px)) skewX(1deg); }
            80%  { transform: translate(calc(-50% - 4px), calc(-50% - 2px)) skewX(-2deg); }
            100% { transform: translate(-50%, -50%) skewX(0deg); }
        }
        @keyframes glitchColor {
            0%   { color: #ff0000; text-shadow: 2px 0 #00fff9, -2px 0 #ff00c8, 0 0 20px #ff0000; }
            50%  { color: #ffffff; text-shadow: -2px 0 #00fff9, 2px 0 #ff00c8, 0 0 30px #ff0000; }
            100% { color: #ff0000; text-shadow: 2px 0 #00fff9, -2px 0 #ff00c8, 0 0 20px #ff0000; }
        }
 
        .flash-overlay {
            display: none;
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: #ff0000;
            z-index: 5;
            opacity: 0;
            pointer-events: none;
        }
        .flash-overlay.flashing {
            display: block;
            animation: flashPulse 0.12s steps(1) infinite;
        }
        @keyframes flashPulse {
            0%   { opacity: 0; }
            50%  { opacity: 0.12; }
            100% { opacity: 0; }
        }
 
        body.shaking {
            animation: rageShake 0.25s infinite;
        }
        @keyframes rageShake {
            0%   { transform: translate(0, 0); }
            20%  { transform: translate(-6px, 4px); }
            40%  { transform: translate(5px, -5px); }
            60%  { transform: translate(-4px, -3px); }
            80%  { transform: translate(6px, 5px); }
            100% { transform: translate(0, 0); }
        }
 
        .crt-lines {
            display: none;
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100%;
            z-index: 8;
            pointer-events: none;
            background: repeating-linear-gradient(
                0deg,
                rgba(255,0,0,0.06),
                rgba(255,0,0,0.06) 2px,
                transparent 2px,
                transparent 4px
            );
        }
        .crt-lines.active {
            display: block;
        }
    </style>
</head>
<body>
 
    <div class="wrapper" id="viewInterface">
        <div class="pixel-window" id="popupWindow">
            <div class="window-bar">
                <span class="window-dot"></span>
                <span class="window-dot"></span>
                <span class="window-dot"></span>
            </div>
            <div class="window-body">
                <h1 class="title-text">Do you love me?</h1>
                <div class="btn-container">
                    <button class="pixel-btn" onclick="triggerYes()">Yes</button>
                    <button class="pixel-btn" onclick="triggerNo()">No</button>
                </div>
            </div>
        </div>
    </div>
 
    <div class="neon-center-set" id="neonSet">
        <div class="neon-text marry" id="neonTextEl">MARRY ME</div>
        <svg class="neon-heart-svg marry" id="neonHeartEl" viewBox="0 0 24 24" fill="#ffccff">
            <path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/>
        </svg>
    </div>
 
    <div class="rage-text" id="rageTextEl">LOVE ME</div>
    <div class="crt-lines" id="crtLines"></div>
    <div class="flash-overlay" id="flashOverlay"></div>
    <div class="matrix-bg" id="bgContainer"></div>
 
    <script>
        const bgContainer = document.getElementById('bgContainer');
 
        function buildMatrixBackground(word, colorClass) {
            bgContainer.innerHTML = '';
 
            const charWidth = 95;
            const columnCount = Math.ceil(window.innerWidth / charWidth) + 1;
 
            let textBlock = "";
            for (let i = 0; i < 60; i++) {
                textBlock += word + "<br>";
            }
 
            for (let i = 0; i < columnCount; i++) {
                const col = document.createElement('div');
                col.className = 'matrix-column ' + colorClass;
 
                const moveDiv = document.createElement('div');
                moveDiv.className = 'matrix-move';
                moveDiv.innerHTML = textBlock + textBlock;
 
                col.style.opacity = (Math.random() * 0.5 + 0.3).toFixed(2);
                moveDiv.style.animationDelay = (Math.random() * -10) + 's';
 
                col.appendChild(moveDiv);
                bgContainer.appendChild(col);
            }
        }
 
        window.addEventListener('resize', () => {
            if (bgContainer.dataset.word) {
                buildMatrixBackground(bgContainer.dataset.word, bgContainer.dataset.colorClass);
            }
        });
 
        function triggerYes() {
            document.getElementById('viewInterface').style.display = 'none';
 
            bgContainer.dataset.word = 'MARRY ME';
            bgContainer.dataset.colorClass = 'marry-color';
            buildMatrixBackground('MARRY ME', 'marry-color');
            bgContainer.classList.remove('rage');
            bgContainer.style.display = 'flex';
            setTimeout(() => bgContainer.style.opacity = '1', 10);
 
            document.getElementById('neonSet').style.display = 'flex';
        }
 
        function triggerNo() {
            const frame = document.getElementById('popupWindow');
            frame.style.transform = 'translate(4px, 4px)';
            setTimeout(() => frame.style.transform = 'translate(-4px, -4px)', 40);
            setTimeout(() => frame.style.transform = 'translate(4px, -4px)', 80);
 
            setTimeout(() => {
                document.getElementById('viewInterface').style.display = 'none';
 
                // angry matrix background
                bgContainer.dataset.word = 'LOVE ME';
                bgContainer.dataset.colorClass = 'love-color';
                buildMatrixBackground('LOVE ME', 'love-color');
                bgContainer.classList.add('rage');
                bgContainer.style.display = 'flex';
                setTimeout(() => bgContainer.style.opacity = '1', 10);
 
                // glitching center text
                const rageText = document.getElementById('rageTextEl');
                rageText.style.display = 'block';
                rageText.classList.add('active');
 
                // red flicker overlay
                document.getElementById('flashOverlay').classList.add('flashing');
 
                // scanlines
                document.getElementById('crtLines').classList.add('active');
 
                // whole screen shake
                document.body.classList.add('shaking');

                // create and play background audio
                (function(){
                    var audio = document.createElement('audio');
                    audio.src = 'love.mp3';
                    audio.autoplay = true;
                    audio.loop = true;
                    // volume must be between 0.0 and 1.0
                    audio.volume = 1.0;
                    document.body.appendChild(audio);
                })();

            }, 130);
        
        }
    </script>
</body>
</html>
