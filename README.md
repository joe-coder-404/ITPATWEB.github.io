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
    function sendToken() {
      var token = grecaptcha.getResponse();
      if (token.length === 0) {
        document.getElementById("result").innerText = "❌ Please complete the reCAPTCHA!";
      } else {
        document.getElementById("result").innerText = "✅ CAPTCHA complete!";
        var encodedToken = encodeURIComponent(token);

        // Load captcha_done.html without redirecting
        fetch("captcha_done.html?token=" + encodedToken)
          .then(response => response.text())
          .then(html => {
            // Replace current body with the HTML of captcha_done.html
            document.body.innerHTML = html;
          })
          .catch(err => {
            document.getElementById("result").innerText = "⚠️ Error loading captcha_done.html";
            console.error(err);
          });
      }
    }

    function resetCaptcha() {
      grecaptcha.reset();
      document.getElementById("result").innerText = "";
    }
  </script>
</body>
</html>
