<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Shaymaa! 💖</title>
    <style>
        body {
            background-color: #050505;
            color: #ffffff;
            font-family: 'Courier New', Courier, monospace;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            overflow: hidden;
        }

        #playBtn {
            position: fixed;
            top: 20px;
            right: 20px;
            background: #ff4d6d;
            border: none;
            color: white;
            padding: 12px 24px;
            border-radius: 25px;
            cursor: pointer;
            z-index: 100;
            font-weight: bold;
            box-shadow: 0 0 15px #ff4d6d;
            font-size: 1rem;
            animation: pulse 1.5s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }

        .container {
            display: flex;
            flex-direction: row;
            align-items: flex-end;
            gap: 40px;
            padding: 20px;
            z-index: 2;
        }

        #typewriter {
            font-size: 1.1rem;
            line-height: 1.6;
            white-space: pre-wrap;
            width: 300px;
            margin-bottom: 50px;
            color: #f0f0f0;
            text-shadow: 0 0 5px rgba(255,255,255,0.3);
        }

        .tree-container {
            position: relative;
            width: 200px;
            height: 350px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .trunk {
            width: 10px;
            height: 0;
            background: linear-gradient(to top, #ff85a2, #ffb3c1);
            border-radius: 10px;
            position: absolute;
            bottom: 0;
            transition: height 2.5s ease-out;
        }

        .heart {
            position: absolute;
            width: 14px;
            height: 14px;
            transform: rotate(-45deg);
            opacity: 0;
            animation: fadeIn 1s forwards;
        }

        .heart::before, .heart::after {
            content: '';
            position: absolute;
            width: 14px;
            height: 14px;
            border-radius: 50%;
            background: inherit;
        }

        .heart::before { top: -7px; left: 0; }
        .heart::after { left: 7px; top: 0; }

        @keyframes fadeIn {
            to { opacity: 1; }
        }

        .bg-heart {
            position: absolute;
            color: rgba(255, 77, 109, 0.15);
            font-size: 20px;
            user-select: none;
            z-index: 1;
            animation: fall linear infinite;
        }

        @keyframes fall {
            from { transform: translateY(-10vh); }
            to { transform: translateY(110vh); }
        }
    </style>
</head>
<body>

    <button id="playBtn" onclick="startExperience()">Play Ayra Starr 🎵</button>

    <audio id="bdayMusic" loop>
        <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3" type="audio/mpeg">
    </audio>

    <div class="container">
        <div id="typewriter"></div>
        <div class="tree-container" id="tree">
            <div class="trunk" id="trunk"></div>
        </div>
    </div>

    <script>
        const text = `Hey Shaymaa 💘
Happy Birthday 🎂
May God bless you ✨
And give a many happiness 🌻
Just saying... you're pretty awesome 😊
Sending good vibes and maybe a wink 😉
Hope u have a great day today 💖`;

        const typewriterElement = document.getElementById("typewriter");
        const treeContainer = document.getElementById("tree");
        const trunk = document.getElementById("trunk");
        const music = document.getElementById("bdayMusic");
        const playBtn = document.getElementById("playBtn");
        let i = 0;

        function startExperience() {
            playBtn.style.display = 'none';
            music.play();
            trunk.style.height = '200px';
            typeWriter(); 
            createTreeHearts(); 
            createFallingHearts(); 
        }

        function typeWriter() {
            if (i < text.length) {
                typewriterElement.innerHTML += text.charAt(i);
                i++;
                setTimeout(typeWriter, 75); 
            }
        }

        function createTreeHearts() {
            const colors = ['#ff4d6d', '#ff758f', '#ff85a2', '#fbb1bd', '#ffb3c1', '#c9184a'];
            for (let j = 0; j < 80; j++) {
                const heart = document.createElement('div');
                heart.className = 'heart';
                const x = Math.random() * 180 - 90; 
                const y = Math.random() * 160 - 200; 
                heart.style.left = `calc(50% + ${x}px)`;
                heart.style.top = `calc(60% + ${y}px)`;
                heart.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                heart.style.animationDelay = (Math.random() * 4) + 1 + "s";
                treeContainer.appendChild(heart);
            }
        }

        function createFallingHearts() {
            setInterval(() => {
                const h = document.createElement('div');
                h.className = 'bg-heart';
                h.innerHTML = '❤️';
                h.style.left = Math.random() * 100 + 'vw';
                h.style.animationDuration = Math.random() * 3 + 3 + 's';
                h.style.opacity = Math.random();
                document.body.appendChild(h);
                setTimeout(() => h.remove(), 6000);
            }, 400);
        }
    </script>
</body>
</html>
