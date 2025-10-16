<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Delphi reCAPTCHA v2 Test</title>
  <script src="https://www.google.com/recaptcha/api.js" async defer></script>
  <style>
    #result { margin-top: 10px; font-weight: bold; }
  </style>
</head>
<body>
  <h2>Verify you’re human</h2>
  <div class="g-recaptcha" data-sitekey="6LdeqOsrAAAAAPkG8Ht1RhUk-xYvRPCODkmrvcNm"></div>
  <button onclick="sendToken()">Submit</button>
  <p id="result"></p>

  <script>
    // Send token to Delphi via redirect
    function sendToken() {
      var token = grecaptcha.getResponse();
      if (token.length === 0) {
        document.getElementById("result").innerText = "❌ Please complete the reCAPTCHA!";
      } else {
        document.getElementById("result").innerText = "✅ CAPTCHA complete!";
        // Redirect to Delphi-handled page with token
       window.location.hash = "token=" + token;
      }
    }

    // Function to reset the CAPTCHA (can be called from Delphi)
    function resetCaptcha() {
      grecaptcha.reset();
      document.getElementById("result").innerText = "";
    }
  </script>
</body>
</html>
