<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Login Page</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: linear-gradient(to bottom, #00008B, #87CEFA);
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      color: white;
      position: relative;
    }
    .copy-link {
      position: absolute;
      top: 20px;
      right: 20px;
      background-color: #004080;
      color: white;
      padding: 10px 15px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-size: 14px;
    }
    .copy-link:hover {
      background-color: #002060;
    }
    .login-container {
      background-color: rgba(0, 0, 0, 0.6);
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
      width: 300px;
      text-align: center;
    }
    .login-container h2 {
      margin-bottom: 20px;
    }
    .login-container input[type="text"],
    .login-container input[type="email"],
    .login-container input[type="password"] {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border: none;
      border-radius: 5px;
    }
    .login-container input[type="submit"] {
      width: 100%;
      padding: 10px;
      margin: 20px 0;
      border: none;
      border-radius: 5px;
      background-color: #004080;
      color: white;
      font-size: 16px;
      cursor: pointer;
    }
    .login-container input[type="submit"]:hover {
      background-color: #002060;
    }
    .error-message {
      color: #ffcccb;
      display: none;
      margin-bottom: 10px;
    }
  </style>
</head>
<body>
  <button class="copy-link" onclick="copyLink()">Copy Link</button>
  <div class="login-container">
    <h2>Login</h2>
    <form id="login-form">
      <input type="text" id="username" placeholder="Username" required>
      <input type="email" id="email" placeholder="Email Address" required>
      <input type="password" id="password" placeholder="Password" required>
      <input type="submit" value="Login">
    </form>
    <div class="error-message" id="error-message"></div>
  </div>

  <script>
    // Function to copy the current page URL to the clipboard
    function copyLink() {
      const url = window.location.href;
      navigator.clipboard.writeText(url).then(() => {
        alert('Link copied to clipboard!');
      }).catch(err => {
        console.error('Failed to copy: ', err);
      });
    }

    // Form submission handler with validation and redirection
    document.getElementById('login-form').addEventListener('submit', function(event) {
      event.preventDefault();
      const username = document.getElementById('username').value.trim();
      const email = document.getElementById('email').value.trim();
      const password = document.getElementById('password').value.trim();
      const errorMessage = document.getElementById('error-message');

      if (username === '' || email === '' || password === '') {
        errorMessage.textContent = 'All fields are required.';
        errorMessage.style.display = 'block';
      } else if (!validateEmail(email)) {
        errorMessage.textContent = 'Please enter a valid email address.';
        errorMessage.style.display = 'block';
      } else {
        errorMessage.style.display = 'none';
        // Redirect to the user's page (e.g., profile.html)
        window.location.href = 'profile.html';
      }
    });

    // Basic email validation function
    function validateEmail(email) {
      const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return emailPattern.test(email);
    }
  </script>
</body>
</html>
