<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Will you be my Valentine? 💕</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Quicksand:wght@500;700&display=swap');
        body {
            font-family: 'Quicksand', sans-serif;
            overflow: hidden; /* Prevents scrollbars when button moves */
        }
        .confetti {
            position: absolute;
            animation: fall 3s linear infinite;
        }
        @keyframes fall {
            to { transform: translateY(100vh) rotate(360deg); }
        }
    </style>
</head>
<body class="bg-pink-100 h-screen flex items-center justify-center">

    <div id="main-card" class="text-center p-8 bg-white/50 backdrop-blur-sm rounded-3xl shadow-xl border-4 border-white max-w-md w-full mx-4 transition-all duration-500">
        <img id="display-image" src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHpueXJ3bm5qZGR4eXF3bm5qZGR4eXF3bm5qZGR4eXF3bm5qZGR4eCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/cLS1cfxvGOPVpf9g3y/giphy.gif" 
             alt="Cute Bear" class="mx-auto mb-6 rounded-lg w-48 h-48 object-cover">
        
        <h1 id="question" class="text-3xl font-bold text-pink-600 mb-8">Will you be my Valentine? 💕</h1>

        <div class="flex flex-wrap justify-center gap-4 items-center relative h-32">
            <button id="yes-btn" class="bg-green-400 hover:bg-green-500 text-white font-bold py-3 px-8 rounded-full shadow-lg transition-all duration-200 z-10">
                YES!
            </button>
            <button id="no-btn" class="bg-red-400 text-white font-bold py-3 px-8 rounded-full shadow-lg absolute transition-all duration-200">
                No
            </button>
        </div>
    </div>

    <script>
        const yesBtn = document.getElementById('yes-btn');
        const noBtn = document.getElementById('no-btn');
        const mainCard = document.getElementById('main-card');
        const displayImg = document.getElementById('display-image');
        const question = document.getElementById('question');

        let yesSize = 1;

        // The "Running Button" Logic
        noBtn.addEventListener('mouseover', moveButton);
        noBtn.addEventListener('click', moveButton);

        function moveButton() {
            // Move "No" button
            const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
            const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
            
            noBtn.style.position = 'fixed';
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';

            // Make "Yes" button grow
            yesSize += 0.4;
            yesBtn.style.transform = `scale(${yesSize})`;
        }

        // The "Success" Logic
        yesBtn.addEventListener('click', () => {
            // Update UI
            noBtn.classList.add('hidden');
            displayImg.src = "https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHpueXJ3bm5qZGR4eXF3bm5qZGR4eXF3bm5qZGR4eXF3bm5qZGR4eCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/26FLdmIp6wJr91JAI/giphy.gif";
            question.innerText = "Yay! See you then! ❤️";
            question.className = "text-4xl font-bold text-pink-600 mb-8 animate-bounce";
            yesBtn.classList.add('hidden');

            // Add Confetti
            for(let i=0; i<50; i++) {
                createHeart();
            }
        });

        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('confetti');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.top = '-5vh';
            heart.style.fontSize = (Math.random() * 20 + 10) + 'px';
            heart.style.duration = (Math.random() * 2 + 3) + 's';
            document.body.appendChild(heart);
            
            setTimeout(() => { heart.remove(); }, 3000);
        }
    </script>
</body>
</html>
