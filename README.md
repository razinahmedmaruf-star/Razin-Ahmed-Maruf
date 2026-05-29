# Razin-Ahmed-Maruf
<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PlayCast - Premium IPTV Stream</title>
    
    <!-- Fluid Player CSS (For Modern Video Player) -->
    <link rel="stylesheet" href="https://cdn.fluidplayer.com/v3/current/fluidplayer.min.css" type="text/css"/>
    
    <style>
        :root {
            --primary-color: #e50914; /* Netflix Red */
            --bg-color: #141414;
            --card-bg: #1f1f1f;
            --text-color: #ffffff;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 0;
        }

        /* Navbar */
        .navbar {
            background-color: #000;
            padding: 15px 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 10px rgba(0,0,0,0.5);
        }

        .logo {
            font-size: 28px;
            font-weight: bold;
            color: var(--primary-color);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .search-box {
            padding: 8px 15px;
            width: 250px;
            border-radius: 20px;
            border: 1px solid #444;
            background: #222;
            color: #fff;
            outline: none;
        }

        /* Main Container */
        .container {
            max-width: 1200px;
            margin: 30px auto;
            padding: 0 20px;
        }

        /* Video Section */
        .player-container {
            background-color: #000;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 10px 25px rgba(0,0,0,0.7);
            margin-bottom: 30px;
        }

        .now-playing {
            padding: 15px;
            background: var(--card-bg);
            font-size: 18px;
            font-weight: 600;
            border-bottom: 3px solid var(--primary-color);
        }

        /* Category Filter */
        .categories {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            overflow-x: auto;
            padding-bottom: 5px;
        }

        .category-btn {
            background: var(--card-bg);
            color: #fff;
            border: 1px solid #333;
            padding: 8px 16px;
            border-radius: 20px;
            cursor: pointer;
            white-space: nowrap;
            transition: 0.3s;
        }

        .category-btn.active, .category-btn:hover {
            background: var(--primary-color);
            border-color: var(--primary-color);
        }

        /* Channel Grid */
        .grid-title {
            font-size: 22px;
            margin-bottom: 15px;
        }

        .channel-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
            gap: 20px;
        }

        .channel-card {
            background-color: var(--card-bg);
            border-radius: 8px;
            overflow: hidden;
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
            border: 1px solid #292929;
            text-align: center;
            padding: 15px;
        }

        .channel-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(229, 9, 20, 0.3);
            border-color: var(--primary-color);
        }

        .channel-logo {
            width: 70px;
            height: 70px;
            object-fit: cover;
            border-radius: 50%;
            margin-bottom: 10px;
            background: #333;
        }

        .channel-name {
            font-size: 16px;
            font-weight: 500;
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 30px;
            margin-top: 5px;
            background-color: #000;
            color: #666;
            font-size: 14px;
        }
    </style>
</head>
<body>

    <!-- Navbar -->
    <div class="navbar">
        <div class="logo">PlayCast 🎬</div>
        <input type="text" id="search" class="search-box" placeholder="চ্যানেল খুঁজুন..." onkeyup="searchChannel()">
    </div>

    <div class="container">
        
        <!-- Video Player -->
        <div class="player-container">
            <div class="now-playing" id="current-channel-title">এখন দেখছেন: টেস্ট স্ট্রিম ১</div>
            <video id="video-player">
                <source id="video-source" src="https://test-streams.mux.dev/x36xhzz/x36xhzz.m3u8" type="application/x-mpegURL">
            </video>
        </div>

        <!-- Categories -->
        <div class="categories">
            <button class="category-btn active" onclick="filterCategory('all')">সব চ্যানেল</button>
            <button class="category-btn" onclick="filterCategory('news')">খবর (News)</button>
            <button class="category-btn" onclick="filterCategory('sports')">খেলাধুলা (Sports)</button>
            <button class="category-btn" onclick="filterCategory('ent')">বিনোদন (Entertainment)</button>
        </div>

        <!-- Channel Grid -->
        <h2 class="grid-title">চ্যানেল সমূহ</h2>
        <div class="channel-grid" id="channel-container">
            
            <!-- Channel 1 -->
            <div class="channel-card" data-category="ent" data-name="টেস্ট স্ট্রিম ১" onclick="playChannel('https://test-streams.mux.dev/x36xhzz/x36xhzz.m3u8', 'টেস্ট স্ট্রিম ১')">
                <img class="channel-logo" src="https://via.placeholder.com/70/ff0000/fff?text=TV1" alt="Logo">
                <div class="channel-name">টেস্ট স্ট্রিম ১</div>
            </div>

            <!-- Channel 2 -->
            <div class="channel-card" data-category="sports" data-name="স্পোর্টস লাইভ" onclick="playChannel('https://diceyk6a7voy4.cloudfront.net/e2312a0c-647a-42c2-99f6-25f0e1555904/playlist.m3u8', 'স্পোর্টস লাইভ')">
                <img class="channel-logo" src="https://via.placeholder.com/70/0000ff/fff?text=Sports" alt="Logo">
                <div class="channel-name">স্পোর্টস লাইভ</div>
            </div>

            <!-- আপনি চাইলে নিচে আরও চ্যানেল কার্ড যোগ করতে পারেন -->

        </div>
    </div>

    <footer>
        &copy; 2026 PlayCast - অল রাইটস রিজার্ভড।
    </footer>

    <!-- Fluid Player JS -->
    <script src="https://cdn.fluidplayer.com/v3/current/fluidplayer.min.js"></script>
    
    <script>
        // প্লেয়ার ইনিশিয়ালাইজেশন
        var myPlayer = fluidPlayer('video-player', {
            layoutControls: {
                fillToContainer: true,
                posterImage: '',
                autoPlay: true
            }
        });

        // চ্যানেল পরিবর্তন করার ফাংশন
        function playChannel(url, title) {
            document.getElementById('current-channel-title').innerText = "এখন দেখছেন: " + title;
            
            // প্লেয়ার সোর্স ডাইনামিকালি চেঞ্জ
            var videoElement = document.getElementById('video-player');
            videoElement.src = url;
            myPlayer.play();
            
            // স্ক্রোল করে প্লেয়ারের কাছে নিয়ে যাওয়া
            window.scrollTo({top: 0, behavior: 'smooth'});
        }

        // সার্চ ফাংশন
        function searchChannel() {
            let filter = document.getElementById('search').value.toUpperCase();
            let cards = document.getElementsByClassName('channel-card');
            
            for (let i = 0; i < cards.length; i++) {
                let name = cards[i].getAttribute('data-name');
                if (name.toUpperCase().indexOf(filter) > -1) {
                    cards[i].style.display = "";
                } else {
                    cards[i].style.display = "none";
                }
            }
        }

        // ক্যাটাগরি ফিল্টার ফাংশন
        function filterCategory(category) {
            let cards = document.getElementsByClassName('channel-card');
            let buttons = document.getElementsByClassName('category-btn');
            
            // অ্যাক্টিভ বাটন স্টাইল পরিবর্তন
            for(let btn of buttons) {
                btn.classList.remove('active');
            }
            event.target.classList.add('active');

            // কার্ড ফিল্টার
            for (let i = 0; i < cards.length; i++) {
                let cat = cards[i].getAttribute('data-category');
                if (category === 'all' || cat === category) {
                    cards[i].style.display = "";
                } else {
                    cards[i].style.display = "none";
                }
            }
        }
    </style>
</body>
</html>

This Is iptv Play And Enjoy
