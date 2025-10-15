<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Delphi reCAPTCHA Test</title>

  <!-- Google reCAPTCHA Enterprise -->
  <script src="https://www.google.com/recaptcha/enterprise.js?render=6LdO2OorAAAAAMXhWusnzWRhD-s8zA6Qjx99LVzb"></script>
</head>
<body>
  <h1>Delphi + reCAPTCHA Test</h1>
  
  <form id="loginForm">
    <input type="text" placeholder="Username" required><br><br>
    <input type="password" placeholder="Password" required><br><br>
    <button type="submit">Login</button>
  </form>

  <div id="status"></div>

  <script>
    document.getElementById('loginForm').addEventListener('submit', async function(e) {
      e.preventDefault(); // stop default form submission

      // Get reCAPTCHA token
      grecaptcha.enterprise.ready(async () => {
        const token = await grecaptcha.enterprise.execute('6LdO2OorAAAAAMXhWusnzWRhD-s8zA6Qjx99LVzb', {action: 'LOGIN'});
        })
        .then(res => res.json())
        .then(data => {
          if(data.success) {
            document.getElementById('status').innerText = "✅ User verified!";
            // Proceed with login logic here
          } else {
            document.getElementById('status').innerText = "❌ Failed verification!";
          }
        })
        .catch(err => {
          document.getElementById('status').innerText = "⚠ Error: " + err;
        });
      });
    });
  </script>
</body>
</html>


