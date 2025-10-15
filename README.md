<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Delphi reCAPTCHA v2 Test</title>

  <!-- Google reCAPTCHA v2 -->
  <script src="https://www.google.com/recaptcha/api.js" async defer></script>
</head>
<body>
  <h2>Verify you’re human</h2>
  <div class="g-recaptcha" data-sitekey="6LdO2OorAAAAAMXhWusnzWRhD-s8zA6Qjx99LVzb"></div>
  <button onclick="sendToken()">Submit</button>

  <p id="result"></p>

  <script>
    function sendToken() {
      var token = grecaptcha.getResponse();
      if (token.length === 0) {
        document.getElementById("result").innerText = "❌ Please complete the reCAPTCHA!";
      } else {
        document.getElementById("result").innerText = "✅ CAPTCHA complete!";
        // Store token in document for Delphi to read
        document.title = token;
      }
    }
  </script>
</body>
</html>

  </script>
</body>
</html>


