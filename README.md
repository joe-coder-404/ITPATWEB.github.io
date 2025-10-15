<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Delphi reCAPTCHA v2 Test</title>
  <script src="https://www.google.com/recaptcha/api.js" async defer></script>
</head>
<body>
  <h2>Verify you’re human</h2>
  <div class="g-recaptcha" data-sitekey="6LdeqOsrAAAAAPkG8Ht1RhUk-xYvRPCODkmrvcNm"></div>
  <button onclick="sendToken()">Submit</button>
  <p id="result"></p>

  <script>
    function sendToken() {
      var token = grecaptcha.getResponse();
      if (token.length === 0) {
        document.getElementById("result").innerText = "❌ Please complete the reCAPTCHA!";
      } else {
        document.getElementById("result").innerText = "✅ CAPTCHA complete!";
        
        // Write token to a local file using a prompt (Delphi can read this file)
        // For demo purposes, just redirect to a "done" page
        window.location.href = "captcha_done.html?token=" + token;
      }
    }
  </script>
</body>
</html>
