<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Twitter Clone</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            display: flex;
            min-height: 100vh;
            background-color: #000;
            color: #ffffff;
        }

        /* Sidebar styles */
        .sidebar {
            width: 275px;
            padding: 20px;
            position: fixed;
            height: 100%;
            border-right: 1px solid #2f3336;
        }

        .logo {
            font-size: 2rem;
            color: #1da1f2;
            margin-bottom: 30px;
            padding: 10px;
        }

        .nav-item {
            display: flex;
            align-items: center;
            padding: 15px;
            font-size: 1.2rem;
            cursor: pointer;
            border-radius: 9999px;
            transition: background-color 0.2s;
            margin-bottom: 5px;
        }

        .nav-item:hover {
            background-color: #181818;
        }

        .nav-item i {
            margin-right: 15px;
            font-size: 1.5rem;
        }

        .tweet-btn {
            background-color: #1da1f2;
            color: white;
            border: none;
            padding: 15px 80px;
            border-radius: 9999px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            margin-top: 20px;
            width: 100%;
        }

        .tweet-btn:hover {
            background-color: #1a91da;
        }

        /* Main content styles */
        .main-content {
            flex: 1;
            margin-left: 275px;
            border-right: 1px solid #2f3336;
            max-width: 600px;
        }

        .header {
            padding: 15px;
            font-size: 1.2rem;
            font-weight: bold;
            border-bottom: 1px solid #2f3336;
            position: sticky;
            top: 0;
            background-color: rgba(0, 0, 0, 0.9);
            backdrop-filter: blur(12px);
        }

        .tweet-box {
            padding: 15px;
            border-bottom: 1px solid #2f3336;
        }

        .tweet-input {
            width: 100%;
            background: transparent;
            border: none;
            color: white;
            font-size: 1.2rem;
            padding: 10px;
            margin-bottom: 15px;
            resize: none;
        }

        .tweet-actions {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding-top: 10px;
            border-top: 1px solid #2f3336;
        }

        .tweet-icons {
            display: flex;
            gap: 15px;
            color: #1da1f2;
        }

        .tweet-submit {
            background-color: #1da1f2;
            color: white;
            border: none;
            padding: 8px 20px;
            border-radius: 9999px;
            font-weight: bold;
            cursor: pointer;
        }

        /* Right sidebar */
        .right-sidebar {
            width: 350px;
            padding: 20px;
            position: fixed;
            right: 0;
            height: 100%;
        }

        .search-box {
            background-color: #202327;
            padding: 12px;
            border-radius: 9999px;
            margin-bottom: 20px;
        }

        .search-box input {
            background: transparent;
            border: none;
            color: white;
            width: 100%;
            font-size: 1rem;
            padding-left: 30px;
        }

        .trends {
            background-color: #202327;
            border-radius: 15px;
            padding: 15px;
        }

        .trend-item {
            padding: 15px;
            cursor: pointer;
        }

        .trend-item:hover {
            background-color: #1c1f23;
        }

        .trend-category {
            font-size: 0.8rem;
            color: #6e767d;
        }

        .trend-name {
            font-weight: bold;
            margin: 5px 0;
        }

        .trend-tweets {
            font-size: 0.8rem;
            color: #6e767d;
        }

        /* Feed styles */
        .tweet {
            padding: 15px;
            border-bottom: 1px solid #2f3336;
            display: flex;
            cursor: pointer;
        }

        .tweet:hover {
            background-color: #080808;
        }

        .tweet-avatar {
            width: 48px;
            height: 48px;
            border-radius: 50%;
            background-color: #333;
            margin-right: 15px;
        }

        .tweet-content {
            flex: 1;
        }

        .tweet-header {
            display: flex;
            align-items: center;
            margin-bottom: 5px;
        }

        .tweet-name {
            font-weight: bold;
            margin-right: 5px;
        }

        .tweet-username, .tweet-time {
            color: #6e767d;
            margin-right: 5px;
        }

        .tweet-text {
            margin-bottom: 10px;
            line-height: 1.4;
        }

        .tweet-engagement {
            display: flex;
            justify-content: space-between;
            max-width: 425px;
            color: #6e767d;
        }

        .engagement-item {
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .engagement-item:hover {
            color: #1da1f2;
        }
    </style>
</head>
<body>
    <!-- Left Sidebar -->
    <div class="sidebar">
        <div class="logo">
            <i class="fab fa-twitter"></i>
        </div>
        <nav>
            <div class="nav-item">
                <i class="fas fa-home"></i>
                <span>Home</span>
            </div>
            <div class="nav-item">
                <i class="fas fa-hashtag"></i>
                <span>Explore</span>
            </div>
            <div class="nav-item">
                <i class="far fa-bell"></i>
                <span>Notifications</span>
            </div>
            <div class="nav-item">
                <i class="far fa-envelope"></i>
                <span>Messages</span>
            </div>
            <div class="nav-item">
                <i class="far fa-bookmark"></i>
                <span>Bookmarks</span>
            </div>
            <div class="nav-item">
                <i class="far fa-user"></i>
                <span>Profile</span>
            </div>
        </nav>
        <button class="tweet-btn">Tweet</button>
    </div>

    <!-- Main Content -->
    <main class="main-content">
        <div class="header">Home</div>
        <div class="tweet-box">
            <textarea class="tweet-input" placeholder="What's happening?"></textarea>
            <div class="tweet-actions">
                <div class="tweet-icons">
                    <i class="far fa-image"></i>
                    <i class="fas fa-film"></i>
                    <i class="far fa-chart-bar"></i>
                    <i class="far fa-smile"></i>
                    <i class="far fa-calendar"></i>
                </div>
                <button class="tweet-submit">Tweet</button>
            </div>
        </div>

        <!-- Sample Tweets -->
        <div class="tweet">
            <img src="IMAGES/Photo.jpg" alt="50px" width="50px">
            <div class="tweet-avatar"></div>
            <div class="tweet-content">
                <div class="tweet-header">
                    <span class="tweet-username">Niyonsaba Lina</span>
                    <span class="tweet-time">· 2h</span>
                </div>
                <div class="tweet-text">
                    This is a sample tweet. Twitter clone built with HTML and CSS!
                </div>
                <div class="tweet-engagement">
                    <div class="engagement-item">
                        <i class="far fa-comment"></i>
                        <span>23</span>
                    </div>
                    <div class="engagement-item">
                        <i class="fas fa-retweet"></i>
                        <span>144</span>
                    </div>
                    <div class="engagement-item">
                        <i class="far fa-heart"></i>
                        <span>1.2K</span>
                    </div>
                    <div class="engagement-item">
                        <i class="far fa-share-square"></i>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <!-- Right Sidebar -->
    <div class="right-sidebar">
        <div class="search-box">
            <i class="fas fa-search"></i>
            <input type="text" placeholder="Search Twitter">
        </div>
        <div class="trends">
            <h2>Trends for you</h2>
            <div class="trend-item">
                <div class="trend-category">Trending in Technology</div>
                <div class="trend-name">#WebDevelopment</div>
                <div class="trend-tweets">50.4K Tweets</div>
            </div>
            <div class="trend-item">
                <div class="trend-category">Trending Worldwide</div>
                <div class="trend-name">#HTML</div>
                <div class="trend-tweets">32.1K Tweets</div>
            </div>
        </div>
    </div>
</body>
</html>
