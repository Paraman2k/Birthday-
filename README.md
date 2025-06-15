<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Birthday Surprise for Eshika!</title>
    <!-- Tailwind CSS for styling -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700&family=Great+Vibes&display=swap" rel="stylesheet">
    <!-- Font Awesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <style>
        /* Custom font for elegant text */
        .font-great-vibes {
            font-family: 'Great Vibes', cursive;
        }

        /* Base styles for the body and pages */
        body {
            font-family: 'Inter', sans-serif;
            overflow: hidden; /* Prevent scrollbars */
        }
        
        /* Each section will be a full-screen "page" */
        .page {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            transition: opacity 0.8s ease-in-out, transform 0.8s ease-in-out;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 1rem;
        }

        /* Page transition animations */
        .page.hidden {
            opacity: 0;
            transform: scale(1.1);
            pointer-events: none;
        }

        /* Pulsing animation for the gift */
        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }
        .animate-pulse-slow {
            animation: pulse 3s infinite ease-in-out;
        }
        
        /* Loading spinner */
        @keyframes spin {
            to { transform: rotate(360deg); }
        }
        .spinner {
            border: 4px solid rgba(255, 255, 255, 0.3);
            border-top-color: #fff;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
        }

        /* Text reveal animation */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .animate-fade-in {
            animation: fadeIn 1s ease-out forwards;
        }
        
        /* Confetti animation */
        @keyframes fall {
            0% { transform: translateY(-10vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(110vh) rotate(720deg); opacity: 0; }
        }
        .confetti {
            position: absolute;
            top: 0;
            left: 0;
            width: 10px;
            height: 10px;
            background-color: #f00;
            opacity: 0;
            animation: fall linear infinite;
        }
        
        /* Gallery image transition */
        .gallery-image {
            transition: opacity 0.5s ease-in-out;
        }
        
        /* Candle flame animation */
        @keyframes flicker {
            0%, 100% { transform: scaleY(1) rotate(-1deg); opacity: 1; }
            50% { transform: scaleY(1.05) rotate(1deg); opacity: 0.95; }
        }
        .flame {
            animation: flicker 1.5s infinite ease-in-out;
            transform-origin: bottom;
        }
        
        @keyframes puff-out {
            0% { transform: scale(1); opacity: 1; }
            100% { transform: scale(0); opacity: 0; }
        }
        .flame.out {
            animation: puff-out 0.5s forwards;
        }
    </style>
</head>
<body class="bg-gray-900">

    <!-- =========== PAGE 1: INVITATION =========== -->
    <div id="page-1" class="page bg-gradient-to-br from-indigo-500 to-purple-600">
        <div class="text-center text-white">
            <div class="animate-pulse-slow">
                <i class="fas fa-gift text-8xl md:text-9xl text-yellow-300 drop-shadow-lg"></i>
            </div>
            <h1 class="text-3xl md:text-5xl font-bold mt-8">A Surprise For Eshika!</h1>
            <p class="mt-4 text-lg md:text-xl text-purple-200">Tap to open</p>
            <button onclick="showPage(2)" class="mt-8 bg-white text-purple-600 font-bold py-3 px-8 rounded-full shadow-xl transform hover:scale-105 transition-transform duration-300">
                Open
            </button>
        </div>
    </div>

    <!-- =========== PAGE 2: MAIN WISH =========== -->
    <div id="page-2" class="page hidden bg-gradient-to-br from-pink-500 via-red-500 to-yellow-500">
        <div id="confetti-container" class="absolute inset-0 z-0"></div>
        <div class="relative z-10 text-center text-white">
            <h1 class="font-great-vibes text-6xl md:text-8xl drop-shadow-md" style="opacity: 0; animation-delay: 0.5s;" data-animate>Happy Birthday, Eshika!</h1>
            <p class="text-lg md:text-2xl mt-4 max-w-2xl" style="opacity: 0; animation-delay: 1.2s;" data-animate>
                Wishing you a day as special as you are, filled with love, laughter, and unforgettable moments.
            </p>
            <button onclick="showPage(3)" class="mt-12 bg-white/30 backdrop-blur-sm text-white font-bold py-3 px-8 rounded-full shadow-lg transform hover:scale-105 transition-transform duration-300">
                Next <i class="fas fa-arrow-right ml-2"></i>
            </button>
        </div>
    </div>

    <!-- =========== PAGE 3: MEMORY LANE =========== -->
    <div id="page-3" class="page hidden bg-gradient-to-br from-teal-400 to-blue-600">
        <div class="text-center w-full max-w-4xl">
            <h2 class="text-4xl md:text-6xl font-bold text-white mb-8">Memory Lane</h2>
            <div class="relative bg-white rounded-2xl shadow-2xl aspect-video w-full max-w-2xl mx-auto overflow-hidden">
                <img id="gallery-img" src="https://placehold.co/1280x720/a78bfa/ffffff?text=Our+Favorite+Moments" alt="Memory photo" class="gallery-image absolute inset-0 w-full h-full object-cover">
            </div>
            <div class="mt-6 flex justify-center space-x-4">
                <button onclick="changeImage(-1)" class="bg-white/30 backdrop-blur-sm text-white font-bold p-3 rounded-full shadow-lg transform hover:scale-110 transition-transform">
                    <i class="fas fa-chevron-left w-6 h-6"></i>
                </button>
                <button onclick="changeImage(1)" class="bg-white/30 backdrop-blur-sm text-white font-bold p-3 rounded-full shadow-lg transform hover:scale-110 transition-transform">
                    <i class="fas fa-chevron-right w-6 h-6"></i>
                </button>
            </div>
             <button onclick="showPage(4)" class="mt-8 bg-white text-blue-600 font-bold py-3 px-8 rounded-full shadow-xl transform hover:scale-105 transition-transform duration-300">
                A special message awaits...
            </button>
        </div>
    </div>
    
    <!-- =========== PAGE 4: GEMINI POEM GENERATOR =========== -->
    <div id="page-4" class="page hidden bg-gradient-to-br from-purple-600 to-indigo-800">
        <div class="text-center w-full max-w-2xl text-white">
            <h2 class="text-4xl md:text-6xl font-bold mb-8">A Poem For You</h2>
            <div id="poem-container" class="bg-white/10 backdrop-blur-md rounded-xl p-6 min-h-[200px] text-lg leading-relaxed text-left">
                Click the button below to generate a unique birthday poem!
            </div>
            <div id="loader" class="hidden my-4 mx-auto spinner"></div>
            <button id="generate-poem-btn" onclick="generatePoem()" class="mt-8 bg-gradient-to-r from-pink-500 to-yellow-500 text-white font-bold py-3 px-8 rounded-full shadow-xl transform hover:scale-105 transition-transform duration-300">
                ✨ Generate Poem
            </button>
            <button id="next-to-cake-btn" onclick="showPage(5)" class="hidden mt-8 bg-white text-purple-600 font-bold py-3 px-8 rounded-full shadow-xl transform hover:scale-105 transition-transform duration-300">
                Time for cake! <i class="fas fa-birthday-cake ml-2"></i>
            </button>
        </div>
    </div>
    
    <!-- =========== PAGE 5: THE CAKE =========== -->
    <div id="page-5" class="page hidden bg-gradient-to-br from-gray-800 to-black">
        <div class="text-center text-white">
            <h2 id="cake-title" class="text-3xl md:text-5xl font-bold mb-4">Make a Wish...</h2>
            <!-- Cake SVG -->
            <svg viewBox="0 0 200 200" class="w-64 h-64 md:w-80 md:h-80 drop-shadow-lg">
              <!-- Cake Base -->
              <rect x="30" y="120" width="140" height="50" rx="10" fill="#f4a261"/>
              <rect x="40" y="115" width="120" height="10" rx="5" fill="#e76f51"/>
              <!-- Candles -->
              <rect x="70" y="85" width="10" height="30" fill="#f1faee"/>
              <rect x="120" y="85" width="10" height="30" fill="#f1faee"/>
              <!-- Flames -->
              <ellipse class="flame" cx="75" cy="80" rx="4" ry="10" fill="#ffcc00" id="flame1"/>
              <ellipse class="flame" cx="125" cy="80" rx="4" ry="10" fill="#ffcc00" id="flame2"/>
            </svg>
            <button id="blow-out-btn" onclick="blowOutCandles()" class="mt-6 bg-gradient-to-r from-cyan-400 to-blue-500 text-white font-bold py-3 px-8 rounded-full shadow-xl transform hover:scale-105 transition-transform duration-300">
                ...and blow out the candles!
            </button>
        </div>
    </div>

    <script>
        let currentPage = 1;

        // --- Navigation ---
        function showPage(pageNumber) {
            const previousPage = document.getElementById(`page-${currentPage}`);
            const nextPage = document.getElementById(`page-${pageNumber}`);

            if (previousPage) {
                previousPage.classList.add('hidden');
            }
            if (nextPage) {
                nextPage.classList.remove('hidden');
            }
            
            currentPage = pageNumber;
            
            // Trigger animations for the new page
            const animatedElements = nextPage.querySelectorAll('[data-animate]');
            animatedElements.forEach(el => {
                el.classList.add('animate-fade-in');
            });
            
            // Special actions for specific pages
            if(pageNumber === 2) {
                startConfetti();
            }
        }
        
        // --- Confetti Logic ---
        function startConfetti() {
            const container = document.getElementById('confetti-container');
            if (container.children.length > 0) return; // Don't add more confetti
            
            const count = 100;
            const colors = ['#fde047', '#a78bfa', '#f472b6', '#4ade80', '#60a5fa'];
            for (let i = 0; i < count; i++) {
                const confetti = document.createElement('div');
                confetti.classList.add('confetti');
                confetti.style.left = `${Math.random() * 100}vw`;
                confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                confetti.style.width = `${Math.random() * 5 + 5}px`;
                confetti.style.height = confetti.style.width;
                confetti.style.animationDuration = `${Math.random() * 3 + 4}s`;
                confetti.style.animationDelay = `${Math.random() * 5}s`;
                container.appendChild(confetti);
            }
        }

        // --- Gallery Logic ---
        const images = [
            'https://placehold.co/1280x720/a78bfa/ffffff?text=Our+Favorite+Moments',
            'https://placehold.co/1280x720/4ade80/ffffff?text=Good+Times',
            'https://placehold.co/1280x720/f472b6/ffffff?text=So+Many+Adventures',
            'https://placehold.co/1280x720/60a5fa/ffffff?text=Cheers+to+Eshika!',
        ];
        let currentImageIndex = 0;
        const galleryImg = document.getElementById('gallery-img');

        function changeImage(direction) {
            currentImageIndex += direction;
            if (currentImageIndex < 0) {
                currentImageIndex = images.length - 1;
            } else if (currentImageIndex >= images.length) {
                currentImageIndex = 0;
            }
            galleryImg.style.opacity = 0;
            setTimeout(() => {
                galleryImg.src = images[currentImageIndex];
                galleryImg.style.opacity = 1;
            }, 500); // Wait for fade out
        }

        // --- Gemini API Poem Generation ---
        async function generatePoem() {
            const generateBtn = document.getElementById('generate-poem-btn');
            const poemContainer = document.getElementById('poem-container');
            const loader = document.getElementById('loader');
            const nextBtn = document.getElementById('next-to-cake-btn');

            generateBtn.disabled = true;
            generateBtn.style.opacity = '0.5';
            loader.classList.remove('hidden');
            poemContainer.innerHTML = 'Crafting a special poem...';
            
            const prompt = "Write a short, four-line, cheerful, and heartfelt birthday poem for a wonderful person named Eshika. Mention joy, laughter, and a bright future.";
            let chatHistory = [{ role: "user", parts: [{ text: prompt }] }];
            const payload = { contents: chatHistory };
            const apiKey = ""; // API key is handled by the environment
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;

            try {
                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });

                if (!response.ok) {
                    throw new Error(`API request failed with status ${response.status}`);
                }
                
                const result = await response.json();

                if (result.candidates && result.candidates.length > 0 && result.candidates[0].content && result.candidates[0].content.parts && result.candidates[0].content.parts.length > 0) {
                    const poemText = result.candidates[0].content.parts[0].text;
                    poemContainer.innerHTML = poemText.replace(/\n/g, '<br>');
                } else {
                   poemContainer.innerText = 'Could not generate a poem right now. Please try again later!';
                }
            } catch (error) {
                console.error("Error generating poem:", error);
                poemContainer.innerText = 'Sorry, an error occurred while creating your poem. Wishing Eshika a very happy birthday anyway!';
            } finally {
                loader.classList.add('hidden');
                generateBtn.classList.add('hidden');
                nextBtn.classList.remove('hidden');
            }
        }


        // --- Cake Logic ---
        function blowOutCandles() {
            document.getElementById('flame1').classList.add('out');
            document.getElementById('flame2').classList.add('out');

            const title = document.getElementById('cake-title');
            const button = document.getElementById('blow-out-btn');
            
            button.style.transform = 'scale(0)';
            
            setTimeout(() => {
                title.style.transition = 'opacity 0.5s';
                title.style.opacity = 0;
            }, 500);
            
            setTimeout(() => {
                title.innerText = 'Hooray! Happy Birthday, Eshika!';
                title.style.opacity = 1;
            }, 1000);
        }
        
        // Initialize first page
        document.addEventListener('DOMContentLoaded', () => {
             showPage(1);
        });

    </script>
</body>
</html>
# Birthday-
