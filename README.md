<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For My Girl, Wasiza 🐾</title>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@600;700&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        body {
            background-color: #ffe6ea;
            font-family: 'Poppins', sans-serif;
            color: #4a3b32;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
            overflow-x: hidden;
        }
        .container {
            max-width: 600px;
            width: 100%;
            text-align: center;
            background: #ffffff90;
            backdrop-filter: blur(8px);
            padding: 30px 20px;
            border-radius: 25px;
            box-shadow: 0 10px 25px rgba(255, 182, 193, 0.5);
            border: 2px solid #ffb6c1;
            margin-top: 20px;
        }
        h1 {
            font-family: 'Dancing Script', cursive;
            font-size: 2.8rem;
            color: #d63384;
            margin-bottom: 10px;
        }
        p.sub-title {
            font-size: 1rem;
            color: #6c757d;
            margin-bottom: 25px;
        }
        .cat-badge {
            font-size: 1.5rem;
            margin-bottom: 15px;
        }
        
        /* Question Card */
        .question-card {
            background: #fff;
            padding: 25px;
            border-radius: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            margin-bottom: 30px;
            position: relative;
        }
        .question-card h2 {
            font-size: 1.3rem;
            color: #333;
            margin-bottom: 20px;
        }
        .btn-group {
            display: flex;
            justify-content: center;
            gap: 20px;
            position: relative;
            min-height: 50px;
        }
        .btn {
            padding: 12px 28px;
            font-size: 1rem;
            font-weight: 600;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            transition: transform 0.2s;
        }
        .btn-yes {
            background-color: #ff4d6d;
            color: white;
            box-shadow: 0 4px 10px rgba(255, 77, 109, 0.4);
        }
        .btn-yes:hover {
            transform: scale(1.08);
            background-color: #ff2a55;
        }
        .btn-no {
            background-color: #6c757d;
            color: white;
            position: absolute;
            transition: all 0.2s ease;
        }

        /* Gifts Section */
        .gifts-title {
            font-family: 'Dancing Script', cursive;
            font-size: 2rem;
            color: #d63384;
            margin: 25px 0 15px 0;
        }
        .gifts-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 15px;
        }
        .gift-box {
            background: #fff;
            border: 2px dashed #ff85a1;
            border-radius: 15px;
            padding: 20px 10px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        .gift-box:hover {
            transform: translateY(-5px);
            background: #fff5f7;
            border-style: solid;
        }
        .gift-icon {
            font-size: 2.2rem;
            display: block;
            margin-bottom: 8px;
        }
        .gift-label {
            font-size: 0.85rem;
            font-weight: 600;
            color: #ff4d6d;
        }

        /* Modal / Popups */
        .modal {
            display: none;
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.5);
            justify-content: center;
            align-items: center;
            z-index: 100;
            padding: 20px;
        }
        .modal-content {
            background: white;
            padding: 30px;
            border-radius: 20px;
            max-width: 450px;
            width: 100%;
            text-align: center;
            position: relative;
            animation: popup 0.3s ease-out;
            border: 3px solid #ffb6c1;
            max-height: 85vh;
            overflow-y: auto;
        }
        @keyframes popup {
            0% { transform: scale(0.7); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }
        .close-btn {
            position: absolute;
            top: 10px; right: 15px;
            font-size: 1.5rem;
            cursor: pointer;
            color: #aaa;
        }
        .modal-body {
            margin-top: 15px;
            font-size: 0.95rem;
            line-height: 1.6;
            color: #4a3b32;
        }
        .gift-image {
            width: 100%;
            max-height: 250px;
            object-fit: cover;
            border-radius: 15px;
            margin-bottom: 15px;
            border: 2px solid #ffb6c1;
        }

        /* Mobile Adjustments */
        @media (max-width: 500px) {
            .gifts-grid { grid-template-columns: 1fr; }
            h1 { font-size: 2.2rem; }
        }
    </style>
</head>
<body>

    <div class="container">
        <div class="cat-badge">🐾 🐱 🐾</div>
        <h1>Hey Wasiza!</h1>
        <p class="sub-title">A special little space created just for my favorite girl 💖</p>

        <!-- Question Section -->
        <div class="question-card">
            <h2>Will you love me more than anyone? 🥺</h2>
            <div class="btn-group" id="btnGroup">
                <button class="btn btn-yes" onclick="handleYes()">Yes! 🐾</button>
                <button class="btn btn-no" id="noBtn" onmouseover="moveNoButton()" onclick="moveNoButton()">No</button>
            </div>
        </div>

        <!-- 3 Gifts Section -->
        <div class="gifts-title">Pick Your 3 Surprise Gifts 🎁</div>
        <div class="gifts-grid">
            <div class="gift-box" onclick="openGift(1)">
                <span class="gift-icon">💌</span>
                <span class="gift-label">Gift #1</span>
            </div>
            <div class="gift-box" onclick="openGift(2)">
                <span class="gift-icon">🎵</span>
                <span class="gift-label">Gift #2</span>
            </div>
            <div class="gift-box" onclick="openGift(3)">
                <span class="gift-icon">🖼️</span>
                <span class="gift-label">Gift #3</span>
            </div>
        </div>
    </div>

    <!-- Modal Popup -->
    <div class="modal" id="modal">
        <div class="modal-content">
            <span class="close-btn" onclick="closeModal()">&times;</span>
            <div id="modalTitle" style="font-family: 'Dancing Script', cursive; font-size: 2rem; color: #d63384;"></div>
            <div class="modal-body" id="modalBody"></div>
        </div>
    </div>

    <script>
        // Runaway No Button Effect
        const noBtn = document.getElementById('noBtn');
        const btnGroup = document.getElementById('btnGroup');

        function moveNoButton() {
            const containerRect = btnGroup.getBoundingClientRect();
            const btnRect = noBtn.getBoundingClientRect();
            
            const maxX = containerRect.width - btnRect.width;
            const maxY = 100;
            
            const randomX = Math.floor(Math.random() * maxX) - (maxX / 2);
            const randomY = Math.floor(Math.random() * maxY) - (maxY / 2);

            noBtn.style.transform = `translate(${randomX}px, ${randomY}px)`;
        }

        // Yes Button Celebration
        function handleYes() {
            confetti({
                particleCount: 120,
                spread: 70,
                origin: { y: 0.6 }
            });
            showModal("Yay! 🐱💖", "I knew you'd say yes! You mean the world to me, Wasiza. Forever & always! 🐾✨");
        }

        // Gift Box Content
        function openGift(number) {
            if (number === 1) {
                showModal("A Letter For Wasiza 💌", 
                    "Hey wasiza my girl I love you more than everyone i know, and I know hurted you sometimes sorry for that but everytime we had a fight I want you and me to solve it and become lovers again and I want to meets you soon as possible since our relationship is long distance please wait for me my dear girl, and don't let anyone into our relationship I love you more than everyone will you love me more than anyone?"
                );
            } else if (number === 2) {
                showModal("Our Special Song 🎵", 
                    "<b>If the World Was Ending - JP Saxe</b><br><br><i>'If the world was ending, you'd come over, right?'</i><br><br>This song always reminds me of us and how much you mean to me, no matter the distance. 🎧💖"
                );
            } else if (number === 3) {
                showModal("Us Meeting Soon! 🐾", 
                    `<img src="our_photo.jpg" alt="Our Special Photo" class="gift-image" onerror="this.src='https://images.unsplash.com/photo-1518791841217-8f162f1e1131?auto=format&fit=crop&w=600&q=80'">
                    <b>A Special Promise for My Girl</b><br><br>
                    Valid for when we finally meet! I promise to hold you tight and make up for every mile between us. Please wait for me! 🐱 Distance is just temporary, but my love for you is forever.`
                );
            }
        }

        function showModal(title, text) {
            document.getElementById('modalTitle').innerHTML = title;
            document.getElementById('modalBody').innerHTML = text;
            document.getElementById('modal').style.display = 'flex';
        }

        function closeModal() {
            document.getElementById('modal').style.display = 'none';
        }

        window.onclick = function(event) {
            const modal = document.getElementById('modal');
            if (event.target == modal) {
                modal.style.display = 'none';
            }
        }
    </script>
</body>
</html>
